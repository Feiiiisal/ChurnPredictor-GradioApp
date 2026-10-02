# Customer Churn Predictor (Gradio)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Python](https://img.shields.io/badge/python-3.8%2B-blue)
![Gradio](https://img.shields.io/badge/UI-Gradio-orange)
![scikit-learn](https://img.shields.io/badge/model-Random%20Forest-green)

A small web app that predicts whether a telecom customer is likely to **churn**
(leave) or **continue**, from 19 inputs such as contract type, services, monthly
charges and tenure. The interface is built with [Gradio](https://gradio.app), so
anyone can try the model without writing code.

## How it works

1. **Enter customer details**: demographics, phone and internet services, add-ons
   (security, backup, tech support, streaming), contract, billing method, monthly
   and total charges, and tenure in months.
2. **Click Predict.** The app turns tenure into a tenure group, applies the saved
   preprocessing pipeline (one-hot encoding and scaling) and runs a pre-trained
   **Random Forest** classifier.
3. **Read the result**: "This customer is likely to be churned." or "This
   customer is likely to continue."

The model and its training notebook live in the companion project
[Customer-Churn-Prediction-Analysis](https://github.com/Feiiiisal/Customer-Churn-Prediction-Analysis).

## Project layout

```
app2.py                           Gradio app (inputs, preprocessing, prediction)
Loaded Models/
  churn_model.pkl                 Trained Random Forest classifier
  churn_pipeline.pkl              Saved preprocessing pipeline
requirements.txt
```

## Setup and run

```bash
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

The app opens its model files from the current folder, so start it from inside
`Loaded Models`:

```bash
cd "Loaded Models"
python ../app2.py
```

`app2.py` ends with `launch(share=True)`, which also creates a temporary public
link. Change it to `launch()` if you only want the app on your own machine.

**Note on versions:** `requirements.txt` pins older library versions
(for example `gradio==2.3.0` and `scikit-learn==0.24.2`). Pickled scikit-learn
models can fail to load on other versions, so use a dedicated virtual
environment with these pins (an older Python such as 3.8 or 3.9 is the safest
choice).

## License

[MIT](LICENSE)
