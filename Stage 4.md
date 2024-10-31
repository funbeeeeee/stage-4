Author:Funbee(@phunbeee3@gmail.com)

**TASK 1**

**Machine Learning in Cancer Drug Discovery**

1. **Background**  
   The application of machine learning (ML) in cancer drug discovery has become an essential tool, proffering solutions to many challenges faced by the pharmaceutical industry. A significant study by Menden et al. (2013) demonstrated the effectiveness of ML in predicting the sensitivity of cancer cells to various drugs. Their research made use of genomic and chemical properties to build predictive models, and these factors were linked to how well different drugs worked on specific cancer types. By integrating ML into the drug development pipeline, researchers can expedite the discovery of new treatments and optimise clinical trial designs.  

2. **Methodology**  
   2.1 **Dataset Preparation**  
   The GDSC1 dataset was downloaded as an Excel file. The dataset was imported, curated, and cleaned, focusing on the columns: CELL\_LINE\_NAME, TCGA\_DESC, DRUG\_NAME, and LN\_IC50. The SK-MEL-2 cell line was selected, which contained 402 entries, ensuring a robust analysis.  
     
   2.2 **SMILES Generation**  
   For each selected drug, the SMILES representation was retrieved using PubChem. This process transformed the chemical names into a format suitable for molecular descriptor calculation.  
     
   2.3 **Molecular Descriptor Calculation and Model Training**  
   The cleaned dataset, now including drug names, SMILES, and LN\_IC50 values, was used to generate molecular descriptors. PyCaret was used to train the model. The Ridge Regression model was selected.  
     
   2.4 **Model Evaluation**  
   The model was evaluated on the test dataset using metrics such as Mean Absolute Error (MAE), Root Mean Square Error (RMSE), and R² score to assess its predictive accuracy.  

3. **Results and Interpretation**  
   3.1 **Model Performance**  
   This model demonstrated the best performance in terms of MSE and MAE, achieving a solid balance between accuracy and efficiency. The Ridge Regression model demonstrated the following predictive performance:  
   * Mean Squared Error (MSE): 7.6088  
   * R-squared (R²): 0.1266  
   * Mean Absolute Error (MAE): 2.1371

3.2 **Prediction and Scatter Plot**  
The optimised model was used to predict the IC50 values for the entire dataset. A scatter plot was generated comparing actual IC50 values against predicted values, illustrating the model's performance visually. The correlation coefficient calculated was 0.2803. The correlation coefficient indicates a weak positive correlation, suggesting that the relationship is not strong, indicating further analysis might be needed.

