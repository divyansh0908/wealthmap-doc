---
# WealthMap Full-Stack Application

WealthMap is a full-stack application that helps users manage and visualize wealth-related data using maps and intuitive UI. The project is built using **React 19**, **Vite**, **Tailwind CSS**, and **TanStack Router** on the frontend, with a **Node.js**, **Express**, and **MongoDB** backend. It also supports features like Google Maps integration, JWT authentication, cloud storage, and scheduled tasks.

---

##  Tech Stack

### Frontend

- React 19 with Vite
- Tailwind CSS 4 + Tailwind Plugins
- TanStack Router & React Query
- Radix UI + Lucide Icons
- Google Maps API
- React Hook Form
- TypeScript

### Backend

- Node.js + Express
- MongoDB (via Mongoose)
- JWT Authentication
- Google Cloud Storage
- Nodemailer for Emails
- MQTT + node-cron

---

## Project Structure

wealthmap
   - frontend/ # React + Vite app
   - backend/ # Node.js + Express server


---

##  Getting Started

### Prerequisites

- Node.js v18+
- Yarn or npm
- MongoDB Atlas or Local instance
- Google Cloud Project with Storage enabled

---

##  Installation Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Aditys018/WealthApp.git
cd WealthApp
```
##  Set Up Environment Variables
Backend .env
Create a .env file inside the backend/ folder:
```
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
EMAIL_USER=your_email@example.com
EMAIL_PASS=your_email_password
GCLOUD_PROJECT=your_project_id
GCLOUD_CLIENT_EMAIL=your_client_email
GCLOUD_PRIVATE_KEY=your_private_key
GCLOUD_BUCKET=your_bucket_name
```
Frontend .env 

```
VITE_GOOGLE_MAPS_API_KEY=your_google_maps_api_key

