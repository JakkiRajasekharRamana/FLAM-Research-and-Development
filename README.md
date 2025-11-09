# FLAM Research: [Colab Notebook Link](https://colab.research.google.com/drive/1BYSuhUHsP0tciXguSopeWNg-b9sUaiKk?usp=sharing)

All these experiments were done in Google Colab w/ proper citations

---
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

As u can see the image there are not much similar changes to both the graphs, so what we though intially was correct. Now we got the new points x' and y'. Its time to think for a possible solution.

---

Solution:


Intially i thought we can diffrenticate find critial points and find values, but looking further it wasnt possible due to sin & cos being in single exuations, using a gradient based optimizer would fail as the local minimum would stuck/converge in that local minima itself. So we should look at alternate ones. 

But the better strategy which i found is to use [gradient free, global optimization algorithm](https://medium.com/@reshma_shaji/differential-evolution-what-it-is-and-how-does-it-work-81d3415c2367). We selected Differential Evolution it also uses the heuristic approach designed to find the global optimum in non-linear, non-differentiable spaces which suits perfectly for the problem statement. Our model is non-linear which contains sin, cos,e terms, and our L1 distance objective function is non differentiable. It is designed as a global optimization method that effectively searches the entire parameter space defined by the bounds provided in the range 6 to 60. The module impoted here is `scipy.optimize.differential_evolution`.

---

# Results

The results come out as 
<img width="774" height="298" alt="image" src="https://github.com/user-attachments/assets/018ea161-b700-4e63-8972-349bca48840b" />


<img width="1200" height="800" alt="final_model_fit" src="https://github.com/user-attachments/assets/02a12ce3-2610-4f1f-93f1-e0559eab184d" />
---


**Optimal Parameters (theta, M, X): [0.826,0.0742,11.5793]**


**Final L1 Loss (MAE): 0.3022915049020612**

---

**[Colab Notebook Link](https://colab.research.google.com/drive/1BYSuhUHsP0tciXguSopeWNg-b9sUaiKk?usp=sharing)**
