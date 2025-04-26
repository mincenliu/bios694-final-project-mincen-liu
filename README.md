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
