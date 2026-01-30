# AfyaPlus-360
A unified digital healthcare ecosystem for clinical efficiency, human capital optimization, and universal health inclusivity.
import streamlit as st
import pandas as pd
import random

# --- SYSTEM CONFIGURATION ---
st.set_page_config(page_title="AfyaPlus 360", page_icon="🏥", layout="wide")

# --- NAVIGATION HUB ---
st.sidebar.title("🏥 AfyaPlus 360")
st.sidebar.markdown("*St. Patrick's High School - Iten*")
menu = st.sidebar.radio("Navigation Hub", [
    "Patient: App Portal", 
    "Patient: USSD Simulator", 
    "Doctor: Clinical Desk", 
    "Careers: Job Matching",
    "Admin: SHA & Analytics"
])

# --- MODULE 1: PATIENT APP PORTAL ---
if menu == "Patient: App Portal":
    st.header("📱 Patient Smart-Portal")
    tab1, tab2, tab3 = st.tabs(["AI Triage & Tickets", "Remote Consultation", "Online Pharmacy"])
    
    with tab1:
        st.subheader("AI-Assisted Symptom Triage")
        p_name = st.text_input("Patient Full Name")
        symptoms = st.text_area("Describe your symptoms:")
        if st.button("Submit for Triage"):
            # Triage logic designed to reduce 5-hour wait times [cite: 548, 580]
            if any(word in symptoms.lower() for word in ["chest", "breath", "bleed"]):
                st.error("🚨 EMERGENCY (Level 1): Proceed to ER. Est. Wait: 5 Mins.")
            else:
                st.success("✅ ROUTINE (Level 3): Est. Wait: 45 Mins.")

    with tab2:
        st.subheader("Telemedicine")
        st.info("Status: Remote Consultation Active. Dr. Koech is online.")
        if st.button("Launch Secure Video Call"):
            st.video("https://www.youtube.com/watch?v=KXmvBOtbBbI") 

# --- MODULE 2: USSD SIMULATOR ---
elif menu == "Patient: USSD Simulator":
    st.header("📟 USSD Inclusivity Portal (*360#)")
    st.write("Ensuring access for users without internet-enabled devices[cite: 76, 568].")
    st.code("Dialing *360# ... \n1. Check Queue Status\n2. Order Medicine\n3. Register for SHA")

# --- MODULE 3: DOCTOR'S DESK ---
elif menu == "Doctor: Clinical Desk":
    st.header("👨‍⚕️ Physician Accessibility Portal")
    st.write("Managing patient flow and agentic AI documentation[cite: 625, 629].")
    queue = pd.DataFrame({
        "Ticket": ["TICK-902", "TICK-441"],
        "Patient": ["Dennis K.", "Fidel M."],
        "Status": ["Awaiting Video", "In-Queue"]
    })
    st.table(queue)

# --- MODULE 4: CAREERS PORTAL ---
elif menu == "Careers: Job Matching":
    st.header("💼 Blockchain-Verified Job Matching")
    st.write("Connecting 42,000+ unemployed nurses with hospitals[cite: 549, 560].")
    st.info("**Nurse Vacancy** - Iten County Referral Hospital")
    st.button("Apply with Immutable Blockchain Credential")

# --- MODULE 5: ADMIN & SHA ANALYTICS ---
elif menu == "Admin: SHA & Analytics":
    st.header("📊 Health Management & SHA Data")
    st.write("Aligning with the Social Health Authority and Digital Health Act[cite: 374, 537].")
    m1, m2, m3 = st.columns(3)
    m1.metric("Wait Time (Manual)", "4.0 Hours")
    m2.metric("Wait Time (AfyaPlus)", "45 Mins", "-81%")
    m3.metric("Revenue (SHA Synced)", "KSh 14,200")
    st.bar_chart(pd.DataFrame({"Minutes": [240, 45]}, index=["Manual Queue", "AfyaPlus 360"]))
