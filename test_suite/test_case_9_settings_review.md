# Test case 9 \- Settings review

## Goal

The goal in this test case is to comprehensively analyze account settings presented by the service providers. These settings are used to reflect the state of various security features offered and nudge the users to utilize such features to improve the security posture of their accounts.  
Additionally, this test checks whether the service provider allows certain changes to the account’s security settings or if they are limited/require additional authentication, both before and after recovery.

## Running the test case

### Actions

1. Use the benign VM  
2. Log in to the service and review the account settings  
3. Use the benign VM  
   1. Trigger a successful account recovery  
   2. Log out (if necessary)  
   3. Log in to the service  
   4. Review the account settings  
4. Use the malicious VM  
   1. Trigger a successful account recovery  
   2. Log out (if necessary)  
   3. Log in to the service  
   4. Review the account settings

## Testcase 9.1. \- Account settings review

### Goal

### Actions

1. Use the benign VM  
2. Log in to the service and review the account settings  
3. Review the Activity log (if it exists)  
4. Review the Recovery methods settings  
5. Review the MFA settings  
6. Make notes about the presentation of these settings in the UI

### Questions

| Test case number | Question |  | Answer type |
| ----- | :---- | :---- | :---- |
| **9.1.1 Activity log review** |  |  |  |
| 9.1.1.1 | Does the service keep a list of sessions? |  | Yes No  |
| 9.1.1.2 | If the service keeps a list of sessions (9.1.1), what kind of information do we have in the list of sessions?  *(e.g., IP address, whether it’s the current active session or not, location, last access timestamp, details about the device)* |  | Free text |
| 9.1.1.3 | Does the service keep a tamperproof log of user actions? |  | Yes No  |
| The following questions are only filled in if the tamperproof log of actions (9.1.1.3) exists. We cover what information is included in the tamperproof log? |  |  |  |
| 9.1.1.3.1 | Does the access log clearly show successful account recovery events? |  | Yes No  |
| 9.1.1.3.2 | Does the access log clearly show the reason for a password change? *For example, to differentiate between a password reset due to account recovery and a user just changing their password from the settings.* |  | Yes No  |
| 9.1.1.3.3 | Does the access log show new logins clearly? |  | Yes No |
| 9.1.1.3.4 | Does the access log show entries for multiple failed recovery attempts (or suspicious activity)? |  | Yes No |
| 9.1.1.3.5 | What other events are shown in the activity log? |  | Free text |
| **9.1.2 Recovery methods** For each available recovery method, add the method (if possible) and fill the information in the cells |  |  |  |
| 9.1.2.1 | Email used during registration (as username) | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Is the verification of the method mandatory? | Yes No |
| 9.1.2.2 | Phone number | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Is the verification of the method mandatory? | Yes No |
| 9.1.2.3 | Recovery/second email (explicitly added) | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Is the verification of the method mandatory? | Yes No |
| **9.1.3 Multi Factor Authentication (MFA) methods** For each available MFA factor, attempt to add the second factor (if possible) and fill the information in the cells. We’re interested in knowing if there are restrictions or additional authentication required for changing settings. |  |  |  |
| 9.1.3.1 | Phone number (SMS) | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| 9.1.3.2 | Authenticator app (totp, offline) | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| 9.1.3.3 | Authenticator app (online, push notifications) | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| 9.1.3.4 | Security key | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A  |
| 9.1.3.5 | Secondary email | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| 9.1.3.6 | Approve login from another session | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| 9.1.3.7 | Backup codes | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| 9.1.3.6 | Passkeys | How clearly is the purpose of the recovery method conveyed to the user? | implicit explicit |
|  |  | Are there any preconditions that need to be met before this method can be added? *For example: the email needs to be verified, phone number added before authenticator app, etc.* | Free text or N/A |
| **9.1.4 Settings UI/UX Presentation** |  |  |  |
| 9.1.4.1 | How are the different options for recovery methods presented to the user? *(for example, is the unverified nature of a method conveyed in the UI to the user? Is there a clear distinction between enabled and disabled methods?)* |  | Free text notes \+ screenshots |
| 9.1.4.2 | How are the different options for MFA factors presented to the user? *(for example, is there a clear distinction between enabled and disabled factors?)* |  | Free text notes \+ screenshots |
| 9.1.4.3 | Is there an explicit distinction between the way that MFA and recovery methods are presented to the user? *(for example, are they in the same section of the UI or different? Are they called by different names?)* |  | Free text notes \+ screenshots |

## Test case 9.2 \- Security settings review before recovery

### Goal

The goal of this test case is to evaluate whether there is additional authentication or confirmation required before changing security-related settings in the account. This establishes a baseline to compare to with test cases 9.3 and 9.4, which test the same thing but directly after a successful recovery from benign and malicious machines.

### Actions

1. Use the benign VM  
2. Log in to the service  
3. For each of the actions in the table, try to do them and take notes about whether it’s possible to do the action and note down any additional confirmation that may be required before taking the action.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 9.2.1 | **Action: remove MFA** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.2.2 | **Action: remove recovery factor** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.2.3 | **Action: add MFA** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.2.4 | **Action: add recovery factor** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.2.5 | **Action: revoke access to existing sessions** Were you able to do the action? Was there any extra authentication required?  *Note: make sure you’re logged in another tab or window.* | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |

## Test case 9.3 \- Security settings review after recovery from a benign machine

### Goal

The goal of this test case is to evaluate whether there is additional authentication or confirmation required before changing security-related settings in the account directly after a recovery from a benign machine. We want to compare this to the results from test case 9.2.

### Actions

1. Use the benign VM  
2. Trigger an account recovery  
3. Log out (if necessary)  
4. Log in to the service  
5. For each of the actions in the table, try to do them and take notes about whether it’s possible to do the action and note down any additional confirmation that may be required before taking the action.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 9.3.1 | **Action: remove MFA** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.3.2 | **Action: remove recovery factor** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.3.3 | **Action: add MFA** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.3.4 | **Action: add recovery factor** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.3.5 | **Action: revoke access to existing sessions** Were you able to do the action? Was there any extra authentication required?  *Note: make sure you’re logged in another tab or window.* | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |

## Test case 9.4 \- Security settings review after a recovery from a malicious machine

The goal of this test case is to evaluate whether there is additional authentication or confirmation required before changing security-related settings in the account directly after a recovery from a malicious machine. We want to compare this to the results from test case 9.2.

### Actions

1. Use the malicious VM  
2. Trigger an account recovery  
3. Log out (if necessary)  
4. Log in to the service  
5. For each of the actions in the table, try to do them and take notes about whether it’s possible to do the action and note down any additional confirmation that may be required before taking the action.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 9.4.1 | **Action: remove MFA** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.4.2 | **Action: remove recovery factor** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.4.3 | **Action: add MFA** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.4.4 | **Action: add recovery factor** Were you able to do the action? Was there any extra authentication required?  | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |
| 9.4.5 | **Action: revoke access to existing sessions** Were you able to do the action? Was there any extra authentication required?  *Note: make sure you’re logged in another tab or window.* | Yes, no extra authentication Yes, extra authentication: \_\_\_\_ No, option is greyed out No, action not allowed due to an account “lock” as communicated by the service provider No, reason:\_\_\_\_\_  |

## Test case 9 \- Wrap up

You are done and can now review the results.
