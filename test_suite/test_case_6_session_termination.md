# Test case 6 \- Session termination

## Goal

The goal of this test case is understand what’s the impact of a successful account recovery on different type of user sessions. We want to evaluate if the following sessions are terminated on successful reset of the password:

* **Logged-in session:** this is a user session that’s authenticated with the old password before the account recovery  
* **Intermediate login session:** this is a rare cas where the password reset happens parallel to a login session.   
* **Intermediate recovery session:** this is the scenario where there are multiple recovery sessions happening in parallel.

There are two scenarios under which we evaluate session termination:

* When both the parallel session and the password recovery happen from benign machines  
* When the parallel session is running on a benign machine, and the recovery is triggered from a malicious machine

## Testcase 6.1. \- Logged-in session termination upon a benign recovery

### Goal

In this test case, we trigger account recovery from a benign machine, while the user is logged in from another benign machine. We observe whether the user is given the opportunity to terminate the existing logged-in sessions or whether the sessions are terminated automatically. We also observe whether the logged-in session is used as a communication channel to alert the user about recovery attempts.

### Actions

| Actions on benign VM1 | Actions on benign VM2 |
| :---- | :---- |
| Log in to the account  |  |
|  | Trigger account recovery Complete the account recovery and change the password to a new one |
| Click on a button in the interface of this logged in session (to check if the session is terminated or not) If the session is terminated, try to log in again with the new credentials |  |

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 6.1.1 | What happens to the active session in VM1 upon a successful account recovery and password reset? | Service provider automatically logs out of that session Service provider presents the user a list of active sessions and gives them the option to log out of the other active sessions The service provider doesn’t log out of the session in VM1 nor do they give the user the option to log out of that session Service provider presents an optional checkbox to re-authenticate on existing sessions |
| 6.1.2 | If the service provider automatically logged out of the session in VM1, after logging in again:  Is there any extra verification required when re-logging in from VM1? What kind? | Yes, kind: \_\_\_\_\_ No |
| 6.1.3 | Does the user receive an alert when VM2 starts the password recovery process? If yes, what are the contents of the alert? | Yes, contents:\_\_\_\_\_\_ No  |
| 6.1.4 | Does the user receive an alert when VM2 successfully completes the password recovery process? If yes, what are the contents of the alert? | Yes, contents:\_\_\_\_\_\_ No  |
| 6.1.5 | What kind of channel is used for alerts? | Free form text  |

## Test case 6.2 \- Intermediate login session termination upon a benign recovery

### Goal

This is a rare case where password reset happens parallel to a login session. Suppose the user has enabled MFA for a website such that password and MFA tokens are expected from a new login. We assume that a new password has been set from a recovery session while there is a parallel, incomplete login session where the user has entered the old password but not the MFA token.   
We observe whether the log-in session is terminated and the user is requested to re-authenticate or whether the log-in session is allowed to continue successfully despite being authenticated with the old password.

### Actions

| Actions on benign VM1 | Actions on benign VM2 |
| :---- | :---- |
| If there are no MFA methods added to the account, add one. Start a log in process Enter the username and password, but stop when you’re prompted to enter the MFA factor |  |
|  | Trigger account recovery Complete the account recovery and change the password to a new one |
| Complete the MFA verification |  |

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 6.2.1 | What happens after the MFA verification is completed in the intermediate log in session in VM1? | The login process succeeds The login process fails |

## Test case 6.3 \- Intermediate recovery session termination upon a benign recovery

### Goal

We assume there are multiple parallel recovery sessions. In such a race condition, if one of the recovery sessions leads to a successful password reset, we observe the behavior of the rest of the intermediate sessions. If the intermediate sessions were not terminated, we noted down the password that is reflected as the new password among the first completed and first triggered recovery sessions.

### Actions

| Actions on benign VM1 | Actions on benign VM2 |
| :---- | :---- |
| Trigger account recovery Click on the link/enter the OTP into the service, but don’t submit the new password (`new_pw1`) yet. |  |
|  | Trigger account recovery Complete the account recovery and change the password to a new one (`new_pw2`) |
| Go back to the intermediate recovery session in this machine and enter the `new_pw1` as the new password in the account Try to log in with `new_pw1` and `new_pw2` to see which password was successfully set for the account. |  |

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 6.3.1 | What happens after `new_pw1` is entered in the intermediate recovery session in VM1? | The password change succeeds and the final password of the account is `new_pw1` The password change fails and the final password of the account is `new_pw2` The password change is shown as successful, but the final password on the account is `new_pw2` |

