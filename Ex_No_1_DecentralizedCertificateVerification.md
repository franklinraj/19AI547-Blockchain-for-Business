### Experiment 1: Decentralized Certificate Verification
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
Name:FRANKLIN RAJ G
Reg no:212223230058

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract CertificateVerification {
    address public university;
    mapping(bytes32 => bool) public certificates; 

    event CertificateIssued(bytes32 indexed certHash);
    constructor() {
        university = msg.sender;
}
  function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
      require(msg.sender == university, "Only university can issue certificates");

      bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));

      certificates[certHash] = true;
      emit CertificateIssued(certHash);
  }

  function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
      bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
      return certificates[certHash];
  }
}

```
# Expected Output:

![Screenshot 2025-04-16 090630](https://github.com/user-attachments/assets/6d91441c-4d55-4d51-89b0-3cbba8f86835)
![Screenshot 2025-04-16 090856](https://github.com/user-attachments/assets/2101650a-a5a9-46f0-88fe-73f6b994c98b)
![Screenshot 2025-04-16 091116](https://github.com/user-attachments/assets/2c74b9ee-32f2-4941-941a-5b44cc1d9eba)
![Screenshot 2025-04-16 090951](https://github.com/user-attachments/assets/84a77b5a-2010-421c-ae6f-90f85f927484)




# Result:
To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity is executed successfully.

