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
  padding:14px;
  background:#111827;
  font-size:20px;
  font-weight:bold;
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
  font-size:15px;
  cursor:pointer;
}
.tabs button.active{
  color:#38bdf8;
  border-bottom:3px solid #38bdf8;
}

/* CONTENT */
.container{
  padding:12px;
}

/* ROUNDS */
.round{
  margin-bottom:18px;
}
.round h3{
  font-size:15px;
  margin-bottom:8px;
  color:#38bdf8;
}

/* MATCH CARD */
.match{
  background:#111827;
  border-radius:10px;
  padding:12px;
  margin-bottom:8px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  font-size:14px;
}
.match span{
  width:40%;
  text-align:center;
}
.match span:nth-child(2){
  width:20%;
  color:#9ca3af;
}

/* STANDINGS */
table{
  width:100%;
  border-collapse:collapse;
  font-size:14px;
}
th, td{
  padding:10px 6px;
  text-align:center;
}
th{
  background:#111827;
  color:#9ca3af;
}
tr{
  background:black;
}
tr:not(:last-child){
  border-bottom:1px solid #1f2933;
}

.hidden{
  display:none;
}

/* MOBILE RESPONSIVE */
@media screen and (max-width: 600px) {
  header{
    font-size:18px;
    padding:10px;
  }
  .tabs button{
    font-size:13px;
    padding:8px 0;
  }
  .match{
    flex-direction: column;
    font-size:13px;
    padding:8px;
  }
  .match span{
    width:100%;
    margin:4px 0;
  }
  .match span:nth-child(2){
    width:100%;
  }
  .round h3{
    font-size:14px;
  }
  table, th, td{
    font-size:12px;
  }
  .container{
    padding:8px;
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

<div class="round">
<h3>Round 3</h3>
<div class="match"><span>ahmed88</span><span>VS</span><span>swra</span></div>
<div class="match"><span>marwan</span><span>VS</span><span>kaka</span></div>
<div class="match"><span>ahmedzlatan</span><span>VS</span><span>esmahil</span></div>
<div class="match"><span>meer</span><span>VS</span><span>hamastar</span></div>
<div class="match"><span>azhdar</span><span>VS</span><span>humar</span></div>
</div>

<!-- Remaining rounds ... keep as-is -->

</div>

<!-- STANDINGS -->
<div id="standings" class="hidden">
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
