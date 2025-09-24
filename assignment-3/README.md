# Assignment 3

Building on the Boolean Networks practical, you will conduct an independent analysis of cancer-causing mutations using Boolean networks

Use the completed BooleanModeling.ipynb notebook from the practical as a starting point.

Create 4 different mutated versions of the cell regulatory network by modifying the Boolean rules:

- Mutation A: p53 Knockout (Loss of tumor suppressor):   network.add_rule('p53', lambda s: False, "p53 = BROKEN (always OFF)")
- Mutation B: MYC Amplification (Oncogene overexpression):   network.add_rule('MYC', lambda s: True, "MYC = AMPLIFIED(always ON)")
- Mutation C: MDM2 Overexpression (p53 pathway disruption):   network.add_rule('MDM2', lambda s: True, "MDM2 = OVEREXPRESSED (always ON)")
- Mutation D: Your Choice (Design your own mutation)

For each mutation (A, B, C, D) + normal network:

1. Scenario Analysis: Test all 3 scenarios from practical
2. Attractor Analysis: Find all attractors for each mutated network (What percentage of states lead to cancer-like states?)

Answer the following questions in your README.md file:

- Which mutation is most dangerous and why? Provide quantitative evidence.
- Explain the role of feedback loops (e.g., MYC → MDM2 → p53)
- What are the limitations of this Boolean network model? Discuss 3 specific limitations.
