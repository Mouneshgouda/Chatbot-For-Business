### Text TO speech

```python
pip install gtts
```

```
from gtts import gTTS
from IPython.display import Audio
text = input("Enter the text to convert to speech: ")
tts = gTTS(text=text,lang='ta',tld='co.in',slow = True)
tts.save("output.mp3")
Audio("output.mp3", autoplay=True)

```

```
!pip install pytesseract #for google lens like ocr
```
### image TO Text

```
from PIL import Image
import pytesseract
img = Image.open('/content/Gemini_Generated_Image_2f6ckc2f6ckc2f6c.png')
text = pytesseract.image_to_string(img)
print(text)
```

### Text TO Image

```
!pip install diffusers
```


```

from transformers import pipeline
import torch
from diffusers import DiffusionPipeline

# Load the image generation pipeline using diffusers
generator = DiffusionPipeline.from_pretrained("CompVis/stable-diffusion-v1-4")
generator.to("cuda")

```


```
# Generate an image from the text prompt
prompt = "A beautiful landscape with mountains and a lake"
image = generator(prompt).images[0]
display(image)

```

```
# Single cell: Manual‑based Groq chatbot in Colab
!pip install groq gradio PyPDF2 --quiet

import os
import gradio as gr
from PyPDF2 import PdfReader
from groq import Groq

# — Set your Groq API key —
os.environ["GROQ_API_KEY"] = 
client = Groq(api_key=os.environ["GROQ_API_KEY"])

# — Load manual text —
def load_manual(file_path):
    text = ""
    if file_path.endswith(".pdf"):
        reader = PdfReader(file_path)
        for page in reader.pages:
            ptext = page.extract_text() or ""
            text += ptext + "\n"
    else:
        with open(file_path, "r", encoding="utf-8") as f:
            text = f.read()
    return text

manual_text = load_manual("/content/Learning_Objectives_of_CP-SAT_4.1_Python-updated-1.pdf")  # <-- Replace with your manual path

# — Chat function using a Groq‑supported model —
def chat_with_manual(question):
    try:
        response = client.chat.completions.create(
            model="openai/gpt-oss-120b",  
            messages=[
                {"role": "system", "content": "You are a helpful assistant. Answer based only on the given manual."},
                {"role": "user", "content": f"Manual:\n{manual_text}\n\nQuestion: {question}"}
            ],
            max_tokens=512
        )
        return response.choices[0].message.content
    except Exception as e:
        return f"Error: {str(e)}"

# — Gradio UI —
iface = gr.Interface(
    fn=chat_with_manual,
    inputs=gr.Textbox(lines=2, placeholder="Ask something about the manual..."),
    outputs="text",
    title="Manual‑Based Groq Chatbot",
    description="Ask questions from your manuawl using Groq API."
)

iface.launch()
```

https://github.com/Nirant07/Azure-AI-Fundamentals-AI-900-Microsoft/blob/main/Azure%20AI%20YT%20Notes.pdf
