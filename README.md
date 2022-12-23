# image2recipes
This project is an implementation of [Recipe1M+: A Dataset for Learning Cross-Modal Embeddings for Cooking Recipes and Food Images](http://pic2recipe.csail.mit.edu/tpami19.pdf) by Salvador et al which uses a cross-modal retrieval method to convert food image input into relevant textual food recipes or in turn convert food recipes into relevant food images. In this project we mainly focus on the image-to-recipe progress.

## Data preparation

- Download the Recipe1M [dataset](http://im2recipe.csail.mit.edu/dataset/download). The contents of the directory ```DATASET_PATH``` should be the following:

```
layer1.json
layer2.json
train/
val/
test/
```
- For the demo part, which using trained model to predict images to recipes, the relevant file ```recipes_with_nutritional_info.json```, ```non_vegetarian.json``` e.t.c. are also needed (can be find in ```nutritional_info.py```). The demo can be implemented without these files, but some slight changes are needed.
- In this project, we used a subset of Recipe1M. We provide the origin id file under the ```data\``` file folder. The subset can be cut by reducing the ids and implement the cutting program on images and two json files.
- Make splits and create vocabulary by running:

```
python preprocessing.py --root DATASET_PATH
```

## Training

- Launch training with:

```
python train.py --model_name model --root DATASET_PATH --save_dir YOURPATH/checkpoints
```
## Evaluation

- Extract features from the trained model for the test set samples of Recipe1M:

```
python test.py --model_name model --eval_split test --root DATASET_PATH --save_dir YOURPATH/checkpoints
```

