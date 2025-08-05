# Test case 3 \- Account recovery using an unverified method

## Goal

The goal of this test case is to check how unverified methods are used for account recovery. Additionally, this test case checks how the service providers warn the users about the unverified nature of the recovery methods.

## Running the test case

### Actions

1. Use a benign VM  
2. Trigger account recovery

## Testcase 3.1. \- Presentation of unverified recovery methods to the user

### Goal

Determine if the service provider makes any design choices in the UI that will alert the user about the “unverified” nature of their recovery method.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 3.1.1 | Before triggering the recovery action, how does the service provider present the ""unverified" nature of the recovery method? | Free text (e.g., shows a sign alert sign next to the unverified recovery method, generic text (you have an unverified email) vs specific text (unless you verify you the recovery method, you cannot use it for recovery) |

## Test case 3.2 \- Usage of implicit recovery methods

### Goal

Check how unverified recovery methods are used in account recovery.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 3.1.2 | What happens when recovery is triggered? | Note what happens: The unverified recovery method is used Additional checks required to verify the user (e.g., personal data, previous passwords) There is a human in the loop |

## Test case 3.3 \- Presentation of recovery information to the user

### Goal

Determine if the action of recovering an account using the unverified recovery method implicitly “verifies” the method and whether this change is reflected in the UI or not.

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 3.1.3 | If the unverified recovery method is used for the recovery, is the method marked as verified in the UI/Settings after recovery? | Yes No |

## Test case 3 \- Wrap-up

### Actions

1. If the recovery method is still unverified, verify it now  
2. At the end of this test case we will have an account in Avr state and we should continue executing test case 4