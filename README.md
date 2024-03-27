# MKR-QE-030305_MakersBnB_Analysis

# Challenge 2 Notes - Makers BnB
## 1. User Sign Up
### Test Areas
- Email format valid.
- The email is unique (the account is not set up).
- New password initial validation.
- New password confirmation (match vs. mismatch).
___
### Risks
- Duplicating accounts using the same email address.
- Password validation - not meeting criteria.
- Password storage - hashed password.
___
### Assumptions
- Text fields will have a unique ID in HTML.
- Buttons will have a unique ID assigned in the HTML code.
___
### Questions
- What will be the criteria for valid passwords? 
	- Minimum length
	- Lowercase
	- Uppercase
	- Special characters
	- Digits
- What protection will be implemented to keep user login details secret?
____

## 2. User Login
### Test Areas
- Email and password match
- Email correct, password wrong.
- Email wrong, password correct.
- Email wrong, password wrong.
___
### Risks
- Password security.
- HTTPS requirement.
- Bot security
___
### Assumptions
- The backend code will crosscheck the details provided by the user with stored records.
___
### Questions
- What happens when the user enters invalid credentials (emails and/or passwords)?
- Will there be a "Forgot password" option?
- How do they return to the "sign up" page?
- Will there be a failed attempts limit?
____
## 3. Spaces Page
____
### Test Areas
- Available from date cannot be in the past. (TC4)
- Available to date needs to be >= from date. (TC5)
- Different date formats (e.g. dd-mm-yy, ddmmyy, mm/dd/yy) (TC to be confirmed see questions).
- List spaces - Does the date range filter list spaces properly after refresh? (TC6)
- List a space button - redirect New Space page (List a Space)? (TC3)
- Sign out button - redirect to the homepage. (TC2)
- Click on a specific space - redirect to the correct booking form (Space page)
- Requests button - redirect to the Requests page (TC1)
___
### Risks
- Connections between pages via click buttons need to be set up correctly.
- Date format confusion results in false positives.
	- 8th March 2024
	- 08/03/24 (dd/mm/yy).
	- 03/08/24 (mm/dd/yy).
___
### Assumptions
- All spaces listed have been previously validated as genuine.
- All spaces with confirmed bookings will be blocked.
- All user accounts have been validated.
___
### Questions
- How will the user input of the date be formatted correctly? 
- Will there be an embedded calendar for from and to?
- Do the shortcut links at the top of the page need amending to remove "Spaces"?  Otherwise, this would just reload the current page.
- Reconsider the wording of the "list spaces" button.  Possible option "Show me results".
- Are there any further filtering options under consideration for this page?
- Could "Available From" date autofill with today's date?
- Have error messages been defined yet?
- What is the default result of the List Spaces section within the Space page?
- On the spaces page, how will results be sorted (e.g. A-Z)?
- Is it worth replacing MM with mmm, e.g. 03 = Mar?
 ____
