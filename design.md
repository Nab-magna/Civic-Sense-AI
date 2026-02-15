# CivicLens AI – System Design Document

## 1. High-Level Architecture

User → Frontend (React + Leaflet)
        ↓
Backend API (FastAPI)
        ↓
PostgreSQL + PostGIS
        ↓
AI Layer:
    - NLP Agents
    - CV Model
    - Vector DB (FAISS)
        ↓
Issue Registry & Representative Dashboard

---

## 2. Frontend Design

Framework:
- React
- Leaflet for maps

Components:
- Interactive Map
- Representative Profile Page
- Issue Submission Form
- Issue Listing Cards
- AI Chat Interface

Mobile-first responsive design.

---

## 3. Backend Design

Framework:
- FastAPI

Responsibilities:
- API endpoints
- AI pipeline orchestration
- Geo-mapping logic
- Duplicate detection
- Data retrieval for dashboard
- Chatbot RAG orchestration

---

## 4. Database Design

### Tables

Users
- id
- created_at

Constituencies
- id
- name
- boundary (PostGIS polygon)
- district
- state

Representatives
- id
- name
- party
- term_start
- term_end
- constituency_id (FK)

Issues
- id
- description
- category
- severity
- latitude
- longitude
- constituency_id
- duplicate_cluster_id
- status
- created_at

VerificationScores
- issue_id
- toxicity_score
- relevance_score
- image_confidence
- geo_valid

DuplicateClusters
- id
- representative_issue_id
- confirmation_count

---

## 5. AI System Design

### 5.1 Modular Agent Pipeline

Step 1: Toxicity Detection
Input: Description text
Output: toxicity_score

Step 2: Infrastructure Relevance
Input: Description text
Output: category + relevance_score

Step 3: Image Classification
Input: Uploaded image
Output: infrastructure_type + confidence

Step 4: Geo Validation
Input: GPS
Output: constituency_id

Step 5: Neutralization
Input: Text
Output: Cleaned description

Decision Logic:
If any agent fails threshold → Reject submission.

---

## 6. Duplicate Detection Engine

1. Generate image embedding (MobileNet/CLIP).
2. Compare with existing embeddings (cosine similarity).
3. Check geo distance threshold (e.g., < 50m).
4. If match:
    - Increment confirmation_count.
    - Link issue to existing cluster.
Else:
    - Create new cluster.

---

## 7. RAG-Based Civic Assistant

Pipeline:

User Query
    ↓
Embed Query
    ↓
Retrieve Relevant Government Documents
    ↓
Inject Context into LLM
    ↓
Generate Answer with Citation

Data Source:
- Structured government datasets
- Cleaned manifesto summaries
- Budget summaries

---

## 8. Security Design

- Input sanitization
- Rate limiting
- AI moderation before publishing
- No direct personal accusations allowed
- Logged verification decisions

---

## 9. Deployment Architecture

Frontend:
- Vercel / Netlify

Backend:
- Render / Railway

Database:
- Managed PostgreSQL with PostGIS

AI:
- Open-source LLM API
- Local FAISS index

---

## 10. Design Principles

- Responsible AI
- Neutral presentation
- Transparency over accusation
- Simplicity over complexity
- Depth over breadth

---
