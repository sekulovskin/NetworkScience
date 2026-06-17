# Bring Your Own Data

This note explains how to prepare your own data for the practical sessions of the Utrecht University Summer School on Network Science.

The most important requirement is: **your data must already be clean before the course starts**.

If your files still need major cleaning, merging, recoding, or restructuring, you will spend the practical time doing data wrangling instead of network analysis.

Below we explain the main data formats we use.

## General rules

- Bring `.csv` files if possible. If your data is in Excel, export it as `.csv`. `.tsv` and `.parquet` files are also fine.
- Use one header row with clear column names.
- Keep one type of data per file.
- Use the same IDs across files.
- Remove blank rows, duplicate rows, missing IDs, and messy Excel formatting before class.
- If your data is large, also bring a smaller version so you can first test the methods within the limited practical time.

## Size guidelines

For laptop-based sessions, small to medium-sized datasets work best. The limits below are practical guidelines, not strict rules. If your full dataset is larger than the suggested size, please still bring it, but also prepare a smaller subset. 

## Types of questions and data

The type of data depends on your type of question. Each one is detailed below.

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

Laptop-friendly size guideline:

- fewer than 10,000 nodes and fewer than 100,000 edges

### I want to know whether the network depends on attributes

Also bring a node table with:

- `node_id`
- one or more attributes such as `class`, `team`, `office`, or `gender`

Example:

- a workplace network: do people connect more often to others in the same department?

Laptop-friendly size guideline:

- fewer than 10,000 nodes and fewer than 100,000 edges

### I want to find communities (clusters) in the network

Use this for:

- community detection

Example:

- a student social network: are there clear groups based on interests or study program?

Laptop-friendly size guideline:

- fewer than 1,000 nodes and fewer than 50,000 edges

### I want to predict whether there may be missing links

Bring a network edge list with `source` and `target`. The candidate pairs (possible missing links) are created automatically during the practical.

Example:

- a protein interaction network: which pairs of proteins are likely to interact, even if the interaction has not yet been observed?

Laptop-friendly size guideline:

- fewer than 1,000 nodes and fewer than 50,000 edges

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

Laptop-friendly size guideline:

- fewer than 5,000 events and fewer than 30 actors

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

Laptop-friendly size guideline:

- fewer than 5,000 observations and fewer than 30 variables

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

Laptop-friendly size guideline:

- fewer than 5,000 observations and fewer than 30 variables


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

If you do not know node thresholds, we can assign example thresholds during the practical.

Laptop-friendly size guideline:

- fewer than 500 nodes and fewer than 5,000 edges

Example:

- a student friendship network: how might a rumor, behavior, or innovation spread through the class?
