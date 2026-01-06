# 🛒 User Behavior Analysis & A/A/B Testing: Font Impact Study

## 🎯 Project Overview
This project examines user behavior within a food product startup's mobile application. The goal was to understand how users move through the sales funnel and evaluate whether a controversial design change (switching the app's fonts) significantly impacted conversion rates using a rigorous **A/A/B testing** methodology.

## 📉 Conversion Funnel Modeling
By analyzing event logs, I reconstructed the user journey to identify where the "leaks" in the revenue pipe were occurring.



* **Critical Drop-off:** The transition from **Main Screen** to **Offers Screen** saw a **38% loss** in users. This is the primary area for future UX optimization.
* **Efficiency:** Once users reach the Cart, **94.7%** complete the purchase, indicating a very efficient checkout process.

## 🧪 A/A/B Test Methodology
To ensure the reliability of the results, the experiment was divided into three groups:
1.  **Group 246 & 247 (Control):** Used to validate that the split-testing mechanism was working correctly (A/A Test).
2.  **Group 248 (Treatment):** Featured the new font design.

### Statistical Rigor
I performed **16 statistical hypothesis tests** to compare proportions across all groups and events. To prevent the "look-elsewhere effect" and control the Type I error rate, I applied **Bonferroni correction** to the significance level ($\alpha$).



## 📊 Key Findings
| Test Type | Result | Interpretation |
| :--- | :--- | :--- |
| **A/A (246 vs 247)** | ✅ No Significant Difference | The groups are homogeneous; the test setup is reliable. |
| **A/B (Combined Control vs 248)** | ❌ No Significant Difference | The font change did not impact user conversion. |

**Statistical Significance:** All p-values were significantly higher than the adjusted threshold, meaning we fail to reject the null hypothesis.

## 💡 Strategic Recommendations
* **Do not implement based on conversion:** The data shows the new font is neutral. Unless there are branding or technical reasons, the change doesn't drive growth.
* **Prioritize the "Main → Offers" Gap:** Instead of cosmetic changes like fonts, the product team should investigate why 38% of users leave the app immediately after the home screen.
* **Funnel Optimization:** Focus on personalized offers or UI improvements in the initial discovery phase to increase the flow towards the cart.

## 🛠️ Tech Stack
* **Python:** Data processing and statistical engine.
* **Pandas:** For event sequence modeling and user segmentation.
* **Statsmodels:** Implementation of Z-tests for proportions.
* **Seaborn/Matplotlib:** Visualization of the conversion funnel and event distribution.

