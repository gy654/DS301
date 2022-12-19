# Neural Style Tranfer

_This is the class project in New York University **Advanced Topics in Data Science: Advanced Techniques in ML and Deep Learning** class during 2022 Fall. All rights reserved._

_We are grateful to Professor [Parijat Dube](https://scholar.google.com/citations?user=bOejjQUAAAAJ&hl=en)'s inspiration and suggestions._


## Description of the Project
The goal of this project is to transfer the artistic style and appearance of famous paintings to photographs taken near the NYU campus. The combination of the two will be a creative generation assimilating the artistic painting in texture while preserving the content of the original photograph. To maximize the quality and artistic style of the output image, we aim to compare the performance of neural networks using content extractors of different architectures such as Resnet, VGG19, and Alexnet. Moreover, several experiments will be conducted to examine the features of the model design and the impact of the hyperparameters on the performance of the model. The final goal is to create a model that can generate artistic images with the best quality and artistic style.

**Experiments that were conducted in this project:**

VGG19 as content and style extractor
- Aggregate (_take means/aggregated mean_) the content features from the layers that were passed into the content extractor while aggregating the style features from all the layers
1. Experiment 1: Aggregate the content features from all the model's convolutional layers while aggregating the style features from all the model's convolutional layers
2. Experiment 2: Aggregate the content features from part of the model's convolutional layers while aggregating the style features from part of the model's convolutional layers
3. Experiment 3: Not aggregate the content features from all the model's convolutional layers but select the content features from the model's last second convolutional layer while aggregating the style features from all the model's convolutional layers
4. Experiment 4: Aggregate the content features from all the model's max pooling layers while aggregating the style features from all the model's max pooling layers

Alexnet as content and style extractor
- Aggregate (take means) the content features from the layers that were passed into the content extractor while aggregating the style features from all the layers
1. Experiment 1: Aggregate the content features from all the model's convolutional layers while aggregating the style features from all the model's convolutional layers
2. Experiment 2: Aggregate the content features from part of the model's convolutional layers while aggregating the style features from part of the model's convolutional layers
3. Experiment 3: Not aggregate the content features from all the model's convolutional layers but select the content features from the model's last second convolutional layer while aggregating the style features from all the model's convolutional layers
4. Experiment 4: Aggregate the content features from all the model's max pooling layers while aggregating the style features from all the model's max pooling layers

Resnet as content and style extractor
1. Experiment 1: Not aggregate the content features from all the model's convolutional layers but select the content features from the model's last second convolutional layer while aggregating the style features from all the model's convolutional layers

Each experiment was conducted for 50000 epochs and the output images were print and saved every 1000 epochs. For additional details, please refer to the folowing sections.

Reference: Original Paper can be looked at: [A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576) by Leon A. Gatys, Alexander S. Ecker, and Matthias Bethge, 2015. The implementation of the code is based on the [Ayush Exel's GitHub repository](https://github.com/AyushExel/Neural-Style-Transfer).


## Description of the Repository and Code Structure

The repository contains the following files:

- `README.md`: This file, which contains the description of the project, the description of the repository, and the instructions to execute the code.
- `images`: This folder contains the images that were used in the project. These images are the content images.
- `style`: This folder contains the images that were used in the project. These images are the style images.
- `output`: This folder contains the output images that were generated by the model.
- `code`: This folder contains the code that was used in the project. It is basically the implementation of the neural style transfer algorithm, and different experiments were conducted by changing the hyperparameters in the code.
- `code/experiment_for_ConvLayers.ipynb`: This file contains the code for the experiments that were conducted using the VGG19 model's and the Alexnet model's convolutional layers as the content and style extractor.
- `code/experiment_for_MaxPoolingLayers.ipynb`: This file contains the code for the experiments that were conducted using the VGG19 model's and the Alexnet model's max pooling layer as the content and style extractor.
- `code/experiment_for_Resnet.ipynb`: This file contains the code for the experiments that were conducted using the Resnet model's last second convolutional layer as the content and style extractor.


## Example Commands to Execute the Code
Since the code is written in  jupyter notebook, the code can be executed by running the jupyter notebook.

In order to do different experiments, the hyperparameters in the code need to be changed. The hyperparameters that can be changed are the following:
- layerALL = True: If this is set to True, the content features will be extracted from all the layers that were passed into the content extractor. If this is set to False, the content features will be extracted from the last second layer that was passed into the content extractor. (If False, additional changes can be made in the main function in order to use different layers as the content extractor.)
- aggregate = True: If this is set to True, the content features will be aggregated by taking the mean of the content features from all the layers that were passed into the content extractor. If this is set to False, the content features will not be aggregated.d

_Note: If one wants to use the model's max pooling layer as the content extractor, please just use the `code/experiment_for_MaxPoolingLayers.ipynb` with the same hyperparameters setup described above._


## Results (including charts/tables) and Your Observations
All the results will be saved and can be looked at the `output` folder. Here the best results are shown:

Style 1 on NYU Stern School of Business

![alt text](https://github.com/gy654/DS301/blob/main/output/aggFalselayerTrue_BestStyle1.png)

Style 6 on NYU Stern School of Business

![alt text](https://github.com/gy654/DS301/blob/main/output/aggFalselayerTrue_BestStyle6.png)

## Preliminary Conclusion
We visually provides some insights on how users can obtain desired output images that assimilates the artistic painting in texture while preserving the content of the original photograph by customizing feature extractors in multiple ways. (feature extractors can be tailored to achieve different artistic effects) 

- Extractor architecture makes a difference
- Using more number of layers during extraction add richer style information to the output
- Using conv layers add richer style information to the output compared with using maxpool layers
- Whether or not aggregating the content loss of multiple layers makes no significant difference
- Training for too many epochs will eventually distort and ruin the output images


## Collaborators
Contributor to this project: Grace Yang (gy654@nyu.edu), Stephen Zhang (stephen.zhang@nyu.edu)
