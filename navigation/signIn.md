---
layout: default
title: Sign-In
permalink: /sign-in/
---

<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login</title>

  <link rel="stylesheet" href="{{site.baseurl}}/signIn.css">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Lexend:wght@100..900&display=swap" rel="stylesheet">
</head>

<body>
  <main id="main-holder">
    <div id="brand-logo">
      <img src="../images/icons/dnhs_logo.png" alt="Brand Logo">
    </div>
    <div id="login-div">
      <h1 id="login-header">Sign-in</h1>
      <!--<div id="login-subheader">If you already have an account.</div>-->
      <form id="login-form">
        <input type="text" name="username" id="username-field" class="login-form-field" placeholder="Email">
        <input type="password" name="password" id="password-field" class="login-form-field" placeholder="Password">
      </form>
      <div id="forgot-password">Forgot Password?</div>
      <input type="submit" value="Sign In" id="login-form-submit" onclick="signIn()">
      <div id="no-account">No account?</div>
      <div id="create-account">Click here to make one!</div>
    </div>
  </main>
</body>

</html>

<script>
  var local = "http://localhost:8911";
  var deployed = "https://jcc.stu.nighthawkcodingsociety.com";


  function signIn() {
    console.log("button clicked");
    var email = document.getElementById('username-field').value;
    var password = document.getElementById('password-field').value;

    var requestBody = {
        email: email,
        password: password
    };

    var requestOptions = {
        method: 'POST',
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'include', // include, *same-origin, omit
        body: JSON.stringify(requestBody),
        headers: {
            "content-type": "application/json",
        },
    };
   
    fetch(deployed + '/authenticate', requestOptions)
    .then((response => {
      if (!response.ok) {
          if (response.status == "401") {
            throw new Error("Invalid email or password")
          }
          else {
            throw new Error("HTTP Error: " + response.status)
          }
      }
      return response.json();
      })) // Get response text
      .then(data => {
        // Check response status
        console.log(data.message);
        localStorage.setItem('jwtToken', data.cookie);
        window.location.replace("{{site.baseurl}}/dashboard/");
        return;
      }
    )
    .catch(error => {
        console.error('There was an error:', error);
        // Error occurred during sign-in
        displayErrorMessage(error.message);
    });
  }

    function displayErrorMessage(message) {
      // check if error message already exists 
      var existingErrorMessage = document.querySelector('.error-message');
      if (!existingErrorMessage) {
        var errorDiv = document.createElement('div');
        errorDiv.className = 'error-message';
        errorDiv.textContent = message;
        document.getElementById('login-div').appendChild(errorDiv);
      }
    }

    /*
    document.getElementById('login-form-submit').onclick = function () {
      signIn();
    }; ^ 
    */
</script>
