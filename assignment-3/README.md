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

This boolean network model is a good baseline to get some insights into the cell's regulatory system. Despite this limitations arrise due to the level of abstraction and simplification that we did to model the system.

A first limitation is in the setup of the nodes being strictly ON or in an OFF state, for example node p53 and MYC. In a real biological cell this would most likely not be the case but rather be a value inside of a range in terms of concentration and activity levels. A clear example would be P53 which it's cell response is dose dependent, so a low dose might not trigger the cell death but in the case of our model it triggers immediately due to the binary nature of the setup. 

A second limitation is the assumption that the components in the network update at the same time. As we use the function update_synchronous, this assumes that every element updates at the exact same time in perfect synch. Again in a real world biological system this would not be the case as some reactions happen quicker or slower. Theoretically this could be integrated into the model but would make it much more complex but might offer more accurate insights. 

A third limitation of our simplified model is the abstraction of time. More specificaly the attractor analysis we conducted shows us the final state of the cell but does not tell us how quickly or slowly this was done. This is quite important as we can see in the Stressed Cell scenario, that damaged DNA can lead to cell death. There's no difference in the model between a slow reaction (aptosis in a few days) and a rapid one which would occur in a few minutes or hours. This is quite important as a cell that has some DNA damage might be able to split in time and pass on mutations before cell death occurs. 

## Running code

The code for this assignemnt is all contained in the BooleanModeling.ipynb notebook. Cells are intended to be run sequentially.

## Contributions

Member | Tihon | Valentino | Jesse
-|-|-|-
Contribution | Q3.3 | Q3.1 Q3.2 | simulation code