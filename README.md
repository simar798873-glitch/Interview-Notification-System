# 🤖 AI-Powered HR Interview Notification System

## 📌 Overview
This project is an automated HR workflow built using **n8n** that streamlines the interview evaluation process.  
It reads candidate data, evaluates performance based on predefined conditions, sends automated emails, and updates records — all without manual intervention.

---

## 🚀 Features
- 📊 Fetch candidate data from Google Sheets  
- 🔄 Process each candidate automatically  
- 🧠 Evaluate interview scores using conditions  
- 📧 Send automated emails (Selected / Not Selected)  
- 📝 Update results back to Google Sheets  
- ⚡ Fully automated workflow  

---

## 🛠️ Technologies Used
- **n8n** – Workflow Automation  
- **Google Sheets** – Data Storage  
- **Gmail API** – Email Notifications  
- **Power BI** – Data Visualization Dashboard  

---

## ⚙️ Workflow Explanation

1. **Trigger**
   - Starts the workflow manually or automatically  

2. **Get Data**
   - Fetches candidate details from Google Sheets  

3. **Loop Over Items**
   - Processes each candidate one by one  

4. **IF Condition**
   - Checks interview score  
   - If score ≥ 60 → Selected  
   - Else → Not Selected  

5. **Send Email**
   - Sends email based on result  

6. **Update Sheet**
   - Appends updated status in Google Sheets  

---

## 📊 Dashboard (Power BI)
The dashboard provides:
- Total number of candidates  
- Selected vs Not Selected ratio  
- Average interview score  
- Candidate-wise details  
- Position-wise analysis  

---

## 💡 Use Case in HR
This system helps HR teams by:
- Reducing manual work  
- Providing instant candidate responses  
- Improving efficiency and accuracy  
- Enabling data-driven hiring decisions  

---

## 🔮 Future Enhancements
- AI-based resume screening  
- Chatbot integration for HR queries  
- Automated interview scheduling  
- Predictive hiring analytics  

---

## 📸 Screenshots

### 🔹 n8n Workflow
![Workflow](workflow.png.jpeg)

### 🔹 Power BI Dashboard
![Dashboard](dashboard.png.jpeg)

---

## 📂 How to Use
1. Import the workflow JSON into n8n  
2. Connect your Google Sheets & Gmail  
3. Update sheet ID and credentials  
4. Run the workflow  

---

## 👩‍💻 Author
**Simarjeet Kaur**

---

## ⭐ Conclusion
This project demonstrates how automation can transform traditional HR processes into a faster, smarter, and more efficient system.
