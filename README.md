# User Management System with OTP Verification

A responsive multi-page website for user and employee management with OTP verification for both email and mobile numbers.

## Features

- **Responsive Design**: Works on mobile, tablet, and desktop devices
- **User Management**: View, add, edit, and delete users
- **Employee Management**: View, add, edit, and delete employees
- **OTP Verification**: Verify both email and mobile numbers using OTP with improved resend functionality
- **Form Validation**: Validate user inputs including robust password validation
- **Enhanced Date Picker**: Intuitive date picker with month and year dropdowns for date of birth and date of joining fields
- **Password Validation**: Alphanumeric validation with 10-20 character length requirement

## Pages

1. **User Management Dashboard**
   - View list of users
   - Search functionality
   - Add, edit, and delete users
   - Pagination

2. **User Registration**
   - Personal information
   - Shop information
   - Contact & security with OTP verification for both email and mobile
   - Password validation with real-time feedback

3. **Employee Management Dashboard**
   - View list of employees
   - Search functionality
   - Add, edit, and delete employees
   - Pagination

4. **Employee Registration**
   - Personal information with enhanced date picker for date of birth
   - Employment details with enhanced date picker for date of joining
   - Contact & security with OTP verification for mobile
   - Password validation with real-time feedback

## Project Structure

`user-management-system/
├── index.html                  # User Management Dashboard
├── register-user.html          # User Registration Form
├── employee-management.html    # Employee Management Dashboard
├── register-employee.html      # Employee Registration Form
├── css/
│   └── styles.css              # Main stylesheet
├── js/
│   ├── script.js               # Common JavaScript
│   ├── register.js             # User Registration JavaScript
│   └── register-employee.js    # Employee Registration JavaScript
└── README.md `

## How to Use

1. Clone the repository
2. Open `index.html` in your browser to start

## OTP Verification

The OTP verification system has been improved with the following features:

- When you click "Verify Phone" or "Send OTP", a random 6-digit OTP is generated and logged to the console
- A 2-minute countdown timer starts for OTP expiration
- The resend button is initially disabled for 10 seconds
- A countdown shows the remaining time until the resend button becomes available
- After 10 seconds, the resend button is enabled and the user can request a new OTP
- When the resend button is clicked, both timers reset properly
- For testing, you can use console in the browser to get the generated otp for testing the otp verification.
- After successful verification, the button will change to "Verified"

## Enhanced Date Picker

An improved date picker has been implemented for date fields with the following features:

- Calendar icon is properly aligned within the input field
- Clicking the calendar icon opens a date picker popup
- Month and year dropdown selectors for quick navigation
- Users can easily select any year within the allowed range
- Dates are selectable and will populate the input field in MM/DD/YYYY format
- Date of birth picker has appropriate min/max year restrictions
- Date of joining picker has appropriate min/max year restrictions
- Today's date is highlighted in the calendar

## Password Validation

Robust password validation has been implemented with the following features:

- Real-time validation as the user types
- Visual feedback with checkmarks and error indicators
- Alphanumeric validation (letters and numbers only)
- Length validation (10-20 characters)
- Password matching validation
- Form submission is prevented if password requirements are not met

## Form Validation

- All required fields must be filled
- Passwords must meet all validation requirements
- Both email and phone must be verified before submitting the user registration form
- Phone must be verified before submitting the employee registration form

## Mock API Implementation

The project uses JavaScript to simulate API calls for OTP generation and verification:

\`\`\`javascript
// Send OTP
function mockSendOTP(contact, type) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const otp = Math.floor(100000 + Math.random() * 900000);
      console.log(`OTP sent to ${type}: ${contact}. OTP: ${otp}`);
      sessionStorage.setItem(`${type}Otp`, otp.toString());
      resolve();
    }, 1000);
  });
}

// Verify OTP
function mockVerifyOTP(otp, type) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const storedOtp = sessionStorage.getItem(`${type}Otp`);
      if (otp === storedOtp || otp === '123456') {
        resolve();
      } else {
        reject(new Error('Invalid OTP'));
      }
    }, 1000);
  });
}
\`\`\`

## Future Enhancements

- Connect to a real backend API
- Implement user authentication and authorization
- Add data persistence with a database
- Implement real email and SMS services for OTP delivery
- Add more advanced form validation

## Technologies Used

- HTML5
- CSS3
- JavaScript (ES6+)
- Font Awesome for icons

