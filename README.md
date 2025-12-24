# EEG-Based Focal Epilepsy Screening Model  
Transforming EEG into Audio-Image Features with Vision Transformer (ViT)

## 👩‍🔬 Research Team
Ji-Eun Kwak, Na-Kyung Kim, Hyuk-Ju Kwon, Seung-Jin Yang, Saem Jeong

---

## 📌 Research Purpose
- **Clinical Challenge**: Most patients undergo EEG during the *interictal* (between seizures) state, where abnormal discharges are rare. Routine EEG detects interictal epileptiform discharges (IEDs) in only **29–55%** of cases.  
- **Goal**: Propose a novel approach that converts EEG signals into audio and image features, enabling automated classification of focal epilepsy beyond the limits of visual inspection.

---

## 📊 Dataset
- **Bern-Barcelona EEG Dataset**  
- **Samples**: 1500 (Focal: 750, Non-Focal: 750)  
- **Condition**: All recorded during *interictal* state  
- **Key Point**: According to Andrzejak et al. (2012), distinguishing focal vs. non-focal signals by visual inspection is *impossible*.  

---

## ⚙️ Preprocessing Pipeline
1. **Signal Reconstruction**  
   - Raw EEG → Resampled to 16,000 Hz → Converted to `.wav` audio  
   - Produces continuous waveform for visualization and listening  

2. **Length Normalization**  
   - Standardized to 3 seconds (48,000 samples)  
   - Zero-padding for short signals, random cropping for long signals  

3. **Multi-Channel Feature Extraction (4 channels)**  
   - **Mel-Spectrogram**  
   - **MFCC (Mel-Frequency Cepstral Coefficients)**  
   - **Spectral Contrast**  
   - **Zero Crossing Rate (ZCR)**  
   → Stacked into a normalized 4-channel image (224×224)

---

## 🧠 Model Architecture
| Model            | Characteristics | Role in Study |
|------------------|-----------------|---------------|
| Standard CNN     | Basic convolutional layers | Baseline performance check |
| ResNet18         | Residual connections, stable deep learning | Benchmark for image classification |
| EfficientNet-B0  | Balanced scaling of depth, width, resolution | Lightweight CNN comparison |
| ViT-Tiny         | Patch-based Transformer | Captures global rhythm imbalance in EEG |

---

## 🚀 Performance Evaluation
| Model        | Accuracy | Precision | Recall | F1-score |
|--------------|----------|-----------|--------|----------|
| CNN          | 0.5833   | 0.7551    | 0.2467 | 0.3479   |
| ResNet18     | 0.6067   | 0.5899    | 0.7000 | 0.6402   |
| EfficientNet | 0.6467   | 0.6467    | 0.6467 | 0.6467   |
| **ViT-Tiny** | **0.6887** | **0.6505** | **0.8067** | **0.7202** |

👉 Clinical importance emphasizes **Recall** and **F1-score**.  
👉 **ViT-Tiny achieved the best overall performance.**

---

## 🔍 Explainable AI (XAI) Analysis
- **Saliency Maps** show ViT focusing on **high-frequency spikes** in EEG spectrograms.  
- **Medical Validity**: Epileptic seizures are characterized by sudden high-frequency discharges.  
- **Conclusion**: The model learned clinically meaningful features without explicit supervision.

---

## 🏁 Conclusion & Future Work
- Proposed a novel **EEG-to-Audio-Image transformation** for epilepsy classification.  
- Demonstrated potential for **low-cost, non-invasive diagnostic support tools**.  
- **Future Directions**:  
  - Patient-specific personalized models (transfer learning)  
  - Larger datasets for generalization  
  - Clinical integration as a decision-support system  

---

## 📚 References
### EEG & Epilepsy
- Fisher, R. S., et al. (2014). *ILAE Official Report: A practical clinical definition of epilepsy.* Epilepsia, 55(4), 475–482.  
- Smith, S. J. (2005). *EEG in the diagnosis, classification, and management of epilepsy.* JNNP, 76(suppl 2).  
- Pillai, J., & Sperling, M. R. (2006). *Interictal EEG in epilepsy.* Epilepsy: The Intersection of Neurosciences, Biology, Mathematics, Engineering and Physics.  

### Dataset & Signal Processing
- Andrzejak, R. G., et al. (2012). *Indications of nonlinear deterministic structures in EEG time series.* Physical Review E, 64(6), 061907.  
- Subasi, A. (2007). *EEG signal classification using wavelet feature extraction and a mixture of expert model.* Expert Systems with Applications, 32(4), 1084–1093.  

### Clinical Importance
- Engel, J. Jr. (2001). *Mesial temporal lobe epilepsy: What have we learned?* The Neuroscientist, 7(4), 340–352.  
- Wiebe, S., et al. (2001). *A randomized, controlled trial of surgery for temporal-lobe epilepsy.* NEJM, 345(5), 311–318.  

### Deep Learning Models
- Dosovitskiy, A., et al. (2021). *An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale.* ICLR.  
- Tan, M., & Le, Q. (2019). *EfficientNet: Rethinking model scaling for convolutional neural networks.* ICML.  

### Explainable AI
- Selvaraju, R. R., et al. (2017). *Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization.* ICCV.  

---

## 💡 Value Proposition
- **Clinical Support**: Detect focal epilepsy during interictal state  
- **Cost Reduction**: Non-invasive, automated analysis  
- **Trustworthy AI**: Explainable results aligned with medical knowledge  
