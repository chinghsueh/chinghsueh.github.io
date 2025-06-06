# Kaggle Competition

## Paddy Doctor: Paddy Disease Classification

### course22 Notebooks

| **Notebook** | **Timm** | **epoch** | **Private Score** | **Public Score** |
|-----|-----|-----|-----|
| 8 | resnet26d | 3 | 0.874 | 0.882 |
| 9 | convnext_small_in22k  & TTA | 2 | 0.957 | 0.967 |

- Notebook 9 achieved a higher score with fewer epochs compared to notebook 8.
- The remote application closed unexpectedly while running notebook 10, so the results are unavailable for comparison. However, based on the results provided by Jeremy Howard in notebook 10 (with scores rounded to three decimal places in the table below), the `vit` models do not have a significant impact on the score. On the other hand, it is interesting to note that the score of notebook 9 (0.983, also achieved using `convnext_small` trained for 12 epochs with TTA) is slightly better than that of notebook 10.

| **Timm** | **Score** |
|-----|-----|
| `convnext_small` trained for 12 epochs, with TTA | 0.980 |
| `convnext_large` trained for 12 epochs, with TTA | 0.988 |
| ensemble in this no.10, with `vit` models not over-weighted | 0.988 |
| ensemble in this no.10, with `vit` models over-weighted | 0.988 |

### Optimizing course22 No.8

| **epoch** | **Timm** | **Private Score** | **Public Score** |
|-----|-----|-----|-----|
| 5 | convnext_small | 0.970 | 0.970 |
| 5 | convnext_small | 0.965 | 0.968 | 
| 5 | convnext_small & TTA | 0.965 | 0.968 | 
| 5 | convnext_small_in22k | 0.962 | 0.960 | 
| 5 | resnet26d | 0.957 | 0.967 |
| 3 | convnext_small | 0.960 | 0.958 |
| 3 | resnet26d | 0.874 | 0.882 |
| 3 | resnet26d | 0.878 | 0.879 |
| 3 | resnet50d | 0.789 | 0.769 |
| 3 | resnet18 | 0.685 | 0.682 |
| 7 | convnext_small | 0.635 | 0.583 |

- Optimizing notebook 8 can result in better performance than notebook 9.
- Overall, the model trained with `convnext_small` for 5 epochs yields a higher score compared to other TIMM models.
- `resnet50d` underperformed, likely due to its reliance on a larger dataset for optimal performance.
- More epochs don't necessarily mean a higher score.
- TTA has no impact on the model in this case.
- Unfortunately, the optimization of notebook 8 did not surpass the score of 0.98846 achieved by notebook 10.





## HackRush - DeepFake Detection

### Attempts

| **Notebook** | **epoch** | **Timm** | **Training Images** | **Resize** | **error_rate** | **Private Score** | **Public Score** |
|-----|-----|-----|-----|-----|-----|-----|-----|
| 8 | 5 | convnext_small | 500 AI, 500 Real | item: 125, batch: 100 | 0.310 | 0.492 | 0.487 |
| 8 | 5 | convnext_small | 500 AI, 500 Real | item: 400, batch: 128 | 0.340 | 0.485 | 0.506 |
| 8 | 5 | convnext_tiny | 500 AI, 500 Real | item: 400, batch: 128 | 0.265 | 0.492 | 0.493 |
| 8 | 5 | convnext_small | 2500 AI, 2500 Real | item: 125, batch: 100 | 0.207 | 0.485 | 0.487 |
| 8 | 5 | convnext_small | 2500 AI, 2500 Real | item: 400, batch: 128 | 0.132 | 0.491 | 0.489 |
| 8 | 5 | convnext_small & TTA | 2500 AI, 2500 Real | item: 400, batch: 128 | 0.132 | 0.491 | 0.489 |
| 8 | 5 | convnext_tiny | 2500 AI, 2500 Real | item: 400, batch: 128 | 0.138 | 0.479 | 0.491 |

- There are more than 60000 training images in the provided dataset. The `RuntimeError` occurs when training the model using all of the images, so only a portion of the dataset is used in this case.
- The model trained using `convnext_small` and resize to 400 / 128 achieves a lower error rate when the total number of training images is 5000, but it achieves a lower score compared to using only 1000 training images. (?)
- The first few attempts using the optimized notebook 8 achieved the same score because the results were not properly saved to the submission csv file.
- Notebook 9 and 10 should perform better but run them on the remote application is a nightmare, especially with a larger dataset. (!)

### Result-Based Assumptions

- Larger GPU is required to train all the images without `RuntimeError` occurs.
- Depending on the Timm module used to train the model, a larger portion of the training images does not necessarily result in a higher score.

### Proposed Solution

- Train the model using different Timm modules.
- Use larger portion of the dataset.
- Try different parameters for the resize operation.
- Adjust the training process according to notebook 9 (TTA) and notebook 10 (ViT).
