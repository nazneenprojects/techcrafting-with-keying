---

layout: single
title:  "Hubspot Integration in webapp(FastAPI+React)"
date:   2025-03-01 10:46:00 +0100
published: true

---


## Introduction
In this blog post, I will walk you through my journey of integrating **HubSpot** with a **FastAPI backend** and a **React frontend**. The goal was to enable OAuth authentication and retrieve contacts and company details from HubSpot.



## What is OAuth 2.0?
OAuth 2.0 is an industry-standard protocol for authorization, allowing secure access to user data without exposing credentials. It enables applications to request **scoped** access to a user's data through a secure **token-based** authentication system.

### **Different Methods of Authentication Security**
1. **Basic Authentication** - Uses a username and password for authentication. Less secure if not encrypted.
2. **OAuth 2.0** - A token-based system that allows apps to access resources without exposing credentials.
3. **API Keys** - Static keys that grant access to APIs but lack fine-grained control.
4. **JWT (JSON Web Token)** - A stateless and secure way to handle authentication between clients and servers.

OAuth 2.0 is one of the most secure methods and is widely used for third-party integrations, including HubSpot.



## Why This Integration?
Many businesses use **HubSpot** for CRM, and integrating it into an application can help in automating workflows, managing contacts, and syncing customer data efficiently. This integration allows:

- Secure authentication using **OAuth 2.0**.
- Fetching **contacts & company details**.
- Storing access tokens securely in **Redis**.



## Tech Stack Used

### **Backend (FastAPI)**
- **FastAPI** for building the API.
- **Redis** for caching OAuth tokens.
- **HTTPX & Requests** for API calls.
- **Logging** for debugging & monitoring.

### **Frontend (React)**
- **React** for UI.
- **Axios** for making API requests.
- **React Context API** for state management.

#### Github Link for Code - 

``` https://github.com/nazneenprojects/integration_airtable_hubspot__notion.git  ```

<div class="video-wrapper">
    <iframe src="static/vlc-record-2025-03-25-17h47m50s-Nazneen_Mulani_screenrecording (copy).mp4-.ts" frameborder="0"></iframe>
</div>

## Setting Up the Project
### **1. Running the Backend**
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

### **2. Running the Frontend**
```bash
cd frontend
npm install
npm start
```

### **3. Starting Redis**
```bash
redis-server
```

To check stored OAuth tokens in Redis:
```bash
redis-cli KEYS "*"
```



## API Endpoints (HubSpot Integration)
- **Authorize HubSpot** → `/integrations/hubspot/authorize`
- **OAuth Callback** → `/integrations/hubspot/oauth2callback`
- **Get Credentials** → `/integrations/hubspot/credentials`
- **Load HubSpot Data** → `/integrations/hubspot/load`



## Key Challenges & Learnings
### **Handling OAuth Flow**
OAuth 2.0 authentication involves multiple steps:
1. Redirecting users to HubSpot's authentication page.
2. Receiving an authorization code upon successful login.
3. Exchanging this code for an access token.
4. Using the token to fetch user data.

### **Using Redis for Token Storage**
- Stored OAuth credentials in Redis for quick access.
- Used Redis expiry to prevent token misuse.



## Future Improvements
- **Enhance the UI**: Display fetched HubSpot contacts in a visually appealing way.
- **Optimize API Calls**: Implement batch fetching for large datasets.
- **Auto-refresh Tokens**: Schedule background tasks to refresh access tokens.



## References
- [HubSpot API Key](https://app-na2.hubspot.com/developer-api-key/242106441)
- [OAuth Authentication](https://developers.hubspot.com/docs/reference/api/app-management/oauth)
- [Contacts API](https://api.hubapi.com/crm/v3/objects/contacts)
- [Companies API](https://developers.hubspot.com/docs/reference/api/crm/objects/companies)



## Conclusion
This integration was a great learning experience, helping me understand OAuth authentication, API security, and Redis caching. In the future, I plan to refine the UI and make API calls more efficient. Stay tuned for updates!

## Redis Blog
For more details on Redis, refer my blog post : [Redis Simple Guide](https://nazneenprojects.github.io/techcrafting-with-keying/2025/02/25/Redis-Guide.html)
   

![img](https://github.com/user-attachments/assets/d9522a37-79ea-4d20-be7f-3589671346f5)



