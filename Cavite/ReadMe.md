# RADAR: Regression-Based Agricultural Drought Analysis and Risk Prediction in Cavite Using Multi-Year NASA POWER Climatological Data, Random Forest, SHapley Additive exPlanations (SHAP), and Accumulated Local Effects (ALE)

🚧 **WORK IN PROGRESS:** *This research project and its accompanying codebase are currently under active development. Methodologies, data pipelines, and predictive models are subject to ongoing refinement and validation.*

*   **School:** Cavite Science Integrated School (RSHS)
*   **Category:** Mathematics and Computational Science  
*   **Level:** Senior High School (STEM)

## 👥 About the Researchers
This research proposal is being developed by:
*   **Elle Rheign Maxeen P. Padilla**
*   **Judiel Kyle I. Ladero**
*   **Bianca Rheizel T. Abelieto**

*The team operates under my technical guidance as their qualified scientist.* To ensure the students build a robust foundational skillset in computational science, **I, Jose Aries E. De Los Santos, provide hands-on mentorship in Python programming and applied machine learning**. This includes teaching the students how to code in Python, utilize standard libraries like Scikit-learn, and implement Explainable AI (XAI) tools.

Through live coding demonstrations, step-by-step guidance on running predictive models, and rigorous validation of their output code, I am equipping these students to address real-world agricultural problems through advanced computational methods—bridging the gap between data science and actionable local governance.

## 🌾 Project Overview
Agricultural resilience relies heavily on accurate, timely, and understandable climate forecasting. This project utilizes meteorological data (harvested via the NASA POWER API) to predict root-zone soil moisture depletion—a primary indicator of agricultural drought. 

Instead of relying on isolated municipal models, this study trains a **Unified Machine Learning Model (Random Forest)** across multiple municipalities. This approach allows the algorithm to learn macro-level climatological patterns (e.g., monsoon cycles, humidity thresholds, and solar radiation impacts) while maintaining the ability to output highly accurate, localized municipal predictions.

