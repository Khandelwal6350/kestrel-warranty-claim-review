# Kestrel Warranty Claim Review

A local machine-learning prototype for ranking warranty claims by review risk. The project uses Python and scikit-learn for model development and FastAPI to expose the workflow through an API. It is intended to support human reviewers by surfacing claims that may need closer inspection—not to make final warranty decisions automatically.

## What this project does

- Loads and prepares warranty-claim data for model-based review.
- Uses a scikit-learn model to produce risk-oriented predictions or scores.
- Exposes the prototype through a local FastAPI service.
- Supports human review: model output should be treated as a prioritisation aid, not proof of fraud or grounds for automatic rejection.
- Includes project code and validation material in the repository archive.

## Requirements

- Python 3.10 or newer recommended
- `pip`
- A terminal / PowerShell

## Setup

1. Clone the repository and enter the project directory:

   ```bash
   git clone https://github.com/Khandelwal6350/kestrel-warranty-claim-review.git
   cd kestrel-warranty-claim-review
   ```

2. Extract the project archive committed in the repository:

   ```text
   kestrel_warranty_review_complete.zip
   ```

   Extract it into a working folder, then open a terminal in the extracted project directory. If you already have the extracted project files, skip this step.

3. Create and activate a virtual environment:

   **Windows PowerShell**
   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   **macOS / Linux**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

4. Install the project dependencies from the supplied requirements file:

   ```bash
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

## Run the API

From the extracted project directory, locate the Python file that defines the FastAPI instance (the variable is commonly named `app`). Start Uvicorn using the module path that matches that file. For example, if the instance is `app` in `app/main.py`:

```bash
uvicorn app.main:app --reload
```

If the entry-point file or instance has a different name, replace `app.main:app` with the corresponding `module_name:instance_name`.

When the server starts, open:

- API documentation: `http://127.0.0.1:8000/docs`
- OpenAPI schema: `http://127.0.0.1:8000/openapi.json`

Keep the terminal running while testing the API. Use the endpoints shown in `/docs`; the exact request fields depend on the project’s API schema.

## Run tests / validation

If the project contains a `tests/` directory and uses pytest, run:

```bash
python -m pytest -q
```

Run any evaluation or validation scripts included with the extracted project using the commands documented in those scripts or their help output. Record the actual results; do not assume a score or metric from a previous run.

## Suggested review workflow

1. Start the API and open `/docs`.
2. Submit a representative claim using the schema displayed by the API.
3. Inspect the model output and the explanation or review cues returned by the prototype.
4. Compare the result with the source claim and any available ground truth.
5. Send uncertain, incomplete, or high-impact cases to a human reviewer.

## Important limitations

- This is a prototype, not a production warranty adjudication system.
- A model score is not a probability unless it has been calibrated and validated as such.
- Model predictions can be wrong and may reflect gaps or bias in the training data.
- Do not use model output as the sole basis for denying a claim.
- Before real-world deployment, validate performance on a held-out dataset, assess class-specific precision/recall and calibration, document data provenance, protect personal information, and establish human oversight and monitoring.

## Repository contents

The repository currently includes `kestrel_warranty_review_complete.zip`, which contains the project files. Extract the archive before running the application. This README describes the intended setup; confirm the exact entry-point module and available scripts against the extracted files.

## Author / submission

Prepared as a Task 1 project submission for review by Banao Technologies.
