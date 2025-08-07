# Test case 8 \- Interchangeability between recovery and MFA methods

## Goal

This test case extends the idea introduced in test case 7 of checking whether multiple factors (if available) are used during the recovery process. In particular, our goal is to analyze the behavior of the service provider when there is a pool of multiple recovery and MFA methods and whether those can be used interchangeably during login and recovery.  
For example, if the user claims to not have access to an MFA method, we check whether it would be enough to use a recovery method as a second channel for login. Similarly, if the user is recovering their account and cannot access one of the recovery methods, we check if they can use an MFA method instead for recovery.

## Running the test case

### Actions

1. Make sure that the account has two recovery methods and at least one MFA method.  
   1. If they don’t exist, add these from the benign VM  
2. Use a malicious VM to log in  
   1. Log in to the account from a clean session (incognito window)  
   2. When prompted for MFA, claim that you don’t have access to it  
   3. See what alternatives are presented to you.  
3. Use a malicious VM to trigger recovery  
   1. Trigger recovery  
   2. When prompted for MFA during recovery, claim that you don’t have access to it

## Testcase 8.1. \- Use of recovery methods as MFA factors during login

### Goal

Evaluate the behavior of the service provider when the user has no access to MFA methods. Check if a recovery method can be used as a second factor when logging in.

### Actions

1. Make sure that the account has two recovery methods and at least one MFA method.  
   1. If they don’t exist, add these from the benign VM  
2. Use a malicious VM  
3. Log in to the account from a clean session (incognito window)  
4. When prompted for MFA, claim that you don’t have access to it  
5. See what alternatives are presented to you.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 8.1.1 | Which recovery methods are listed as alternatives? | Multiple choice: None Phone number/SMS Email Other: \_\_\_\_ |

## Test case 8.2 \- Use of recovery methods as MFA factors during a recovery

### Goal

The goal of this test case is to evaluate the behavior of the service provider when the user has no access to MFA methods. Check if a recovery method can be used as a second factor for account recovery.

This test case requires that the MFA factors are used as a second factor for recovery (see results test case 7 to determine if the service uses MFA during recovery).

### Actions

1. Make sure that the account has two recovery methods and at least one MFA method.  
   1. If they don’t exist, add these from the benign VM  
2. Use a malicious VM  
3. Trigger recovery  
4. When prompted for MFA during recovery, claim that you don’t have access to it

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 8.2.1 | Does the service provider allow us to use a recovery method as an MFA factor during recovery? If yes, note which method.  | Yes, method:\_\_\_\_\_\_ No |

## Test case 8 \- Wrap up

After this test case, move to test case 9
