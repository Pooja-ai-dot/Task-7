# Task-7
##  Task 7:Fetch and Display Data from a Public API Using Fetch API.
🌐 Public API Used
We'll use the JSONPlaceholder API — a free fake REST API for testing and prototyping.
### Display Fetched user data
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Fetch Users</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f0f0;
      padding: 2rem;
    }

    h1 {
      text-align: center;
      margin-bottom: 2rem;
    }

    .user-list {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
    }

    .user-card {
      background: white;
      padding: 1rem;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      width: 250px;
    }

    .user-card h3 {
      margin-bottom: 0.5rem;
    }

    .user-card p {
      margin: 0.3rem 0;
      font-size: 0.9rem;
    }
  </style>
</head>
<body>
  <h1>User Directory</h1>
  <div class="user-list" id="userList"></div>

  <script>
    const userList = document.getElementById('userList');

    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(users => {
        users.forEach(user => {
          const card = document.createElement('div');
          card.className = 'user-card';
          card.innerHTML = `
            <h3>${user.name}</h3>
            <p><strong>Email:</strong> ${user.email}</p>
            <p><strong>Phone:</strong> ${user.phone}</p>
            <p><strong>City:</strong> ${user.address.city}</p>
          `;
          userList.appendChild(card);
        });
      })
      .catch(error => {
        userList.innerHTML = `<p style="color:red;">Failed to load user data.</p>`;
        console.error('Error fetching users:', error);
      });
  </script>
</body>
</html>
```
