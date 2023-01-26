Are you worried you're not giving your cat enough attention? Don't fret because Kitty Cuddles is a serverless application that lets your cat send you an email to tell you to come pet them! 

Configure SES to add verified emails that AWS can use. 
![InkedScreenshot_1](https://user-images.githubusercontent.com/109190196/214945216-37ddf044-7622-4a6b-9f6d-007f9bd2dfa6.jpg)

Create an IAM Role for a Lambda Function so it can assume the role and interact with other AWS Services. Create a Lambda Function to send an email via SES.
![Screenshot_5](https://user-images.githubusercontent.com/109190196/214946258-07f3bac0-5823-45ac-b736-dfa87399044a.jpg)

Create an IAM Role for the StateMachine so it can assume the role and interact with other AWS Services. Create the StateMachine using the contents from the ASL file. The StateMachine is created to wait for a timer to expire before the next task of sending an email happens.
![Screenshot_2](https://user-images.githubusercontent.com/109190196/214946537-93e96eb1-178f-4be2-9a01-408a2e1128a6.jpg)
![Screenshot_9](https://user-images.githubusercontent.com/109190196/214946854-65e5eb9c-b503-4e01-80d4-992812796943.jpg)

Create a Lambda Function which will support the API Gateway.
![Screenshot_3](https://user-images.githubusercontent.com/109190196/214947096-831cc8be-6e9b-4836-a6df-b81cfc577de4.jpg)

Build a REST API, this will be what the frontend part of the serverless application will communicate with.
![Screenshot_4](https://user-images.githubusercontent.com/109190196/214947496-589375b6-608b-406b-bfcc-83f1a6570656.jpg)

Create an S3 bucket that allows public access and enable static website hosting. Create a bucket policy that allows anyone to GetObject. Upload the contents of "serverless_frontend" into the bucket.
![Screenshot_6](https://user-images.githubusercontent.com/109190196/214948009-28e60f9d-9694-40fd-8418-7163477f8b01.jpg)

Use the bucket endpoint URL to open the application in your browser. Input your timer, message, and email and press Email Minion. If sent successfully, it will say so.
![Screenshot_8](https://user-images.githubusercontent.com/109190196/214948450-1ae82df0-24c8-409f-964d-b2baaa60c1c4.jpg)
![InkedScreenshot_7](https://user-images.githubusercontent.com/109190196/214949591-eee61ea8-eb62-4cd3-beaa-87a08acf47f7.jpg)

If successful the StateMachine will wait for the timeout and then send the email.
![InkedScreenshot_10](https://user-images.githubusercontent.com/109190196/214949818-425d0dd8-d62d-4886-bdf2-3ee4a400181d.jpg)

You can also access the logs via CloudWatch Logs.
![InkedScreenshot_11](https://user-images.githubusercontent.com/109190196/214950191-8c0d4f20-87c2-4f70-b275-6fe79769f4ce.jpg)

When the StateMachine task is complete, you will receive an email with the message from your cat.
![InkedScreenshot_12](https://user-images.githubusercontent.com/109190196/214949004-12fa0281-eedc-4ad6-ba2d-8420f02b2280.jpg)
