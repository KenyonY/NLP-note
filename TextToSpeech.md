# Introduction

 The Tacotron 2 and WaveGlow models form a text-to-speech system that enables users to synthesize natural sounding speech from raw transcripts without any additional information such as patterns and/or rhythms of speech. 



# Tacotron2

​     The Tacotron 2 model is a recurrent sequence-to-sequence model with attention that predicts mel-spectrograms from text.  

<img src="https://github.com/NVIDIA/DeepLearningExamples/blob/master/PyTorch/SpeechSynthesis/Tacotron2/img/tacotron2_arch.png?raw=true" alt="architecture " style="zoom:65%;" />

<center>Model architecture</center>
​    The encoder (blue blocks in the figure below) transforms the whole text into a fixed-size hidden feature representation. This feature representation is then consumed by the autoregressive decoder (orange blocks) that produces one spectrogram frame at a time. In our implementation, the autoregressive WaveNet (green block) is replaced by the flow-based generative WaveGlow. 

 

# Waveglow

​    The WaveGlow model is a flow-based generative model that generates audio samples from Gaussian distribution using mel-spectrogram conditioning.  During training, the model learns to transform the dataset distribution into spherical Gaussian distribution through a series of flows.  

 

<img src="https://github.com/NVIDIA/DeepLearningExamples/blob/master/PyTorch/SpeechSynthesis/Tacotron2/img/waveglow_arch.png?raw=true" alt="architecture " style="zoom:65%;" />

<center>Model architecture</center>
​    流程的第一步包括可逆卷积，然后是用作仿射耦合层的改良WaveNet架构。在推理期间，网络被反转，并且从高斯分布生成音频样本。我们的实现在耦合层中使用512个残留通道。 