## Testcase 6.4 \- Logged-in session termination upon a malicious recovery

### Goal

In this test case, we trigger account recovery from a malicious machine, while the user is logged in from another benign machine. We observe whether the user is given the opportunity to terminate the existing logged-in sessions or whether the sessions are terminated automatically. We also observe whether the logged-in session is used as a communication channel to alert the user about recovery attempts.

### Actions

| Actions on benign VM1 | Actions on malicious VM3 |
| :---- | :---- |
| Log in to the account  |  |
|  | Trigger account recovery Complete the account recovery and change the password to a new one |
| Click on a button in the interface of this logged in session (to check if the session is terminated or not) If the session is terminated, try to log in again with the new credentials |  |

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 6.4.1 | What happens to the active session in VM1 upon a successful account recovery and password reset? | Service provider automatically logs out of that session Service provider presents the user a list of active sessions and gives them the option to log out of the other active sessions The service provider doesn’t log out of the session in VM1 nor do they give the user the option to log out of that session Service provider presents an optional checkbox to re-authenticate on existing sessions |
| 6.4.2 | If the service provider automatically logged out of the session in VM1, after logging in again:  Is there any extra verification required when re-logging in from VM1? What kind? | Yes, kind: \_\_\_\_\_ No |
| 6.4.3 | Does the user receive an alert when VM3 starts the password recovery process? If yes, what are the contents of the alert? | Yes, contents:\_\_\_\_\_\_ No  |
| 6.4.4 | Does the user receive an alert when VM2 successfully completes the password recovery process? If yes, what are the contents of the alert? | Yes, contents:\_\_\_\_\_\_ No  |
| 6.4.5 | What kind of channel is used for alerts? | Free form text  |

## Test case 6.5 \- Intermediate login session termination upon a malicious recovery

### Goal

This is a rare case where password reset happens parallel to a login session. Suppose the user has enabled MFA for a website such that password and MFA tokens are expected from a new login. We assume that a new password has been set from a recovery session while there is a parallel, incomplete login session where the user has entered the old password but not the MFA token.   
We observe whether the log-in session is terminated and the user is requested to re-authenticate or whether the log-in session is allowed to continue successfully despite being authenticated with the old password.

### Actions

| Actions on benign VM1 | Actions on malicious VM3 |
| :---- | :---- |
| If there are no MFA methods added to the account, add one. Start a log in process Enter the username and password, but stop when you’re prompted to enter the MFA factor |  |
|  | Trigger account recovery Complete the account recovery and change the password to a new one |
| Complete the MFA verification |  |

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 6.5.1 | What happens after the MFA verification is completed in the intermediate log in session in VM1? | The login process succeeds The login process fails |

## Test case 6.6 \- Intermediate recovery session termination upon a malicious recovery

### Goal

We assume there are multiple parallel recovery sessions. In such a race condition, if one of the recovery sessions leads to a successful password reset, we observe the behavior of the rest of the intermediate sessions. If the intermediate sessions were not terminated, we noted down the password that is reflected as the new password among the first completed and first triggered recovery sessions.

### Actions

| Actions on benign VM1 | Actions on malicious VM3 |
| :---- | :---- |
| Trigger account recovery Click on the link/enter the OTP into the service, but don’t submit the new password (`new_pw1`) yet. |  |
|  | Trigger account recovery Complete the account recovery and change the password to a new one (`new_pw2`) |
| Go back to the intermediate recovery session in this machine and enter the `new_pw1` as the new password in the account Try to log in with `new_pw1` and `new_pw2` to see which password was successfully set for the account. |  |

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 6.6.1 | What happens after `new_pw1` is entered in the intermediate recovery session in VM1? | The password change succeeds and the final password of the account is `new_pw1` The password change fails and the final password of the account is `new_pw2` The password change is shown as successful, but the final password on the account is `new_pw2` |

## Test case 6 \- Wrap up

After this test case, move to test case 7  