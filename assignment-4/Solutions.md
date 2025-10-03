# Question 1:

Open the model and run it – as it is – for 4h. What is happening? What do you observe?

## Observations

| Hour  | **Current State**                                     | **Observation**
| -     | -                                                     | -
| 0     | ![initial state](./screenshots/q1.initialstate.png)   | The whole cell is still healthy. The cells are all well defined and bright green. We introduce a pathogen (red cell) into the tissue.
| 1     | ![after 1 hour](./screenshots/q1.state1.png)          | The pathogens starts spreading to the nearest cells,a s indicated by the yellowing color of the plant tissue. The cell walls begin to weaken and look more irregular.
| 2     | ![after 2 hour](./screenshots/q1.state2.png)          | Further spreading of the pathogen and more noticeable weakening of the cell walls.
| 3     | ![after 3 hour](./screenshots/q1.state3.png)          | Pathogen infects approximately 1/3 of the cell. Some infected cells take on irregular shapes and cell walls are weak.
| 4     | ![after 4 hour](./screenshots/q1.state4.png)          | More cells are infected, with the integrity of the cell walls for infected cells being significantly compromised. There is a clear difference in structure between the healthy and infected cells.

# Question 4:

## Comparison of Diffusion Coefficients

| Hour | **Diffusion Coefficient: E-4**                         | **Diffusion Coefficient: E-5 (default)**      | **Diffusion Coefficient: E-6**
| -    | -                                                      | -                                             | -
| 1    | ![1.0, 1h](./screenshots/q4.diffusion-10.state1.png)   | ![after 1 hour](./screenshots/q1.state1.png)  | ![2.0, 1h](./screenshots/q4.diffusion-20.state1.png)
| 2    | ![1.0, 2h](./screenshots/q4.diffusion-10.state2.png)   | ![after 2 hour](./screenshots/q1.state2.png)  | ![2.0, 2h](./screenshots/q4.diffusion-20.state2.png)
| 3    | ![1.0, 3h](./screenshots/q4.diffusion-10.state3.png)   | ![after 3 hour](./screenshots/q1.state3.png)  | ![2.0, 3h](./screenshots/q4.diffusion-20.state3.png)
| 4    | ![1.0, 4h](./screenshots/q4.diffusion-10.state4.png)   | ![after 4 hour](./screenshots/q1.state4.png)  | ![2.0, 4h](./screenshots/q4.diffusion-20.state4.png)

**Observation:**  
Increasing the diffusion coefficient results in faster and more widespread pathogen movement through the tissue. At higher coefficients, more cells are infected earlier, and the structural changes in the tissue are more pronounced. The growth of the pathogen cell is similar between different diffusion coefficients.

# Question 5:

Let’s suppose the plant has developed a defense mechanism that detects the chemical and triggers a signal for uninfected plant cells to strengthen their cell walls. How could this be implemented in the model?

To model such a defense mechanism we would need to introduce a second chemical into the system. The additions in the iteration loop of the model would look something like:

#### Produce signal molecule when pathogen is detected
```
if pathogen_chem_level > 0.05:
    signal_chem_level = 0.1
```

#### When the signal molecule is detected, the cell reinforces it's cell walls increasing stiffness
```
stiffness = baseline_stiffness - patho_chem_level

if signal_chem_level > 0.05:
    stiffness += signal_chem_level
```

#### Apply decay to the concentration of the signal molecule. (relevant for when it stops being produced)
```
signal_chem_level = 0.99 * signal_chem_level
```