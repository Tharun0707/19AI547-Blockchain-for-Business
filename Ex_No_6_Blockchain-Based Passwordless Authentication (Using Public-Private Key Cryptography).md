# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)

**Name : Tharun Sridhar**

**Reg No : 212223230230**

# Aim:
To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks.

# Algorithm:
Step 1: User Registration
A user registers with their Ethereum public key (instead of a password).


Step 2: Login Process
When logging in, the user signs a random challenge message using their private key.


The smart contract verifies the signature using the user’s public key.



# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PasswordlessAuth {
    mapping(address => bool) public registeredUsers;

    event UserRegistered(address user);
    event UserAuthenticated(address user);

    function registerUser() public {
        require(!registeredUsers[msg.sender], "Already registered");
        registeredUsers[msg.sender] = true;
        emit UserRegistered(msg.sender);
    }

    function authenticate(bytes32 hash, uint8 v, bytes32 r, bytes32 s) public view returns (bool) {
        require(registeredUsers[msg.sender], "User not registered");
        address signer = ecrecover(hash, v, r, s);
        return signer == msg.sender;
    }
}
```

# Expected Output:
Users can register without a password.
![6th exp authenticate](https://github.com/user-attachments/assets/c643cd8e-5dfe-4755-af2c-d12c5e072dd3)


Users sign a challenge with their private key for authentication.
![6th exp pbkprk](https://github.com/user-attachments/assets/922faebf-3501-47e2-abb5-1c1223a9a571)


The smart contract verifies signatures to confirm identity.
![6th exp pbkprk false](https://github.com/user-attachments/assets/70922809-60d8-4fd7-bade-5b731be63be1)



# High-Level Overview:
Eliminates password hacks & phishing attacks.


Uses Ethereum's built-in cryptographic functions.


Inspired by Web3 login solutions like MetaMask authentication.

# RESULT: 
Thus, we have successfully developed a smart contract to implement a secure passwordless authentication system using public key and private key cryptography on Ethereum.
