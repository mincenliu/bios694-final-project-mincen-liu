# BIOS 694 Final Project: Knowledge Distillation in Practice
 
This project explores **knowledge distillation (KD)**—a model compression technique that transfers knowledge from a high-capacity teacher model to a smaller student model—using the MNIST handwritten digit classification dataset. All models and experiments were implemented in **R** using the `{torch}`, `{torchvision}`, and `{luz}` packages.

> **Author**: Mincen Liu  
> **Institution**: McGill University  
> **Date**: April 2025  

---

## 📂 Repository Structure

├── model/                                          # Saved .pt models  
│   ├── mnist-cnn-teacher.pt                            # Teacher model (T = 3)  
│   ├── mnist-student-kd-{α}.pt                         # Student models trained with KD (α = 0, 0.3, 0.7, 1)  
│   ├── mnist-cnn-studentT.pt                           # Models trained without KD to illustrate temperature scaling (T = 1, 3, 10)  
├── output/                                         # Rendered PDF reports  
│   ├── KD/                                             # KD experiment reports  
│   ├── softmax/                                        # Temperature scaling report and plot  
├── BIOS694_Final_Project_Teacher_Model.Rmd         # Source code for training the teacher model  
├── BIOS694_Final_Project_KD_{α}.Rmd                # Source code for training the student models with KD (α = 0, 0.3, 0.7, 1)  
├── BIOS694_Final_Project_Student_Model_noKD.Rmd    # Source code for training models to illustrate temperature scaling (without KD)  
├── BIOS694_Final_Project_Softmax_Plot.Rmd          # Source code for plotting the softmax distribution under different temperatures  

*Note:* The MNIST dataset will be automatically downloaded by the scripts when running the RMarkdown files.

---

## 📌 Project Objectives

- Summarize and reproduce the results of Hinton et al. (2015) using MNIST.
- Investigate how softmax temperature scaling affects output distributions.
- Train student models with various α values in the KD loss:
  
  `L = α · L_CE + (1 − α) · L_KL`

- Evaluate the trade-off between learning from hard targets (true labels) and soft targets (teacher output probabilities).

---

## 🧠 Models

- **TeacherNet**: CNN with ~1.63M parameters; trained with temperature ( T = 3 ).
- **StudentNet**: Compact CNN with ~102K parameters (6.3% of TeacherNet).

---

## 🔬 Experiments

- **KD with fixed temperature (T = 3)** and α ∈ {0, 0.3, 0.7, 1}.
- **Temperature scaling** on softmax output with T ∈ {1, 3, 10}.
- **Evaluation metric**: Test set accuracy.

### 📈 Results

| α value | Description                  | Test Accuracy (%) |
|--------:|------------------------------|-------------------|
| 0.0     | Only soft targets            | 98.10             |
| 0.3     | Small weight on hard targets | **98.34**         |
| 0.7     | Large weight on hard targets | 98.11             |
| 1.0     | Only hard targets (baseline) | 98.00             |
| —       | Teacher model                | 98.75             |

---

## 🚀 Getting Started

1. **Clone or download the repo**  
   git clone https://github.com/mincenliu/bios694-final-project-mincen-liu.git

2. **Open R and install dependencies**  
    install.packages("torch")
    install.packages("torchvision")
    install.packages("luz")
    install.packages("reshape2")
    install.packages("ggplot2")
    install.packages("dplyr")
    install.packages("tibble")
    install.packages("caret")
    install.packages("here")

3. **Run the scripts**  
    Open any of the .Rmd files to reproduce the KD experiments or plots.

---

## 📚 References

```
Hinton et al. (2015). Distilling the Knowledge in a Neural Network. arXiv:1503.02531
Menon et al. (2021). A Statistical Perspective on Distillation. ICML
```
---

## 🔧 Future Work

```
Compare R vs Python implementations of KD.

Extend to more complex datasets.

Explore feature-based or attention-based distillation techniques.
```