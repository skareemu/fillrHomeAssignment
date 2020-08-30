# Test Cases for Log in Functionality

### Feature: Log in functionality

**Boundary Value Analysis (BVA) & Equivalence Class Partitioning (ECP) for User Name**  
BVA:- Min chars = 1 & Max value = 64 characters
ECP:- Valid = [(a-z) (A-Z) (0-9)]+	& Invalid = Special chars, Blank Space, Blank Field 

**Boundary Value Analysis (BVA) & Equivalence Class Partitioning (ECP) for Password**  
BVA:- Min chars = 4 & Max value = 6 characters
ECP:- Valid = [(a-z) (A-Z) (0-9)]+	& Invalid = Special chars, Blank Space, Blank Field  
 
Scenario: New Customer log in

	Given a new customer navigates to Signin page
	When the customer click on "Create Account" link
	Then customer is presented with "Create Account" page
	
    Given a new customer navigates to Create Account page
    When the customer enter the following invalid details
			|	username		| password		|
			| min-1@domain		| min value		|
			| max+1@domain		| min value		|
			| min@domain		| min-1 value	|
			| min@domain		| max+1 value	|
			| min-1@domain		| max+1 value	|
			| max+1@domain		| max+1 value	|
			| min-1@domain		| min-1 value	|
			| max+1@domain		| min-1 value	|
			| max@				| min value		|
			| min				| max value		|
			| 					| max value		|
			| min@domain		| 				|
			| 					| 				|
			| max#$%^&@domain	| min value		|
	And click on "Create Account" button
    Then the customer gets error message
	
	Given a new customer navigates to Create Account page
    When the customer enter the following valid details
			|	username	| password		|
			| min@domain	| min value		|
			| min+1@domain	| min+1 value	|
			| max@domain	| max value		|
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
Scenario: Existing Customer log in

    Given an existing customer navigates to Sign in page
    When the customer enter the following invalid details
			|	username		| password		|
			| min-1@domain		| min value		|
			| max+1@domain		| min value		|
			| min@domain		| min-1 value	|
			| min@domain		| max+1 value	|
			| min-1@domain		| max+1 value	|
			| max+1@domain		| max+1 value	|
			| min-1@domain		| min-1 value	|
			| max+1@domain		| min-1 value	|
			| max@				| min value		|
			| min				| max value		|
			| 					| max value		|
			| min@domain		| 				|
			| 					| 				|
			| max#$%^&@domain	| min value		|
	And click on "Sign in" button
    Then the customer gets error message
	
	Given a new customer navigates to Sign in page
    When the customer enter the following valid details
			|	username	| password		|
			| min@domain	| min value		|
			| min+1@domain	| min+1 value	|
			| max@domain	| max value		|
			| Max-1@domain	| max-1 value	|
	And click on "Sign in" button
    Then the customer is presented with home page
	
	Given a new customer navigates to Sign in page
    When the customer enter the valid username
	And enter wrong password 3 times
	And click on "Sign in" button
    Then the customer is presented with 'Account locked' error message
   -------------------
