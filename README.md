# 🎙️ Text-to-Speech Converter using AWS Polly (Serverless + Free Tier)

This is a serverless **Text-to-Speech web application** built using:
- **AWS Lambda** (Python backend)
- **Amazon Polly** (text-to-speech service)
- **API Gateway** (HTTP API)
- **HTML/CSS/JS frontend**
- ✅ Hosted on S3 (optional)
- ✅ Built entirely within AWS Free Tier

---

## 🧠 What It Does

- You enter any text into a web form
- Click **Convert to Speech**
- The text is sent to an **AWS Lambda function**
- Lambda uses **Amazon Polly** to generate an `.mp3`
- The audio is streamed back as a **Base64 URL**
- The browser plays the audio instantly 🎧

---

## 💡 Why I Built This

I wanted to explore how real cloud applications work behind the scenes:

- Understand serverless architecture
- Learn about CORS, preflight, and Lambda routing
- Build an actual AI-powered tool using AWS services
- Handle frontend → backend → cloud AI → return to browser

---

## 🛠️ Tech Stack

| Layer      | Technology         |
|------------|--------------------|
| Frontend   | HTML, CSS, JS      |
| Backend    | AWS Lambda (Python 3.13) |
| AI Service | Amazon Polly       |
| Routing    | API Gateway (HTTP API) |
| Hosting    | AWS S3 (Static Website) |
| Auth       | None (CORS Secured) |

---

## 📷 Project Walkthrough

Here’s how I built this — step-by-step with screenshots:

---

### 🔹 Step 1: Built the UI with HTML/CSS

Simple text input and "Convert to Speech" button.

![Step 1]
<img width="1919" height="981" alt="Screenshot 2025-07-12 162559" src="https://github.com/user-attachments/assets/227cef9c-c4ff-42ef-9d79-c88c16e5496b" />


---

### 🔹 Step 2: Created Lambda Function (Python 3.13)

Used `boto3` to talk to Amazon Polly and convert text to `.mp3`.

![Step 2]
<img width="1919" height="982" alt="Screenshot 2025-07-09 213409" src="https://github.com/user-attachments/assets/39194853-32ca-463b-abd2-cb551e4357c0" />

<img width="1919" height="982" alt="Screenshot 2025-07-09 213431" src="https://github.com/user-attachments/assets/0b6f6c9c-b1d0-4bef-a770-005dcc638a70" />

<img width="1919" height="984" alt="Screenshot 2025-07-09 213553" src="https://github.com/user-attachments/assets/93800b3e-1504-4816-98bd-c488a6364cdc" />
## 🧠 Lambda Function Code

This is the AWS Lambda function written in Python that converts input text to speech using Amazon Polly and returns the audio as a Base64-encoded stream:

<img width="769" height="924" alt="Screenshot 2025-07-12 163552" src="https://github.com/user-attachments/assets/8a385f69-75f3-44ee-a626-d08b320933c5" />
<img width="791" height="385" alt="Screenshot 2025-07-12 163604" src="https://github.com/user-attachments/assets/f3383c2e-9b0c-431b-92bb-63b4e30ef0a8" />

---

### 🔹 Step 3: Given Lambda Permission to Use Polly through IAM roles

Inside the role page, click “Add permissions” → “Attach policies” (AmazonPollyFullAccess).

![Step 3]
<img width="1918" height="985" alt="Screenshot 2025-07-09 213608" src="https://github.com/user-attachments/assets/1a724f2b-8326-430b-a58c-a0bfaf12572b" />
<img width="1919" height="981" alt="Screenshot 2025-07-09 213714" src="https://github.com/user-attachments/assets/e0281dde-53e0-4c05-9656-12dc66d3b003" />
<img width="1919" height="980" alt="Screenshot 2025-07-09 213722" src="https://github.com/user-attachments/assets/f8006e50-547a-4b65-9128-ba3413bcf8c8" />
<img width="1919" height="987" alt="Screenshot 2025-07-09 213742" src="https://github.com/user-attachments/assets/41ffba97-c95a-46c0-af0c-dee8273f87f5" />

---

