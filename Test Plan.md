# Test Plan

## 1. Introduction
### Test plan Id: TP_REALogin_001
### Feature Description
Login functionality of the REA website
### 2. User stories
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
#### Functional Tests
* Verify 'Your email' field with BVA & ECP testing techniques
* Verify 'Your password' field with BVA & ECP testing techniques
* Verify masking/unmasking password link
* Verify Log in Button   
        * Successful log in with valid credentials  
        * Unsuccessful log in with invalid credentials  
        * Account locked when user attempted more than 3 times with wrong email/password
* Verify create account creates an account and logs in user
* Verify comeback user get email and able to log in
