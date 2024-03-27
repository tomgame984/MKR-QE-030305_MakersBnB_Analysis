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
# Challenge 2 - Makers BnB - Test Cases
## Spaces Page - Book a Space
### Test Case 1
```
Test purpose:
To check that the "Requests" link redirects the user to the Requests page.

Input / Action:
The user clicks the "Requests" link.

Expected output:
Redirects and loads Requests page.
Assert by title "Requests".

```

### Test Case 2
```
Test purpose:
To check that the "Sign out" link redirects the user to the Homepage and confirms that they have successfully logged out.

Input / Action:
The user clicks the "Sign out" link.

Expected output:
Redirects and loads Homepage.
Displays a message "You have successfully logged out."
Assert by title "Feel at home, anywhere".
Assert by logout message.
```

### Test Case 3
```
Test purpose:
To check that the "List a Space" button redirects the user to the New Space page.

Input / Action:
The user clicks the "List a Space" button.

Expected output:
Redirects and loads "New Space" page.
Assert by the title "List a Space".
```

### Test Case 4
```
Test purpose:
This is to check that when the user accesses the "Available From" field, they cannot enter a date from the past.

Input / Action:
The user enters a date = today - 5 days
Example
Today = 27/03/24 
Date entered = 22/03/24

Expected output:
Assert Error message - "This date is in the past. Please enter a date that is at least the same as today."

```

### Test Case 5
```
Test purpose:
This is to check that when the user accesses the "Available To" field, they cannot enter a date is before the date entered in the "Available from Field"

Input / Action:
The user enters a date that is less than Available From date.
Example
Available from = 27/03/24 
Available to entered = 22/03/24

Expected output:
Assert Error message - "Available date needs to be after Available from date."

```

### Test Case 6
```
Test purpose:
Assuming the dates entered are valid when the "List Spaces" button is clicked, the page refreshes and lists available spaces within the date range provided.

Input / Action:
User enters:
1. Valid Available from date.
2. Valid Available to date.
3. Clicks "List Spaces Button".

Expected output:
Reloaded page, with spaces listed that are available within the specified date range.
Assert that the records displayed are available according to the database.
```

### Test Case 7
```
Test purpose:
This tests what happens if the user enters the date in the wrong format.

Input / Action:
The user enters a date in "Available From" as DD-MM-YY (field specifies DD/MM/YY)

Expected output:
Program automatically replaces "-" with "/" and returns a valid date.
Assert reformatted date displays.
```

### Test Case 8
```
Test purpose:
To test that, when user clicks on a specific space, they are redirected to the Space page displaying the correct space.

Input / Action:
The user clicks on the first property in the list.

Assumption:
Beautiful Relaxing Space is the name of the Space.

Expected output:
Program loads Space page.
Assert title "Beautiful Relaxing Space"
```
