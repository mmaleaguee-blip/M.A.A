<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>MAA League</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family: Arial, Helvetica, sans-serif;
}
body{
  background:#0e1217;
  color:#fff;
}

/* HEADER */
header{
  text-align:center;
  padding:16px 10px;
  background:#111827;
  font-size:22px;
  font-weight:bold;
  letter-spacing:1px;
}

/* TABS */
.tabs{
  display:flex;
  background:#0b1220;
}
.tabs button{
  flex:1;
  padding:12px 0;
  border:none;
  background:none;
  color:#9ca3af;
  font-size:16px;
  cursor:pointer;
  transition: 0.3s;
}
.tabs button:hover{
  color:#38bdf8;
}
.tabs button.active{
  color:#38bdf8;
  border-bottom:3px solid #38bdf8;
}

/* CONTAINER */
.container{
  padding:14px 10px;
}

/* ROUNDS */
.round{
  margin-bottom:20px;
}
.round h3{
  font-size:16px;
  margin-bottom:10px;
  color:#38bdf8;
  border-left:4px solid #38bdf8;
  padding-left:6px;
}

/* MATCH CARD */
.match{
  background:#111827;
  border-radius:12px;
  padding:12px 8px;
  margin-bottom:10px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  font-size:15px;
  box-shadow:0 2px 6px rgba(0,0,0,0.5);
  transition:0.2s;
}
.match:hover{
  background:#1f2933;
}
.match span{
  width:40%;
  text-align:center;
  overflow-wrap: break-word;
}
.match span:nth-child(2){
  width:20%;
  color:#9ca3af;
}

/* STANDINGS TABLE */
.standings-wrapper{
  overflow-x:auto;
}
table{
  width:100%;
  border-collapse:collapse;
  font-size:15px;
  min-width:300px;
}
th, td{
  padding:10px 8px;
  text-align:center;
}
th{
  background:#111827;
  color:#9ca3af;
}
tr{
  background:#000;
}
tr:not(:last-child){
  border-bottom:1px solid #1f2933;
}

/* HIDDEN */
.hidden{
  display:none;
}

/* MOBILE RESPONSIVE */
@media screen and (max-width:600px){
  header{
    font-size:20px;
    padding:12px 8px;
  }
  .tabs button{
    font-size:14px;
    padding:10px 0;
  }
  .round h3{
    font-size:15px;
  }
  .match{
    flex-direction:column;
    font-size:14px;
    padding:10px;
  }
  .match span{
    width:100%;
    margin:4px 0;
  }
  .match span:nth-child(2){
    width:100%;
  }
  table, th, td{
    font-size:13px;
  }
  .container{
    padding:10px 6px;
  }
}
</style>
</head>

<body>

<header>🏆 MAA League</header>

<div class="tabs">
  <button class="active" onclick="showMatches()">Matches</button>
  <button onclick="showStandings()">Standings</button>
</div>

<div class="container">

<!-- MATCHES -->
<div id="matches">

<div class="round">
<h3>Round 1</h3>
<div class="match"><span>ahmed88</span><span>VS</span><span>marwan</span></div>
<div class="match"><span>ahmedzlatan</span><span>VS</span><span>swra</span></div>
<div class="match"><span>meer</span><span>VS</span><span>kaka</span></div>
<div class="match"><span>azhdar</span><span>VS</span><span>esmahil</span></div>
<div class="match"><span>humar</span><span>VS</span><span>hamastar</span></div>
</div>

<div class="round">
<h3>Round 2</h3>
<div class="match"><span>ahmed88</span><span>VS</span><span>ahmedzlatan</span></div>
<div class="match"><span>meer</span><span>VS</span><span>marwan</span></div>
<div class="match"><span>azhdar</span><span>VS</span><span>swra</span></div>
<div class="match"><span>humar</span><span>VS</span><span>kaka</span></div>
<div class="match"><span>hamastar</span><span>VS</span><span>esmahil</span></div>
</div>

<!-- Add remaining rounds as before -->

</div>

<!-- STANDINGS -->
<div id="standings" class="hidden">
<div class="standings-wrapper">
<table>
<tr><th>Team</th><th>P</th><th>Pts</th></tr>
<tr><td>ahmed88</td><td>0</td><td>0</td></tr>
<tr><td>meer</td><td>0</td><td>0</td></tr>
<tr><td>azhdar</td><td>0</td><td>0</td></tr>
<tr><td>humar</td><td>0</td><td>0</td></tr>
<tr><td>hamastar</td><td>0</td><td>0</td></tr>
<tr><td>esmahil</td><td>0</td><td>0</td></tr>
<tr><td>kaka</td><td>0</td><td>0</td></tr>
<tr><td>swra</td><td>0</td><td>0</td></tr>
<tr><td>marwan</td><td>0</td><td>0</td></tr>
<tr><td>ahmedzlatan</td><td>0</td><td>0</td></tr>
</table>
</div>
</div>

</div>

<script>
function showMatches(){
  matches.classList.remove("hidden");
  standings.classList.add("hidden");
  document.querySelectorAll(".tabs button")[0].classList.add("active");
  document.querySelectorAll(".tabs button")[1].classList.remove("active");
}
function showStandings(){
  matches.classList.add("hidden");
  standings.classList.remove("hidden");
  document.querySelectorAll(".tabs button")[1].classList.add("active");
  document.querySelectorAll(".tabs button")[0].classList.remove("active");
}
</script>

</body>
</html>
