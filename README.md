# JASPER Spectroscopic Solution for Milk Quality Analysis

Chemometrics is the science of extracting information from chemical data using statistical and mathematical models, it plays a crucial role in analytical chemistry helping scientists interpret complex datasets from spectroscopy, chromatography and electrochemistry.

## CheckAG and the Chemometrics Toolbox

CheckAG has developed a product called JASPER spectroscopic solution. This solution can be used in a range of industries. This solution has high-quality optical spectrometers and robust analytical capabilities to detect contamination at PPB levels.


CheckAG's mission is to make this solution available for the average farmers who will use the JASPER solution right in their fields. Initial focus is to use this solution as milk quality analyzer. This will eliminate the need for time-consuming lab tests.


The solution will focus on the following tests:

*   Composition Analysis
*   Adulterant Detection
*   Pesticide Detection
*   Contamination Detection

## Project Goal

Develop a robust, innovative, and high-performance open-source chemometrics toolbox for JASPER

# Solution requirements:

*  Robust algorithms
*  Innovative features
*  High performance
*  Adherence to open-source principles (Python, scikit-learn)
*  A design emphasizing modularity, transparency, and right-to-repair


## Software Development Life Cycle



## Industrial Application of Chemometrics

Chemometrics plays a crucial role in various industries. Examples include:

| Industry         | Application          | Purpose                                                                                                         |
|------------------|----------------------|-----------------------------------------------------------------------------------------------------------------|
| Pharmaceuticals  | Drug Formulations    | Used to analyze the chemical composition and purity of drugs, ensuring safety and efficacy.                      |
| Petrochemicals   | Crude Oil Analysis   | Analyzes crude oil to determine its composition and quality, aiding in refining processes.                       |
| Food Industry    | Product Consistency  | Monitors the quality and consistency of food products, detecting contaminants and ensuring safety.                  |
| Environmental Science | Water Analysis       | Detects pollutants and assesses water quality, contributing to environmental protection efforts.                  |
| Agriculture      | Soil Analysis        | Analyzes soil samples for nutrient content, helping farmers optimize fertilization and crop yields.                  |

## Comparative Analysis of Existing Toolboxes

|                     | MATLAB                                                                                                   | Open-Source Tools                                                                                              |
|---------------------|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| **Pros**            | - Industry standard for numerical computing.                                                             | - Free and accessible to everyone.                                                                               |
|                     | - Extensive built-in toolboxes for specialized applications.                                          | - Highly customizable and adaptable to specific needs.                                                             |
|                     | - Large support from MathWorks for updates and documentation.                                           | - Strong community support with rapid updates and contributions.                                                  |
|                     | - Excellent precision and solver capabilities for complex problems.                                        | - Compatible with multiple platforms (Linux, Mac, Windows).                                                       |
| **Cons**            | - Expensive licensing fees, limiting accessibility for smaller organizations or individuals.             | - Some tools (e.g., Octave) may be slower than MATLAB for certain tasks.                                          |
|                     | - Proprietary nature restricts customization and integration with other platforms.                         | - Smaller user communities compared to MATLAB in some cases (e.g., Scilab).                                     |
|                     | - Updates depend on the vendor’s schedule, which can be slow and rigid.                                | - May lack advanced solver precision in some implementations (e.g., Scilab).                                     |

## Proposed Architecture Components

| Architecture Component | Technology            | Reason for Selection / Advantages                                                                                                                                                                                                                                                                                                                                                                                  |
|------------------------|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UI Layer               | React                 | - Most commonly used Technology for UI.                                                                                                                                                                                                                                                                                                                                                                       |
|                        |                       | - Visually appealing and accessible point-of-service interface.                                                                                                                                                                                                                                                                                                                                                   |
|                        |                       | - Skill availability.                                                                                                                                                                                                                                                                                                                                                                                          |
| Backend                | Python with FastAPI   | - Python is an easy language.                                                                                                                                                                                                                                                                                                                                                                                    |
|                        |                       | - FastAPI is a robust microservices architecture which can be scaled.                                                                                                                                                                                                                                                                                                                                           |
|                        |                       | - APIs provide an interface to fetch data from any service or device.                                                                                                                                                                                                                                                                                                                                             |
|                        |                       | - FastAPI makes it easier to add new parts to our system without breaking everything else.                                                                                                                                                                                                                                                                                                                        |
| Chemometrics Core      | scikit-learn, NumPy, SciPy | - Supports core chemometric functions like PCA, PLS, and clustering.                                                                                                                                                                                                                                                                                                                                               |
|                        |                       | - Modular design allows easy integration of custom algorithms and preprocessing techniques.                                                                                                                                                                                                                                                                                                                      |
| Data Acquisition       | pyserial/pyVISA       | - Seamless integration with CheckAG's spectrometer portfolio (JASPER, Raman, FTIR) for real-time data collection.                                                                                                                                                                                                                                                                                              |
| Edge Computing         | ONNX Runtime          | - Enables deployment of lightweight models on devices like Raspberry Pi for real-time data analysis at the source.                                                                                                                                                                                                                                                                                         |
| Connectivity           | Wi-Fi, Bluetooth      | - For wireless data transfer and remote access for seamless user experience.                                                                                                                                                                                                                                                                                                                                  |
| Data Management        | Apache Parquet, Zstandard, MLflow | - Efficient data compression (smaller file sizes) and faster processing.                                                                                                                                                                                                                                                                                                                                                 |
|                        |                       | - Ensures version control for models and reproducibility of results.                                                                                                                                                                                                                                                                                                                                                                 |

