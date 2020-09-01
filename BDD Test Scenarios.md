# Test Cases for Log in Functionality

### Feature: Log in functionality

**Boundary Value Analysis (BVA) & Equivalence Class Partitioning (ECP) for User Name**  
BVA:- Min chars = 1 & Max value = 64 characters
ECP:- Valid = [(a-z) (A-Z) (0-9)]+	& Invalid = Special chars, Blank Space, Blank Field 

**Boundary Value Analysis (BVA) & Equivalence Class Partitioning (ECP) for Password**  
BVA:- Min chars = 4 & Max value = 6 characters
ECP:- Valid = [(a-z) (A-Z) (0-9)]+	& Invalid = Special chars, Blank Space, Blank Field  
 
**Scenario: New Customer log in**

	Given a new customer navigates to Signin page
	When the customer click on "Create Account" link
	Then customer is presented with "Create Account" page
	
    Given a new customer navigates to Create Account page
    When the customer enter the following invalid details
			|	username	| password	|
			| min-1@domain		| min value	|
			| max+1@domain		| min value	|
			| min@domain		| min-1 value	|
			| min@domain		| max+1 value	|
			| min-1@domain		| max+1 value	|
			| max+1@domain		| max+1 value	|
			| min-1@domain		| min-1 value	|
			| max+1@domain		| min-1 value	|
			| max@			| min value	|
			| min			| max value	|
			| 			| max value	|
			| min@domain		| 		|
			| 			| 		|
			| max#$%^&@domain	| min value	|
	And click on "Create Account" button
    Then the customer gets error message
	
	Given a new customer navigates to Create Account page
    When the customer enter the following valid details
			|username	| password	|
			| min@domain	| min value	|
			| min+1@domain	| min+1 value	|
			| max@domain	| max value	|
			| Max-1@domain	| max-1 value	|
	And click on "Create Account" button
    Then the customer is presented with home page
	
	Given a new customer navigates to Signin page
	When the customer click on "Continue with Google" button
	And enter the credentials on Google log in page
	And click on continue
	Then customer is presented with home page
	
	Given a new customer navigates to Signin page
	When the customer click on "Continue with Facebook" button
	And enter the credentials on Facebook log in page
	And click on continue
	Then customer is presented with home page
	
	Given a new customer navigates to Signin page
	When the customer click on "Continue with Apple" button
	And enter the credentials on Apple log in page
	And click on continue
	Then customer is presented with home page
	
-------------------	
**Scenario: Existing Customer log in**

    Given an existing customer navigates to Sign in page
    When the customer enter the following invalid details
			|	username	| password	|
			| min-1@domain		| min value	|
			| max+1@domain		| min value	|
			| min@domain		| min-1 value	|
			| min@domain		| max+1 value	|
			| min-1@domain		| max+1 value	|
			| max+1@domain		| max+1 value	|
			| min-1@domain		| min-1 value	|
			| max+1@domain		| min-1 value	|
			| max@			| min value	|
			| min			| max value	|
			| 			| max value	|
			| min@domain		| 		|
			| 			| 		|
			| max#$%^&@domain	| min value	|
	And click on "Sign in" button
    Then the customer gets error message
	
	Given a new customer navigates to Sign in page
    When the customer enter the following valid details
			|username	| password	|
			| min@domain	| min value	|
			| min+1@domain	| min+1 value	|
			| max@domain	| max value	|
			| Max-1@domain	| max-1 value	|
	And click on "Sign in" button
    Then the customer is presented with home page
	
	Given a new customer navigates to Sign in page
    When the customer enter the valid username
	And enter wrong password 3 times
	And click on "Sign in" button
    Then the customer is presented with 'Account locked' error message
    
    Given a new customer navigates to Sign in page
    When the customer enter the valid username
	And enter password
	And click on "show" link
    Then the customer is able to see the typed in password
   -------------------
**Scenario: Comeback Customer log in**

	Given an existing customer(comeback) navigates to Sign in page
	When the customer clicks on 'Forgot your password?' link
	Then the customer is presented with Forgot password screen
	And the customer see the 'Go back to Sign in' link
	And upon click on it takes the user to sign page

	Given an existing customer(comeback) is in Forgot password screen  
	When the customer enter following invalid email address  
            		|  Email adress		|  
			| min-1@domain		|  
			| max+1@domain		|  
			| min@domain		|  
			| min@domain		|  
			| min-1@domain		|  
			| max+1@domain		|  
			| min-1@domain		|  
			| max+1@domain		|  
			| max@			|  
			| min			|  
			| 			|
			| min@domain		|  
			|                   	|  
			| max#$%^&@domain	|   
	and click on 'Reset my password' button  
	Then the customer is presented with Error message  

	Given an existing customer(comeback) is in Forgot password screen
	When the customer enter following invalid email address   
			|	Email adress    |   
			| min@domain		|   
			| max@domain		|   
			| min+1@domain		|   
			| max-1@domain		|   
	And click on 'Reset my password' button     
	Then the customer is presented with 'Update your password'      
	And email is sent to the customer's email address

	Given an existing(comeback) customer is in 'Update your password'   
	And the customer is ready with the password code(from email)    
	When the customer enters invalid/expired code, new password and confirm password    
	And click on 'Change password'      
	Then the customer is presented with the error message   

	Given an existing(comeback) customer is in 'Update your password'   
	And the customer is ready with the password code(from email)    
	When the customer enters valid code, new password and confirm password  
	And click on 'Change password'  
	Then the customer is presented with the sign in page    
	And upon entering valid email address and new password  
	And click on 'Sign in' button takes the customer to home page  
	
-------------------
**Scenario: Non-Functional scenarios**

	Given an existing/new/comeback customer is in sign in/forgot password/create account page
	When the customer examine for all the static text, logo, font and font sizes
	Then the customer will see all of them are aligned properly with UX
	
	Given an existing/new/comeback opens the sign in page with the following browsers
			|	Browsers  	|   
			|      Chrome		|   
			|      Firefox		|   
			|      Safari		|   
	When the customer navigates through sign in/forgot password/create account pages
	Then the customer will see the same functionality across all browsers
	
	Given an existing/new/comeback opens the sign in page with the following mobile browsers
			|	Browsers  	|   Device		|
			|      Chrome		|   ios, android	|
			|      Firefox		|   ios, android	|  
			|      Safari		|   ios			| 
			|      Native		|   android		|
	When the customer navigates through sign in/forgot password/create account pages
	Then the customer will see the same functionality across all browsers
