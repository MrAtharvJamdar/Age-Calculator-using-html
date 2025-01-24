# Age-Calculator-using-html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Age Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      text-align: center;
      background-color: #f4f4f4;
    }
    h1 {
      color: #333;
    }
    .container {
      max-width: 400px;
      margin: 0 auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }
    input {
      width: 90%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ddd;
      border-radius: 5px;
      font-size: 16px;
    }
    button {
      padding: 10px 20px;
      border: none;
      background-color: #007bff;
      color: #fff;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .result {
      margin-top: 20px;
      font-size: 18px;
      color: #555;
    }
  </style>
</head>
<body>
  <h1>Age Calculator</h1>
  <div class="container">
    <label for="dob">Enter Your Date of Birth:</label>
    <input type="date" id="dob">
    <button onclick="calculateAge()">Calculate Age</button>
    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateAge() {
      const dobInput = document.getElementById('dob').value;
      if (!dobInput) {
        document.getElementById('result').innerText = "Please enter your date of birth.";
        return;
      }

      const dob = new Date(dobInput);
      const today = new Date();

      let ageYears = today.getFullYear() - dob.getFullYear();
      let ageMonths = today.getMonth() - dob.getMonth();
      let ageDays = today.getDate() - dob.getDate();

      // Adjust if the current month or day is before the birth month/day
      if (ageDays < 0) {
        ageMonths--;
        ageDays += new Date(today.getFullYear(), today.getMonth(), 0).getDate();
      }

      if (ageMonths < 0) {
        ageYears--;
        ageMonths += 12;
      }

      document.getElementById('result').innerText = 
        Your Age: ${ageYears} years, ${ageMonths} months, and ${ageDays} days.;
    }
  </script>
</body>
</html>
