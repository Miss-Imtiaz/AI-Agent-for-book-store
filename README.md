# 📊 Book Inventory Manager - n8n Automation Workflow

## 📝 Description

This n8n automation workflow provides two core functionalities:

1. **AI-Powered Airtable Assistant** – Chat with an AI agent to search and update book inventory records in Airtable.
2. **Website Uptime Monitor** – Periodically checks a website status and sends email alerts (UP/DOWN) via Gmail.

---

## 🚀 Features

### 🤖 AI Agent (Chat Trigger)
- Natural language interface to interact with your book inventory
- Search records in Airtable using plain English
- Update stock quantity, minimum quantity, and reorder point automatically
- Uses **Groq LLM** (Llama 4 Scout) for intelligent responses
- Maintains conversation memory for contextual interactions

### 📧 Website Status Monitor (Schedule Trigger)
- Runs every **1 minute** (configurable)
- Sends HTTP request to any website URL
- Evaluates response status code
- Sends instant email notification:
  - ✅ **"Website is UP"** when status code = 200
  - ❌ **"Website is DOWN"** for any other status code

---

## 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation platform |
| Airtable | Inventory database (Books table) |
| Groq (Llama 4 Scout) | AI language model |
| Gmail OAuth2 | Email notifications |
| HTTP Request | Website status checking |

---

## 📁 Airtable Schema

| Field Name | Type | Description |
|------------|------|-------------|
| `id` | String | Unique record identifier |
| `Current Stock Quantity` | Number | Available stock |
| `Min Quantity` | Number | Minimum stock threshold |
| `Reorder Point` | Number | Calculated as `Min Quantity × 1.2` |

---

## 🔧 Setup Instructions

### Prerequisites
- n8n instance (self-hosted or cloud)
- Airtable account with Base named "Book Inventory Manager"
- Groq API key
- Gmail account with OAuth2 configured

### Steps

1. **Import Workflow**
   - Copy the `My workflow.json` file
   - Import into your n8n instance

2. **Configure Credentials**
   - Airtable OAuth2 API
   - Groq API (Groq account)
   - Gmail OAuth2 API

3. **Update Airtable Base/Table IDs**
   - Replace `appHdfDTLLwfZzB9f` with your Airtable Base ID
   - Replace `tbl0eineaLIuoTwr9` with your Table ID

4. **Update Email Recipient**
   - Change `missimtiazimtiazahmed@gmail.com` to your email address

5. **Activate Workflow**
   - Toggle the workflow to **Active** status

---

## 🔄 Workflow Nodes

### AI Assistant Branch
Chat Trigger → AI Agent → Airtable Tools (Search/Update) → Groq LLM


### Website Monitor Branch
Schedule Trigger → HTTP Request → IF Node → Edit Fields → Gmail


---

## 📧 Email Example

**Subject:** Website status

**Message:** 
- `Website is UP ✅`
- `Website is DOWN ❌`

---

## ⚙️ Customization

### Change Website URL
Edit **HTTP Request** node → URL field

### Change Check Frequency
Edit **Schedule Trigger** node → interval settings

### Modify Reorder Point Formula
Edit **Update record in Airtable** node → `Reorder Point` field expression

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Email not sending | Check Gmail OAuth2 credentials |
| Airtable not updating | Verify Base/Table IDs and field names |
| AI not responding | Ensure Groq API key is valid |
| Website status incorrect | Check if URL is accessible |

---


## ⭐ Support

If this workflow helped you, please give it a star ⭐ on GitHub!
