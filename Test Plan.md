# Agile Test Plan

## 1. Introduction
### Test plan Id: TP_REALogin_001
### Feature Description
Login functionality of the REA website
## 2. User stories
As an existing user   
 I want to enter user credentials  
So that I can log into the website   

As a new user  
 I want to create user credentials  
So that I can log into the website    

As a comeback user  
 I want to ask for forgot user credentials   
So that I can log into the website    
### 2.1 Test Scenarios
#### 2.1.1 Functional Tests
* Verify 'Your email' field with BVA & ECP testing techniques
* Verify 'Your password' field with BVA & ECP testing techniques
* Verify masking/unmasking password link
* Verify Log in Button   
        * Successful log in with valid credentials  
        * Unsuccessful log in with invalid credentials  
        * Account locked when user attempted more than 3 times with wrong email/password
* Verify create account creates an account and logs in user
* Verify comeback user get email and able to log in
#### 2.1.2 Non-Functional Tests(_Usability,Compatibility,Performance,Security etc)
* Cross browser testing ( Chrome, Firefox, Safari, IE )
* Web responsive testing ( iOS devices, Android devices & native, chrome, safari, firefox browsers)
* UX testing based out of inVision app or Ux design screens(static text, logo, font & font sizes etc)
* Accessibility testing
* Basic performance testing(checking response times, trafic, caching etc)
* Basic security testing
#### 2.1.3 API Tests
* Verify log in end point generates authToken and gives 200 OK response code when valid payload is given
   Endpoint: https://xxxxxxxx/account/login  
   Swagger URL: http://xxxxxx/swagger/index.html   
   Valid Payload:  
    {  
     "Password" : "Passxxxx",  
     "Mode" : 0,  
     "Identifier" : "xxxxxxxxx"  
    }
* Verify log in end point for other response codes as per swagger documentation
## 3. Test Scope  
Ticket name: Jira ticket 786  
Summary: Login Functionality  
Build: app-staging-build-1.2.3  
<img src="https://github.com/skareemu/fillrHomeAssignment/blob/master/Login_TC_Mindmapping.png" width="1000"> 
## 4. Test Environment  
* Level 1 Tests – Unit Testing in Dev environment
* Level 2 Tests – API Tests in Dev or CI environment
* Level 3 Tests – Functional/Regression/Exploratory Testing in SIT/Test environment
## 5. Test Approach/Process  
<img src="https://github.com/skareemu/fillrHomeAssignment/blob/master/Testing%20Pyramid.png" width="500">  
* Level 1 Tests – Automated Unit Tests  
* Level 2 Tests – Automated API Tests    
* Level 3 Tests    
       •	Functional tests – Both Manual & Automated    
       •	Regression tests – Automated      
       •	Exploratory tests – Manual    
## 6. Risk and Dependencies  
* API Readiness  
* Test Environment set up  
## 7. Test Deliverables  
* Test Case Design Mindmap   
* Test Plan
* Test Cases
* Defect tracking
* Functional Test Results
* Traceability Matrix
* Updated Regression test Pack
* Updated Smoke test Pack
 


