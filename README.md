# Data-Analysis_Project.
This Project Title "Data Analysis_Project" and include in Assignment by the data visualization course, SQL, Python library (Numpy), and MS Excel in full information and knowledge by the assignment session. 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Global Data Analysis Dashboard</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>🌍 Global Data Analysis Dashboard</h1>

  <div class="chart-container">
    <canvas id="gdpChart"></canvas>
  </div>

  <button onclick="fetchData()">Analyze Data</button>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="script.js"></script>
</body>
</html>
# Css code. 
body {
  background-color: #f4f8fb;
  font-family: Arial, sans-serif;
  text-align: center;
  color: #333;
}
h1 {
  margin-top: 30px;
}
.chart-container {
  width: 80%;
  margin: auto;
  padding: 20px;
}
button {
  background: #0078d7;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
button:hover {
  background: #005fa3;
}
# jscript code
async function fetchData() {
  const res = await fetch('/api/data');
  const json = await res.json();
  renderChart(json);
}

function renderChart(data) {
  const ctx = document.getElementById('gdpChart');
  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: data.countries,
      datasets: [{
        label: 'GDP (in Trillions)',
        data: data.gdp,
        backgroundColor: 'rgba(75,192,192,0.6)',
      }]
    }
  });
}
