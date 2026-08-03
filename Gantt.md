<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>EDIDRIFT Gantt Chart</title>
<style>
  body {
    font-family: Arial, sans-serif;
  }

  .gantt {
    width: 100%;
    max-width: 900px;
    margin: 20px auto;
  }

  .months {
    display: grid;
    grid-template-columns: 150px repeat(10, 1fr);
    margin-bottom: 5px;
  }

  .months div {
    text-align: center;
    font-size: 12px;
    color: #333;
  }

  .row {
    display: grid;
    grid-template-columns: 150px repeat(10, 1fr);
    align-items: center;
    margin: 6px 0;
  }

  .label {
    font-size: 13px;
    text-align: right;
    padding-right: 10px;
  }

  .bar {
    height: 18px;
    border-radius: 6px;
  }

  .t1 { background: #d9d9d9; grid-column: 2 / 7; }
  .t2 { background: #bfbfbf; grid-column: 3 / 8; }
  .t3 { background: #999999; grid-column: 4 / 10; }
  .t4 { background: #666666; grid-column: 6 / 12; }

  .caption {
    text-align: center;
    font-size: 13px;
    margin-top: 10px;
    color: #444;
  }
</style>
</head>

<body>

<div class="gantt">

  <!-- Months -->
  <div class="months">
    <div></div>
    <div>M1</div><div>M2</div><div>M3</div><div>M4</div><div>M5</div>
    <div>M6</div><div>M7</div><div>M8</div><div>M9</div><div>M10</div>
  </div>

  <!-- Tasks -->
  <div class="row">
    <div class="label">Task 1: Lagrangian advection</div>
    <div class="bar t1"></div>
  </div>

  <div class="row">
    <div class="label">Task 2: Wave spectra integration</div>
    <div class="bar t2"></div>
  </div>

  <div class="row">
    <div class="label">Task 3: Interactive visualisation</div>
    <div class="bar t3"></div>
  </div>

  <div class="row">
    <div class="label">Task 4: Documentation & training</div>
    <div class="bar t4"></div>
  </div>

  <div class="caption">
    Figure: Indicative 10-month implementation timeline for the EDIDRIFT project.
  </div>

</div>

</body>
</html>