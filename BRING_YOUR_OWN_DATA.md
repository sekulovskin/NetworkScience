# Bring Your Own Data

This note explains how to prepare your own data for the practical sessions of the Utrecht University Summer School on Network Science.

The most important requirement is: **your data must already be clean before the course starts**.

If your files still need major cleaning, merging, recoding, or restructuring, you will spend the practical time doing data wrangling instead of network analysis.

Below we explain the main data formats we use.

## General rules

- Bring `.csv` or `.tsv` files.
- Use one header row with clear column names.
- Keep one type of data per file.
- Use the same IDs across files.
- Remove blank rows, duplicate rows, missing IDs, and messy Excel formatting before class.

## Types of questions and data

1. I already have a network (nodes interacted or are connected)
   - I want to describe the network
   - I want to know whether the network depends on attributes
   - I want to find communities (clusters) in the network
   - I want to predict whether there may be missing links
2. I have event data (interactions over time with a sender and a receiver)
3. I do not have a network yet, but I have many variables and want to study their interactions
   - Numerical data
   - Categorical data
4. I want to study contagion or diffusion

---

## 1. I already have a network (nodes interacted or are connected)

Bring an **edge list**.

Required columns:

- `source`
- `target`

Optional columns:

- `weight`
- `time`
- `layer`

Optional second file:

- a node table with `node_id` and node attributes

### I want to describe the network

Use this for:

- centrality
- basic network description

Example:

- a friendship network in a classroom: who is connected to whom, and who is most central?

### I want to know whether the network depends on attributes

Also bring a node table with:

- `node_id`
- one or more attributes such as `class`, `team`, `office`, or `gender`

Example:

- a workplace network: do people connect more often to others in the same department?

### I want to find communities (clusters) in the network

Use this for:

- community detection

Example:

- a student social network: are there clear groups based on interests or study program?

### I want to predict whether there may be missing links

Bring two files:

- a network edge list with `source` and `target`
- a file with candidate pairs and a label

Candidate-pair file:

- `source`
- `target`
- `label`

Where:

- `label = 1` means a true edge
- `label = 0` means a non-edge

Example:

- a protein interaction network: which pairs of proteins are likely to interact, even if the interaction has not yet been observed?

---

## 2. I have event data (interactions over time with a sender and a receiver)

Bring a **directed event list**.

Required columns:

- `time`
- `sender`
- `receiver`

Optional second file:

- an actor table with `actor_id` and actor attributes

Best if:

- `time` is numeric or written in one consistent timestamp format
- rows are already in time order
- IDs are consistent
- actor IDs are integers from `1` to `N`

Example:

- email data: who emailed whom, and when?

---

## 3. I do not have a network yet, but I have many variables and want to study their interactions

### Numerical data

Bring a **numeric matrix**.

- one row = one observation
- one column = one numeric variable

Rules:

- all analysis columns must be numeric
- do not include text, IDs, or dates in the matrix
- column names should be short and unique
- remove missing values before class

Example:

- gene expression data: each row is a patient or cell, and each column is a gene

### Categorical data

Bring a table where:

- one row = one observation
- one column = one categorical variable

Rules:

- categories must be clean and consistent
- avoid free text
- avoid spelling differences like `Yes`, `yes`, and `Y`

Example:

- survey data: each row is one respondent, and the columns are answers such as education level, job type, or voting preference

---

## 4. I want to study contagion or diffusion

Bring a **static undirected edge list**.

Required columns:

- `source`
- `target`

Optional second file:

- a node table with `node_id` and `threshold`

Example:

- a student friendship network: how might a rumor, behavior, or innovation spread through the class?
