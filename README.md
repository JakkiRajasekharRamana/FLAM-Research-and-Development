# FLAM Research

All these experiments were done in Google Colab w/ proper citations

##  How the Idea came into place
   When the dataset (`xy_data.csv`) was observed it looked random but looked like it was repeating the same pattern (the parabola- I mean expected for fxm's containing sin and cos ). 
<img width="845" height="553" alt="Relationship btw x   y" src="https://github.com/user-attachments/assets/d0ae9bbb-ccdd-492b-8312-5e2fbe6f3c82" />

While searching i was checking if there could be method to arrange data in a [timly order](https://stackoverflow.com/questions/994054/curve-fitting-unsorted-points-on-a-plane), to understand the relationshit between them.
When checking the equations provided, as theta lies from 0 to 50, during this time sin theta value is less and cos theta value will be greater. While keeping these in mind x and y can be re-written with domainant terms in x and y.

X now will be `X=t(cos(theta))+X`
Y now will be `Y=42+t(sin(theta))`
sin(0.3t) - ignored as t lies btw 6 to 60 and value is negligible here. When from t=7 to 59, the value will steadly increase as 0.3t increases, similar to how the x & y points provided in the csv file. If we add both x & y we will get an equation `t(sin(theta)+cos(theta))+X+42` and this can be used as a sorting key to find out t.

Keeping the above point in mind Data Preprcoessing is to be done for the CSV file given,
For each x and y point find the new sort key for each point and plot, the graph should be similar in theory, when comaired we get the image 
[Normal vs heurustic graph]
<img width="1550" height="592" alt="Dominant X Y" src="https://github.com/user-attachments/assets/be1581a0-6a5b-4461-aa70-a4d9e16dd033" />

As u can see the image there are not much similar changes to both the graphs, so what we though intially was correct.

   I introduced an `(x + y)` sorting strategy — a simple yet powerful heuristic that imposes a *pseudo-temporal sequence* on unordered points.

4. **Optimization Approach:**  
   Once sorted, the data is passed through **Differential Evolution (`scipy.optimize.differential_evolution`)**,  
   which optimizes model parameters to minimize reconstruction error.

5. **Visualization:**  
   The notebook compares raw vs. sorted vs. reconstructed data visually —  
   allowing intuitive understanding of how optimization recovers hidden trends.

---

## 🧠 Concept Summary
FLAM demonstrates how **evolutionary optimization** can serve as a **function approximator** —  
fitting models to unordered, nonlinear, and potentially incomplete datasets.

**Key ideas:**
- No gradient or predefined model required  
- Robust against noisy, chaotic data  
- Visual and interpretable  
- A stepping stone for hybrid physics-AI modeling

---

## 🔬 Implementation Overview

| Component | Description |
|------------|-------------|
| **Language** | Python (Jupyter Notebook) |
| **Notebook** | `FLAM_Research_v3.ipynb` |
| **Core Libraries** | NumPy, Pandas, SciPy, Matplotlib, TQDM |
| **Optimization Engine** | `scipy.optimize.differential_evolution` |
| **Input Data** | `xy_data.csv` (loaded from Google Drive) |
| **Output** | Optimized parameters + visualized approximations |

---

## 📈 What Makes It Unique
- Introduces **data ordering heuristics** to preprocess unordered points  
- Combines **metaheuristic optimization** with visual analysis  
- Completely **interpretable pipeline** — no hidden layers or weights  
- Serves as a foundation for **physics-informed or explainable AI** modeling

---

## 🚀 Potential Applications
- Reconstructing sensor or experimental trajectories  
- Reverse-engineering system dynamics  
- Estimating parameters in sustainability or control models  
- Curve fitting for chaotic or incomplete datasets  

---

## 🧩 Future Work
- Implement adaptive ordering heuristics  
- Extend to higher-dimensional datasets  
- Integrate symbolic regression for interpretable equations  
- Benchmark against GA, PSO, and gradient-based methods  

---

## 📁 Repository Structure

