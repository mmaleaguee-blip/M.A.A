<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
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
header{
  text-align:center;
  padding:15px;
  background:#111827;
  font-size:22px;
  font-weight:bold;
}
.tabs{
  display:flex;
  justify-content:center;
  gap:12px;
  padding:10px;
  background:#0b1220;
}
.tabs button{
  padding:8px 20px;
  border:none;
  border-radius:20px;
  background:#1f2933;
  color:#fff;
  cursor:pointer;
  font-size:14px;
}
.tabs button.active{
  background:#38bdf8;
  color:#000;
}
.container{
  padding:15px;
}
.round{
  margin-bottom:20px;
}
.round h3{
  color:#38bdf8;
  margin-bottom:8px;
}
.match{
  display:flex;
  justify-content:space-between;
  padding:8px 10px;
  background:#0e1625;
  border-radius:6px;
  margin-bottom:6px;
  font-size:14px;
}
table{
  width:100%;
  border-collapse:collapse;
  font-size:14px;
}
th, td{
  padding:10px;
  text-align:center;
}
th{
  background:#0e1625;
}
tr:nth-child(even){
  background:#0e1625;
}
.hidden{
  display:none;
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
<div class="match"><span>ahmed88</span><span>vs</span><span>marwan</span></div>
<div class="match"><span>ahmedzlatan</span><span>vs</span><span>swra</span></div>
<div class="match"><span>meer</span><span>vs</span><span>kaka</span></div>
<div class="match"><span>azhdar</span><span>vs</span><span>esmahil</span></div>
<div class="match"><span>humar</span><span>vs</span><span>hamastar</span></div>
</div>

<div class="round">
<h3>Round 2</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>ahmedzlatan</span></div>
<div class="match"><span>meer</span><span>vs</span><span>marwan</span></div>
<div class="match"><span>azhdar</span><span>vs</span><span>swra</span></div>
<div class="match"><span>humar</span><span>vs</span><span>kaka</span></div>
<div class="match"><span>hamastar</span><span>vs</span><span>esmahil</span></div>
</div>

<div class="round">
<h3>Round 3</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>swra</span></div>
<div class="match"><span>marwan</span><span>vs</span><span>kaka</span></div>
<div class="match"><span>ahmedzlatan</span><span>vs</span><span>esmahil</span></div>
<div class="match"><span>meer</span><span>vs</span><span>hamastar</span></div>
<div class="match"><span>azhdar</span><span>vs</span><span>humar</span></div>
</div>

<div class="round">
<h3>Round 4</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>kaka</span></div>
<div class="match"><span>swra</span><span>vs</span><span>esmahil</span></div>
<div class="match"><span>marwan</span><span>vs</span><span>hamastar</span></div>
<div class="match"><span>ahmedzlatan</span><span>vs</span><span>humar</span></div>
<div class="match"><span>meer</span><span>vs</span><span>azhdar</span></div>
</div>

<div class="round">
<h3>Round 5</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>esmahil</span></div>
<div class="match"><span>kaka</span><span>vs</span><span>hamastar</span></div>
<div class="match"><span>swra</span><span>vs</span><span>humar</span></div>
<div class="match"><span>marwan</span><span>vs</span><span>azhdar</span></div>
<div class="match"><span>ahmedzlatan</span><span>vs</span><span>meer</span></div>
</div>

<div class="round">
<h3>Round 6</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>hamastar</span></div>
<div class="match"><span>esmahil</span><span>vs</span><span>humar</span></div>
<div class="match"><span>kaka</span><span>vs</span><span>azhdar</span></div>
<div class="match"><span>swra</span><span>vs</span><span>meer</span></div>
<div class="match"><span>marwan</span><span>vs</span><span>ahmedzlatan</span></div>
</div>

<div class="round">
<h3>Round 7</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>humar</span></div>
<div class="match"><span>hamastar</span><span>vs</span><span>azhdar</span></div>
<div class="match"><span>esmahil</span><span>vs</span><span>meer</span></div>
<div class="match"><span>kaka</span><span>vs</span><span>ahmedzlatan</span></div>
<div class="match"><span>swra</span><span>vs</span><span>marwan</span></div>
</div>

<div class="round">
<h3>Round 8</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>azhdar</span></div>
<div class="match"><span>humar</span><span>vs</span><span>meer</span></div>
<div class="match"><span>hamastar</span><span>vs</span><span>ahmedzlatan</span></div>
<div class="match"><span>esmahil</span><span>vs</span><span>marwan</span></div>
<div class="match"><span>kaka</span><span>vs</span><span>swra</span></div>
</div>

<div class="round">
<h3>Round 9</h3>
<div class="match"><span>ahmed88</span><span>vs</span><span>meer</span></div>
<div class="match"><span>azhdar</span><span>vs</span><span>ahmedzlatan</span></div>
<div class="match"><span>humar</span><span>vs</span><span>marwan</span></div>
<div class="match"><span>hamastar</span><span>vs</span><span>swra</span></div>
<div class="match"><span>esmahil</span><span>vs</span><span>kaka</span></div>
</div>

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
