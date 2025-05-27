<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Gym Finder & Subscription</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f3f3f3;
      margin: 0;
      padding: 0;
    }
    header {
      background: #2d2d2d;
      color: white;
      padding: 15px;
      text-align: center;
    }
    .container {
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    .search-box input {
      width: 70%;
      padding: 10px;
    }
    .search-box button {
      padding: 10px 15px;
      margin-left: 10px;
    }
    .gym-list, .subscription-form {
      margin-top: 30px;
      background: lightblue;
      padding: 20px;
      border-radius: 8px;
    }
    .gym-item {
      margin-bottom: 15px;
      border-bottom: 1px solid #ccc;
      padding-bottom: 10px;
    }
    .subscription-form label {
      display: block;
      margin: 10px 0 5px;
    }
    .subscription-form input, .subscription-form select {
      width: 100%;
      padding: 8px;
      margin-bottom: 15px;
    }
    .subscription-form button {
      background: #007bff;
      color: white;
      padding: 10px 15px;
      border: none;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <header>
    <h1>Find Gyms Near You & Subscribe</h1>
  </header>

  <div class="container">
    <div class="search-box">
      <input type="text" id="searchInput" placeholder="Enter your location or city..." />
      <button onclick="searchGyms()">Search</button>
    </div>

    <div class="gym-list" id="gymList">
      <!-- Search results will be shown here -->
    </div>

    <div class="subscription-form">
      <h2>Subscribe to a Gym Plan</h2>
      <form>
        <label for="name">Full Name</label>
        <input type="text" id="name" required />

        <label for="email">Email</label>
        <input type="email" id="email" required />

        <label for="plan">Choose a Plan</label>
        <select id="plan" required>
          <option value="daily">Daily - 150Rs</option>
          <option value="weekly">Weekly - 300Rs</option>
          <option value="monthly">Monthly - 1500Rs</option>
        </select>

        <button type="submit">Subscribe Now</button>
      </form>
    </div>
  </div>

  <script>
    const gyms = [
      { name: "preetham Gym", location: "Downtown", distance: "1.2km" },
      { name: "pramod Gym", location: "Midtown", distance: "2.3km" },
      { name: "Rahul Gym", location: "Suburbs", distance: "3.5km" }
    ];

    function searchGyms() {
      const searchInput = document.getElementById('searchInput').value.toLowerCase();
      const results = gyms.filter(gym =>
        gym.name.toLowerCase().includes(searchInput) ||
        gym.location.toLowerCase().includes(searchInput)
      );

      const gymList = document.getElementById('gymList');
      gymList.innerHTML = '<h2>Nearby Gyms</h2>';
      if (results.length === 0) {
        gymList.innerHTML += '<p>No gyms found.</p>';
        return;
      }

      results.forEach(gym => {
        gymList.innerHTML += `
          <div class="gym-item">
            <strong>${gym.name}</strong><br/>
            Location: ${gym.location}<br/>
            Distance: ${gym.distance}
          </div>
        `;
      });
    }
  </script>

</body>
</html>
