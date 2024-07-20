To make the sign-in/sign-up form responsive and provide different interfaces for various screen sizes, we need to use media queries and JavaScript to handle the transitions. Below is the updated code with the necessary changes.

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sign in || Sign up form</title>
    <!-- font awesome icons -->
    <link rel="stylesheet" href="../../../fontawesome-free-6.2.1-web/css/all.css">
    <!-- css stylesheet -->
    <link rel="stylesheet" href="./style.css">
</head>
<body>

    <div class="container" id="container">
        <div class="form-container sign-up-container">
            <form action="#">
                <h1>Create Account</h1>
                <div class="social-container">
                    <a href="#" class="social"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social"><i class="fab fa-google-plus-g"></i></a>
                    <a href="#" class="social"><i class="fab fa-linkedin-in"></i></a>
                </div>
                <span>or use your email for registration</span>
                <div class="infield">
                    <i class="fas fa-user" id="icons"></i>
                    <input type="text" placeholder="User Name" required>
                    <label></label>
                </div>
                <div class="infield">
                    <i class="fas fa-envelope" id="icons"></i>
                    <input type="email" placeholder="Email" name="email" required>
                    <label></label>
                </div>
                <div class="infield">
                    <i class="fas fa-key" id="icons"></i>
                    <input type="password" placeholder="Password" required>
                    <i id="eye" class="fas fa-eye"></i>
                    <label></label>
                </div>
                <button>Submit</button>
                <p class="animation_forms">Already have an account <a href="#" id="goToLogin">LOGIN</a></p>
            </form>
        </div>
        <div class="form-container sign-in-container">
            <form action="#">
                <h1>Sign in</h1>
                <div class="social-container">
                    <a href="#" class="social"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social"><i class="fab fa-google-plus-g"></i></a>
                    <a href="#" class="social"><i class="fab fa-linkedin-in"></i></a>
                </div>
                <span>or use your account</span>
                <div class="infield">
                    <i class="fas fa-envelope" id="icons"></i>
                    <input type="email" placeholder="Email" name="email" required>
                    <label></label>
                </div><br>
                <div class="infield">
                    <i class="fas fa-key" id="icons"></i>
                    <input type="password" name="password" placeholder="Password" minlength="8" maxlength="16" required>
                    <i id="eye" class="fas fa-eye"></i>
                    <label></label>
                </div>
                <a href="../error/./error.html" class="forgot">Forgot your password?</a>
                <button>Log In</button>
                <p class="animation_forms">Don't have an account ?<a href="#" id="goToSignup">SIGNUP</a></p>
            </form>
        </div>
        <div class="overlay-container" id="overlayCon">
            <div class="overlay">
                <div class="overlay-panel overlay-left">
                    <h1>Welcome Back!</h1>
                    <p>To keep connected with us please login with your personal info</p>
                    <button id="signIn" style="margin-top: 5%;">Sign In</button>
                </div>
                <div class="overlay-panel overlay-right">
                    <h1>Hello, Friend!</h1>
                    <p>Enter your personal details and start journey with us</p>
                    <button id="signUp">SIGN UP</button>
                </div>
            </div>
            <button id="overlayBtn"></button>
        </div>
    </div>

    <script src="./script.js"></script>

