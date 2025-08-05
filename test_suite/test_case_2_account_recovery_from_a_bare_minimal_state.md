# Test case 2 \- Account recovery from a bare minimal state

## Goal

The goal of this test case is to see how the service provider behaves when recovering an account with no recovery methods. This test aims to discover any flaws in the recovery protocol, including not being able to recover the account, unnecessary involvement of humans in the loop.

## Running the test case

### Actions

1. Use a benign VM  
2. Try to recover the account

### Questions

| Test case number | Question | Answer type |
| :---- | :---- | :---- |
| 1.2 | What happens when we trigger recovery? | Free form text |

# Test case 2 \- Wrap up

### Actions

1. Add a recovery method   
2. Depending on whether the verification of the recovery method is mandatory or not, the resulting account state will be one of the following: Aur or Avr. Based on the resulting account state, move to the next test case.

| Account state | Description | Next testcase |
| :---- | :---- | :---- |
| Aur | Account with an unverified recovery method | Test case 3 |
| Avr | Account with a verified recovery method | Test case 4 |
