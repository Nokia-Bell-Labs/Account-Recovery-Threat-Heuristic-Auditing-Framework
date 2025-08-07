# Test case 1 \- Account creation tests

## Goal

The goal of this test case is to check which account state is reached by following the normal account creation process. The account is created by filling out the forms strictly mandatory to move forward with the account creation.  
The results of this test case can already give an indicator on whether some attacks are invalid or not.

## Running the test case

### Actions

1. Use a benign VM  
2. Follow the site’s process to create an account

*Notes for testers:*  
*If prompted, and it’s mandatory to add both a second factor for authentication (MFA) and a recovery method, use different channels.*

## Testcase 1.1. \- Information collected during account creation

### Goal

Collect what information does the site request during the account creation to check if any of this information is used during recovery.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 1.1.1 | What information is requested upon account creation? | Free form text |

## Test case 1.2 \- Default account recovery methods

### Goal

List all possible options for recovery methods and their enforcement (prompted, mandatory, verified)

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 1.2.1 | What is the default recovery method? | Free form (e.g., email, phone) |
| 1.2.2 | Does the service provider clearly state the purpose of the method (that it will be used for recovery)? | Yes (explicit recovery method) No (implicit recovery method) |
| 1.2.3 | Is the default recovery method required while creating the account?  | Prompted (also means optional) Mandatory Verified (this also means mandatory)  |
| 1.2.4 | How is the default recovery method presented in the settings (after account creation)? | `uinfo` \- User information `rm` \- recovery method `mfa` \- MFA factor  |
| 1.2.5 | Are backup recovery codes generated? | Yes No |
| 1.2.6 | Are we prompted to add more than one recovery method? | Yes No |

## Test case 1.3 \- Default MFA methods presented

### Goal

Determine whether recovery methods and multi-factor authentication methods are considered the same. Also, list of all possible options for MFA factors’ nature and enforcement (prompted, mandatory, verified)

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 1.3.1 | What is the default MFA method? | Free form or None, if None, then the rest of the fields in test case 1.3 are N/A |
| 1.3.2 | Does the service provider clearly state the purpose of the method (that it will be used for MFA)? | Yes No |
| 1.3.3 | Is the default MFA method required while creating the account? | Prompted (also means optional) Mandatory Verified (verified is also mandatory)  |
| 1.3.4 | How is the default MFA method presented in the settings (after account creation)? | `uinfo` \- User information `rm` \- recovery method `mfa` \- MFA factor |
| 1.3.5 | Can we add the same method that we used as a recovery method earlier?  *Note: if the same method is observed for both MFA and recovery change one of them. Prioritise phone number for MFA.* | Yes No |
| 1.3.6 | Are backup recovery codes generated? | Yes No |
| 1.3.7 | Are we prompted to add more than one recovery method? | Yes No |

## Test case 1.4 \- Account functionality restrictions

### Goal

To explore what site functionalities (if any) may be restricted after creating a user account.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 1.4.1 | What security settings are we allowed to access after creating the user account? | Free form notes and screenshots |
| 1.4.2 | What site functionalities are restricted after creating a user account?  | Free form notes and screenshots |

## Test case 1 \- Wrap-up

When wrapping up, determine which state does a new account result in, and based on the state that the account is in, continue to the next test case

| Account state | Description | Next testcase |
| :---- | :---- | :---- |
| Abm | Bare minimal Account with username and password | Test case 2 |
| Aur | Account with an unverified recovery method | Test case 3 |
| Avr | Account with a verified recovery method | Test case 4 |
| Aur,mfa | Account with an unverified recovery method and MFA | Test case 3 |
| Avr,mfa | Account with a verified recovery method and MFA | Test case 5 |

### Actions

1. Log in to the account 10 times from the benign VM