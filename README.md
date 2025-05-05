# AI Job Applications Tracker

A simple AI-powered assistant that helps you automatically extract job details from listings and logs them into a structured CSV file—saving you time and effort during your job hunt.
## 🚀Features
* Uses Gemini AI to extract job listing details with high accuracy.
* Supports scraping structured content from job sites using Jina AI.
* Logs results into a Google Drive CSV file with consistent formatting.
* Easy to reuse—just plug in new job links, and it handles the rest.
---
## 📸Demo
* Add links when prompted

  <img width="576" alt="image" src="https://github.com/user-attachments/assets/80337e16-a9d4-4af0-83c3-6e1d1b2a8692" />

* Get all job related details organized
  
  <img width="758" alt="image" src="https://github.com/user-attachments/assets/d8cb692d-dc86-4a26-b005-8f9962d7075a" />

---
## ⚙️ Setup & Usage
Follow these steps to get started with the AI Job Application Tracker in minutes:

1. Clone the github repository
```
https://github.com/achalaspandit/ai-job-app-tracker.git
```

2. Open the Notebook in Google Colab
   * Launch the .ipynb file using Google Colaboratory.
   * Colab allows you to run the notebook without needing to install any libraries locally.
     
3. Generate and add API keys
   You’ll need two API keys:
  * 🔑 Google Gemini API Key: [Generate here](https://aistudio.google.com/app/apikey) and save it in Colab as a secret named: GEMINI_API_KEY
  * 🔑 Jina AI Reader API Key:[Generate here](https://jina.ai/reader/) and save it in Colab as a secret named: JINA_API_KEY

4. Mount Google Drive in Colab
   * Mount your Google Drive to allow the notebook to access your CSV file.
   * By default the tracker will create/append into 'Job Applications Tracker.csv' in your drive folder.
   * To add details to a different location or file update link to 'csv_file_link' variable in code and ensure that the csv file contains below columns in header row.
     ```
     job_link, id, title, location, company, pay_range, about_company, roles_and_responsibilities, keywords
     ```
5. Run the Notebook
   * From the Colab menu, go to: Runtime > Run all
   * When prompted, enter job links one by one for which you’d like to extract details.
   * To stop processing links at any point, type q/quit/exit when prompted for the next job link.

---

## 🧠 How It Works (Behind the Scenes)

This project is powered by an **AI workflow built using LangGraph**, and integrates:

- **Jina AI Reader** – to scrape and convert web content into clean markdown.
- **Gemini API (Google)** – to extract structured job information using large language models.
- **Google Colab & Drive** – for easy access and storage of job application records.

**Workflow:**

1. You input a job listing URL.
2. The **LangGraph**-based workflow kicks in.
3. The **Jina AI Reader** fetches the job page and converts it into markdown format.
4. This markdown, along with a detailed prompt, is passed to the **Gemini AI model**.
5. Gemini returns a **structured JSON object** containing all relevant job details.
6. The notebook parses this JSON, maps it to your defined CSV schema, and appends a new row to the job tracker file.

