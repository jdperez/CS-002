# Programming Project 12: Election Ballot Tabulator

## Problem Description

Your city is instituting a new voting procedure to combat election fraud. Each ballot item has a letter associated with every possible selection a voter may make.

**Sample Ballot:**

| # | Item | Option | Letter |
|---|------|--------|--------|
| 1 | Vote for Mayor | Pincher, Penny | A |
| | | Dover, Skip | B |
| | | Perman, Sue | C |
| 2 | Proposition 17 | Yes | D |
| | | No | E |
| 3 | Measure 1 | Yes | F |
| | | No | G |
| 4 | Measure 2 | Yes | H |
| | | No | I |

After submitting a ballot, each voter receives a receipt with a unique ID and a string encoding their selections (e.g., ID `4925 : CDGH` means Sue Perman, Yes on Prop 17, No on Measure 1, Yes on Measure 2).

The next day the city posts all votes publicly, sorted by ID, so voters can verify their own submission and anyone can independently tally the results.

---

## Your Task

Write a program that reads the posted voting list from a file and outputs the **percent of votes cast** for each ballot item.

---

## Requirements

### `Voter` Class
Define a class named `Voter` that:
- Stores an individual's complete voting record
- Has a **constructor** that takes:
  - A voter ID (integer)
  - A string of votes (e.g., `"CDGH"`)
- Has **accessor functions** that return:
  - The voter's ID
  - The voter's selection for a specific ballot question (by index for a specific question). For example, getSelection(1) given a string of votes "CDGH", would return "Voter voted NO for Prop 17.

### Input File Format
- No header lines
- Each line contains a voter ID and a vote string, e.g.:
  ```
  4925 CDGH
  4926 AEGH
  4927 CDGI
  4928 BEGI
  4929 ADFH
  ```

### Program Behavior
1. Read all records from the file and store each as a `Voter` object in an **array or vector**
2. Iterate over the collection and compute the **percent of votes** for each candidate, proposition, and measure — output the results
3. Prompt the user to **enter a voter ID**
4. Search the collection for that ID and **print that voter's selections**

---

## Sample Output

```
=== Vote Totals ===
Mayor:
  A. Pincher, Penny  : 40.0%
  B. Dover, Skip     : 20.0%
  C. Perman, Sue     : 40.0%

Proposition 17:
  D. Yes             : 40.0%
  E. No              : 60.0%

Measure 1:
  F. Yes             : 40.0%
  G. No              : 60.0%

Measure 2:
  H. Yes             : 80.0%
  I. No              : 20.0%

Enter voter ID: 4927
Voter 4927 voted: C G I (Perman, No on Prop 17, No on Measure 1, No on Measure 2)
```

---

## Hints
- Each vote string is always exactly **4 characters** long (one per ballot item)
- Use the character's position in the string to determine which ballot item it belongs to
- Letters `A/B/C` → Mayor, `D/E` → Proposition 17, `F/G` → Measure 1, `H/I` → Measure 2
