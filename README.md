<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SecureBank - Customer Registration</title>
<style>
* {
margin: 0;
padding: 0;
box-sizing: border-box;
}

body {
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
min-height: 100vh;
}

/* Header */
header {
background: rgba(255, 255, 255, 0.95);
backdrop-filter: blur(10px);
padding: 0.8rem 2rem;
box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
position: sticky;
top: 0;
z-index: 100;
}

.header-content {
max-width: 1400px;
margin: 0 auto;
display: flex;
justify-content: space-between;
align-items: center;
}

.logo {
display: flex;
align-items: center;
gap: 10px;
font-size: 1.5rem;
font-weight: bold;
color: #2c3e50;
}

.logo-icon {
width: 40px;
height: 40px;
background: linear-gradient(45deg, #3498db, #2980b9);
border-radius: 8px;
display: flex;
align-items: center;
justify-content: center;
color: white;
font-weight: bold;
}

.nav-links {
display: flex;
list-style: none;
gap: 2rem;
}

.nav-links a {
color: #2c3e50;
text-decoration: none;
font-weight: 500;
transition: color 0.3s ease;
}

.nav-links a:hover {
color: #3498db;
}

/* Page Background */
.page-background {
min-height: calc(100vh - 80px);
padding: 2rem;
display: flex;
align-items: center;
justify-content: center;
}

.register-container {
background: rgba(255, 255, 255, 0.95);
backdrop-filter: blur(10px);
border-radius: 20px;
padding: 3rem;
box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
max-width: 800px;
width: 100%;
animation: slideUp 0.8s ease-out;
}

.register-container h2 {
text-align: center;
color: #2c3e50;
font-size: 2.5rem;
margin-bottom: 2rem;
position: relative;
}

.register-container h2::after {
content: '';
position: absolute;
bottom: -10px;
left: 50%;
transform: translateX(-50%);
width: 80px;
height: 4px;
background: linear-gradient(135deg, #3498db, #2980b9);
border-radius: 2px;
}

/* Form Styling */
form {
display: grid;
gap: 1.5rem;
}

.form-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1.5rem;
}

.form-group {
display: flex;
flex-direction: column;
position: relative;
}

label {
color: #2c3e50;
font-weight: 600;
margin-bottom: 0.5rem;
font-size: 0.9rem;
text-transform: uppercase;
letter-spacing: 0.5px;
}

input, select {
padding: 1rem;
border: 2px solid #ecf0f1;
border-radius: 12px;
font-size: 1rem;
transition: all 0.3s ease;
background: rgba(255, 255, 255, 0.8);
}

input:focus, select:focus {
outline: none;
border-color: #3498db;
background: white;
box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
transform: translateY(-2px);
}

.input-icon {
position: absolute;
right: 15px;
top: 50%;
transform: translateY(-50%);
font-size: 1.2rem;
color: #7f8c8d;
pointer-events: none;
}

/* Error Messages */
.error-message {
color: #e74c3c;
font-size: 0.85rem;
margin-top: 0.5rem;
padding: 0.5rem;
background: rgba(231, 76, 60, 0.1);
border-radius: 6px;
border-left: 3px solid #e74c3c;
animation: shake 0.3s ease-in-out;
}

@keyframes shake {
0%, 100% { transform: translateX(0); }
25% { transform: translateX(-5px); }
75% { transform: translateX(5px); }
}

/* Submit Button */
button[type="submit"] {
background: linear-gradient(135deg, #3498db, #2980b9);
color: white;
border: none;
padding: 1.2rem 2rem;
border-radius: 12px;
font-size: 1.1rem;
font-weight: 600;
cursor: pointer;
transition: all 0.3s ease;
margin-top: 1rem;
text-transform: uppercase;
letter-spacing: 1px;
}

button[type="submit"]:hover {
transform: translateY(-3px);
box-shadow: 0 10px 25px rgba(52, 152, 219, 0.4);
}

button[type="submit"]:active {
transform: translateY(-1px);
}

/* Success State */
.success-container {
text-align: center;
padding: 2rem;
}

.success-container h4 {
color: #27ae60;
font-size: 1.5rem;
margin-bottom: 1rem;
display: flex;
align-items: center;
justify-content: center;
gap: 0.5rem;
}

.success-container button {
background: linear-gradient(135deg, #95a5a6, #7f8c8d);
color: white;
border: none;
padding: 1rem 2rem;
border-radius: 10px;
font-size: 1rem;
cursor: pointer;
transition: all 0.3s ease;
}

.success-container button:hover {
transform: translateY(-2px);
box-shadow: 0 5px 15px rgba(149, 165, 166, 0.3);
}

/* Responsive Design */
@media (max-width: 768px) {
.page-background {
padding: 1rem;
}

.register-container {
padding: 2rem;
}

.form-row {
grid-template-columns: 1fr;
}

.register-container h2 {
font-size: 2rem;
}

.nav-links {
display: none;
}
}

/* Animations */
@keyframes slideUp {
from {
opacity: 0;
transform: translateY(30px);
}
to {
opacity: 1;
transform: translateY(0);
}
}

/* Loading Animation */
.loading {
display: inline-block;
width: 20px;
height: 20px;
border: 2px solid #ffffff;
border-radius: 50%;
border-top-color: transparent;
animation: spin 1s ease-in-out infinite;
margin-right: 10px;
}

@keyframes spin {
to { transform: rotate(360deg); }
}
</style>
</head>
<body>
<!-- Header for login page -->
<header *ngIf="router.url==='/userLogin'">
    <div class="header-content">
        <div class="logo">
            <div class="logo-icon">SB</div>
            SecureBank
        </div>
        <nav>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </div>
</header>

<div class="page-background">
    <div class="register-container">
        <h2>Customer Registration</h2>

        <!-- Registration Form -->
        <div [hidden]="isVisible">
            <form (ngSubmit)="addCustomer()">
                <div class="form-row">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" name="name" placeholder="Enter your full name" [(ngModel)]="customer.name">
                        <div class="error-message" *ngIf="hasValidationError('name')">
                            {{getValidationErrorMessage('name')}}
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="dateOfBirth">Date of Birth</label>
                        <input type="date" name="dateOfBirth" [(ngModel)]="customer.dateOfBirth">
                        <div class="error-message" *ngIf="hasValidationError('dateOfBirth')">
                            {{getValidationErrorMessage('dateOfBirth')}}
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="gender">Gender</label>
                        <select name="gender" id="gender" [(ngModel)]="customer.gender">
                            <option value="">Select Gender</option>
                            <option value="Male">Male</option>
                            <option value="Female">Female</option>
                        </select>
                        <div class="error-message" *ngIf="hasValidationError('gender')">
                            {{getValidationErrorMessage('gender')}}
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="mobileNum">Mobile Number</label>
                        <input type="text" name="mobileNum" placeholder="Enter 10-digit mobile number" [(ngModel)]="customer.mobileNum">
                        <div class="error-message" *ngIf="hasValidationError('mobileNum')">
                            {{getValidationErrorMessage('mobileNum')}}
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="emailId">Email Address</label>
                        <input type="email" name="emailId" placeholder="Enter your email address" [(ngModel)]="customer.emailId">
                        <div class="error-message" *ngIf="hasValidationError('emailId')">
                            {{getValidationErrorMessage('emailId')}}
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="aadharNo">Aadhar Number</label>
                        <input type="text" name="aadharNo" placeholder="Enter 12-digit Aadhar number" [(ngModel)]="customer.aadharNo">
                        <div class="error-message" *ngIf="hasValidationError('aadharNo')">
                            {{getValidationErrorMessage('aadharNo')}}
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="streetName">Street Address</label>
                        <input type="text" name="streetName" placeholder="Enter street address" [(ngModel)]="customer.streetName">
                        <div class="error-message" *ngIf="hasValidationError('streetName')">
                            {{getValidationErrorMessage('streetName')}}
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="city">City</label>
                        <input type="text" name="city" placeholder="Enter city name" [(ngModel)]="customer.city">
                        <div class="error-message" *ngIf="hasValidationError('city')">
                            {{getValidationErrorMessage('city')}}
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="state">State</label>
                        <select name="state" [(ngModel)]="customer.state">
                            <option value="">Select State</option>
                            <option *ngFor="let s of state" value="{{s}}">{{s}}</option>
                        </select>
                        <div class="error-message" *ngIf="hasValidationError('state')">
                            {{getValidationErrorMessage('state')}}
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="pincode">Pincode</label>
                        <input type="text" name="pincode" placeholder="Enter 6-digit pincode" [(ngModel)]="customer.pincode">
                        <div class="error-message" *ngIf="hasValidationError('pincode')">
                            {{getValidationErrorMessage('pincode')}}
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="username">Username</label>
                        <input type="text" name="username" placeholder="Create a unique username" [(ngModel)]="customer.username">
                        <div class="error-message" *ngIf="hasValidationError('username')">
                            {{getValidationErrorMessage('username')}}
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" name="password" placeholder="Create a strong password" [(ngModel)]="customer.password">
                        <span class="input-icon">🔒</span>
                        <div class="error-message" *ngIf="hasValidationError('password')">
                            {{getValidationErrorMessage('password')}}
                        </div>
                    </div>
                </div>

                <div class="form-group">
                    <label for="accountType">Account Type</label>
                    <select name="accountType" id="accountType" [(ngModel)]="customer.accountType">
                        <option value="">Select Account Type</option>
                        <option value="Saving">Savings Account</option>
                        <option value="Current">Current Account</option>
                        <option value="Fixed Deposit">Fixed Deposit</option>
                    </select>
                    <div class="error-message" *ngIf="hasValidationError('accountType')">
                        {{getValidationErrorMessage('accountType')}}
                    </div>
                </div>

                <button type="submit">
                    <span class="loading" style="display: none;"></span>
                    Register Account
                </button>
            </form>
        </div>

        <!-- Success Message -->
        <div class="success-container" [hidden]="!isVisible">
            <h4>
                ✅ Your Verification is Under Review
            </h4>
            <p>We'll notify you once your account is approved. This usually takes 1-2 business days.</p>
            <button (click)="backToHome()">Back to Home</button>
        </div>
    </div>
</div>
</body>
</html>
