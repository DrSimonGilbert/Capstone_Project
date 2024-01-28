# Datasheet Template

The dataset was provided as part of the Kaggle competition "SenNet + HOA - Hacking the Human Vasculature in 3D" which ran from November 2023 - February 2024.

The Common Fund’s Cellular Senescence Network (SenNet) Program works on the Vasculature Common Coordinate Framework (VCCF) using manually produced maps to trace vascular structures in Hierarchical Phase-Contrast Tomography (HiP-CT) scans of human organs. The scan images are provided by the Human Reference Atlas (HRA).

The dataset is a series of TIFF files that represent sequential slices from several human kidneys with the corresponding maps as a TIFF mask representing the areas of vasculature.

## Motivation

The SenNet researchers from University College London and Indiana University Bloomington provided the data. Currently the vascular maps are produced by manual tracing of vascular structes. This can take many months to complete for an organ. A typical 1000x1000 TIFF slice with 1500 slices in an organ would have 1.5 billion pixels to classify. A more rapid technique to build the annotation maps will impove the data available for research on disease, aging and pharmacology. 

The SenNet team reference the following sponsors: Kaggle Cifar ThermoFisher Scientific; Indiana University Bloomington; University College London; Royal Academy of Engineering; Chan Zuckerberg Initiative; Technpoint. 

 
## Composition

The images are Grayscale TIFF images of varying sizes. A typical kidney is around 1500 slices of 1000x1000 pixel 8 bit grayscale. The maps images are the same size and correspond to each slice with values of either 0 (black, no vasculature) or 255 (white, vasculature). 

3 kidneys are in the training dataset with corresponding labels. These are at different resolutions and segementation. There is no missing data. There is no confidential data and no identifiable medical data in the images. 


## Collection process

The Human Organ Atlas (https://human-organ-atlas.esrf.eu/help) obtained control organs from 2 bodies donate to the Laboratoie d'Anatomie des Alpes Francaises (LADAF) under appropriate ethical regulations and guidelines. See Methods in: Imaging intact human organs with local resolution of cellular structures using hierarchical phase-contrast tomography https://www.nature.com/articles/s41592-021-01317-x. Age, sex and medical summary of the donors is described in the paper's Methods section.

The exact timing of the dissections was not stated but the paper was published in November 2021 and the researches describe using Covid-19 precautions so the work would have been done in 2020 or 2021.

## Preprocessing/cleaning/labelling

For the Capstone Project I initially worked on a subset of the data, Kidney 1, due to CPU/GPU and storage restrictions on Kaggle. 
Sequential slices from a kidney were batched as 5 layer 'stacks'. These were divided into 100x100 pixel 'chunks'. There was no overlap between stacks and chunks to avoid data leakage when the chunks were later randomised into test and training data. The chunks were transformed to normalised tensors with a binary classification label representing the map value at the centrepoint of the middle layer of the chunk. 

For edges of the image or stack the outermost row, column or lowest/highet slice are used as padding.

 
## Uses

The main usage of this dataset is to identify areas of vasculature (blood vessels) in an organ. The map value data does not reveal anything else that might be used to train a model.
The images themselves could be used if further expert processing was used to map other structures, for example the collecting system of the kidney, but this would require manual tracing of the areas of interest by researchers.
The images could also be used for 3d reconstruction of an organ, for example in anatomy training or radiology training. 
There is no known information in the dataset that points to risk of bias, however any wider use of the model should always review whether methods are transferable across age, sex and ethnicity.  


## Distribution

The dataset was distributed under the Kaggle competition as cited:
@misc{blood-vessel-segmentation,
    author = {Yashvardhan Jain, Katy Borner, Claire Walsh, Nancy Ruschman, Peter D. Lee, Griffin M. Weber, Ryan Holbrook,  Addison Howard},
    title = {SenNet + HOA - Hacking the Human Vasculature in 3D},
    publisher = {Kaggle},
    year = {2023},
    url = {https://kaggle.com/competitions/blood-vessel-segmentation}
}


The competition dataset was made available under an Attribution 4.0 International (CC by 4.0) licences. https://creativecommons.org/licenses/by/4.0/ 

## Maintenance

The SenNet group maintains the dataset.
