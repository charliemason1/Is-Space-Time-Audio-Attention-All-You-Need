# Is-Space-Time-Audio-Attention-All-You-Need
This is a repository to implement a late fusion implementation of a TimeSformer and an AST, modulating each respective model's influence on the final output.

The abstract from the original paper which can be found below is as follows: 

Recent advancements in video understanding models have built upon the adap-
tation of the transformer architecture to specific modalities. However, current
spatial-temporal transformers lack input from other types of data like audio. On
the other hand, many models that fuse modalities have no built-in methods to
modulate the influence of each data type. The human brain is inherently biased
toward visual information. As a result, models seeking to mirror or improve on
human performance on video classification tasks should use all relevant infor-
mation types but avoid unneeded audio bias, for example, in the model’s final
output. This paper proposes a novel architecture to integrate multiple modality
specific transformers using late fusion. It allows the representation of each con-
tributing model to be changed by a hyperparameter. In the implementation, we
leverage the spatial-temporal processing from the TimeSformer and the audio
understanding from the Audio Spectrogram Transformer (AST). We remove the
fully-connected layers, free model weights, and concatenate their outputs in a late
fusion strategy, followed by fine-tuning with new fully connected layers. However,
when the features are concatenated, we apply a scalar to the audio data to mirror
the brain’s prioritization of visual over audio data. We utilize a subset of the
VGGSound dataset to validate our approach. This research has practical applica-
tions in video classification, video production, and content management

A diagram of the exact process can also be found here and in the paper: 
<img width="931" alt="figure1" src="https://github.com/charliemason1/Is-Space-Time-Audio-Attention-All-You-Need/assets/110631759/b9c175df-5a4c-482c-9582-4d5a5c1c2e2a">

# Additional Notes:

Those wishing to replicate the code should follow the instructions in the Google Collab file in the repository. Make sure when running any additional dataset that the required dimensions are met for the AST and the TimeSformer. Moreover, the data processing code may have to be modified to meet those requirements. The training procedure was 25 epochs using an Adams Optimizer and Cross Entropy Loss.

To find additional TimeSformer and AST models to try and adapt the results, see the following links: 
TimeSformer: https://github.com/facebookresearch/TimeSformer
AST: https://github.com/YuanGongND/ast

The models we used to fine-tune our fully connected layer is as follows: 
TimeSformer: https://www.dropbox.com/s/15bvqltl1j5vyp3/TimeSformer_divST_64x32_224_HowTo100M.pyth?dl=0
AST: https://www.dropbox.com/s/ca0b1v2nlxzyeb4/audioset_10_10_0.4593.pth?dl=1

# Our Models: 
We trained six models based on the different hyperparameters discussed in the paper. For more information view table 1 in the paper attached. Our models are labeled 'alpha_model_#.pyt
