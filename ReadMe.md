# 📝 Real Time Blog Generator

This project is a fully serverless blog generation system powered by **Amazon Bedrock** and the **LLaMA 3 70B Instruct** model. Users can input a topic via a REST API, and the system generates a ~200-word blog using generative AI. The resulting blog is automatically saved to **Amazon S3**.

---

## 🎯 Objective

To demonstrate how **Large Language Models (LLMs)** can be integrated into a cloud-native, production-ready pipeline using AWS services. This project automates content generation while maintaining scalability, cost-efficiency, and observability.

---

## 🏗️ Architecture Overview

[Client / API Caller]
↓
[API Gateway]
↓
[AWS Lambda]
↓
[Amazon Bedrock (LLaMA 3)]
↓
[Generated Blog Text]
↓
[Amazon S3]


- **API Gateway**: Exposes an HTTP endpoint.
- **AWS Lambda**: Processes input, invokes Bedrock, and stores the blog.
- **Amazon Bedrock**: Hosts Meta’s LLaMA 3 for generating blog content.
- **Amazon S3**: Stores the generated blog as a `.txt` file.
- **Amazon CloudWatch**: Logs all activities for monitoring and debugging.

---

## ✨ Features

- 📝 Topic-based blog generation (~200 words)
- 🤖 Uses Meta LLaMA 3 (8B-Instruct) via Amazon Bedrock
- ☁️ Fully serverless and event-driven using AWS Lambda
- 📂 Blog storage in Amazon S3
- 📊 Logging and monitoring with CloudWatch

---

## 📁 Folder Structure

blog-generator/
├── app.py # Lambda function with Bedrock + S3 logic
├── requirements.txt # Python dependencies for local testing
├── .gitignore # Ignored files and folders
└── README.md # Project documentation


---

## ⚙️ How It Works

1. A POST request is sent to the API Gateway with a blog topic.
2. The Lambda function is triggered and invokes the LLaMA 3 model via Amazon Bedrock.
3. The generated blog is saved as a `.txt` file in an S3 bucket.
4. All steps are logged using Amazon CloudWatch.

---

## 📥 Sample Input (API Request)

```json
{
  "blog_topic": "The Future of Generative AI"
}

```

## 🛠️ Setup Instructions

1. Local Setup (Optional)

```
# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

```

2. AWS Lambda Deployment
Upload app.py to a new AWS Lambda function.
Set the Lambda handler to:
```
app.lambda_handler

```

3. API Gateway Configuration
Create a REST API in Amazon API Gateway.
Add a POST method and integrate it with your Lambda function.
Deploy the API to generate a public endpoint.

4. S3 Bucket Setup
Create an S3 bucket (e.g., awsbedrockcoursepp or any name of your choice).
The Lambda function will store generated blogs at:

```
blog-output/HHMMSS.txt

```



