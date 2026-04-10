# Project Spam

## Objective

The objective of this project is to analyse messages and predict which of them are spams. 

## Dataset

The dataset can be found in the file spam.csv, in the data folder.
It is composed of 2 columns, one of which is the target (spam/ham) while the second contains the messages.
There are also 3 empty columns that will need to be deleted during 

## Study

This study aimed at producing a prediction model in 2 different ways: 
- Create an original embedding and a model for this project (in the file 01-Embedding_notebook.ipynb).
- Use transformers in order to reuse powerful models already trained(in the file 02-Transformer_notebook.ipynb). 

### Original embedding and modeling

**Data processing**
The data are loaded, and the empty columns dropped. 
The labels are also transformed into numerical values (0 and 1 for hams and spams, respectively).

**Embedding**
The tokenizer is generated using the cl100k_base encoding applied to our documents.
In order for the training to work, the max token size for a document is fixed at 50 (93% of the dataset), and a padding is applied if necessary.

**Modelling**
The model is created using three layers: 
- One Embedding layer
- One pooling layer
- One Linear layer (output)

**Result**
After training, we reached the following results:
                0       1
- Precision:    1       0.83
- recall:       0.97    0.98
- f1-score:     0.98    0.90

Which appear to be satisfactory results, especially for such a simple model.

### Transformer

The "bert-base-uncased" was selected due to its generally good results, but this could potentially be improved upon by selecting a more appropriate model.

**Data processing**
The data are processed similarly to the previous part of the study.

**Embedding**
The tokenizer is generated using the tokenizer associated with our selected model and then applied to our dataset.

**Modelling**
The calculation of the metrics is prepared to be fed to the Trainer function from the transformer library.

**Results**
