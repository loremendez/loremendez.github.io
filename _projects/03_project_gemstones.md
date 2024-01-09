---
layout: page
title: classification of gemstones
description: cnn with explainability for fun
img: assets/img/gemstones/gemstones.png
importance: 3
category: machine learning
---

### <a href="https://github.com/loremendez/Gemstones">CODE</a>

For this project, I wanted to classify gemstones using deep convolutional neural networks and then use an explainability method to be able to identify which features influence the prediction the most.

I used the <a href="https://www.kaggle.com/lsind18/gemstones-images">gemstones dataset</a> from Daria Chemkaeva. It includes 2856 images belonging to 87 classes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gemstones/gemstones_dataset.png" title="gemstones dataset" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Since the shape of the gemstone is not really important, but the color and the patterns of the gem, I performed a data augmentation step.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gemstones/gemstones_augmented_data.png" title="gemstones data augmentation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Then I built a convolutional neural network with residual blocks and batch normalization. I trained the model for 137 epochs, due to the early stopping. The accuracy on the training set was around 80% and the accuracy on the validation around 70%.

And of course, when implementing the <a href="https://arxiv.org/abs/1810.03307">VarGrad (VG)</a> explainability method, we can see nothing in the score maps. This is only confirming what we already know, that the categorisation of gemstones is done through the color. And therefore, the performance may also not be so high, because we have gemstones with very similar colors and patterns.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gemstones/gemstones_scoremaps.png" title="gemstones scoremaps" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

However, if we use a different dataset, we may obtain better results. For example, for the classification of buildings according to their architectural style or more complex things, such as <a href="https://github.com/andresbecker/master_thesis/tree/main">predicting the transcription rates from multiplexed protein maps</a> .

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gemstones/architecture_score_map.png" title="architecture score map" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gemstones/architecture_foto.png" title="architecture image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Score map and original photo when classificating of buildings according to their architectural style, using the <a href="https://arxiv.org/abs/1810.03307">Architectural styles dataset</a>.
</div>

Thanks to Andres Becker for helping me to build this project!