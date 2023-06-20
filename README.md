# Solidity-Quiz-smart-contract

QuizContract
Table of Contents
License
Description
Usage
Functions
addQuiz
getQuizzesByDifficulty
License
This project is licensed under the MIT License. See the LICENSE file for details.

Description
The QuizContract is a Solidity smart contract that allows users to add quizzes and retrieve quizzes based on their difficulty level. It provides a simple interface to manage quizzes and retrieve them efficiently.

Usage
To use the QuizContract, follow the steps below:

Install a Solidity compiler compatible with version ^0.8.0.
Deploy the QuizContract to a compatible blockchain network.
Interact with the QuizContract using a web3 provider or a compatible client.
Functions
addQuiz
solidity
Copy code
function addQuiz(string memory _question, string memory _answer, uint8 _difficulty) public
The addQuiz function allows users to add a new quiz to the contract. It takes the following parameters:

_question: The question of the quiz (string)
_answer: The answer to the quiz (string)
_difficulty: The difficulty level of the quiz (uint8)
getQuizzesByDifficulty
solidity
Copy code
function getQuizzesByDifficulty(uint8 _difficulty) public view returns (Quiz[] memory)
The getQuizzesByDifficulty function retrieves quizzes based on the specified difficulty level. It takes the following parameter:

*_difficulty: The difficulty level to filter quizzes (uint8)
It returns an array of Quiz structs that match the specified difficulty level.
**Note**: The **Quiz** struct has the following properties:

*question: The question of the quiz (string)
*answer: The answer to the quiz (string)
difficulty: The difficulty level of the quiz (uint8)
### Example

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract QuizContract {
    struct Quiz {
        string question;
        string answer;
        uint8 difficulty;
    }

    Quiz[] internal quizzes;

    function addQuiz(string memory _question, string memory _answer, uint8 _difficulty) public {
        Quiz memory newQuiz = Quiz(_question, _answer, _difficulty);
        quizzes.push(newQuiz);
    }

    function getQuizzesByDifficulty(uint8 _difficulty) public view returns (Quiz[] memory) {
        uint256 count = 0;
        for (uint256 i = 0; i < quizzes.length; i++) {
            if (quizzes[i].difficulty == _difficulty) {
                count++;
            }
        }
        
        Quiz[] memory result = new Quiz[](count);
        uint256 index = 0;
        
        for (uint256 i = 0; i < quizzes.length; i++) {
            if (quizzes[i].difficulty == _difficulty) {
                result[index] = quizzes[i];
                index++;
            }
        }
        
        return result;
    }
}
```
This is a basic example showcasing the QuizContract.
You can interact with the contract by calling the addQuiz function 
to add quizzes and the getQuizzesByDifficulty function 
to retrieve quizzes based on their difficulty level.

Feel free to modify and enhance the contract according to your requirements.

For detailed instructions on deploying and interacting with the contract, refer to the documentation provided by your Solidity compiler and blockchain network.