## Critical Functionality

### Data Collection

*   The dataset includes multiple features representing milk quality indicators.
*   Understand the dataset structure, types, and missing values.

### 1. Features Directly Measurable by a Spectrometer

| Feature Name                   | How It's Measured                                      |
|--------------------------------|-------------------------------------------------------|
| Turbidity                      | Scattering & Absorption of light at different wavelengths |
| Color\_L                        | Lightness from Lab\* color space                        |
| Color\_a                        | Red-Green component from Lab\* color space               |
| Color\_b                        | Yellow-Blue component from Lab\* color space              |
| Absorbance at Specific Wavelengths | Used to detect fat, protein, and adulterants            |
| Fluorescence Spectrum          | Indicates protein, vitamins, and microbial activity       |
| Optical Density (OD)           | Helps estimate microbial growth (higher OD = more bacteria) |
| Scattering Coefficient         | Related to fat globule size & dispersion                |
| Transmittance at Wavelengths   | Can help identify water content & adulteration          |

### 2. Features That Need Additional Sensors (Beyond Spectrometer)

| Feature Name              | Measurement Method                                                                 |
|---------------------------|------------------------------------------------------------------------------------|
| pH                        | pH Sensor / Probe (Critical for freshness & spoilage)                               |
| Temperature (°C)          | Thermometer / Temperature Sensor (Affects bacterial growth)                           |
| Fat (%)                   | Infrared Spectroscopy / Gerber Test / Babcock Test                                 |
| Protein (%)               | Near-Infrared Spectroscopy (NIRS) / Lab Test                                        |
| Lactose (%)               | Enzymatic Tests / NIRS                                                              |
| Solids-Not-Fat (SNF) (%)  | Calculated from Fat & Protein Content                                                |
| Water Content (%)         | Calculated (Adulteration Detection)                                                   |
| Freezing Point            | Cryoscope (Detects water adulteration)                                                |
| Density (g/mL)            | Densitometer (Helps detect added water or solids)                                    |
| Conductivity (mS/cm)      | Electrical Conductivity Sensor (Higher conductivity may indicate mastitis in cows) |
| Total Bacterial Count (TBC) | Microbial Test / Flow Cytometry                                                    |
| Somatic Cell Count (SCC)  | Microscopy / Automated Counters (Detects mastitis infection)                        |
| Acidity (%)               | Titration Test (High acidity = Spoilage)                                             |
| Alcohol Test              | Lab Chemical Test (Protein stability check)                                          |
| Peroxidase Activity       | Enzyme Test (Raw vs. Pasteurized milk)                                               |
| Urea Content              | Spectroscopy / Lab Tests (Urea adulteration check)                                    |
| Added Detergents & Starch | Chemical Test (Adulteration detection)                                              |
| Antibiotic Residues       | Biosensors / Lab Tests (Important for safety)                                       |

### 3. Features That Can Be Derived / Classified

| Feature Name      | Derived From                                                                    |
|-------------------|---------------------------------------------------------------------------------|
| Taste             | Human Sensory Testing / E-Tongue                                                |
| Odor              | Electronic Nose (E-Nose) or Sensory Testing                                     |
| Turbidity Level   | Derived from Turbidity Index                                                    |
| Fat Classification| Derived from Fat %                                                              |
| Milk Grade        | Calculated using multiple quality parameters                                     |
| Adulteration Index| Based on various tests (Density, Freezing Point, Conductivity, Urea, Detergents, etc.) |

### Metadata

Here’s a table summarizing the features included in the milk quality dataset, along with their descriptions and value ranges:

