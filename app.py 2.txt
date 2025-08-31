import streamlit as st

# --------------------------
# 1. Define required keywords
# --------------------------
required_keywords = [
    "python", "machine learning", "deep learning", "data science",
    "sql", "cloud computing", "nlp", "computer vision", "statistics"
]

# --------------------------
# 2. Function to find missing keywords
# --------------------------
def find_missing_keywords(resume_text, required_keywords):
    resume_text_lower = resume_text.lower()
    missing = [kw for kw in required_keywords if kw not in resume_text_lower]
    return missing

# --------------------------
# 3. Streamlit App
# --------------------------
st.title("📄 Resume Screener App")

st.write("Upload or paste your resume, and we'll check for missing keywords!")

# Input box for resume text
resume_text = st.text_area("✍️ Paste your Resume Text Here")

# Button to analyze
if st.button("🔍 Analyze Resume"):
    if resume_text.strip() == "":
        st.warning("⚠️ Please paste some resume text before analyzing.")
    else:
        # Dummy accuracy (later you can connect ML model here)
        st.write("✅ Resume Match Score: **52%**")

        # Find missing keywords
        missing = find_missing_keywords(resume_text, required_keywords)

        if missing:
            st.error("⚠️ Missing important keywords:")
            for kw in missing:
                st.write(f"- {kw}")
        else:
            st.success("🎉 Great! All important keywords are present in your resume.")
