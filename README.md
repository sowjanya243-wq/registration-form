# registration-form
<!DOCTYPE html>
<html>
<head>
  <title>Registration Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 40px;
    }
    .form-container {
      background: white;
      padding: 20px 25px;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      width: 350px;
    }
    h2 {
      text-align: center;
      margin-bottom: 15px;
    }
    label {
      display: block;
      margin: 8px 0 4px;
      font-weight: bold;
    }
    input[type="text"],
    input[type="email"],
    input[type="date"],
    input[type="password"] {
      width: 100%;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    .checkbox {
      display: flex;
      align-items: center;
      margin-top: 10px;
    }
    button {
      margin-top: 15px;
      width: 100%;
      padding: 10px;
      background: #4CAF50;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background: #45a049;
    }
    .output {
      margin-top: 25px;
      padding: 15px;
      background: #fff;
      border-radius: 8px;
      width: 350px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .error {
      color: red;
      font-size: 13px;
    }
  </style>
</head>
<body>

  <div class="form-container">
    <h2>Registration Form</h2>
    <form id="regForm">
      <label>Full Name:</label>
      <input type="text" id="name" required>
      <div class="error" id="nameError"></div>

      <label>Email:</label>
      <input type="email" id="email" required>
      <div class="error" id="emailError"></div>

      <label>Password:</label>
      <input type="password" id="password" required>
      <div class="error" id="passwordError"></div>

      <label>Date of Birth:</label>
      <input type="date" id="dob" required>
      <div class="error" id="dobError"></div>

      <div class="checkbox">
        <input type="checkbox" id="terms">
        <label for="terms">I agree to Terms & Conditions</label>
      </div>
      <div class="error" id="termsError"></div>

      <button type="submit">Register</button>
    </form>
  </div>

  <div class="output" id="output" style="display:none;">
    <h3>Registration Details:</h3>
    <p><b>Name:</b> <span id="outName"></span></p>
    <p><b>Email:</b> <span id="outEmail"></span></p>
    <p><b>Password:</b> <span id="outPassword"></span></p>
    <p><b>Date of Birth:</b> <span id="outDob"></span></p>
  </div>

<script>
  document.getElementById("regForm").addEventListener("submit", function(e) {
    e.preventDefault();

    // Collect values
    const name = document.getElementById("name").value.trim();
    const email = document.getElementById("email").value.trim();
    const password = document.getElementById("password").value.trim();
    const dob = document.getElementById("dob").value;
    const terms = document.getElementById("terms").checked;

    // Error elements
    const nameError = document.getElementById("nameError");
    const emailError = document.getElementById("emailError");
    const passwordError = document.getElementById("passwordError");
    const dobError = document.getElementById("dobError");
    const termsError = document.getElementById("termsError");

    // Reset errors
    nameError.textContent = "";
    emailError.textContent = "";
    passwordError.textContent = "";
    dobError.textContent = "";
    termsError.textContent = "";

    let isValid = true;

    // Validations
    if (name.length < 3) {
      nameError.textContent = "Name must be at least 3 characters";
      isValid = false;
    }

    const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
    if (!email.match(emailPattern)) {
      emailError.textContent = "Enter a valid email";
      isValid = false;
    }

    if (password.length < 6) {
      passwordError.textContent = "Password must be at least 6 characters";
      isValid = false;
    }

    if (!dob) {
      dobError.textContent = "Please select your Date of Birth";
      isValid = false;
    }

    if (!terms) {
      termsError.textContent = "You must agree to Terms & Conditions";
      isValid = false;
    }

    // If all valid, show details
    if (isValid) {
      document.getElementById("outName").textContent = name;
      document.getElementById("outEmail").textContent = email;
      document.getElementById("outPassword").textContent = password;
      document.getElementById("outDob").textContent = dob;
      document.getElementById("output").style.display = "block";
      document.getElementById("regForm").reset();
    }
  });
</script>

</body>
</html>
