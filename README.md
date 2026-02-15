 
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>MAA League</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial, Helvetica, sans-serif;}
html,body{width:100%;overflow-x:hidden;background:#0e1217;color:#fff;}
body{max-width:480px;margin:auto;}
header{background:#111827;padding:15px;text-align:center;font-size:20px;font-weight:bold;border-bottom:1px solid #1f2937;}
nav{display:flex;background:#111827;}
nav button{flex:1;padding:12px;background:none;border:none;color:#9ca3af;font-size:14px;cursor:pointer;}
nav button.active{color:#fff;border-bottom:2px solid #22c55e;}
.section{padding:15px;}
.round-title{margin:15px 0 8px;font-weight:bold;color:#22c55e;}
.match{background:#111827;border-radius:10px;padding:12px;margin-bottom:6px;display:flex;align-items:center;justify-content:space-between;font-size:14px;}
.team{flex:1;display:flex;align-items:center;justify-content:center;gap:6px;min-width:0;}
.team img{width:26px;height:26px;border-radius:50%;object-fit:cover;}
.vs{width:50px;text-align:center;color:#9ca3af;font-weight:bold;}
.details{text-align:center;font-size:12px;margin-bottom:10px;color:#9ca3af;}
.result{font-weight:bold;color:#22c55e;margin-top:2px;}
/* STANDINGS FIX */
table { width: 100%; border-collapse: collapse; font-size: 14px; table-layout: fixed; background: #0e1217; }
th, td { padding: 8px; text-align: center; word-wrap: break-word; background: #111827; color: #fff; border-bottom: 1px solid #1f2937; }
.team-cell { display: flex; align-items: center; gap: 6px; justify-content: flex-start; overflow: hidden; }
.team-cell img { width: 22px; height: 22px; border-radius: 50%; object-fit: cover; flex-shrink: 0; }
</style>
</head>
<body>

<header>MAA League</header>
<nav>
  <button class="active" onclick="showMatches()">Matches</button>
  <button onclick="showStandings()">Standings</button>
</nav>

<div id="matches" class="section"></div>
<div id="standings" class="section" style="display:none;"></div>

<script>
// ======== TEAMS AND IMAGES ========
const teamsImg = {
  ahmed88:"ahmed88.jpg",
  ahmedzlatan:"ahmedzlatan.jpg",
  marwan:"marwan.jpg",
  swra:"swwra.jpg",
  meer:"meeer.jpg",
  kaka:"kaka.jpg",
  azhdar:"azhdar.jpg",
  esmahil:"esmahil.jpg",
  humar:"humar.jpg",
  hamastar:"hamast4r.jpg"
};

// ======== MATCHES DATA ========
const rounds = [
  [["ahmed88","marwan","1","2"],["ahmedzlatan","swra","1","3"],["meer","kaka","3","2"],["azhdar","esmahil","4","1"],["humar","hamastar","0","5"]],
 
  [["ahmed88","ahmedzlatan","2","0"],["meer","marwan","4","5"],["azhdar","swra","4","3"],["humar","kaka","1","5"],["hamastar","esmahil","3","2"]],
 
  [["ahmed88","swra","2","2"],["marwan","kaka","1","2"],["ahmedzlatan","esmahil","3","6"],["meer","hamastar","2","4"],["azhdar","humar","3","4"]],
 
  [["ahmed88","kaka","6","2"],["swra","esmahil","2","0"],["marwan","hamastar","6","1"],["ahmedzlatan","humar","5","1"],["meer","azhdar","2","1"]],
 
  [["ahmed88","esmahil","2","4"],["kaka","hamastar","1","1"],["swra","humar","-","-"],["marwan","azhdar","5","3"],["ahmedzlatan","meer","5","4"]],
 
  [["ahmed88","hamastar","-","-"],["esmahil","humar","-","-"],["kaka","azhdar","-","-"], ["swra","meer","3","3"],["marwan","ahmedzlatan","-","-"]],
  [["ahmed88","humar","-","-"],["hamastar","azhdar","3","3"],["esmahil","meer","6","2"],["kaka","ahmedzlatan","-","-"],["swra","marwan","-","-"]],
  [["ahmed88","azhdar","-","-"],["humar","meer","-","-"],["hamastar","ahmedzlatan","-","-"],["esmahil","marwan","-","-"],["kaka","swra","-","-"]],
  [["ahmed88","meer","4","4"],["azhdar","ahmedzlatan","-","-"],["humar","marwan","-","-"],["hamastar","swra","-","-"],["esmahil","kaka","-","-"]]
];

// ======== GENERATE MATCHES ========
const matchesDiv = document.getElementById("matches");
rounds.forEach((round,i)=>{
  const roundTitle = document.createElement("div");
  roundTitle.className="round-title";
  roundTitle.textContent=`Round ${i+1}`;
  matchesDiv.appendChild(roundTitle);

  round.forEach(match=>{
    const [t1,t2,s1,s2] = match;
    const matchDiv=document.createElement("div");
    matchDiv.className="match";
    matchDiv.innerHTML=`<div class="team"><img src="${teamsImg[t1]}"> ${t1}</div>
                        <div class="vs">VS</div>
                        <div class="team"><img src="${teamsImg[t2]}"> ${t2}</div>`;
    matchesDiv.appendChild(matchDiv);

    const detailsDiv=document.createElement("div");
    detailsDiv.className="details";
    detailsDiv.innerHTML=`Time<div class="result">${s1==='-'?'-':s1} - ${s2==='-'?'-':s2}</div>`;
    matchesDiv.appendChild(detailsDiv);
  });
});

// ======== CALCULATE STANDINGS ========
const standingsDiv=document.getElementById("standings");
function calcStandings(){
  const teamStats={};
  Object.keys(teamsImg).forEach(team=>{
    teamStats[team]={P:0,Pts:0,GF:0,GA:0,GD:0};
  });

  rounds.forEach(round=>{
    round.forEach(match=>{
      const [t1,t2,s1,s2] = match;
      if(s1!=='-' && s2!=='-'){
        const g1=parseInt(s1), g2=parseInt(s2);
        teamStats[t1].P++;
        teamStats[t2].P++;
        teamStats[t1].GF+=g1;
        teamStats[t1].GA+=g2;
        teamStats[t2].GF+=g2;
        teamStats[t2].GA+=g1;
        teamStats[t1].GD=teamStats[t1].GF-teamStats[t1].GA;
        teamStats[t2].GD=teamStats[t2].GF-teamStats[t2].GA;
        if(g1>g2){teamStats[t1].Pts+=3;}
        else if(g1<g2){teamStats[t2].Pts+=3;}
        else{teamStats[t1].Pts+=1;teamStats[t2].Pts+=1;}
      }
    });
  });

  // Sort by points then GD then GF
  const sortedTeams = Object.keys(teamStats).sort((a,b)=>{
    if(teamStats[b].Pts!==teamStats[a].Pts) return teamStats[b].Pts-teamStats[a].Pts;
    if(teamStats[b].GD!==teamStats[a].GD) return teamStats[b].GD-teamStats[a].GD;
    return teamStats[b].GF-teamStats[a].GF;
  });

  let tableHTML="<table><tr><th>#</th><th>Team</th><th>P</th><th>GF</th><th>GA</th><th>+/-</th><th>Pts</th></tr>";
  sortedTeams.forEach((team,i)=>{
    tableHTML+=`<tr>
      <td>${i+1}</td>
      <td class="team-cell"><img src="${teamsImg[team]}"> ${team}</td>
      <td>${teamStats[team].P}</td>
      <td>${teamStats[team].GF}</td>
      <td>${teamStats[team].GA}</td>
      <td>${teamStats[team].GD}</td>
      <td>${teamStats[team].Pts}</td>
    </tr>`;
  });
  tableHTML+="</table>";
  standingsDiv.innerHTML=tableHTML;
}
calcStandings();

// ======== TOGGLE ========
function showMatches(){
  matchesDiv.style.display="block";
  standingsDiv.style.display="none";
  document.querySelectorAll("nav button")[0].classList.add("active");
  document.querySelectorAll("nav button")[1].classList.remove("active");
}
function showStandings(){
  matchesDiv.style.display="none";
  standingsDiv.style.display="block";
  document.querySelectorAll("nav button")[1].classList.add("active");
  document.querySelectorAll("nav button")[0].classList.remove("active");
}
</script>

</body>
</html>
