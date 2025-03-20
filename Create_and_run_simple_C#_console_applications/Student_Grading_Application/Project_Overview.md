# Student Grading Application

## Overview

This C# console application automates the calculation of grades for students based on their exam scores and extra credit assignments.

## Application Requirements

- Create a C# console application.
- Start with four students, each having five exam scores.
- Each exam score is an integer value between 0-100.
- The overall exam score is the average of five exam scores.

## Extra Credit Assignment Criteria

- Extra credit scores are included in the student's scores array.
- Extra credit assignments contribute 10% of an exam score when calculating the final numeric grade.
- Extra credit scores are added to the total exam score before computing the final grade.

## Functionality Updates

The existing code needs to be updated with the following features:

- Use arrays to store student names and scores.
- Implement a `foreach` loop to iterate through student names.
- Use an `if` statement to access the correct student’s scores.
- Implement a `foreach` loop to iterate through scores and calculate the total.
- Update the algorithm to compute the final average score per student.
- Use an `if-elseif-else` construct to determine the letter grade automatically.
- Detect extra credit assignments dynamically based on array length.
- Apply the 10% weighting factor to extra credit assignments.

## Letter Grade Criteria

| Numeric Score | Letter Grade |
| ------------- | ------------ |
| 97 - 100      | A+           |
| 93 - 96       | A            |
| 90 - 92       | A-           |
| 87 - 89       | B+           |
| 83 - 86       | B            |
| 80 - 82       | B-           |
| 77 - 79       | C+           |
| 73 - 76       | C            |
| 70 - 72       | C-           |
| 67 - 69       | D+           |
| 63 - 66       | D            |
| 60 - 62       | D-           |
| 0 - 59        | F            |

## Expected Output

Student                 Grade

Sophia:        92.2              A-

Andrew:        89.6             B+

Emma:          85.6                B   

Logan:         91.2                A-