### 🔹 Step 4: Created API Gateway (HTTP API)

Set up a `POST /texttospeech01` route and connected it to my Lambda.

![Step 4]
<img width="1919" height="978" alt="Screenshot 2025-07-09 213804" src="https://github.com/user-attachments/assets/eff0dd10-f126-413e-b6df-3a9fa19e910b" />
<img width="1919" height="977" alt="Screenshot 2025-07-09 213823" src="https://github.com/user-attachments/assets/299d09bf-ad00-46ca-9fca-a6e673ee2330" />
<img width="1919" height="990" alt="Screenshot 2025-07-09 214431" src="https://github.com/user-attachments/assets/babec1bc-0525-4850-99a9-9bfc561b7678" />

---

### 🔹 Step 5: Solved CORS Issues (Preflight & Headers)

Added an `OPTIONS /texttospeech01` route after the creation of API.

![Step 5]
<img width="1919" height="987" alt="Screenshot 2025-07-09 214517" src="https://github.com/user-attachments/assets/af2d3b26-c6ed-4354-8b85-f8e20e398278" />
<img width="1919" height="985" alt="Screenshot 2025-07-09 214529" src="https://github.com/user-attachments/assets/999c8ad5-07d0-4665-a67f-69308a42d31e" />
<img width="1919" height="982" alt="Screenshot 2025-07-09 213938" src="https://github.com/user-attachments/assets/889bdd93-9eb1-4b6a-9347-83de34cac2c0" />
<img width="1919" height="981" alt="Screenshot 2025-07-09 214001" src="https://github.com/user-attachments/assets/a5f8253f-48e9-45b6-9a86-54a152a7574d" />

---

### 🔹 Step 6: Connected Frontend to API Endpoint

Sent JSON via `fetch()` to the API Gateway route. Audio returned as base64 stream.

![Step 6]
<img width="1919" height="984" alt="Screenshot 2025-07-09 214557" src="https://github.com/user-attachments/assets/f992782e-04fb-4cb1-905d-6e23a530ef4f" />
<img width="1163" height="153" alt="Screenshot 2025-07-09 214610" src="https://github.com/user-attachments/assets/b5593c94-e7b1-4d92-990d-60a3aeb74f5a" />

---

### 🔹 Step 7: Final Result – AI Voice from Web Form!

The audio plays instantly in the browser — all serverless, all cloud.

![Step 7]
<img width="1919" height="981" alt="Screenshot 2025-07-09 214740" src="https://github.com/user-attachments/assets/3a6ae9d2-91cb-4768-bb56-877c95cda71d" />

---

## 💬 What I Learned

- How to structure real-world Lambda functions
- How CORS and `OPTIONS` routes actually work in browser + cloud
- How to use **Amazon Polly** to synthesize speech
- How to create public APIs using API Gateway
- How to debug serverless apps using CloudWatch logs

---

## 💼 What Makes This Impressive

✅ Built completely with AWS  
✅ Solves a real problem  
✅ Uses AI (Amazon Polly)  
✅ No server, no database  
✅ Fully working and tested  
✅ Explained clearly in GitHub

---

## 🧪 How to Test It Locally

1. Clone the repo  
2. Open `index.html` in browser (via Live Server or Python server)  
3. Make sure API URL is set correctly  
4. Type text → click Convert  
5. Enjoy AI-powered voice 💬🔊

---

## 🧼 Note on AWS Cost

This project uses only AWS Free Tier limits:
- Polly gives 5 million characters/month (Free for 12 months)
- Lambda, API Gateway, and S3 stay within free usage if you clean up

✅ All services have been deleted after testing to avoid charges.

---

## 📌 Want to Try This Yourself?

- Fork this repo  
- Replace the API URL with your own Gateway  
- Deploy to your own S3 bucket or Open locally on Browser 
- Done!

---

## 👋 Author

**[Ujjwal Wadhai]**  
Aspiring Cloud Developer & AWS Enthusiast

🔗 GitHub: [your-username] 
🔗 LinkedIn: [www.linkedin.com/in/ujjwal-wadhai] 
🎯 Resume project: ✅

---


