# 🧠 Cloud Resume Analyzer (AI + Serverless + NLP)

**Cloud Resume Analyzer** is an intelligent, serverless web app that helps job seekers instantly match their resume against job descriptions — powered by **AWS**, **Node.js**, and **Natural Language Processing (NLP)** via **Amazon Comprehend**.

🚀 Whether you're applying for your dream job or screening hundreds of resumes, this tool delivers **smart insights**, a **match percentage**, and **real-time feedback** — all inside a beautiful, scalable web interface.

---

## 🎬 Demo Video  
[📽️ Watch the project demo here](https://drive.google.com/file/d/1MQH6g_TEzLc6Ne2IhBCc7I128oAc1mC_/view?usp=sharing)

---

## 🧑‍💻 How It Works

1. Open the web app (hosted on **Amazon S3**).
2. Upload your **PDF resume**.
3. Paste the **job description** text.
4. Get instant analysis with:
   - Extracted key phrases
   - Match percentage score
   - Suggestions to improve alignment
5. The results are logged in **DynamoDB** for future tracking.

---

## 📊 Architecture Overview

### System Design Diagram 1  
![Architecture 1](Architecture%201.png)

### System Design Diagram 2  
![Architecture 2](Architecture%202.jpg)

---

## 🔧 Tech Stack & AWS Services

| Service           | Role                                        |
|------------------|---------------------------------------------|
| **Amazon S3**     | Hosts the static frontend (HTML/CSS/JS)     |
| **API Gateway**   | Exposes secure HTTP endpoint `/analyze-nlp` |
| **AWS Lambda**    | Backend logic, keyword extraction & scoring |
| **Amazon Comprehend** | NLP service to extract key phrases    |
| **Amazon DynamoDB** | Stores match logs with timestamp & UUID |
| **IAM**           | Grants scoped permissions to Lambda         |

---

## 🧩 Backend Logic Summary (Lambda)

- Accepts resume text and job description
- Sends both to **Amazon Comprehend**
- Extracts key phrases
- Calculates keyword overlap and match %
- Stores the result in DynamoDB with a timestamp
- Returns JSON result to frontend

---

## 🖼️ Example DynamoDB Record

```json
{
  "id": "a1b2c3d4-e5f6-7890-gh12-ijkl3456mnop",
  "resumeText": "Software engineer with IoT and ML experience...",
  "jobDescription": "Looking for a Java and AWS expert...",
  "matchPercent": 78,
  "timestamp": "2025-05-29T00:32:10.532Z"
}
