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


##### 3.1 Which mutation is most dangerous and why? Provide quantitative evidence.

Mutations A, B and C appear equally dangerous. Looking at the final states resulting from all the possible 256 initial states, we see that for mutations A, B and C the only possibilities are 128 instances of Normal growth and 128 instances of cancerous growth with DNA damage. All three mutations make it impossible for the cell death mechanism to be triggered.

On the other hand, mutation D (MDM2 knockout) seems to make growth with DNA damage impossible. Across the 256 possible initial states, we saw 128 final states of normal growth (DNA damage OFF) and 128 with cell death (DNA damage ON)

##### 3.2 Explain the role of feedback loops (e.g., MYC → MDM2 → p53)

In this simulation, the feedback loops are what allow the system to have multiple steady states. For example, MYC activates MDM2 which suppresses p53. Which in turn suppresses MYC. Looking at just these 3 genes, we get 2 possible steady states.

| Steady State | MYC | MDM2 | p53 |
|--------------|-----|------|-----|
| 1            | ON  | ON   | OFF |
| 2            | OFF | OFF  | ON  |

If the network were a tree instead, you could simply evaluate if each gene is active starting from the top of the tree going downwards. No simulation would be necessary to determine the final state as you could solve for it analytically. However, such a network would be a poor model for most biological networks as it wouldn't be able to model mechanisms with cycles (eg circadian rhythm) and memory.

##### 3.3 What are the limitations of this Boolean network model? Discuss 3 specific limitations.
- 