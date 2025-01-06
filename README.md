# age-calculator-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Age Calculator</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Pacifico&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Roboto', sans-serif;
      margin: 0;
      padding: 0;
      background: url('https://images.unsplash.com/photo-1506748686214-e9df14d4d9d0?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&q=80&w=1920') no-repeat center center/cover;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #333;
    }
    .container {
      background-color: rgba(255, 255, 255, 0.9);
      padding: 30px;
      border-radius: 15px;
      width: 350px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
      text-align: center;
    }
    h1 {
      font-family: 'Pacifico', cursive;
      font-size: 2.5em;
      color: #4a90e2;
      margin-bottom: 20px;
    }
    input {
      width: calc(100% - 20px);
      padding: 12px;
      margin: 10px 0;
      border: 2px solid #ddd;
      border-radius: 8px;
      font-size: 1em;
      transition: border-color 0.3s ease;
      font-family: 'Roboto', sans-serif;
    }
    input:focus {
      border-color: #4a90e2;
    }
    button {
      background-color: #4a90e2;
      color: white;
      padding: 12px;
      margin-top: 15px;
      border: none;
      border-radius: 8px;
      font-size: 1.1em;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.2s;
    }
    button:hover {
      background-color: #357ABD;
      transform: scale(1.05);
    }
    .result {
      margin-top: 20px;
      font-size: 1.5em;
      color: #333;
      font-weight: bold;
      text-shadow: 0 3px 5px rgba(0, 0, 0, 0.2);
    }
    .result span {
      color: #4a90e2;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Age Calculator</h1>
    <form id="ageForm">
      <input type="number" id="day" placeholder="Day" min="1" max="31" required>
      <input type="number" id="month" placeholder="Month" min="1" max="12" required>
      <input type="number" id="year" placeholder="Year" min="1900" max="2100" required>
      <button type="button" onclick="calculateAge()">Calculate Age</button>
    </form>
    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateAge() {
      const day = parseInt(document.getElementById('day').value);
      const month = parseInt(document.getElementById('month').value);
      const year = parseInt(document.getElementById('year').value);

      const today = new Date();
      const birthDate = new Date(year, month - 1, day);
      const result = document.getElementById('result');

      if (birthDate > today) {
        result.innerHTML = "<span>Invalid Date!</span> Future date entered.";
        return;
      }

      let age = today.getFullYear() - birthDate.getFullYear();
      const m = today.getMonth() - birthDate.getMonth();
      if (m < 0 || (m === 0 && today.getDate() < birthDate.getDate())) {
        age--;
      }

      result.innerHTML = `You are <span>${age}</span> years old.`;
    }
  </script>
</body>
</html>
