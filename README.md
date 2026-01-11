# Wi-Fi-assisted-UAV-based-CSI_Localization
A Wi-Fi–assisted UAV-based CSI localization framework for accurate node positioning in complex and dynamic environments.
A. Step-by-Step Architecture Description 
Step 1. CSI Phase Preprocessing

This module implements a three-step CSI phase preprocessing pipeline:
1. **Phase unwrapping** to remove 2π discontinuities
2. **Linear phase correction** to compensate hardware-induced phase distortion
3. **DWT-based denoising** using Daubechies-5 wavelet (2 levels)

Step 2.CSI Phase Preprocessing

This script preprocesses raw CSI phase data stored in CSV format.
Each phase column (phase_1 to phase_30) undergoes:
1. Phase unwrapping
2. Linear phase correction
3. DWT-based denoising (db5, level 2)
   
Step 3. Preprocessed CSI amplitude and phase are independently processed using a four-block 1D ResNet to extract modality-specific deep features. The resulting representations are concatenated and fed into a 1D Swin Transformer, which models long-range interdependencies and cross-modal correlations for robust feature embedding.

Step 4. A two-hidden-layer BPNN is employed for coordinate regression, where the number of neurons in each layer and the learning rate are automatically optimized using Quantum-behaved Particle Swarm Optimization (QPSO) to minimize validation MAE.
