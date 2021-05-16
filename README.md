# Project Description

For my Apprentice Capstone in the Deloitte Machine Learning Guild, I was tasked with developing and deploying a deep learning model to solve a problem relevant to my life. During the pandemic, I picked up the hobby of brewing Kombucha at home. Relying on online forums and blogs to learn the basics, I quickly identified a problem in the Kombucha community - the problem of mold growing on Kombucha SCOBYs. A symbiotic cultre of bacteria and yeast (SCOBY) is the fermenting agent of the brew, and as it is reused over time it requires optimally clean environments in order to avoid contamination.

While mold is not common in brews, there is cause for continual concern due to the fact that SCOBYs grow yeast clumps, bubbles, and all end up looking unique - sometimes very odd. Due to this continual concern across the community, online forums become flooded with posts about mold concerns, and the actual knowledge transfer is muddied.

To combat this problem, I trained a Convolutional Neural Network (CNN) to detect the presence of mold in photos of Kombucha brew. Since there is no existing kombucha-image dataset, I had to manually collect images from blogs and forums that I deemed credible. I made sure no photo had text, whether website logos, links, or the target labels themselves. Given my cleaned dataset of 241 photos (63 of the target class, "Mold"), I began by building a baseline model using a pretrained model, ResNet18, which comes equipped with dense feature representations that can be leveraged to build a quick classifier for my problem. To improve performance, I implemented transfer learning on the pretrained model by unfreezing the ResNet model, and retraining the model so that the weights of the ResNet model can be updated and tailored to the dataset and target feature at hand. In doing so, I implemented a discriminative learning rate to focus the updates on the later layers, while avoiding large edits to the early layers responsible for the basic feature representations.

Given my small dataset, I paid particular attention to the convergence of the validation loss out of a fear of overfitting. I succeeded in doing so, and attribute much of that success to the variety of generalization techniques that I implemented, such as progressize resizing and other batch transformations to augment the images.

My final model achieved strong performance, and I am confident that the deployment of this model to a public website can help mitigate the Kombucha mold problem. Regarding performance, the metric I focussed most on was recall, as I want to avoid classifying a brew as not moldy, when it is in fact moldly and dangerous to consume. My final CNN model delivered a recall of 85.7% and an overall accuracy of 88.9% on the validation set, and the validation loss decreased consistently across epochs, indicating that my model is well-generalized.

I developed the CNN model in Python using the fast.ai library, which is built on top of PyTorch and enables one to quickly spin-up a state-of-the-art deep learning model. The fast.ai training materials were my first introduction to the world of Deep Learning, and I would highly recommend any beginners to check out the free, online courses (https://course.fast.ai/). 

Additionally, fast.ai models can easily be deployed to a website using Render, which is connected to this GitHub Repo and deploys the site based only on the contents of this repo. I have left some of the initial links to helpful resources for both fast.ai and Render deployment.

# Starter for deploying [fast.ai](https://www.fast.ai) models on [Render](https://render.com)

This repo can be used as a starting point to deploy [fast.ai](https://github.com/fastai/fastai) models on Render.

The guide for production deployment to Render is at https://course.fast.ai/deployment_render.html.

Please use [Render's fast.ai forum thread](https://forums.fast.ai/t/deployment-platform-render/33953) for questions and support.
