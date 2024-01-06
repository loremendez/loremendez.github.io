---
layout: page
title: The Gene Thicket
description: TUM Master's Thesis
img: assets/img/gene_thicket.png
importance: 2
category: machine learning
related_publications:
---


### <a href="https://loremendez.github.io/assets/pdf/Inference_of_Gene_Regulatory_Networks.pdf">PDF</a>  and <a href="https://github.com/loremendez/The-Gene-Thicket">CODE</a>

The gene thicket is my Master's thesis project. The gene thicket is a deep learning-based model, which goal is to build gene regulatory networks that are capable to predict future gene expressions.

### What is so amazing about gene regulatory networks?

Gene Regulatory Networks are graphs that describe the regulatory process of a system. Their nodes are genes and their edges represent the regulatory relationship between two genes. The edges have a direction (which gene regulates which other gene), a sign (activation or repression) and a weight (strength of the relationship). If we understand how a system works, then we can develop better products to help people, animals and every other living organism.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/grn_overview.png" title="grn overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The inference of gene regulatory networks (GRNs) has been an area of research for more than twenty years! GRNs are an amazing challenge in Computational Biology since they relate to many different things, such as perturbations, trajectory inference, RNA velocity and much more! We can also be creative and incorporate different types of data.

### The gene thicket

The gene thicket is a GRN inference method that predicts the future of each cell incorporating scATAC-seq data as prior, temporal data, a CNN architecture that predicts using only the past, and modified filters of attention to include the signs and magnitude of how the transcription factors affect the target genes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gene_thicket_architecture.png" title="gene thicket" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The motivation to build the gene thicket is to have a method that considers non-linear relationships between target genes and transcription factors, such as <a href="https://github.com/aertslab/pySCENIC">SCENIC</a>, but that also considers time series data. This is because the change in expression of transcription factors has an impact in the change of expression of target genes, which is observed when the expression profiles are sorted through time.


An advantage of having a time series approach is that we can make forecasts about the expression values of target genes using the previous expression values of transcription factors. Then, we could compute displacements and simulate trajectories, in a similar way that <a href="https://github.com/morris-lab/CellOracle ">CellOracle</a> does.
The idea of using deep learning comes from the fact that neural networks are universal non-linear approximators. By using temporal convolutional neural networks with attention, we ensure the scalability and interpretability.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gene_thicket_interpretability.png" title="interpretability" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gene_thicket_causal_validation.png" title="causal" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/gene_thicket_signs.png" title="signs" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Besides the use of scATAC-seq data, the gene thicket has the advantage of interpretability by using attention scores, the causal validation by using temporal data and knowing the relation of the influence between the transcription factors and the target genes by using signs.
</div>

### The results

To evaluate the quality of any reconstructed gene regulatory network is extremely challenging, because a ground truth does not exist. Moreover, there are diverse factors that have an impact on experimental data and could affect the interactions in a system. These factors can be primary cell types, environmental conditions, technology platforms and cell lines. To overcome these limitations, I evaluated the model’s performance using <a href="https://www.biorxiv.org/content/10.1101/642926v3">synthetic and curated data</a>, and investigated the model’s behavior in <a href="https://pubmed.ncbi.nlm.nih.gov/31160421/">real biological data that describes the Pancreatic endocrinogenesis</a>.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/results_synthetic_linear.png" title="results linear" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/results_curated_bifurcated.png" title="results bifurcation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The gene thicket is able to predict linear interactions between transcription factors and target genes from the synthetic data (left), however it struggles to predict bifurcations on curated data, since this behaviour was not considered when modelling.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/results_pancreas_good.png" title="results pancreas 1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/results_pancreas_not_so_good.png" title="results pancreas 2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    When using the pancreas data, the gene thicket is able to predict many trajectories (as we can see on the left side), however it struggles with some abrupt changes in transcription (on the right side).
</div>

### Conclusions and Outlook

* The gene thicket is a first step to iterative GRN-velocity approach.
* We can compute cell displacements using a GRN inference method.
* CNN’s are flexible when computing GRNs.
    * able to look at many points in the past
    * approximate non-linear trends
    * scalable
    * can be interpretable (even discover delays)
* We need to consider:
    * multiple trajectories
    * abrupt changes in gene expression trends
    * uncertainty
