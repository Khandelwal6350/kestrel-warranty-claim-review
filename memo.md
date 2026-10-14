# Task 1 Memo — Kestrel Warranty Claim Review

**Project:** Kestrel Warranty Claim Review  
**Purpose:** Prototype for risk-oriented prioritisation of warranty claims  
**Prepared for:** Banao Technologies Hiring Team

## Executive summary

Kestrel Warranty Claim Review is a local machine-learning prototype intended to help a reviewer prioritise warranty claims for closer inspection. It combines Python and scikit-learn model logic with a FastAPI interface. The intended role of the model is decision support: it can surface claims that warrant attention, while a human reviewer remains responsible for the final outcome.

The repository currently distributes the implementation as `kestrel_warranty_review_complete.zip`. The README accompanying this memo explains how to extract the archive, install dependencies, start the API, and inspect its interactive API documentation.

## Objective and proposed workflow

The practical objective is to make the review process more consistent and easier to triage. A typical workflow is:

1. Receive claim information in the format expected by the API.
2. Apply the project’s input preparation and trained model.
3. Return the model output or risk-oriented review cue.
4. Use the output to prioritise human attention.
5. Check the claim against supporting evidence before taking action.

The model should not be treated as a substitute for policy interpretation, document checks, or human judgement.

## Implementation

The project is described in the repository as a local ML prototype using Python, scikit-learn, and FastAPI. This separation allows the model workflow to be exercised locally through an API. The exact model configuration, feature set, dataset composition, and endpoint schema should be confirmed from the source files and evaluation artifacts in the project archive.

## Validation and evidence

The implementation should be assessed using a held-out dataset that was not used to fit the model. At minimum, validation should report:

- Number of records used for training and evaluation.
- Class distribution and the definition of each target class.
- Confusion matrix.
- Precision, recall, and F1-score for each class.
- Overall accuracy, with class imbalance taken into account.
- False-positive and false-negative examples, especially where an incorrect risk flag could harm a claimant.
- Any data leakage checks and limitations in the available labels.

No numerical performance result is asserted in this memo because a verified evaluation output was not available while preparing this document. Results should be copied from a reproducible run of the project’s own validation code rather than estimated or invented.

## Risks and limitations

- **False positives:** a legitimate claim may be flagged for extra review.
- **False negatives:** a claim needing attention may not be flagged.
- **Data quality:** missing, inconsistent, or outdated claim fields can reduce reliability.
- **Bias and representativeness:** historical decisions or uneven data coverage can cause systematic errors.
- **Interpretability:** a score or label alone may not give a reviewer enough context to understand the model’s output.
- **Deployment readiness:** a local prototype is not, by itself, evidence of production reliability, security, scalability, or compliance.

## Recommendations

1. Keep a human reviewer in the decision loop; never automatically reject a claim solely because of the model output.
2. Validate on a representative held-out set and report class-specific metrics.
3. Review false positives and false negatives with domain experts.
4. Make missing inputs and uncertain predictions visible, and route these cases to manual review.
5. Document the model’s intended use, training data provenance, known limitations, and retraining process.
6. Before any deployment, add appropriate access controls, logging, privacy safeguards, monitoring, and a process for contesting or correcting decisions.

## Conclusion

Kestrel is a useful prototype direction for supporting warranty-claim triage. Its value should be judged by reproducible validation and whether it helps reviewers make better-informed decisions—not by a single headline accuracy number. The safest use is as a prioritisation aid with transparent limitations and human oversight.

---
*This memo describes the project at a high level. Confirm exact model details and measured results against the code and evaluation outputs before making claims about performance.*
