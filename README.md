# Calculator using AWS Step Functions

> **🎉 Update:** This project has been updated to use [JSONata](https://docs.aws.amazon.com/step-functions/latest/dg/transforming-data.html), AWS Step Functions' modern query and transformation language (released November 2024). The original thought-provoking exercise from 2022 demonstrated how to achieve basic math operations by combining intrinsic functions and loops - but that approach is no longer relevant now that Step Functions supports native arithmetic operators through JSONata.

## Modern Implementation (2024)

Please find `calculator.asl.json`, an [Amazon States Language](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html) definition that can Add, Subtract, Multiply and Divide two numbers using native JSONata operators.

This implementation uses JSONata's native arithmetic operators (`+`, `-`, `*`, `/`) instead of simulating math operations with loops and intrinsic functions. The result is cleaner, more maintainable code that's easier to understand.

To use, please see [Getting started with AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/getting-started.html) and update the ASL. No additional IAM permissions are required.

**Note:** When creating the state machine, ensure you select **JSONata** as the query language, or the state machine will default to JSONPath and fail validation. 

## Overview
The StepFunction uses JSONata to perform native arithmetic operations on two numbers (X and Y) with a specified operation (+-*/÷).

![stepfunctions_graph_2024](./img/stepfunctions_graph_2024.png?raw=true "Step Functions Graph 2024")

The result is: `X operation Y`

### What's New in This Version
- **Native arithmetic operators** - Direct `+`, `-`, `*`, `/` operations instead of loops
- **JSONata query language** - Modern data transformation (November 2024 feature)
- **Simplified logic** - 6 states instead of 20+
- **Fail-fast validation** - Input validation before calculation for efficiency
- **Better error handling** - Descriptive error messages with proper error codes
- **Support for both division symbols** - Works with both `÷` and `/`


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
  "x": 5,
  "y": 25,
  "operation": "+",
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
  "x": 50,
  "y": 8,
  "operation": "-",
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
  "x": 6,
  "y": 4,
  "operation": "*",
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
  "x": 70,
  "y": 10,
  "operation": "÷",
  "result": 7
}
```

**Note: Division returns integer results (floor division). For example, 10 ÷ 4 = 2**

## Learn More

- [JSONata in Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/transforming-data.html) - Official AWS documentation
- [JSONata Language](https://jsonata.org/) - JSONata reference and playground
- [Step Functions Intrinsic Functions](https://docs.aws.amazon.com/step-functions/latest/dg/intrinsic-functions.html) - For JSONPath-based workflows

## Security

See CONTRIBUTING for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
