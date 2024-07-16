# ERROR HANLDING DEMONSTRATION

This Solidity program is a simple Eror handling program that demonstrates the basic syntax and functionality of the Solidity programming language. The purpose of the programis to make aware the concept of error handling.

## Description

This is a error handling program which uses require assert and revert method to handle the error present in the program and perform the task task to add remove and get the medical history of the patients.

## Getting Started

### Executing program
->to run this program use remix etherum ide 
->open remix ide and add a new file by naming it using the .sol extension .
->copy the paste the below giving code 
->compile the code by changing the solidity version as wriiten on the code .
->deploy it and give input to perform the task .

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract HealthcareContract {
    address public owner;
    mapping(uint => string) public medicalHistories;

    constructor() {
        owner = msg.sender;
    }

    function patientsadd(uint _id, string memory _medicalHistory) public {
        require(msg.sender == owner, "Only the owner can add or update patients");
        require(bytes(_medicalHistory).length > 0, "Medical history cannot be empty");
        
        medicalHistories[_id] = _medicalHistory;
        assert(bytes(medicalHistories[_id]).length > 0);
    }

    function retrievemediaclhistroy(uint _id) public view returns (string memory) {
        require(bytes(medicalHistories[_id]).length > 0, "Patient does not have medical history");
        return medicalHistories[_id];
    }

    function removePatient(uint _id) public {
        require(msg.sender == owner, "Only the owner can remove patients");
        require(bytes(medicalHistories[_id]).length > 0, "Patient does not exist");

        delete medicalHistories[_id];
        assert(bytes(medicalHistories[_id]).length == 0);

        if (bytes(medicalHistories[_id]).length != 0) {
            revert("Failed to remove the patient");
        }
    }
}
```

## Authors

Amrita Kumari
https://www.linkedin.com/in/amrita-kumari-753319232/

## License

This project is licensed under the MIT License 