## 🗂️ Repository Structure
```text
├── Bacoor/                            # Municipal case study and local explainability (SHAP/ALE)
├── Silang/                            # Municipal case study and local explainability (SHAP/ALE)
├── archive/                           # Archived scripts and previous model iterations
├── agriML_Cavite.ipynb                # Main Jupyter Notebook for model training and XAI
├── cavite_weather_master.csv          # Raw NASA POWER climatological dataset
├── cavite_weather_master_reshaped.csv # Processed dataset formatted for Random Forest
├── nasa-power-parameters.csv          # Metadata and definitions for NASA POWER features
└── ReadMe.md                          # Project documentation and methodology

## 🚀 Getting Started
To replicate this environment and run the predictive models locally, ensure you have Python 3.8+ installed, then install the required dependencies:

```bash
git clone https://github.com/Ariestootl/machine_learning.git
cd machine_learning/Agriclimatology/Cavite
pip install -r requirements.txt
```
*(Core dependencies include: `scikit-learn`, `pandas`, `shap`, `PyALE`, `matplotlib`)*

## 📊 Data Dictionary (NASA POWER Climatology Features)
The predictive model utilizes the following meteorological and satellite-derived features to assess agricultural drought risk:

| Feature Code | Parameter Name | Description |
| :--- | :--- | :--- |
| **RH2M** | Near-Surface Relative Humidity | The ratio of actual water vapor to the saturation vapor pressure at 2 meters above the surface. |
| **T2M_MAX** | Maximum Temperature (2m) | The maximum dry bulb temperature at 2 meters above the surface. |
| **T2M_MIN** | Minimum Temperature (2m) | The minimum dry bulb temperature at 2 meters above the surface. |
| **ALLSKY_SFC_SW_DWN** | Downward Shortwave Radiation | The downwelling shortwave solar radiation at the surface under all sky conditions. |
| **PRECTOTCORR** | Bias-Corrected Precipitation | The bias-corrected average precipitation (rainfall). |
| **TS** | Earth Skin Temperature | The average land surface temperature. |
| **GWETROOT** | Root Zone Soil Saturation | The amount of water retained in the root zone (Primary Target Variable). |
| **EVLAND** | Land Surface Evaporation | The total evaporation from the land surface. |

## 📈 Methodology and Model Evaluation
To validate the Random Forest's predictive capability, the dataset undergoes temporal splitting to respect the time-series nature of climatological data (preventing data leakage from the future into the past). Model performance is rigorously quantified using metrics such as Mean Squared Error (MSE), Relative MSE, and R-squared to ensure high fidelity and mathematical rigor in predicting continuous soil moisture depletion.

## 🧠 Explainable AI (XAI): Moving Beyond the "Black Box"
A major limitation of modern machine learning is the "black box" problem—algorithms can make highly accurate predictions, but they cannot explain *why* they made them. In agriculture and public policy, trust is paramount. Local Government Units (LGUs) and farmers cannot risk resources on a prediction they do not understand.

To solve this, our methodology heavily integrates **Explainable Artificial Intelligence (XAI)**. XAI transforms our predictive model from a simple warning system into a diagnostic tool at three critical levels:

### 1. Global Explainability via SHAP (Provincial Climatology)
We utilize SHAP Beeswarm and Dependence plots to uncover the governing laws of the model across the entire province. XAI allows us to:
*   **Rank Climatological Drivers:** Mathematically prove which weather features have the strongest impact on soil moisture.
*   **Identify Tipping Points:** Discover non-linear thresholds, such as the exact humidity percentage where atmospheric moisture actively prevents soil evaporation.
*   **Validate Physics:** Ensure the model's logic aligns with actual hydrological laws and local seasonal cycles.

### 2. Feature Robustness via ALE (Handling Correlated Data)
Meteorological features (such as temperature and solar radiation) are often highly correlated. To ensure robust feature effect estimation without introducing bias from unlikely data combinations, we employ **Accumulated Local Effects (ALE)**. ALE isolates the main effects of individual features, providing a clearer, unbiased picture of how a specific climate variable independently influences drought conditions.

### 3. Local Explainability via SHAP (Municipal Case Studies)
Using SHAP Waterfall plots, XAI breaks down individual predictions for specific municipalities on a month-by-month basis. If the model predicts a severe drought risk for a specific town, XAI provides an exact "receipt" of that decision.
*   *Example:* Rather than simply stating, "Town A is at High Risk," XAI clarifies, "Town A is at High Risk primarily due to a 20% deficit in precipitation combined with abnormally high surface solar radiation, despite cooler-than-average temperatures."

## 🎯 Research Impact
By combining a robust predictive algorithm with the transparency of Explainable AI, this research provides agricultural stakeholders with an early-warning system that is not only mathematically sound but physically interpretable, actionable, and trustworthy.

## 📡 Data Source and Licensing
The climatological data utilized in this repository is harvested from the **NASA Prediction Of Worldwide Energy Resources (POWER)** project. 

*   **Source:** [NASA POWER Project](https://power.larc.nasa.gov/)
*   **Licensing:** NASA POWER datasets are open-access and freely available for public and academic use. 
*   **Attribution:** We acknowledge the NASA POWER team for providing the high-resolution meteorological parameters that serve as the foundational data for our agricultural drought risk predictions.

## 📝 How to Cite
If you utilize this codebase, methodology, or the unified predictive model in your own research or policy planning, please cite this repository:

**APA Format:**
> Padilla, E. R. M. P., Ladero, J. K. I., Abelieto, B. R. T., & De Los Santos, J. A. E. (2026). *RADAR: Regression-Based Agricultural Drought Analysis and Risk Prediction in Cavite*. GitHub. https://github.com/Ariestootl/machine_learning/tree/main/Agriclimatology/Cavite

**BibTeX:**
```bibtex
@software{padilla2026radar,
  author = {Padilla, Elle Rheign Maxeen P. and Ladero, Judiel Kyle I. and Abelieto, Bianca Rheizel T. and De Los Santos, Jose Aries E.},
  title = {RADAR: Regression-Based Agricultural Drought Analysis and Risk Prediction in Cavite},
  year = {2026},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{[https://github.com/Ariestootl/machine_learning/tree/main/Agriclimatology/Cavite](https://github.com/Ariestootl/machine_learning/tree/main/Agriclimatology/Cavite)}}
}