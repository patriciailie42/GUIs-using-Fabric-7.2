# GUIs-using-Fabric-7.2
GUI using Fabric stylesheet and HTMX 

# Introduction
This guide is designed for users who are new to building GUIs in K2View Fabric using HTMX. It will cover how to set up a basic web interface for managing customer data including CRUD operations (Create, Read, Update, Delete).

# Requirements
- K2View Fabric Installation
- Basic understanding of HTML and JavaScript
- Access to K2View Fabric Studio and the database

  
# Steps
Step 1: Define Web Services
Create the necessary web services for interacting with the Customer Logical Unit:

GET to fetch customer details
PUT for updating and inserting customer data
DELETE to remove customer data
Each service should be configured in Fabric Studio with appropriate verbs and paths (e.g., GET /customer/{customerId}).

Step 2: Set Up HTML with HTMX
Create an HTML file that includes:
Form inputs for customer ID, SSN, first name, and last name.
HTMX attributes to bind forms with Fabric web services.

Example HTML snippet for fetching customer data:
```html
<form id="getCustomer" hx-get="http://localhost:3213/api/customer/{customerId}" hx-ext="path-params" hx-target="#customerContent">
    <input type="text" id="customerId" name="customerId" required>
    <button type="submit">Get Customer</button>
</form>
<div id="customerContent"></div>
html```

Step 3: Integrate HTMX for Dynamic Interaction
Include HTMX scripts to manage asynchronous requests without needing to refresh the page. HTMX will help in dynamically loading and submitting data to the server.
<script src="https://unpkg.com/htmx.org"></script>

Step 4: Styling
Apply CSS for basic styling. You can use Fabric's default stylesheet or your custom CSS.
<link rel="stylesheet" href="../styles/k2.css">

Step 5: Test Your Application
Ensure all operations (GET, PUT, DELETE) work as expected:
Test inserting a new customer.
Update customer details and check if they reflect correctly.
Delete a customer and verify removal.

Step 6: Debugging and Validation
Utilize browser developer tools to debug and ensure data flows correctly between the client (HTMX) and server (Fabric). Check console logs for errors or unexpected behaviors.

Benefits of Using HTMX with Fabric
Simplicity: HTMX allows you to interact with server-side logic without writing much JavaScript, making it straightforward to bind HTML directly to Fabric web services.
Efficiency: Reduces the amount of data sent over the network by requesting only needed content, speeding up interactions.
Maintainability: Separation of concerns between the frontend (HTML/HTMX) and backend (Fabric) makes the system easier to maintain and scale.

By following these steps, users can effectively create a responsive web interface for managing customer data in K2View Fabric using HTMX. This setup is ideal for rapid prototyping and can be extended for more complex applications.


Next step is including the GUI in the K2View Fabric Web Framework

# Overview
The K2View Web Framework hosts multiple web applications, streamlining access through a unified interface. Here's how you can integrate your custom GUI into this framework.

Step 1: Understanding the Framework
The Framework hosts applications on the same server, providing a single access point via a structured menu.

Step 2: Accessing the Web Framework
Open the Framework using the URL: http://[Fabric IP address]:[Fabric port]. For local systems, this is usually http://localhost:3213.
Log in using your credentials for Single Sign On (SSO), allowing access to multiple applications with one login.

Step 3: Preparing Your Application
Your application should be ready with basic functionality and UI elements styled using k2.css for consistency with Fabric or your custom CSS for a unique design.

Step 4: Integrating the Application
Update apps.json: Add your application's details to the apps.json file in the Fabric installation directory under K2View\Fabric_[version]\Server\fabric\staticWeb. Example entry:
{
  "name": "My Simple Web App",
  "appId": "myApp",
  "hidden": false
}
Deploy Application Code: Place your application code in a new folder named after the appId within the same directory.

Step 5: Finalizing Integration
Clear your browser's cache to load the new configurations.
Test the application via the Web Framework to ensure it's correctly integrated and functioning.

Step 6: Documentation and Support
For further customization and troubleshooting, refer to the Web Framework API/Styles documentation available within the Framework's menu.
By following these steps, your application will be seamlessly integrated into the K2View Fabric Web Framework, enhancing the overall functionality and user experience.
