# SynChain AI 

SynChain AI is an Autonomous Supply Chain Procurement Agent for Indian SMBs (Small and Medium Businesses).

The Problem It Solves:

Indian small businesses waste hours every day on procurement:
1) Calling vendors for price quotes
2) Comparing offers manually
3) Negotiating prices over phone/WhatsApp
4) Checking GST compliance
5) Generating purchase orders
6) Getting manager approvals

## Quick Start

```bash
# Clone & enter project
cd synchain-ai

# Copy environment files
cp .env.example .env

# Start all services
docker-compose up -d

# Initialize database
docker exec -i synchain-postgres psql -U postgres -d synchain < backend/init.sql

# Access services:
# Frontend:    http://localhost:5173
# Backend API: http://localhost:8000/docs
# AI Service:  http://localhost:8001/docs

HOW ALL PIECES CONNECT:

USER → Frontend (React) → Backend (FastAPI) → AI Service (FastAPI)
                ↕                ↕                    ↕
           WebSocket        PostgreSQL            ML Models
                            Redis (Celery)        Vendor CSV
                            Cloudinary            Policy Docs
                            Mailtrap              FAISS Index
                            WhatsApp API
