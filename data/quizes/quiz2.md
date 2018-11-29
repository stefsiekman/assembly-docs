# Quiz 2

The weekly quizes contain, of course, information that is important for the
exam. To help learn for these exams later, this document contains a summary of
the theoretical knowledge required for quiz 2.

## Keys

### Super key

Any set of columns, that can be used to uniquely identify a row.

### Candidate key

Set of columns that is a minimal super key. I.e. removing a column from the set
would mean it can no longer be used for identification.

### Composite key

Set of columns that can be used to indentify rows, but single columns of this
set cannot be used for identification. I.e. the case where the key is not just
a single column.

## Normal forms

## 1NF

Atomic columns: cells have single values

## 2NF

No partial dependencies: values depend on the whole of every candidate key

## 3NF

No transtive dependencies: values depend only on candidate keys

## BCNF

No redundencies from functional dependencies
