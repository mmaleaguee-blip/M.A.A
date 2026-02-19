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

table { width: 100%; border-collapse: collapse; font-size: 14px; table-layout: fixed; background: #0e1217; }
th, td { padding: 8px; text-align: center; word-wrap: break-word; background: #111827; color: #fff; border-bottom: 1px solid #1f2937; }
.team-cell { display: flex; align-items: center; gap: 6px; justify-content: flex-start; overflow: hidden; }
.team-cell img { width: 22px; height: 22px; border-radius: 50%; object-fit: cover; flex-shrink: 0; }
.knockout-image{
  width:100%;
  height:auto;
  display:block;
  border-radius:0;
}

</style>
</head>
<body>

<header>MAA League</header>

<nav>
  <button class="active" onclick="showMatches()">Matches</button>
  <button onclick="showStandings()">Standings</button>
  <button onclick="showKnockout()">Knockout</button>
</nav>

<div id="matches" class="section"></div>
<div id="standings" class="section" style="display:none;"></div>
<div id="knockout" class="section" style="display:none;"></div>

<script>

// ======== TEAMS AND IMAGES ========
const teamsImg = {
  sarhad:"sarhad.png",
  matin:"matin.jpg",
  ramin:"ramin.jpg",
  masud:"masud.jpg",
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

const rounds = [
  // r1

  [["meer","ramin","-","-"],["masud","kaka","-","-"],["ahmed88","sarhad","-","-"],["swra","humar","-","-"],["marwan","matin","-","-"],["esmahil","azhdar","-","-"],["hamastar","ahmedzlatan","-","-"]],
//r2
    [["meer","masud","-","-"],["ahmed88","ramin","-","-"],["swra","kaka","-","-"],["marwan","sarhad","-","-"],["esmahil","humar","-","-"],["hamastar","matin","-","-"],["ahmedzlatan","azhdar","-","-"]],
  //r3
  [["meer","kaka","-","-"],["ramin","sarhad","-","-"],["masud","humar","-","-"],["ahmed88","matin","-","-"],["swra","azhdar","-","-"],["marwan","ahmedzlatan","-","-"],["esmahil","hamastar","-","-"]],
  //r4
  [["meer","sarhad","-","-"],["kaka","humar","-","-"],["ramin","matin","-","-"],["masud","azhdar","-","-"],["ahmed88","ahmedzlatan","-","-"],["swra","hamastar","-","-"],["marwan","esmahil","-","-"]],
  //r5
  [["meer","humar","-","-"],["sarhad","matin","-","-"],["kaka","azhdar","-","-"],["ramin","ahmedzlatan","-","-"],["masud","hamastar","-","-"],["ahmed88","esmahil","-","-"],["swra","marwan","-","-"]],
  //r6
  [["meer","matin","-","-"],["humar","azhdar","-","-"],["sarhad","ahmedzlatan","-","-"],["kaka","hamastar","-","-"],["ramin","esmahil","-","-"],["masud","marwan","-","-"],["ahmed88","swra","-","-"]],
  //r7
  [["meer","azhdar","-","-"],["matin","ahmedzlatan","-","-"],["humar","hamastar","-","-"],["sarhad","esmahil","-","-"],["kaka","marwan","-","-"],["ramin","swra","-","-"],["masud","ahmed88","-","-"]],
  //r8
  [["meer","ahmedzlatan","-","-"],["azhdar","hamastar","-","-"],["matin","esmahil","-","-"],["humar","marwan","-","-"],["sarhad","swra","-","-"],["kaka","ahmed88","-","-"],["ramin","masud","-","-"]],
  //r9
  [["meer","hamastar","-","-"],["ahmedzlatan","esmahil","-","-"],["azhdar","marwan","-","-"],["matin","swra","-","-"],["humar","ahmed88","-","-"],["sarhad","masud","-","-"],["kaka","ramin","-","-"]],
  //r10
  [["meer","esmahil","-","-"],["hamastar","marwan","-","-"],["ahmedzlatan","swra","-","-"],["azhdar","ahmed88","-","-"],["matin","masud","-","-"],["humar","ramin","-","-"],["sarhad","kaka","-","-"]],
  //r11
  [["meer","marwan","-","-"],["esmahil","swra","-","-"],["hamastar","ahmed88","-","-"],["ahmedzlatan","masud","-","-"],["azhdar","ramin","-","-"],["matin","kaka","-","-"],["humar","sarhad","-","-"]],
  //r12
  [["meer","swra","-","-"],["marwan","ahmed88","-","-"],["esmahil","masud","-","-"],["hamastar","ramin","-","-"],["ahmedzlatan","kaka","-","-"],["azhdar","sarhad","-","-"],["matin","humar","-","-"]],
  //r13

  [["meer","ahmed88","-","-"],["swra","masud","-","-"],["marwan","ramin","-","-"],["esmahil","kaka","-","-"],["hamastar","sarhad","-","-"],["ahmedzlatan","humar","-","-"],["azhdar","matin","-","-"]]
];

// ======== GENERATE MATCHES ========
const matchesDiv = document.getElementById("matches");
rounds.forEach((round,i)=>{
  const roundTitle=document.createElement("div");
  roundTitle.className="round-title";
  roundTitle.textContent=`Round ${i+1}`;
  matchesDiv.appendChild(roundTitle);

  round.forEach(match=>{
    const [t1,t2,s1,s2]=match;
    const matchDiv=document.createElement("div");
    matchDiv.className="match";
    matchDiv.innerHTML=`<div class="team"><img src="${teamsImg[t1]}"> ${t1}</div>
                        <div class="vs">VS</div>
                        <div class="team"><img src="${teamsImg[t2]}"> ${t2}</div>`;
    matchesDiv.appendChild(matchDiv);

    const detailsDiv=document.createElement("div");
    detailsDiv.className="details";
    detailsDiv.innerHTML=`Time<div class="result">${s1} - ${s2}</div>`;
    matchesDiv.appendChild(detailsDiv);
  });
});

// ======== KNOCKOUT SECTION ========
const knockoutDiv=document.getElementById("knockout");
knockoutDiv.innerHTML=`<div class="round-title">round 8</div>
<img src="r88.jpg" class="knockout-image">`;

// ======== CALCULATE STANDINGS (FIXED) ========
const standingsDiv=document.getElementById("standings");
function calcStandings(){
  const teamStats={};
  Object.keys(teamsImg).forEach(team=>{
    teamStats[team]={P:0,Pts:0,GF:0,GA:0,GD:0};
  });

  rounds.forEach(round=>{
    round.forEach(match=>{
      const [t1,t2,s1,s2]=match;
      const g1=parseInt(s1);
      const g2=parseInt(s2);

      // Only count match if scores are numbers
      if(!isNaN(g1) && !isNaN(g2)){
        teamStats[t1].P++; teamStats[t2].P++;
        teamStats[t1].GF+=g1; teamStats[t1].GA+=g2;
        teamStats[t2].GF+=g2; teamStats[t2].GA+=g1;
        teamStats[t1].GD=teamStats[t1].GF-teamStats[t1].GA;
        teamStats[t2].GD=teamStats[t2].GF-teamStats[t2].GA;
        if(g1>g2){ teamStats[t1].Pts+=3; }
        else if(g1<g2){ teamStats[t2].Pts+=3; }
        else{ teamStats[t1].Pts+=1; teamStats[t2].Pts+=1; }
      }
    });
  });

  const sortedTeams=Object.keys(teamStats).sort((a,b)=>{
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
  knockoutDiv.style.display="none";
  document.querySelectorAll("nav button").forEach(btn=>btn.classList.remove("active"));
  document.querySelectorAll("nav button")[0].classList.add("active");
}
function showStandings(){
  matchesDiv.style.display="none";
  standingsDiv.style.display="block";
  knockoutDiv.style.display="none";
  document.querySelectorAll("nav button").forEach(btn=>btn.classList.remove("active"));
  document.querySelectorAll("nav button")[1].classList.add("active");
}
function showKnockout(){
  matchesDiv.style.display="none";
  standingsDiv.style.display="none";
  knockoutDiv.style.display="block";
  document.querySelectorAll("nav button").forEach(btn=>btn.classList.remove("active"));
  document.querySelectorAll("nav button")[2].classList.add("active");
}

</script>
</body>
</html>
