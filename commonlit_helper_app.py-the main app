import streamlit as st
import openai
import os

# Use a Streamlit secret or hardcoded key
openai.api_key = os.getenv("OPENAI_API_KEY", "sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

st.set_page_config(page_title="CommonLit AI Helper", layout="centered")

st.title("CommonLit AI Helper")
st.markdown("Paste your reading passage below, ask a question, and get help from AI!")

passage = st.text_area("Paste the CommonLit Passage:", height=250)

question = st.text_input("Enter your question about the passage:")

if st.button("Get Answer"):
    if not passage or not question:
        st.warning("Please provide both the passage and a question.")
    else:
        with st.spinner("Thinking..."):
            try:
                response = openai.ChatCompletion.create(
                    model="gpt-4",
                    messages=[
                        {"role": "system", "content": "You are a helpful tutor."},
                        {"role": "user", "content": f"Passage:\n{passage}\n\nQuestion: {question}"}
                    ],
                    max_tokens=500
                )
                answer = response.choices[0].message["content"].strip()
                st.success("AI Answer:")
                st.write(answer)
            except Exception as e:
                st.error(f"Error: {e}")
