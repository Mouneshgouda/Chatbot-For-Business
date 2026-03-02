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
##image TO Text

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

