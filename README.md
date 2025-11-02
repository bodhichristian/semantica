# semantica
An engine for category prediction during the software ticket submission process.

## Overview
Software tickets come in all shapes and sizes. The category of ticket often determines the relevant details necessary to sort and solve. By predicting the category during the issue submission workflow, we can streamline the issue submission flow, while targeting the contextually relevant data. To achieve this, title, body, and label content from a dataset of 16,000 GitHub issues found on Kaggle was processed into phrases and character sequences as TF-IDF data for token analysis. Random oversampling was then used to balance minority classes, and a Logistic Regression model was trained to predict one of 5 categories: bug, help wanted, documentation, enhancement, and other. The web app mentioned below simply reverses the pipeline, combining the text and body before processing semantic calculations to return a prediction.

### Initial Dataset
Helpdesk Tickets - High Quality Github Issue  
https://www.kaggle.com/datasets/tobiasbueck/helpdesk-github-tickets/data

### Model Performance
The model's has an F1 score of 0.885 for accuracy. Currently the model best predicts for _Bug_ with 0.924 precision and an F1 score of 0.945. The poorest performance is for predicting _Help Wanted_ with a precision and F1 score of 0.571 and 0.403 respectively. More details are available in the /model_training directory mentioned below. The web app mentioned below leverages the Google Sheets API to collect user input in a research demo setting, and will be used to further enhance the model performance. The title, body, predicted category, and additional context are stored. This helps to understand model performance in a real-world setting, and potentially gain deeper insights. Future iterations may provide automatic predictions during issue body composition by leveraging a prediction for the following texts prior to a prediction for category.

<img width="1620" height="447" alt="Screenshot 2025-11-02 at 6 22 54 PM" src="https://github.com/user-attachments/assets/6a867da8-9c18-42fb-bd48-b1df764f13f4" />


### /model_training
This folder contains a jupyter notebook exploring various machine learning models in an attempt to create a model that can predict an issue's category based on the semantic and heuristic data available in just the title and body text. The best performing pipeline and corresponding metadata are available in `/model_training/models/`

### Demo repository
The code that powers the app is also available on Hugging Face [here](https://huggingface.co/spaces/bodhichristian/semantica/tree/main). A single app.py file drives an intelligent form submission experience with an interface powered by Gradio.

### Research demo
A playground for model interaction is available on Hugging Face [here]( https://huggingface.co/spaces/bodhichristian/semantica). It simulates a software issue submission form experience, and takes title and description input from the user. When the user advances through the flow, the model predicts the category based on the input, and returns a category prediction. This prediction is used to present additionally, contextually relevant form fields. The Google Sheets API is implemented to capture and store input data, model predictions, and final category selections.

https://github.com/user-attachments/assets/cef36faf-044b-4d16-adbc-8a77cd29cbc5

**Improvements in progress:**
- Leverage Hugging Face to expose and document model API 


