# CivicLens AI – Requirements Document

## 1. Project Overview

CivicLens AI is a map-based civic transparency and community infrastructure reporting platform.

It enables citizens to:
- Access structured public governance data
- Report infrastructure issues safely
- View issues mapped to constituencies
- Interact with a multilingual AI civic assistant

The system ensures responsible reporting using a Modular AI Verification Pipeline to prevent abuse, spam, and defamation.

---

## 2. Problem Statement

Access to public governance data in India is fragmented and difficult for citizens to interpret. 

There is no structured and AI-moderated platform where:
- Infrastructure issues can be safely reported
- Issues are mapped to administrative regions
- Public data is accessible in simple language
- Duplicate complaints are intelligently merged
- Abuse and political defamation are automatically filtered

This results in:
- Low civic awareness
- Poor transparency
- Limited public participation
- Misinformation risks

---

## 3. Objectives

1. Provide structured civic information via interactive map.
2. Enable AI-verified infrastructure issue reporting.
3. Prevent abusive or defamatory submissions.
4. Detect and merge duplicate community reports.
5. Map issues to constituencies (neutral, non-accusatory).
6. Offer multilingual AI civic assistant (English + Hindi).

---

## 4. Scope (Hackathon Version)

Included:
- India Map (Maharashtra fully implemented)
- 1–2 districts active
- Representative dashboard (MLA/MP)
- Issue submission system
- Modular AI verification agents
- Duplicate issue detection
- RAG-based chatbot
- Basic voice input (optional if time permits)

Excluded:
- Full India coverage
- Real-time government integration
- Live official complaint escalation
- Political commentary or opinion systems

---

## 5. Functional Requirements

### 5.1 Map Interface
- Zoom-based hierarchy (National → State → District)
- Display representative profiles
- Display issue density in region

### 5.2 Issue Submission
User must:
- Upload image
- Provide description
- Enable location

System must:
- Validate content using AI pipeline
- Map issue to constituency
- Store in database
- Display verification status

### 5.3 Modular AI Verification System

The system must include:

1. Toxicity Detection Agent
2. Infrastructure Relevance Classifier
3. Image Classification Agent
4. Geo Validation Agent
5. Neutralization/Rephrasing Agent

Only approved issues are published.

### 5.4 Duplicate Detection

System must:
- Generate image embeddings
- Check proximity (geo distance threshold)
- Compute similarity score
- Merge duplicate reports
- Increment community confirmation count

### 5.5 Representative Dashboard

Each representative page must show:
- Basic profile data
- Fund allocation summary (if available)
- Total reported issues in constituency
- Issue category breakdown
- Top reported community issues

Neutral framing must be maintained.

### 5.6 AI Civic Assistant

System must:
- Use RAG architecture
- Retrieve from verified public datasets
- Provide citations
- Support English and Hindi

---

## 6. Non-Functional Requirements

- Scalable database design
- Secure API endpoints
- Input validation
- AI moderation before publishing
- Mobile-friendly UI
- Low-bandwidth compatibility

---

## 7. Ethical & Legal Considerations

- No political accusations allowed
- Automatic filtering of defamatory language
- Only verified public datasets used
- Clear disclaimer on data sources
- AI moderation transparency

---

## 8. Success Metrics

- Successful issue verification pipeline
- Accurate geo mapping
- Duplicate issue clustering
- Functional chatbot with citation
- Clean, responsible UI

---

## 9. Future Enhancements

- Multi-state expansion
- Real-time government dataset integration
- Civic education modules
- Resolution tracking workflow
- NGO/journalist integration
- Integration with AWS infrastructure and products

---
