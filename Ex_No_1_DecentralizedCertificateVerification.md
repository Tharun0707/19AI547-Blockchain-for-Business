### Experiment 1: Decentralized Certificate Verification

**Name : Tharun Sridhar**

**Reg No : 212223230230**

## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.

## Algorithm:
1. Open up Remix or any other Ethereum IDE.
2. Create a new .sol file and type in the required code.
3. Run and Debug the code.
4. Execute the program and verify the given data.
5. Check and authenticate if the certificates searched are the same using smart contract.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
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
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
# Output:
![image](https://github.com/user-attachments/assets/7132c83d-42dc-4864-b2bf-03b73e8b1216)

![image](https://github.com/user-attachments/assets/10a68d99-0b9b-4f0b-90c0-9b45952b4a64)

# Result:
Thus, to develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity is successfully executed.
