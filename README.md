# **Instructions for Using MQ_MZ_Ejection_SingleQ** 

This program is an _ad hoc_ derevative of Demiurge_MultiQ_486 program developed in **Processing** and **Java**. It simulates ion motion within a single qudrupole of 486-quadrupole MultiQ-IT ion trap configured for m/z-dependent ion jection from the MultiQ-IT.  The computer model is based on work described in greater detailes by **A.N. Krutchinsky, I.V. Chernushevich, V.L. Spicer, W. Ens, K.G. Standing.** *Collisional Damping Interface for an Electrospray Ionization Time-of-Flight Mass Spectrometer*, **Journal of the American Society for Mass Spectrometry**, Volume 9, Issue 6, June 1998, Pages 569–579.

The program calculates ion trajectories in the single quadrupole. It is assumed that ions enter the quadrupole from the side facing the confinement region of the MultiQ-IT. To achieve m/z dependent ion ejection, two neigboring rods of a quadrupole ( 6.35mm in diameter, 12 mm long, see parmeters defined in MQ MZ ejection singleQ folder) are squized together at the qudrupole entrence at an angle 0.02 radian (Geometry folder, line 516). Ions entering the quadrupole operating in FR-only mode with addition of a small excitation voltage ( see parameters around line 90 in MQ MZ Ejection singleQ folder) from the confiment region of a MultiQ are moving along the quadrupole until they are stopped by a plate postioned at the other end of a quadrupole by a 5 V potential difference (line 86 MQ MZ EjectionQ folder). Ions whose frequency of oscillation in the quadrupole resonate with excitation frequency will experince ecitation leading to increase of amplitude of their oscillations. The excited ions are either pushed towards the plate by the tapered electrical field of two squized rods and overcome the potential barier and exit from the trap, or ions returned back to the confinment region of the MultiQ.  The after the plate quadrupole operates with the same RF ( same phase as ejection quadrupole minus excitation). It lenght is short to minimize a potential array for calcultaions. Prior to simulation of ion motion, the program needs to compute three potentials "RF" (RF-only motion in the quadrupole) DC (motion at the exit of the quadrupole near the sopping plate) and "AC" (ion excitation between two not squized sets of rods. Below are the instructions of how to set up and use the program


## **Usage Instructions**

fownload Processing (4.3) and the programs

### **Step 1: Create Geometry**
1. run the progrqm
2. Press **F1** (or **Alt+F1**) to open the dialog menu.
3. Select **"Create Geometry"** to define the electrode geometry.
   - Geometry details are in the `"Geometry"` folder, starting from **line 26**.
   - Default geometry uses the `define_RF(float x, float y, float z)` function.

---

### **Step 2: Calculate Potential**
1. Press **F1** again and select the **Calculate Potential** option.
2. Once calculations finish, save the potential file in the program folder.
   - Default filename: **`RF`** (referenced by the `DEFAULT_RFPOT_FILE` variable).

---

### **Step 3: Define and Save Additional Geometries**
1. To calculate a different geometry, edit **line 26** in the `"Geometry"` folder.
   - Example: Replace `define_RF(x, y, z)` with `define_DC(x, y, z)` for DC potentials.
2. Repeat **Steps 1 and 2** to save a DC potential file named **`DC`**.

---
### **Step 4: Define and Save Additional Geometries**
1. To calculate AC excitation geometry, edit **line 26** in the `"Geometry"` folder.
   - Example: Replace `define_DC(x, y, z)` with `define_AC(x, y, z)` for AC potentials.
2. Repeat **Steps 1 and 2** to save a DC potential file named **`DC`**.

---

### **Step 4: Load Precalculated Potentials**
1. Place the generated `RF` (~100MB) and `DC` (~100MB) files in the `Demiurge_MultiQ_486` folder.
2. Run the program and press **F2** to open the options menu.
3. Select **"Load Precalculated Potentials"** to load the potential arrays into memory.

---

### **Step 5: Run Simulations**
1. Use the following key commands to examine geometry, potential, or ion trajectories:
   - **1–6**: Set flags to visualize various simulation parameters (refer to the `"Draw"` folder).
   - **i**: Examine the trajectory of a single ion with **m/z = 500/1+**.
   - **m**: Examine the trajectory of a single ion with **m/z = 1500/3+**.
2. Press **F2** to open the options menu again.
3. Select simulation options such as:
   - Simulating ion motion for multiple ions.
   - Computing ion depletion effects.

---

## **Additional Notes**
- You are welcome to modify or adapt the program as needed.
- If you encounter issues or have suggestions, contributions are encouraged.
