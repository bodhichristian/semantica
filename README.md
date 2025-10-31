# semantica
An engine for category prediction during the software ticket submission process.

### /model_training
This folder contains a jupyter notebook exploring various machine learning models in an attempt to create a model that can predict an issue's category based on the semantic and heuristic data available in just the title and body text. The best performing pipeline and corresponding metadata are available in `/model_training/models/`

### research demo
A playground for model interaction is available on Hugging Face [here]( https://huggingface.co/spaces/bodhichristian/semantica). It simulates a software issue submission form experience, and takes title and description input from the user. When the user advances through the flow, the model predicts the category based on the input, and returns a category prediction. This prediction is used to present additionally, contextually relevant form fields.

**Improvements in progress:**
- Leverage Hugging Face to expose and document model API 
- Form submission enhancements, terms of use
- Analytics, logging

### demo repository
The code that powers the app is also available on Hugging Face [Here](https://huggingface.co/spaces/bodhichristian/semantica/tree/main). A single app.py file drives an intelligent form submission experience with an interface powered by Gradio.
