# Cloud-Based-Notification-System

The Cloud-Based Notification System is a serverless AWS application that sends notifications through email using an event-driven architecture.
The system receives a notification request through an API, processes it using AWS Lambda, stores the message temporarily in Amazon SQS, and sends the notification through Amazon SNS.

## Objective

To build a scalable and serverless notification system using AWS cloud services.

## AWS Services Used

- Amazon API Gateway
- AWS Lambda
- Amazon SQS
- Amazon SNS
- AWS IAM
- AWS CloudFormation
- Amazon CloudWatch

## Architecture

User / Client
      |
      v
API Gateway
      |
      v
Lambda - Notification Receiver
      |
      v
Amazon SQS
      |
      v
Lambda - Notification Processor
      |
      v
Amazon SNS
      |
      v
Email Notification

## Working

1. The user sends a notification request using the API.
2. API Gateway receives the HTTP POST request.
3. The first Lambda function validates and sends the message to SQS.
4. SQS temporarily stores the notification message.
5. The second Lambda function reads the message from SQS.
6. Lambda publishes the message to the SNS topic.
7. SNS sends the notification to the confirmed email subscriber.

## API Endpoint

Method:

POST

Endpoint:

/prod/notify

Example Request:

{
  "name": "Tejashri",
  "message": "Test notification from Cloud-Based Notification System"
}

## Expected Response

{
  "success": true,
  "message": "Notification request accepted"
}

## Infrastructure as Code

AWS CloudFormation is used to create and manage the complete infrastructure.

The CloudFormation template creates:

- SNS Topic
- SNS Email Subscription
- SQS Queue
- Lambda Functions
- IAM Roles and Policies
- API Gateway
- Lambda-SQS Event Source Mapping

## Project Benefits

- Serverless architecture
- Event-driven processing
- Scalable notification processing
- Reduced infrastructure management
- Cloud-based email notifications
- Infrastructure managed using CloudFormation

## Testing

The system was tested by sending a POST request to the API Gateway endpoint.

The notification was successfully processed through:

API Gateway → Lambda → SQS → Lambda → SNS → Email

## Author

Yogesh