```

## Running the app locally

# Frontend
```
cd frontend
yarn install
yarn dev
```
# Backend

```
cd backend
yarn install
yarn dev:server
```
For any queries or contributions, please reach out at [WealthApp](https://github.com/Aditys018/WealthApp) or create a GitHub issue.
---


<h2 id="admin-features">Admin Features</h2>
<p>WealthApp provides a comprehensive set of admin features for company management:</p>
<h3 id="company-management">Company Management</h3>
<ul>
<li><strong>Company Registration</strong> Users can register a company and automatically become the company admin</li>
<li><strong>Company Information Management</strong>: Company admins can view and update company details</li>
<li><strong>Company Data Access Preferences</strong>: Company admins can set company-wide data access preferences</li>
</ul>
<h3 id="employee-management">Employee Management</h3>
<ul>
<li><strong>Employee Invitation</strong>: Company admins can invite employees via email</li>
<li><strong>Permission Management</strong>: Company admins can manage employee permission levels</li>
<li><strong>Activity Monitoring</strong>: Company admins can view employee activity and usage statistics</li>
<li><strong>Access Control</strong>: Company admins can revoke access for former employees</li>
</ul>
<h2 id="user-authentication-and-security">User Authentication and Security</h2>
<h3 id="email-notifications">Email Notifications</h3>
<ul>
<li><strong>Registration Confirmation</strong>: Users receive an email confirmation after successful registration</li>
<li><strong>Login OTP Verification</strong>: Two-factor authentication with OTP sent via email during login</li>
<li><strong>Employee Invitations</strong>: Employees receive email invitations with clear instructions and temporary credentials</li>
</ul>
<h3 id="otp-verification">OTP Verification</h3>
<ul>
<li><strong>Login Security</strong>: Enhanced security with one-time passwords for login verification</li>
<li><strong>Time-Limited OTPs</strong>: OTPs expire after 10 minutes for improved security</li>
<li><strong>Resend Functionality</strong>: Users can request a new OTP if needed</li>
</ul>
<h2 id="employee-onboarding">Employee Onboarding</h2>
<h3 id="secure-account-setup">Secure Account Setup</h3>
<ul>
<li><strong>Email Invitations</strong>: Employees receive email invitations with clear instructions</li>
<li><strong>Secure Password Requirements</strong>: Passwords must meet strict security requirements (length, complexity, etc.)</li>
<li><strong>Multi-Factor Authentication</strong>: Employees can set up MFA for enhanced account security</li>
</ul>
<h3 id="terms-and-onboarding">Terms and Onboarding</h3>
<ul>
<li><strong>Terms of Service</strong>: Employees must review and accept the terms of service</li>
<li><strong>Onboarding Tutorial</strong>: Step-by-step tutorial to help employees learn the platform</li>
<li><strong>Notification Preferences</strong>: Employees can customize how they receive notifications</li>
</ul>
<h2 id="api-documentation">API Documentation</h2>
<h3 id="authentication-apis">Authentication APIs</h3>
<ul>
<li><code>POST /user/login</code>
<ul>
<li><strong>Description</strong>: Login with email and password (triggers OTP email)</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>email</code> (string, required): User’s email address</li>
<li><code>password</code> (string, required): User’s password</li>
</ul>
</li>
<li><strong>Response</strong>: OTP details for verification</li>
</ul>
</li>
<li><code>POST /user/verify-otp</code>
<ul>
<li><strong>Description</strong>: Verify the OTP sent during login</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>email</code> (string, required): User’s email address</li>
<li><code>otp</code> (string, required): One-time password received via email</li>
<li><code>otpId</code> (string, required): OTP identifier</li>
</ul>
</li>
<li><strong>Response</strong>: Authentication tokens and user details</li>
</ul>
</li>
<li><code>POST /user/resend-otp</code>
<ul>
<li><strong>Description</strong>: Request a new OTP for verification</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>email</code> (string, required): User’s email address</li>
</ul>
</li>
<li><strong>Response</strong>: New OTP details</li>
</ul>
</li>
<li><code>POST /user/change-password</code>
<ul>
<li><strong>Description</strong>: Change user password</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>oldPassword</code> (string, required): Current password</li>
<li><code>newPassword</code> (string, required): New password (min 8 characters)</li>
</ul>
</li>
<li><strong>Response</strong>: Success message</li>
</ul>
</li>
<li><code>GET /user/random-wealth</code>
<ul>
<li><strong>Description</strong>: Get random wealth information</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN, EMPLOYEE)</li>
<li><strong>Response</strong>: Random wealth data</li>
</ul>
</li>
<li><code>POST /user/upload</code>
<ul>
<li><strong>Description</strong>: Upload files</li>
<li><strong>Request Body</strong>:
<ul>
<li>Files (multipart/form-data)</li>
</ul>
</li>
<li><strong>Response</strong>: Uploaded file links</li>
</ul>
</li>
</ul>
<h3 id="identity-apis">Identity APIs</h3>
<ul>
<li><code>POST /identity/token</code>
<ul>
<li><strong>Description</strong>: Get a new access token using a refresh token</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>refreshToken</code> (string, required): Valid refresh token</li>
</ul>
</li>
<li><strong>Response</strong>: New access token</li>
</ul>
</li>
<li><code>POST /identity/send-otp</code>
<ul>
<li><strong>Description</strong>: Send an OTP to an email address</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>firstName</code> (string, required): Recipient’s first name</li>
<li><code>email</code> (string, required): Recipient’s email address</li>
</ul>
</li>
<li><strong>Response</strong>: OTP details</li>
</ul>
</li>
</ul>
<h3 id="company-apis">Company APIs</h3>
<h4 id="company-management-1">Company Management</h4>
<ul>
<li><code>POST /company/register</code>
<ul>
<li><strong>Description</strong>: Register a new company (automatically becomes company admin)</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>name</code> (string, required): Company name</li>
<li><code>logo</code> (string, optional): Company logo URL</li>
<li><code>description</code> (string, optional): Company description</li>
<li><code>website</code> (string, optional): Company website URL</li>
<li><code>industry</code> (string, optional): Company industry</li>
<li><code>email</code> (string, required): Admin email</li>
<li><code>password</code> (string, required): Admin password (min 8 chars, must include uppercase, lowercase, number, special char)</li>
<li><code>otp</code> (string, required): OTP for verification</li>
<li><code>otpId</code> (string, required): OTP identifier</li>
<li><code>size</code> (string, optional): Company size (1-10, 11-50, 51-200, 201-500, 501-1000, 1000+)</li>
<li><code>address</code> (object, optional): Company address</li>
<li><code>contactEmail</code> (string, optional): Contact email</li>
<li><code>contactPhone</code> (string, optional): Contact phone</li>
<li><code>dataAccessPreferences</code> (object, optional): Data access preferences</li>
</ul>
</li>
<li><strong>Response</strong>: Company and admin details</li>
</ul>
</li>
<li><code>PUT /company/:id</code>
<ul>
<li><strong>Description</strong>: Update a company’s information</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN)</li>
<li><strong>Path Parameters</strong>:
<ul>
<li><code>id</code> (string, required): Company ID</li>
</ul>
</li>
<li><strong>Request Body</strong>: Company data to update</li>
<li><strong>Response</strong>: Updated company details</li>
</ul>
</li>
</ul>
<h4 id="employee-management-1">Employee Management</h4>
<ul>
<li><code>POST /company/:companyId/employees/invite</code>
<ul>
<li><strong>Description</strong>: Invite an employee to join the company</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN)</li>
<li><strong>Path Parameters</strong>:
<ul>
<li><code>companyId</code> (string, required): Company ID</li>
</ul>
</li>
<li><strong>Request Body</strong>:
<ul>
<li><code>email</code> (string, required): Employee’s email</li>
<li><code>role</code> (string, required): Employee’s role</li>
<li><code>firstName</code> (string, optional): Employee’s first name</li>
<li><code>lastName</code> (string, optional): Employee’s last name</li>
</ul>
</li>
<li><strong>Response</strong>: Employee details</li>
</ul>
</li>
<li><code>GET /company/:companyId/employees</code>
<ul>
<li><strong>Description</strong>: Get all employees of a company</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN)</li>
<li><strong>Path Parameters</strong>:
<ul>
<li><code>companyId</code> (string, required): Company ID</li>
</ul>
</li>
<li><strong>Response</strong>: List of employees</li>
</ul>
</li>
<li><code>DELETE /company/:companyId/employees/:employeeId</code>
<ul>
<li><strong>Description</strong>: Revoke an employee’s access</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN)</li>
<li><strong>Path Parameters</strong>:
<ul>
<li><code>companyId</code> (string, required): Company ID</li>
<li><code>employeeId</code> (string, required): Employee ID</li>
</ul>
</li>
<li><strong>Response</strong>: Success message</li>
</ul>
</li>
<li><code>GET /company/:companyId/employees/:employeeId/activities</code>
<ul>
<li><strong>Description</strong>: Get employee activities</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN)</li>
<li><strong>Path Parameters</strong>:
<ul>
<li><code>companyId</code> (string, required): Company ID</li>
<li><code>employeeId</code> (string, required): Employee ID</li>
</ul>
</li>
<li><strong>Response</strong>: Employee activity logs</li>
</ul>
</li>
</ul>
<h3 id="places-apis">Places APIs</h3>
<ul>
<li><code>GET /places/list-properties</code>
<ul>
<li><strong>Description</strong>: Get a list of properties</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN, EMPLOYEE)</li>
<li><strong>Query Parameters</strong>:
<ul>
<li><code>lat</code> (number, optional): Latitude (default: 40.7589)</li>
<li><code>long</code> (number, optional): Longitude (default: -73.9851)</li>
<li><code>radius</code> (number, optional): Search radius in miles (default: 5)</li>
<li><code>page</code> (number, optional): Page number (default: 1)</li>
<li><code>listingStatus</code> (string, optional): Listing status (default: “Sold”)</li>
<li><code>propertyType</code> (string, optional): Property type</li>
</ul>
</li>
<li><strong>Response</strong>: List of properties</li>
</ul>
</li>
<li><code>GET /places/property/:id</code>
<ul>
<li><strong>Description</strong>: Get details of a specific property</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN, EMPLOYEE)</li>
<li><strong>Path Parameters</strong>:
<ul>
<li><code>id</code> (string, required): Property ID</li>
</ul>
</li>
<li><strong>Response</strong>: Property details</li>
</ul>
</li>
<li><code>GET /places/property-types</code>
<ul>
<li><strong>Description</strong>: Get all property types</li>
<li><strong>Authentication</strong>: Required (ADMIN, COMPANY_ADMIN, EMPLOYEE)</li>
<li><strong>Response</strong>: List of property types</li>
</ul>
</li>
</ul>

