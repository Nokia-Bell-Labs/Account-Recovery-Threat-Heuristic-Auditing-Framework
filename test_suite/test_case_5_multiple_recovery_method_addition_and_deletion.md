# Test case 5 \- Multiple recovery method addition and deletion

## Goal

The goal of this test case is to evaluate how service providers behave when adding and removing multiple recovery methods and how those methods are used in an account recovery scenario.  
This aims to check details about how the recovery methods are presented to the users during recovery, including whether some recovery methods are given priority over others, whether only verified methods are used, which methods are sent alerts regarding the changes in the account and whether the service provider even alerts on addition and deletion of recovery methods.

This test case can’t be run if only one recovery method is supported by the service provider.

## Running the test case

### Actions

1. Use a benign VM  
2. Add two additional recovery methods   
3. If the recovery methods added do not require to be verified upon addition  
   1. Trigger recovery without verifying the new recovery method  
   2. Verify the recovery method  
4. Trigger recovery from the benign VM   
   1. Note which recovery method is used as default  
   2. Complete the account recovery successfully and change the password  
5. Trigger recovery from the malicious VM   
   1. Note which recovery method is used as default  
   2. Complete the account recovery successfully and change the password

*Note: We complete the recovery successfully and change the password so we can review any alerts sent to the user afterwards.*

## Testcase 5.1. \- Adding recovery methods

### Goal

Evaluate the behavior of the service provider when new recovery methods are added to the account.

### Actions

1. Use a benign VM  
2. Add two additional recovery methods  
3. If the recovery methods added do not require to be verified upon addition  
   1. Trigger recovery without verifying the new recovery method  
   2. Verify the recovery method

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 5.1.1 | When adding a recovery method, what options are available? | Phone number Email Other: \_\_\_\_\_ |
| 5.1.2 | Which recovery methods were added? | Free text |
| 5.1.3 | When a new recovery method is added, does the service provider enforce verification of the method? | Yes No  |
| 5.1.4 | When a recovery method is added without verification, is that method offered as a recovery method when triggering password recovery? *(optional, only if verification of the recovery method was not enforced in 5.1.3)* | Yes No  |
| 5.1.5 | Is the recovery method presented in the settings as verified after recovery? *(optional, only if verification of the recovery method was not enforced in 5.1.3 and if the recovery method is offered as a recovery option in 5.1.4)* | Yes No  |
| 5.1.6 | Does the service provider send an alert when a new recovery method is added? *If the answer is yes: note down which channels.* | Yes, channels: \_\_\_\_\_ No |
| 5.1.7 | What is the content of the alert? *(optional, only if an alert is sent in 5.1.6)* | Free test |

## Test case 5.2 \- Recovery with multiple recovery methods from a benign machine

### Goal

The goal of this test case is to see how recovery methods are presented to the user and how the recovery process happens when there are multiple recovery methods to choose from. 

### Actions

1. Trigger recovery from the benign VM   
   1. Note which recovery method is used as default  
   2. Complete the account recovery successfully and change the password

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 5.2.1 | Which recovery method is presented as default when triggering recovery? | Free text |
| 5.2.2 | Can the user choose to use a different recovery method? (i.e., not the default one) | Yes No |
| 5.2.3 | If the account has MFA methods, are they shown as possible recovery methods?*(This can happen when the website forced the user to set up an MFA method upon sign up)* | Yes No  |

## Test case 5.3 \- Recovery with multiple recovery methods from a malicious machine

### Goal

The goal of this test case is to see how recovery methods are presented to the user and how the recovery process happens when there are multiple recovery methods to choose from.   
In this test case, we have multiple channels through which alerts can be sent to the user (multiple recovery methods). We want to evaluate as well if those channels are used to alert the user when there is a recovery from a suspicious location.

### Actions

1. Trigger recovery from the malicious VM   
   1. Note which recovery method is used as default  
   2. Complete the account recovery successfully and change the password

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 5.3.1 | Which recovery method is presented as default when triggering recovery? | Free text |
| 5.3.2 | Can the user choose to use a different recovery method? (i.e., not the default one) | Yes No  |
| 5.3.3 | Does the service provider send alert to each of the recovery methods | Free form text *The answer can be yes/no. If alerts are sent only to a subset of the methods, write down which method.* |

## Test case 5.4 \- Removing recovery methods

### Goal

Evaluate the behavior of the service provider when existing recovery methods are removed from the account.

### Actions

1. Use the malicious VM  
2. Remove one of the recovery methods added in this test case

### Questions 

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 5.4.1 | Does the service provider send an alert when a recovery method is removed? *If yes, through which channels?* | Yes, channel(s):\_\_\_\_\_\_ number No |
| 5.4.2 | What is the content of the alert? | Free text |

## Test case 5 \- Wrap up

After this test case, move to test case 6