</body>
</html>
```

### CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

* {
    padding: 0px;
    margin: 0px;
    box-sizing: border-box;
}

:root {
    --linear-grad: linear-gradient(to right, #141E30, #243B55);
    --grad-clr1: #141E30;
    --grad-clr2: #243B55;
}

body {
    height: 100vh;
    background: #f6f5f7;
    display: grid;
    place-content: center;
    font-family: 'Poppins', sans-serif;
}

.container{
    position: relative;
    width: 850px;
    height: 500px;
    background: #fff;
    box-shadow:  25px 30px 55px #5557;
    border-radius: 13px;
    overflow: hidden;
}

.form-container {
    position: absolute;
    width: 60%;
    height: 100%;
    padding: 0 px 40px;
    transition: all 0.6s ease-in-out;
}

.sign-up-container{
    opacity: 0;
    z-index: 1;
}

.sign-in-container{
    z-index: 2;
}

form{
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 8px 50px;
}

h1{
    color: var(--grad-clr1);
}

.social-container{
    margin: 20px 0px;
}

.social-container a{
    border: 1px solid #ddd;
    border-radius: 50%;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    margin: 0px 5px;
    height: 40px;
    width: 40px;
}

.social-container a:hover{
    color: #fff;
    background-color: var(--grad-clr1);
}

span{
    font-size: 12px;
}

.infield{
    position: relative;
    margin: 8px 0px;
    width: 100%;
}

.input{
    width: 100%;
    padding: 12px 15px;
    background: #f3f3f3;
    border: none;
    outline: none;
}

label{
    position: absolute;
    left: 50%;
    top: 100%;
    transform: translate(-50%);
    width: 100%;
    height: 2px;
    background: var(--linear-grad);
    transition: 0.3s;
    display: none;
}

input{
    width: 100%;
    padding: 12px;
}

input:focus{
    width: 100%;
    padding: 13px;
    outline: none;
    color: var(--grad-clr1);
    /* border: none; */
}

/* showing psd  */
    
.infield i{
    position: absolute;
    right: 15px;
    color: var(--grad-clr1);
    top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
    background-color: #fff;
    padding: 8px;
}

.infield i.active::before{
    color: var(--grad-clr1);
    content: "\f070";
}

.infield i:hover{
    color: #001;
}

a{
    color: #333;
    font-size: 14px;
    text-decoration: none;
    margin: 15px 0px;
}

a.forgot:hover{
    padding-bottom: 3px;
    transition: .3s ease;
    transition-duration: 0.4s;
    border-bottom: 2px solid var(--grad-clr2);
}

button{
    border-radius: 10px;
    border: 1px solid var(--grad-clr2); 
    background: var(--grad-clr2);
    color: #fff;
    font-size: 12px;
    font-weight: bold;
    padding: 12px 45px;
    letter-spacing: 1px;
    text-transform: uppercase;
}

.form-container button{
    margin-top: 17px;
    transition: 80ms ease-in;
}

.form-container button:hover{
    background: #fff;
    color: var(--grad-clr1);
}

.overlay-container{
    position: absolute;
    top: 0;
    left: 60%;
    width: 40%;
    height: 100%;
    overflow: hidden;
    transition: transform 0.6s ease-in-out;
    z-index: 9;
}

#overlayBtn{
    cursor: pointer;
    position: absolute;
    left: 50%;
    top: 304px;
    transform: translate(-50%);
    width: 143.67px;
    height: 40px;
    border: 

1px solid #fff;
    background: transparent;
    border-radius: 10px;
}

.overlay{
    position: relative;
    background: var(--linear-grad);
    color: #fff;
    left: -150%;
    height: 100%;
    width: 250%;
    transition: transform 0.6s ease-in-out;
}

.overlay-panel{
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 0px 40px;
    text-align: center;
    height: 100%;
    width: 340px;
    transition: 0.6s ease-in-out;
}

.overlay-left{
    right: 60%;
    transform: translate(-12%);
}

.overlay-right{
    right: 0;
    transform: translate(0%);
}

.overlay-panel h1{
    color: #fff;
}

p{
    font-size: 14px;
    font-weight: 300;
    line-height: 20px;
    letter-spacing: 0.5px;
    margin: 25px 0px 35px;
}

.overlay-panel button{
    border: none;
    background-color: transparent;
}

.right-panel-active .overlay-container{
    transform: translateX(-150%);
}

.right-panel-active .overlay{
    transform: translateX(50%);
}

.right-panel-active .overlay-left{
    transform: translateX(25%);
}

.right-panel-active .overlay-right{
    transform: translateX(35%);
}

.right-panel-active .sign-in-container{
    transform: translateX(20%);
    opacity: 0;
}

.right-panel-active .sign-up-container{
    transform: translate(66.7%);
    opacity: 1;
    z-index: 5;
    animation: show 0.6s;
}

@keyframes show{
    0%,50%{
        opacity: 0;
        z-index: 1;
    }

    50.1%,100%{
        opacity: 1;
        z-index: 5;
    }
}

.btnScaled{
    animation: scaleBtn 0.6s;
}

@keyframes scaleBtn{
    0%{
        width: 143.67px;
    }

    50%{
        width: 250px;
    }

    100%{
        width: 143.67px;
    }
}

/* Media Queries for Responsive Design */
@media (max-width: 861px) {
    .container {
        width: 100%;
        height: auto;
        box-shadow: none;
        border-radius: 0;
    }
    
    .form-container {
        width: 100%;
        height: auto;
        position: relative;
    }
    
    .overlay-container {
        display: none;
    }
    
    .sign-up-container,
    .sign-in-container {
        width: 100%;
        height: 100%;
        opacity: 1;
        z-index: 1;
        transform: translateX(0%);
    }

    .right-panel-active .sign-in-container {
        transform: translateX(-100%);
    }

    .right-panel-active .sign-up-container {
        transform: translateX(0%);
        z-index: 5;
    }
}
```

### JavaScript
```javascript
// Form animation
const container = document.getElementById('container');
const overlayCon = document.getElementById('overlayCon');
const overlayBtn = document.getElementById('overlayBtn');
const goToSignup = document.getElementById('goToSignup');
const goToLogin = document.getElementById('goToLogin');

overlayBtn.addEventListener('click', () => {
    container.classList.toggle('right-panel-active');

    overlayBtn.classList.remove('btnScaled');
    window.requestAnimationFrame(() => {
        overlayBtn.classList.add('btnScaled');
    });
});

goToSignup.addEventListener('click', () => {
    container.classList.add('right-panel-active');
});

goToLogin.addEventListener('click', () => {
    container.classList.remove('right-panel-active');
});

// Visibility of password
document.querySelectorAll(".infield i").forEach((toggleBtn) => {
    toggleBtn.addEventListener('click', () => {
        const pswrdfield = toggleBtn.previousElementSibling;

        if (pswrdfield.type === "password") {
            pswrdfield.type = "text";
            toggleBtn.classList.add("active");
        } else {
            pswrdfield.type = "password";
            toggleBtn.classList.remove("active");
        }
    })
})
```

### Summary of Changes:
1. **Media Queries**: Added media queries in the CSS to handle different screen sizes. For screens smaller than or equal to 861px, the overlay container is hidden, and the form containers take up the full width.
2. **JavaScript**: Added event listeners for the "SIGNUP" and "LOGIN" links to handle the transition animation on smaller screens.
3. **CSS Animations**: Modified the CSS to include the appropriate transitions and animations for smaller screens.

With these changes, your form will be responsive and provide a smooth user experience across different devices.
