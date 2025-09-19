# Assignment 1: Metabolic Modelling

## Objective

The objective of this assignment is to explore enzyme activity-constrained metabolic modeling using COBRApy. The tasks include analyzing reaction fluxes, implementing maximal reaction activity data, performing Flux Variability Analysis (FVA), and optimizing biomass production. The assignment aims to deepen understanding of metabolic networks and their constraints.

## Instructions to Run the Code

1. **Setup Environment**:
   - Ensure Python is installed on your system.
   - Install the required Python libraries using the following command:

        ```bash
        pip install cobra pandas
        ```

2. **Prepare Input Files**:
   - Place the `e_coli_core.json` file (E. coli core model) in the same directory as the notebook.
   - Ensure the `e_coli_core_expression.csv` file (containing estimated maximal activity data) is also in the same directory.

3. **Run the Notebook**:
   - Open the `assignment-1.ipynb` notebook in a Jupyter environment.
   - Execute the cells sequentially to complete the tasks.

4. **Output**:
   - The notebook will print tables and results for each task, including reaction bounds, FVA results, and biomass optimization outcomes.

## Notes

- The specific instruction for this assignment can be found in `KEN3170_Assignment_Metabolic_Modeling_06_09_2025`.
- The glucose exchange reaction and ATPM energy maintenance reaction are handled with specific constraints as described in Task 2.
- The notebook includes detailed explanations for each task, providing insights into the metabolic model's behavior.
- This folder contains `assignment-1.pdf`. This is the exported notebook with our final outputs. In case any issues arise while running the notebook this pdf serves as a backup.

## Dependencies

- Python 3.7 or higher
- COBRApy
- pandas
- CSV file containing estimated maximal activity data (`e_coli_core_expression.csv`)
- JSON file for the E. coli core model (`e_coli_core.json`)

## Group contributions

Member | Tihon | Valentino | Jesse
-|-|-|-
Contribution | Q2 | Q1, Q3 | Q4, README
Points | 30 | 45 | 25, \

The distribution of task was decided unanimously using a Whatsapp group.

## Use of Generative AI Tools

We used generative AI tools to help write and proofread this README file. AI was only used for documentation support, not for generating code or analysis. All generated output has been reviewed and modified by a human.

### Recorded conversations

`JesseHoydonckx`:

```md
Create a readme file for this assignment. The README should:
- Describe the objective of the assignment
- Provide instructions on how to run your code
- Include any other relevant notes or dependencies
```

`GitHub Copilot`:

````md
Made changes.

The README file has been created with the requested content, including the objective, instructions, and dependencies. Let me know if you need further adjustments or fixes for the linting issues.
````