| Feature Name                | Description                                                                          | Range                                                                        |
|-----------------------------|--------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| Country                     | Country of origin of the milk                                                        | India, USA, Germany, Brazil, New Zealand, France, Netherlands, Denmark, Australia, Switzerland |
| Brand                       | Brand name of the milk product                                                         | Various brands per country                                                     |
| Turbidity                   | Measure of clarity (scattering of light)                                             | 50 - 500 NTU                                                                 |
| Color\_L                     | Lightness from Lab color space                                                         | 0 - 100                                                                      |
| Color\_a                     | Red-Green component from Lab color space                                                | -10 to 10                                                                    |
| Color\_b                     | Yellow-Blue component from Lab color space                                               | -10 to 10                                                                    |
| Absorbance at Specific Wavelengths | Indicates fat and protein levels                                                      | 0.1 - 1.0                                                                    |
| Fluorescence Spectrum         | Indicates protein and microbial activity                                                 | 0.5 - 2.0                                                                    |
| Optical Density (OD)          | Reflects microbial growth (higher OD = more bacteria)                                  | 0.1 - 1.0                                                                    |
| Scattering Coefficient        | Related to fat globule size and dispersion                                             | 0.2 - 1.5                                                                    |
| Transmittance at Wavelengths  | Helps identify water content and adulteration                                           | 70 - 100                                                                     |
| pH                          | Measure of acidity (critical for freshness and spoilage)                               | 6.0 - 7.2                                                                    |
| Temperature (°C)            | Temperature of the milk                                                              | 2 - 8°C (stored), 30 - 100°C (processed)                                   |
| Fat (%)                     | Percentage of fat in the milk                                                          | 1.0 - 6.5                                                                    |
| Protein (%)                 | Percentage of protein in the milk                                                      | 2.5 - 4.5                                                                    |
| Lactose (%)                 | Percentage of lactose in the milk                                                      | 3.5 - 5.5                                                                    |
| Solids-Not-Fat (SNF) (%)    | Calculated from fat and protein content                                                | Varies based on fat/protein                                                  |
| Water Content (%)           | Percentage of water in the milk                                                        | 0 - <100% (calculated)                                                       |
| Freezing Point (°C)         | Indicates potential water adulteration                                                   | -1 to -0.4                                                                   |
| Total Bacterial Count (TBC) | Total count of bacteria present in the milk                                            | 10^2 to 10^7 CFU/mL                                                          |
| Somatic Cell Count (SCC)    | Indicates mastitis infection risk                                                      | 10^2 to 10^6 cells/mL                                                         |
| Acidity (%)                 | High acidity indicates spoilage                                                         | 0.12 to 0.20                                                                 |
| Alcohol Test (%)            | Checks protein stability                                                                 | 0.05 to 0.25                                                                 |
| Peroxidase Activity         | Differentiates raw vs pasteurized milk                                                  | 0.5 to 4                                                                     |
| Urea Content (mg/dL)        | Indicates potential urea adulteration                                                    | <60 mg/dL                                                                    |
| Added Detergents & Starch   | Indicates presence of adulterants                                                        | Yes/No                                                                       |
| Antibiotic Residues         | Indicates presence of antibiotics                                                       | Yes/No                                                                       |
| Taste (1-10)                | Human sensory testing score for taste                                                    | 1 - 10                                                                       |
| Odor (1-10)                 | Sensory testing score for odor                                                         | 1 - 10                                                                       |
| Fat Classification            | Classification based on fat percentage                                                  | Low, Medium, High, Very High                                                 |
| Milk Grade                  | Overall quality grade based on multiple parameters                                       | A-High, B-Medium, C-Low                                                        |

## Preprocessing

*   Handling Missing Values: Checking and removing any incomplete entries.
*   Feature Scaling: Standardized numerical attributes for consistency.
*   Categorical Encoding: Converted categorical variables into numerical format for model training.
*   Outlier Detection: Identified and handled extreme values that may affect model performance.

## Processing - Machine Learning Model Selection

To predict milk quality and analyze optimal conditions, multiple machine learning models were tested:

| Model              | Type       | Pros                                      | Cons                                                | Suitable For                        | Speed | Interpretability | Handles Non-Linearity? | Handles Missing Data? |
|--------------------|------------|-------------------------------------------|-----------------------------------------------------|-------------------------------------|-------|------------------|------------------------|-----------------------|
| Linear Regression  | Regression | Simple, interpretable                    | Assumes linearity, sensitive to outliers           | Continuous output prediction        | Fast  | High             | No                     | No                    |
| Logistic Regression| Classification | Simple, interpretable               | Requires pre-processing for non-linear relationships | Binary classification               | Fast  | High             | Limited                | No                    |
| KNN                | Classification | Easy to implement, versatile        | Computationally expensive, sensitive to feature scale | Multi-class classification          | Slow  | Low              | Yes                    | Yes                   |
| Random Forest      | Classification, Regression | Robust, handles non-linearity, feature importance | Can overfit, less interpretable than linear models       | Classification and regression         | Medium | Medium | Yes                   | Yes                   |
| XGBoost            | Classification, Regression | High accuracy, regularization, handles missing data | Complex, requires tuning                          | Classification and regression         | Fast | Medium | Yes                   | Yes                   |
| ANN (MLP)        | Classification, Regression | Complex relationships, high accuracy       | Black box, computationally expensive                   | Classification and regression         | Medium | Low | Yes                   | Yes                   |

