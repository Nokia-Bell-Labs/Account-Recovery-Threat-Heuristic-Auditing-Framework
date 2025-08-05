# Test case 7 \- Use of MFA during recovery

## Goal

The goal of this test case is to evaluate how service providers handle account recovery when there are both recovery methods and MFA methods. We observe whether MFA factors are used as a second factor during recovery or their use is limited to the log in flow only.   
In this testcase, we also evaluate whether the use of MFA during recovery changes depending on whether the recovery is done from a benign or malicious machine.  
We also evaluate whether recovery methods are used as communication channels to send alerts when adding or removing MFA methods.

This test case can’t be run if only one MFA method is supported by the service provider.

## Running the test case

### Actions

1. Use a benign VM  
2. If there are no MFA factors, or there is only one MFA factor, add a second one.  
   1. Note: backup codes for a MFA factor can be considered a separate MFA factor.  
3. Trigger recovery from the benign VM   
   1. Complete the account recovery successfully and change the password  
   2. Log out (if necessary)  
   3. Log in with the new credentials  
4. Trigger recovery from the malicious VM   
   1. Complete the account recovery successfully and change the password  
   2. Log out (if necessary)  
   3. Log in with the new credentials  
5. Remove one of the MFA factors added in step 2

*Note: We complete the recovery successfully and change the password so we can review any alerts sent to the user afterwards.*

## Testcase 7.1. \- Adding MFA factors

### Goal

Evaluate the behavior of the service provider when new MFA factors are added to the account.

### Actions

1. Use a benign VM  
2. If there are no MFA factors, or there is only one MFA factor, add a second one.  
   1. Note: backup codes for a MFA factor can be considered a separate MFA

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 7.1.1 | Does the service provider send an alert when a new MFA factor is added? If yes, through which channels? | Yes, channel(s):\_\_\_\_ No |
| 7.1.2 | What is the content of the alert? | Free text |

## Test case 7.2 \- Use of MFA during recovery from a benign machine

### Goal

The goal of this test case is to evaluate how and whether MFA factors are used as part of the account recovery if they are available. This test case focuses on the use of MFA factors when recovery is happening from a benign machine.

### Actions

1. Use a benign VM  
2. Trigger recovery from the benign VM   
   1. Complete the account recovery successfully and change the password  
   2. Log out (if necessary)  
3. Log in with the new credentials

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 7.2.1 | Are MFA factors presented alongside recovery methods when recovering the account? *Note: Our goal with this question is to figure out if the service provider considers both recovery methods and second factors as "channels" and can use them interchangeably for sending verification information to the user* | Yes No |
| 7.2.2 | When doing password recovery, does the service provider ask for a second factor (additional to the factor/method you used to verify your identity when triggering recovery)?  *Pay special attention if MFAs and recovery factors are distinguished and make note of it.* | Yes No Any additional notes as free text: \_\_\_\_ |
| 7.2.3 | When does the service provider ask for the second factor (MFA)? | Right after clicking the link/OTP in the email As a confirmation after setting a new password On the next login with the new password It doesn’t  |

## Test case 7.3 \- Use of MFA during recovery from a malicious machine

### Goal

The goal of this test case is to evaluate how and whether MFA factors are used as part of the account recovery if they are available. This test case focuses on the use of MFA factors when recovery is happening from a malicious machine.  
The main goal is to evaluate whether the results of this test case show a deviation from the benign case in test case 7.2.

### Actions

1. Use a malicious VM   
2. Trigger recovery from the malicious VM   
   1. Complete the account recovery successfully and change the password  
   2. Log out (if necessary)  
3. Log in with the new credentials  
   1. Note which recovery method is used as default  
   2. Complete the account recovery successfully and change the password

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 7.3.1 | Are MFA factors presented alongside recovery methods when recovering the account? *Note: Our goal with this question is to figure out if the service provider considers both recovery methods and second factors as "channels" and can use them interchangeably for sending verification information to the user* | Yes No |
| 7.3.2 | When doing password recovery, does the service provider ask for a second factor (additional to the factor/method you used to verify your identity when triggering recovery)?  *Pay special attention if MFAs and recovery factors are distinguished and make note of it.* | Yes No Any additional notes as free text: \_\_\_\_ |
| 7.3.3 | When does the service provider ask for the second factor (MFA)? | Right after clicking the link/OTP in the email As a confirmation after setting a new password On the next login with the new password It doesn’t  |

## Test case 7.4 \- Removing MFA factors

### Goal

Evaluate the behavior of the service provider when existing MFA factors are removed from the account.

### Actions

1. Use the malicious VM  
2. Remove one of the MFA factors added in this test case

### Questions 

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 7.4.1 | Does the service provider send an alert when an MFA factor is removed? *If yes, through which channels?* | Yes, channel(s):\_\_\_\_\_\_ number No |
| 7.4.2 | What is the content of the alert? | Free text |

## Test case 7 \- Wrap up

After this test case, move to test case 8  