![image1](https://github.com/funbeeeeee/stage-4/blob/48c53a23e33817d7131034ee188bb33d911b3e1d/ICD50.png)

3.3 **Comparison with Target Paper**  
The model’s R² of 0.1266 indicates weak explanatory power, and the Menden et al. paper exhibited higher R² values. Menden’s models showed lower MSE values, reflecting reduced prediction errors. The MAE between the predicted and actual IC50 is 2.137, representing a notable difference. Menden et al.'s models exhibited smaller errors with RMSE values ranging from 0.83 to 0.89, and they also had a higher correlation coefficient of 0.85 for the majority of their cell lines.

**4.Conclusion**  
This study highlighted the potential of machine learning in cancer drug discovery, demonstrating its ability to predict drug efficacy based on molecular features. Although our model varied extensively from Menden’s et al. model, it still provided valuable insights.

**References**

Menden, M. P., Iorio, F., Garnett, M., McDermott, U., Benes, C. H., Ballester, P. J., & et al. (2013). Machine learning prediction of cancer cell sensitivity to drugs based on genomic and chemical properties. *PLoS ONE, 8*(4), e61318. [https://doi.org/10.1371/journal.pone.0061318](https://doi.org/10.1371/journal.pone.0061318)

 
**TASK 2**

**Final Report on Molecular Docking of HDAC Subtypes**

**1\. Background**

Histone deacetylases (HDACs) are a group of enzymes that play a critical role in regulating gene expression by removing acetyl groups from lysine residues located on the amino-terminal tails of histone proteins. This deacetylation process can lead to the repression of gene transcription and is associated with various types of cancer. HDAC inhibitors are natural or synthetic chemical compounds with broad cellular functions. Abnormal HDAC activity is linked to cancer progression; therefore, HDAC inhibitors represent a strategic approach in cancer therapy.

**2\. Methodology**

**2.1 Preparation of Protein Structures**

The 3D structures of the 11 HDAC subtypes were downloaded from the Protein Data Bank (PDB). Each structure was analysed and curated to ensure suitability for docking studies.

![image2](https://github.com/funbeeeeee/stage-4/blob/48c53a23e33817d7131034ee188bb33d911b3e1d/molecule.png)
Figure 1: Visualisation

**2.2 Curating Ligand Library**

A validated inhibitor library for each of the 11 HDAC subtypes was compiled based on literature evidence. In addition to these known inhibitors, 50 phytochemicals identified in previous research from *Artemisia annua* were included, resulting in a total of 61 inhibitors for docking analysis.

 **2.3 Molecular Docking**

Using the molecular docking pipeline developed in the previous stage, molecular docking was performed for each of the 61 compounds across the 11 HDAC proteins. PyMOL was used to remove water molecules, and hydrogen atoms were added to the structures. The 61 ligands underwent energy minimization and were converted to PDBQT format. Each docking experiment was conducted in triplicate, and a grid box was applied over the active site. Docking scores were recorded for each replicate, with mean values and standard deviations calculated for accuracy.

 **2.4 Results Analysis**

The docking scores were analysed and compared across the HDAC subtypes. Kaempferol demonstrated the highest binding affinity for the HDAC1 protein, with an average docking score of \-9.4, indicating strong binding affinity. This result was consistent across all replicates, supporting Kaempferol’s potential as a high-affinity HDAC1 inhibitor. A heatmap was generated to visualise the mean docking scores, facilitating the identification of the most promising inhibitors. Interaction profiles were compared with those reported in the target paper to assess the consistency of findings.

![image3](https://github.com/funbeeeeee/stage-4/blob/48c53a23e33817d7131034ee188bb33d911b3e1d/ligand.png)
Figure 2: Kaempferol Interactions
 
**3\. Results and Interpretation**

The docking analysis revealed varying binding affinities for the inhibitors across the HDAC subtypes. Mean docking scores indicated that certain compounds exhibited significantly stronger interactions with specific HDAC targets. A comparison with the findings of the target paper showed alignment in the identified inhibitors and their interaction profiles, reinforcing the validity of the docking approach. Kaempferol stood out with consistent, high-affinity binding to HDAC1.

Visualisations of the docking poses and interactions were generated, highlighting key binding interactions between the inhibitors and HDAC active sites. These images provided insights into the molecular basis of inhibitor specificity and binding efficiency.

![image4](https://github.com/funbeeeeee/stage-4/blob/48c53a23e33817d7131034ee188bb33d911b3e1d/heatmap.png)
Figure 3:Heatmap
 
**4\. Comparison**

This study identifies Kaempferol as a promising HDAC1 inhibitor with a high binding affinity of \-9.4, consistent across triplicate tests. In contrast, the target article utilised the AlphaFold protein model to improve the accuracy of inhibitor binding predictions for HDAC11, demonstrating a more specialised approach to targeting HDAC11 over other HDAC subtypes.

 **5\. Conclusion**

This study identified Kaempferol as a strong and selective HDAC1 inhibitor, consistently achieving high docking scores across triplicate tests. The results align with other research utilising AI models like AlphaFold for HDAC inhibitor design, emphasising Kaempferol’s potential in HDAC1-targeted cancer therapy. Future experimental validation will be essential to confirm its therapeutic efficacy.

**References**

Amo-Aparicio, J., & Penas, C. (2022). Beneficial and detrimental effects of cytokines after spinal cord injury. In *Cellular, Molecular, Physiological, and Behavioral Aspects of Spinal Cord Injury*. [https://doi.org/10.1016/B978-0-12-822427-4.00009-5](https://doi.org/10.1016/B978-0-12-822427-4.00009-5)

Baselious, F., Hilscher, S., Hagemann, S., Tripathee, S., Robaa, D., Barinka, C., Hüttelmaier, S., Schutkowski, M., & Sippl, W. (2024). Utilization of an optimized AlphaFold protein model for structure-based design of a selective HDAC11 inhibitor with anti-neuroblastoma activity. *Journal Name*, *Volume*(Issue), Article Number. [https://doi.org/10.1002/ardp.202400486](https://doi.org/10.1002/ardp.202400486)

Chen, H. P., Zhao, Y. T., & Zhao, T. C. (2015). Histone deacetylases and mechanisms of regulation of gene expression (Histone deacetylases in cancer). *Critical Reviews in Oncology/Hematology, 20*(1-2), 35–47. [https://doi.org/10.1615/critrevoncog.2015012997](https://doi.org/10.1615/critrevoncog.2015012997)

Dallakyan, S., & Olson, A. J. (2015). Small-molecule library screening by docking with PyRx. In *Chemical Biology* (pp. 243–250). Humana Press.
