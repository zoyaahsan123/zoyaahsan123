<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Contact Us</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 500px;
            margin: 50px auto;
            background-color: #fff;
            padding: 30px;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
            border-radius: 5px;
        }

        h2 {
            text-align: center;
            margin-top: 0;
            color: rgb(41, 38, 38);
        }

        .form-group {
            margin-bottom: 20px;
            position: relative; /* For icon placement */
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: rgb(0, 0, 0);
            position: relative; /* To create space for the icon */
        }

        /* Add this for icon alignment */
        label i.icon-left,
        label i.icon-right {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            color: #aaa;
            pointer-events: none;
        }

        label i.icon-left {
            left: 10px;
        }

        label i.icon-right {
            right: 10px;
        }

        input,
        textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }

        textarea {
            resize: vertical;
            height: 150px;
        }

        button {
            display: block;
            width: 100%;
            background-color: #4CAF50;
            color: #fff;
            padding: 12px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        .error-message {
            color: #e74c3c;
            font-size: 14px;
            margin-top: 5px;
        }

        /* Responsive styles */
        @media screen and (max-width: 500px) {
            .container {
                padding: 20px;
            }
        }
      label{
          margin-left: 30px;
      }
      .icon{
          color: rgb(165, 158, 158);
          size: -1px;
      }
    
    </style>
</head>
<body>
    
    <div class="container">
        <img src="logo.jpg" alt="Logo" style="display: block; margin: 0 auto; width: 100px;">
        <center><h2 style="color: rgb(18, 31, 151);font-weight: 800;font-size:30px ;">Contact Us <i class="icon fas fa-phone-alt"></i></h2></center>
        <center><p> We provide the best servive you fill the foam</p></center>
        <form id="contactForm" method="post">
            <div class="form-group">
                <label for="name">Name: <i class="icon fas fa-user icon-left" style="margin-left: -30px;"></i></label>
                <input type="text" id="name" name="name" required>
                <div class="error-message" id="nameError"></div>
            </div>

            <div class="form-group">
                <label for="email">Email: <i class="icon fas fa-envelope icon-left" style="margin-left: -30px;"></i></label>
                <input type="email" id="email" name="email" required>
                <div class="error-message" id="emailError"></div>
            </div>

            <div class="form-group">
                <label for="phone">Phone Number: <i class="icon fas fa-phone-alt icon-left" style="margin-left: -30px;"></i></label>
                <input type="tel" id="phone" name="phone" required>
                <div class="error-message" id="phoneError"></div>
            </div>

            <div class="form-group">
                <label for="message">Message: <i class="icon fas fa-comment icon-left" style="margin-left: -30px;"></i></label>
                <textarea id="message" name="message" required></textarea>
                <div class="error-message" id="messageError"></div>
            </div>

            <button type="submit" class="submit-button">Submit <i class="fas fa-paper-plane"></i></button>
        </form>
    </div>
    
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>
        $(document).ready(function() {
            $('#contactForm').submit(function(event) {
                event.preventDefault();
    
                const nameInput = $('#name');
                const emailInput = $('#email');
                const phoneInput = $('#phone');
                const messageInput = $('#message');
    
                function displayError(inputElement, errorMessage) {
                    const errorDiv = $('#' + inputElement.attr('id') + 'Error');
                    errorDiv.text(errorMessage);
                }
    
                function isValidEmail(email) {
                    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
                    return emailRegex.test(email);
                }
    
                function isValidPhoneNumber(phone) {
                    const phoneRegex = /^\d{11}$/;
                    return phoneRegex.test(phone);
                }
    
                if (nameInput.val().trim() === '') {
                    displayError(nameInput, 'Please enter your Name.');
                    return;
                } else if (nameInput.val().trim().length < 5) {
                    displayError(nameInput, 'Name must be at least 5 characters long.');
                    return;
                }
    
                if (emailInput.val().trim() === '') {
                    displayError(emailInput, 'Please enter your Email.');
                    return;
                } else if (!emailInput.val().trim().endsWith('@gmail.com')) {
                    displayError(emailInput, 'Please enter a valid Gmail address (e.g., user@gmail.com).');
                    return;
                } else if (!isValidEmail(emailInput.val().trim())) {
                    displayError(emailInput, 'Please enter a valid Email address.');
                    return;
                }
    
                if (phoneInput.val().trim() === '') {
                    displayError(phoneInput, 'Please enter your Phone Number.');
                    return;
                } else if (!isValidPhoneNumber(phoneInput.val().trim())) {
                    displayError(phoneInput, 'Please enter a valid 11-digit Phone Number.');
                    return;
                }
    
                if (messageInput.val().trim() === '') {
                    displayError(messageInput, 'Please enter your Message.');
                    return;
                } else if (messageInput.val().trim().length < 10) {
                    displayError(messageInput, 'Message must be at least 10 characters long.');
                    return;
                }
    
                alert('Form submitted successfully!');
                // You can uncomment the next line if you want to submit the form
                // $('#contactForm').submit();
            });
    
            // Helper function to clear error messages
            function clearError(inputElement) {
                const errorDiv = $('#' + inputElement.attr('id') + 'Error');
                errorDiv.text('');
            }
    
            // Event listeners for clearing error messages on input
            $('#name').on('input', function() {
                clearError($(this));
            });
    
            $('#email').on('input', function() {
                clearError($(this));
            });
    
            $('#phone').on('input', function() {
                clearError($(this));
            });
    
            $('#message').on('input', function() {
                clearError($(this));
            });
        });
    </script>
    
    
    
    
    
    

</body>
</html>

