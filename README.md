Overview

This project is a simple Node.js microservice that provides basic and advanced mathematical operations via RESTful API endpoints. The service is built using Express.js and logs operations using Winston. Error handling is implemented with meaningful responses for invalid inputs.
Prerequisites
Before running the application, ensure you have the following installed:
•	Node.js and npm (Download from Node.js Official Site)
•	Git (Optional, for version control and pushing code to GitHub)

Project Setup

Follow these steps to set up and run the project:
1.	Install Node.js and npm
o	Download and install Node.js from https://nodejs.org
Verify installation:
node -v
npm -v
2.	Create a new project folder
mkdir sit737-2025-prac4p
cd sit737-2025-prac4p
3.	Initialize the Node.js project
npm init -y
This creates a package.json file with default settings.
4.	Install required dependencies
npm install express winston
o	express: For creating the REST API
o	winston: For logging operations and errors

Microservice Implementation

1. Basic API Endpoints
The microservice provides the following basic arithmetic operations:
Endpoint	Description	Example Request
/add?num1=&num2=	Adds two numbers	/add?num1=5&num2=3 → 8
/subtract?num1=&num2=	Subtracts second number from first	/subtract?num1=10&num2=4 → 6
/multiply?num1=&num2=	Multiplies two numbers	/multiply?num1=3&num2=7 → 21
/divide?num1=&num2=	Divides first number by second	/divide?num1=10&num2=2 → 5
2. Advanced API Endpoints
The microservice also includes advanced mathematical operations:
Endpoint	Description	Example Request
/power?base=&exponent=	Computes power	/power?base=2&exponent=3 → 8
/sqrt?num=	Computes square root	/sqrt?num=16 → 4
/modulo?num1=&num2=	Computes remainder	/modulo?num1=10&num2=3 → 1

Error Handling

The application includes robust error handling for the following cases:
•	Invalid Inputs: If inputs are not numbers, the API returns HTTP 400 Bad Request.
•	Division by Zero: If num2 is 0 in /divide, an error message is returned.
•	Missing Parameters: If required parameters are missing, an appropriate error response is sent.
•	Invalid Operations: The API gracefully handles non-numeric values and returns meaningful error messages.
Example Error Response
{
  "error": "Invalid input: num1 and num2 must be numbers."
}

Logging

A Winston logger is configured to log:
•	INFO Logs: Each API request is logged with details like operation, operands, and results.
•	ERROR Logs: Errors are logged separately in logs/error.log.
Log files:
logs/combined.log → Stores all log entries.
logs/error.log → Stores only error messages.

Running the Application

1.	Start the microservice
node index.js
The service will start on http://localhost:3000.
2.	Test the API Endpoints
o	Open a browser and try: http://localhost:3000/add?num1=5&num2=3
o	Use Postman or cURL for API testing.
Error Handling Report
A short report (error_handling_report.md) is included, explaining:
•	Circuit Breaker: Prevents the system from making repeated failed requests.
•	Retry Mechanism: Automatically retries failed requests.
•	Fallback Mechanism: Provides alternative responses in case of failures.

Documentation

A README.md file includes:
•	API usage
•	Setup instructions
•	Error handling details
•	Logging implementation

Version Control & GitHub
1.	Initialize Git
git init
2.	Add and commit files
git add .
git commit -m "Initial commit"
3.	Push to GitHub
git remote add origin https://github.com/kema94/sit737-2025-prac4p.git
git branch -m main
git push -u origin main

