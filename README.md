<!DOCTYPE html>
<html>
<head>
  <title>Interactive Form Validation</title>
  <style>
    input { display: block; margin: 10px 0; padding: 8px; }
    span { font-size: 14px; }
  </style>
</head>
<body>

  <h2>Interactive Form Validation using JavaScript</h2>
  <form id="myForm">
    <label>Email:</label>
    <input type="text" id="email" placeholder="Enter your email">
    <span id="emailMsg"></span>

    <label>Password:</label>
    <input type="password" id="password" placeholder="Enter password">
    <span id="passMsg"></span>

    <button type="submit">Submit</button>
  </form>

  <script>
    const email = document.getElementById('email');
    const password = document.getElementById('password');
    const emailMsg = document.getElementById('emailMsg');
    const passMsg = document.getElementById('passMsg');

    // Email validation
    email.addEventListener('input', () => {
      const pattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (email.value.match(pattern)) {
        emailMsg.textContent = "Valid email ✔️";
        emailMsg.style.color = "green";
      } else {
        emailMsg.textContent = "Invalid email ❌";
        emailMsg.style.color = "red";
      }
    });

    // Password validation
    password.addEventListener('input', () => {
      if (password.value.length >= 8) {
        passMsg.textContent = "Strong password ✔️";
        passMsg.style.color = "green";
      } else {
        passMsg.textContent = "Password must be at least 8 characters ❌";
        passMsg.style.color = "red";
      }
    });

    // Form submission validation
    document.getElementById('myForm').addEventListener('submit', (e) => {
      if (!email.value || !password.value) {
        alert("Please fill out all fields before submitting!");
        e.preventDefault(); // stops form submission
      }
    });
  </script>

</body>
</html>
