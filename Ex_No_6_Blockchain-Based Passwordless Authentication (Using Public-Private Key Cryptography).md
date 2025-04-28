# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)
# NAME: FRANKLIN RAJ G
# REG NO:212223230058
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

# OUTPUT:
# password authentication:
![alt text](<Screenshot 2025-04-28 145228.png>)

# password register:
![alt text](<Screenshot 2025-04-28 145249.png>)
![alt text](<Screenshot 2025-04-28 145303.png>)

# RESULT: 
PASSWORD HAS BEEN AUTHENTICATED SUCCESSFULLY.
