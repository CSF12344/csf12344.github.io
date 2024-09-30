# csf12344.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ROI Calculator</title>
  <style>
    /* CSS Styles */
    #roi-calculator-container {
      font-family: 'Muli', sans-serif;
      max-width: 400px;
      margin: 0 auto;
      padding: 30px;
      text-align: center;
      border: 2px solid #012533; /* Primary color */
      border-radius: 5px;
      background-color: #83e10f; /* Secondary color */
    }

    #roi-calculator-container h1, #roi-calculator-container h2 {
      color: #012533; /* Primary color */
    }

    #roi-calculator-container label {
      display: block;
      margin-top: 10px;
      text-align: left;
    }

    #roi-calculator-container input {
      width: 100%;
      padding: 5px;
      border: 1px solid #ccc;
      border-radius: 3px;
    }

    #roi-calculator-container button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #012533; /* Primary color */
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    #roi-calculator-container h3 {
      margin-top: 30px;
      color: #012533; /* Primary color */
    }

    #roi-calculator-container p {
      margin-top: 10px;
      text-align: center;
    }

    #roi-calculator-container p span.result {
      font-weight: bold;
    }
  </style>
  <script>
    function calculateROI() {
      // Get the input values
      var averageClientValue = parseFloat(document.getElementById("averageClientValue").value);
      var missedCallsPerMonth = parseFloat(document.getElementById("missedCallsPerMonth").value);
      var averageCloseRate = parseFloat(document.getElementById("averageCloseRate").value);
      var agencyFee = 297; // Fixed agency fee

      // Validate input
      if (isNaN(averageClientValue) || isNaN(missedCallsPerMonth) || isNaN(averageCloseRate)) {
        alert("Please fill in all the fields with valid numbers.");
        return;
      }

      // Calculate monthly left on the table
      var monthlyLeftOnTable = missedCallsPerMonth * averageClientValue * (averageCloseRate / 100);

      // Calculate ROI
      var netProfit = monthlyLeftOnTable - agencyFee;
      var roi = (netProfit / agencyFee) * 100;

      // Display results
      document.getElementById("monthlyLeftOnTable").innerHTML = "<span class='result'>$" + monthlyLeftOnTable.toFixed(2) + "</span>";
      document.getElementById("amountCharged").innerHTML = "<span class='result'>$" + agencyFee.toFixed(2) + "</span>";
      document.getElementById("roi").innerHTML = "<span class='result'>" + roi.toFixed(2) + "%</span>";
    }
  </script>
</head>
<body>
  <div id="roi-calculator-container">
    <h1>Missed Call Text Back</h1>
    <h2>ROI Calculator</h2>

    <label for="averageClientValue">Average Client Value:</label>
    <input type="number" id="averageClientValue" step="0.01" />

    <label for="missedCallsPerMonth">Missed Calls Per Month:</label>
    <input type="number" id="missedCallsPerMonth" step="1" />

    <label for="averageCloseRate">Average Close Rate (%):</label>
    <input type="number" id="averageCloseRate" step="0.01" />

    <button onclick="calculateROI()">Calculate My ROI</button>

    <h3>Results:</h3>
    <p>Monthly $$$ Left on Table: <span id="monthlyLeftOnTable"></span></p>
    <p>We Charge $297/month: <span id="amountCharged"></span></p>
    <p>ROI: <span id="roi"></span></p>
  </div>
</body>
</html>
