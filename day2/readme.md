
```
!pip install --upgrade google-generativeai pandas

import pandas as pd
import google.generativeai as genai
from getpass import getpass

api_key = getpass("Enter your Google API Key: ")

genai.configure(api_key=api_key)
model = genai.GenerativeModel("gemini-2.5-flash")

csv_path = "/content/business_data.csv"  
df = pd.read_csv(csv_path)

context_text = ""
for _, row in df.iterrows():
    context_text += f"Q: {row['question']}\nA: {row['answer']}\n\n"

def ask_gemini(query):
    prompt = f"""
You are a Q&A assistant.

Answer ONLY using the context below.
If the answer is not present, say: No relevant Q&A found.

Context:
{context_text}

Question: {query}
"""
    response = model.generate_content(prompt)
    return response.text.strip()

print("Chatbot is running! Type 'exit' to quit.\n")
while True:
  
    user_input = input("You: ")
    if user_input.lower() == "exit":
        print("Goodbye!")
        break
    answer = ask_gemini(user_input)
    print(f"Bot: {answer}\n")

```




