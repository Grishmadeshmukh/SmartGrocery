## 🛒 FoodGuard 

Grocery Detection:
Fine-tuned ResNet-50 classifier on combined grocery datasets (25 classes)
Handles packaged and loose items (fruits & vegetables)
Trained using Adam optimizer with ReduceLROnPlateau and EarlyStopping

Label Text Extraction:
EasyOCR used for extracting text from product packaging
Text cleaning pipeline includes:
Lowercasing
Noise & OCR artifact removal
Stopword filtering
Blacklist-based garbage token rejection
If OCR fails → fallback to classifier label

Nutritional Information Retrieval:
Intelligent query construction using:
Extracted brand name
Cleaned keywords (≤3 tokens)
Nutrition facts fetched using OpenFoodFacts API

Expiry Date Detection:
Bounding box regression to localize expiry label
OCR applied on detected region to extract date
Used to estimate remaining shelf life

Recipe Generation:
Gemini 2.5 Flash used for recipe generation
Inputs include product names and nutritional values
Items closer to expiry are prioritized in recipes
