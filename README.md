# RoBERTa_qa
Analyzing RoBERTa's limitations on 'why' questions in QA tasks and exploring data augmentation techniques to improve causal reasoning performance

Overview
This project investigates the performance challenges of the RoBERTa model when handling "why" questions in the Stanford Question Answering Dataset (SQuAD). Through systematic analysis and experimentation, we identify key limitations and explore various approaches to enhance model robustness on complex reasoning questions.
Key Findings

Performance Gap: RoBERTa achieves only 51% accuracy on "why" questions compared to 78.57% exact match on general QA tasks
Context Sensitivity: Model struggles with longer contexts and questions requiring careful parsing of multiple entities or events
Adversarial Vulnerability: Significant performance degradation (F1: 86.22 → 20.68) when evaluated on Adversarial SQuAD

Methodology
Error Analysis
Manual categorization of model errors revealed primary failure modes:

Incorrect entity/date selection from multiple options (24% of errors)
Missing critical passage elements (18% of errors)
Complex passage interpretation challenges (18% of errors)

Experimental Approaches

Data Augmentation: TextAttack library for synonym replacement and back-translation
Context Perturbation: CLARE augmenter for context modification
Cross-Dataset Training: Fine-tuning on Quoref dataset for coreference resolution

Datasets Used
DatasetTotal EntriesWhy QuestionsMean EntitiesMean DatesSQuAD10,5701507.131.87Adversarial SQuAD30,0007957.291.92Quoref19,3991718.185.52
Results Summary

Best Overall Performance: Original SQuAD-trained model (F1: 86.22)
Adversarial Robustness: Quoref fine-tuning showed modest improvement (F1: 21.30 vs 20.67)
Augmentation Limitations: Automatic data augmentation showed quality issues and limited effectiveness

Key Insights

Question Type Specificity: "Why" questions require fundamentally different reasoning compared to factual questions
Context Structure Dependency: Models heavily rely on training data structure patterns
Augmentation Quality: Automatic augmentation techniques may introduce context-inappropriate modifications
Dataset Design Impact: Specialized datasets like Quoref provide marginal but measurable improvements

Implications
This research highlights the need for:

More sophisticated data augmentation techniques for QA tasks
Manual curation of augmented data to ensure quality
Specialized training approaches for causal reasoning questions
Better evaluation metrics for complex reasoning tasks

Technical Stack

Model: RoBERTa (Robustly Optimized BERT Pretraining Approach)
Datasets: SQuAD, Adversarial SQuAD, Quoref
Augmentation: TextAttack library (synonym replacement, back-translation, CLARE)
Analysis: Logistic regression for error pattern identification


Citation
If you use this work in your research, please cite:
@misc{roberta-why-qa,
  title={Comparing Methods to Improve Performance on Why Questions in QA Tasks},
  author={[Mario Paulin Vega},
  year={2024},
  note={Research project examining RoBERTa limitations on causal reasoning questions}
}

Note: The code for this project is private. 
