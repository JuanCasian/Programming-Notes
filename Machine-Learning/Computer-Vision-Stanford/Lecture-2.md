# Lecture 2 | Image Classification

## Image Classification

- Assing fix semantic labels to images
- Images are only a grid of numbers

| 0   | 0   | 0   | 0   |
| --- | --- | --- | --- |
| 256 | 0   | 34  | 0   |
| 0   | 0   | 0   | 0   |

- RGB images are [N x N x 3] arrays

- Challenges:
  - View point
  - Illumination
  - deformation
  - occlusion
    - only part of the object is visible
  - Background clutter
    - object gets lost with the background
  - Intra class variation
    - The same type of objects vary a little bit between each other
      - Ex: Not all cats look the same

- Before engineers would try to make filters to find ways to detect objects, but know they took a data driven approach

### Data Driven Approach
1. Collect Data
2. Use ML to train the classifier
3. Evaluate the classifier in new images

- API gets divided into 2 parts:
	1. Training
	2. Predicting

### Nearest Neighbor
- Data Driven approach
- Trainning:
  - memorize all data
- Prediction:
  - Find the image which is the most similar to the input and use the same label
### Comparison
- How you compare each point against the other

![Comparisons](res/Lecture2-1.png)

- On L1 if you rotate the image the distance actually changes, while on L2 distance if you rotate the image the distance will still be the same.


### K-Nearest Neighbor
- Usually you use more than one neighbor because it will make your decision more accurate
  - This is called K-Nearest Neighbors algorithm
  - It will smooth out the decision boundaries
  - It will prevent that a outlier of a label could give a wrong guess

**Decision Boundaries**

![K-Nearest_Neighbor](res/Lecture2-2.png)

## Hyperparameters
- Choices about the algorithm that we set instead of making the algorithm learn them
  - K in k-nearest neighbor
  - The loss function

### How to set the hyperparameters
1. Divide your data into 3 sets
  - Training set ~80%
  - Validation set ~10%
  - Testing set ~10%
    - Don't touch until the end
2. **Cross Validation**: Split data into folds and try each fold as a validation and average the results
	- Useful for small datasets but not common in deep learning because trainning is so computational expensive
	- Gold Standardk

![CrossValidation](res/Lecture2-3.png)