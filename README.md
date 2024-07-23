
# AWS Lambda S3 Event Handler

This project contains an AWS Lambda function written in Python to handle S3 events. The function retrieves an object from an S3 bucket and prints its content type.

## Prerequisites

- Python 3.x
- `boto3` library

## Installation

1. **Clone the repository:**

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install required libraries:**

   Ensure you have `pip` installed. Then, run:

   ```bash
   pip install boto3
   ```

## Usage

1. **Modify the Lambda function:**

   The main function is in the `lambda.py` file. You can modify this file according to your requirements.

2. **Run the Lambda function locally:**

   You can test the function locally using a simulated event:

   ```bash
   python lambda.py
   ```

## AWS Lambda Deployment

1. **Zip the Lambda function:**

   ```bash
   zip function.zip lambda.py
   ```

2. **Create an AWS Lambda function:**

   - Go to the AWS Lambda console.
   - Click on **Create function**.
   - Choose **Author from scratch**.
   - Configure the basic settings and create the function.

3. **Upload the function code:**

   - In the Lambda function's configuration, upload the `function.zip` file.
   - Set the handler to `lambda.lambda_handler`.

4. **Configure the S3 trigger:**

   - Go to the S3 bucket where you want to trigger the Lambda function.
   - In the **Properties** tab, add an event notification to trigger the Lambda function on object creation.

## Example Event

Here's an example of the event JSON structure that triggers the Lambda function:

```json
{
  "Records": [
    {
      "s3": {
        "bucket": {
          "name": "your-bucket-name"
        },
        "object": {
          "key": "your-object-key"
        }
      }
    }
  ]
}
```

## Troubleshooting

- Ensure that `boto3` is installed:
  ```bash
  pip install boto3
  ```
- Check the AWS IAM permissions for the Lambda function to ensure it has access to the S3 bucket.
