# 🏥 AI-Assisted Medical Intake & Navigation Platform

An **AI-powered patient onboarding system** that captures medical requirements via a **voice bot**, recommends the appropriate **specialist department** and **nearby hospital** with **real-time ETA and queue data**, books appointments (or adds to a virtual queue), and guides patients to the correct location within the hospital.

---

## 📖 Overview

This system streamlines the patient journey from first contact to arriving at the correct treatment location.  
It uses **Generative AI** for natural medical note-taking, integrates **mapping APIs** for real-time travel estimates,  
connects to **hospital systems** for slot booking and queue management, and provides **indoor navigation** at the hospital.

---

## 🚀 Features

1. **Voice-Based Symptom Collection**  
   - Patients speak to a **Gen-AI Medical Voice Bot**.  
   - Symptoms, elaboration, and start time are rephrased into clear, concise, medical phrasing.

2. **Triage & Recommendation**  
   - AI selects the correct department: `respiratory`, `cardio`, or `neuro`.  
   - Finds nearby hospitals using patient’s location.  
   - Retrieves **real-time traffic ETA** and **current queue status**.

3. **Hospital & Doctor Selection**  
   - Patient can choose hospital and doctor.  
   - If no doctor selected, AI auto-assigns based on availability.

4. **Automated Booking & Virtual Queue**  
   - Books the doctor’s slot.  
   - Notifies hospital of patient’s expected arrival.  
   - Adds patient to the virtual queue.

5. **On-Site Navigation**  
   - Provides **step-by-step indoor navigation** using checkpoints (QR/NFC/BLE).  
   - Guides the patient to the correct department or room.

---

## 🗺️ System Flow

1. **Gen-AI Voice Bot** → captures symptoms + location → sends structured JSON to **n8n**.
2. **n8n AI Agent** → rephrases data, determines department, fetches hospitals, ETA, and queue.
3. **Frontend** → displays ranked hospitals with doctor options.
4. **Patient Selection** → triggers booking API in n8n.
5. **Virtual Queue & Arrival Notice** → updates hospital.
6. **Indoor Navigation** → guides patient to treatment location.

---

## 📂 Data Contracts

**Intake → n8n**
```json
{
  "symptoms": "breathing difficulties",
  "start_time": "five hours before",
  "symptom_elaboration": "cannot breathe properly",
  "location": { "lat": 0, "lng": 0 }
}
