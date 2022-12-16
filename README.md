# Calculator using AWS Step Functions

Please find `calculator.asl.json`, an [Amazon states language](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html) definition that can Add, Subtract, Divide and multiply two whole numbers together.

This was a thought-provoking exercise not intended to be used for workloads, but to demonstrate how you can achieve basic math operations by combining [intrinsic functions](https://docs.aws.amazon.com/step-functions/latest/dg/amazon-states-language-intrinsic-functions.html).

To use, please see [Getting started with AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/getting-started.html) and update the ASL. No Additional IAM permissions are required. 

## Overview
Please see the StepFunction graph below:
![stepfunctions_graph](./img/stepfunctions_graph.png?raw=true "stepfunctions_graph")

This StepFunction inputs 2 whole numbers (X and Y) and an operation (+-*÷).

The result is: `X operation Y`


## Examples:

### Example 1 - Adding

Input:
```
{
    "x": 5,
    "y": 25,
    "operation": "+"
}
```
Output:
```
{
  "result": 30
}
```
### Example 2 - Subtraction

Input:
```
{
    "x": 50,
    "y": 8,
    "operation": "-"
}
```
Output:
```
{
  "result": 42
}
```

### Example 3 - Multiplication

Input:
```
{
    "x": 6,
    "y": 4,
    "operation": "*"
}
```
Output:
```
{
  "result": 24
}
```

### Example 4 - Division

Input:
```
{
    "x": 70,
    "y": 10,
    "operation": "÷"
}
```
Output:
```
{
  "result": 7
}
```

**Note: When the result is not a whole number it will always round up. e.g. 10 ÷ 4 = 3**

## Security

See CONTRIBUTING for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