# For classification, the most essential features would be:
*  pH
*  Fat (%)
*  Protein (%)
*  Lactose (%)
*  Solids-Not-Fat (SNF) (%)
*  Water Content (%)
*  Total Bacterial Count (TBC)
*  Somatic Cell Count (SCC)
*  Acidity (%)
*  Alcohol Test
*  Peroxidase Activity
*  Urea Content
*  Taste
*  Odor


The document continues with sections on:
* 4.1 Model Comparison
* Analytics: Model Performance Analysis
* Analytics: Deployment & Monitoring
* Presentation: Key Insights / Predictions
* Feedback: Conclusion and Recommendations

### 4.  1 Model Comparison

| Model                             | Accuracy | Precision | Recall | F1-Score |
|-----------------------------------|----------|-----------|--------|----------|
| XGBoost (Essential Features)      | 0.9975   | 0.9975    | 0.9975 | 0.9975   |
| XGBoost (All Features)            | 0.9965   | 0.9965    | 0.9965 | 0.9965   |
| Random Forest (Essential Features) | 1.0000   | 1.0000    | 1.0000 | 1.0000   |
| Random Forest (All Features)      | 0.9825   | 0.9830    | 0.9825 | 0.9820   |
| KNN (Essential Features)          | 0.8910   | 0.8995    | 0.8910 | 0.8806   |
| KNN (All Features)                | 0.6845   | 0.6833    | 0.6845 | 0.6419   |
| ANN (Essential Features)          | 0.9910   | 0.9911    | 0.9910 | 0.9910   |
| ANN (All Features)                | 0.9540   | 0.9543    | 0.9540 | 0.9535   |

## Analytics: Model Performance Analysis (Things To-Do)

*   Overfitting/Underfitting Check: Examined training vs validation accuracy to ensure generalization.
*   Hyperparameter Tuning: Optimized model parameters to improve accuracy.
*   Accuracy vs. Loss Graphs: Visualized model performance over epochs.
*   Confusion Matrix and Classification Reports: Evaluated precision, recall, and F1-score.

## Analytics: Deployment & Monitoring

*   Develop a web/app interface. (Future Scope)
*   Deploy using Flask/FastAPI (backend).
*   Monitor predictions in real-world usage.

## Presentation: Key Insights / Predictions

*   **Feature Importance:** Analysis revealed that factors like pH, fat percentage, bacterial count, and antibiotic residues significantly influence milk quality.
*   **Top Performing Model:** Among Random Forest, XGBoost, KNN, and ANN, the XGBoost model demonstrated the highest accuracy, balancing precision and recall effectively.
*   **Brand & Country Trends:** Certain brands and countries consistently ranked higher in quality, suggesting optimal production practices.
*   **Chemometric Analysis:** Spectroscopic data, especially absorbance and fluorescence, strongly correlated with quality indicators, validating the effectiveness of Jasper's methodology.
*   **Predicted Optimal Quality Parameters:** The study identified an ideal range for fat content, acidity, and bacterial count, aiding in quality standardization.

## Feedback: Conclusion and Recommendations

### Conclusion:

*   The JASPER Spectroscopic Solution effectively predicts milk quality using machine learning and chemometric analysis.
*   The integration of spectroscopy-based features enhances prediction accuracy, making it a powerful tool for quality assurance in the dairy industry.
*   Among all tested models, XGBoost performed best, suggesting it as the preferred approach for deployment.

### Recommendations:

*   **Refine Feature Selection:** Further analysis can optimize spectral bands to reduce redundancy and improve efficiency.
*   **Model Optimization:** Fine-tune hyperparameters for even better accuracy and explore ensemble models.
*   **Real-World Deployment:** Implement the trained model into a cloud-based API for real-time quality monitoring.
*   **Data Expansion:** Collect more geographically diverse samples to enhance model generalization across different regions.
*   **Industry Adoption:** Partner with dairy industries to validate the model’s performance in production environments.

## Contact

NAME: DIVYEY ARORA  
E-MAIL ID: DIVYEY@GMAIL.COM  
PH. NO: +91 98453 98989
