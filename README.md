# A Cluster Analysis of Ground Reaction Forces

## Table of Contents

1. [Introduction](#introduction)
2. [Methods](#methods)
3. [Results](#results)
4. [Acknowledgements](#acknowledgements)
5. [References](#references)

## Introduction

Foot strike patterns, a fundamental aspect of running, play a role in determining injury risk, performance, and footwear design (Gruber et al., 2013; Hasegawa et al., 2007; Lieberman et al., 2010). Historically, runners have been classified into three foot strike categories: rearfoot strike (RFS), midfoot strike (MFS), and forefoot strike (FFS) from the foundational work of Cavanaugh & La Fortune (1980). More recently, kinematic methods have been used for such classification (Altman & Davis, 2012).  However, recent advances in machine learning (ML) suggest that a comprehensive, data-driven classification system could capture a continuous spectrum of foot strike behaviors, thereby offering deeper insight into biomechanical function during ground contact in stance which may have implications on mechanisms underlying injuries (Ferber et al., 2016; Halilaj et al., 2018; Leporace et al., 2025; Martin et al., 2022).

Ground reaction force (GRF) data, particularly focusing on its vertical and anterior-posterior components, provide quantitative information on the dynamic interaction between the foot and ground during running. GRFs illustrate key events during stance, such as the presence or absence of an impact transient, variations in loading rate, and the timing of peak force, which are influenced by the runner's foot strike pattern (Gruber et al., 2017). For example, runners categorized as rearfoot strikers typically exhibit a pronounced impact transient in vertical GRF early in stance while forefoot strikers present a much smoother force-time curve, having a delayed or even absent vertical impact peak during the first 25% of stance coupled with a reduced loading rate (Almeida et al., 2015; Lieberman et al., 2010). These observed differences suggest that GRF’s can serve as powerful and high-resolution indicators for identifying and categorizing foot strike patterns.

Recent studies have suggested that three categories of foot strike patterns may not adequately capture all salient features of GRFs (Stiffler-Joachim et al., 2019). Other GRF components such as AP forces (Boyer et al., 2014) and high-frequency characteristics of the GRF signal (Gruber et al., 2017) may also have implications on tissue loading that may go unappreciated when traditional labels are used to classify foot strike pattern (Malisoux et al., 2021). 

ML techniques and unsupervised clustering methodologies offer the potential for automated classification of these data, circumventing the necessity for predetermined labels (Ferber et al., 2016; Jauhiainen et al., 2020; Mahoney et al., 2024; Martin et al., 2022). By employing techniques to cluster GRF waveforms, researchers can uncover naturally occurring patterns, potentially identifying previously unrecognized subtypes of foot strike behavior. This innovative approach not only enables scalable and objective analysis across extensive datasets but is also particularly valuable in both research and practical application within sports and clinical research.

The primary aim of this study was to explore the use of ML techniques to identify latent biomechanical groupings in GRFs that extend beyond tradtional foot strike classifications. Using large-scale feature extraction, dimensionality-reduction, and unsuperived clustering methods, we sought to determine whether distinct data-driven categories of running mechanics emerge from GRFs alone and how these groupings relate to labels derived form conventional kinematic classificiton methods. Ultimately, this investigation seeks to refine the precision and applicability of foot strike analysis using GRF data through sophisticated, data-driven methods that enhance our understanding of running biomechanics and its implications for injury prevention and performance optimization.

## Methods

#### *Participants*

This was a sub-analysis of an ongoing prospective trial of NCAA Division III Cross-country athletes. Incoming athletes were invited to participate during their first season from 2016-2023. Exclusion criteria included lower extremity surgery (last 12 months), current injury, or any condition precluding participation in running. Each provided informed consent to participate using a protocol approved by the university institutional review board.

#### *Procedures*

Overground running trials were collected on a 19.8 m runway using a force plate mounted flush with the surface. Several warm-up trials were allowed at each runner’s self-reported training pace. Running speed was monitored using photoelectric timing gates with a 2 m span centered on the plate to ensure that each trial was collected within ±5% of the participant’s training pace. Five trials were collected for each limb. Successful trials had the foot entirely on the force plate, no plate “targeting” was observed, and had a speed within the desired range.

#### *Cluster Analysis*

Ground reaction forces (GRFs) from the left and right foot strikes were processed and analyzed seperatley. A Fourier filter was used to decompose the vertical (V) and anterior-posterior (AP) force signals into low- and high-frequency components using a 10 Hz cutoff. Features were extracted using the TSFRESH Python package. Zero variance features were removed, and remaining features were normalized. Principle Component Analysis (PCA) was then applied, retaining PCs that accounted for 90% of total variance. Finally, Hierarchical Agglomerative Clustering (HAC) was performed to partition the dataset into distinct groupings using Ward linkage and the Euclidean distance metric. The number of clusters to form was determined through visual inspection of the resulting dendrograms.

#### *Interpretation and Comparison of Clusters*

Running profiles were defined based on clusters formed through HAC, and their charecteristics were compared using spider charts of externally selected biomechanically relevant GRF features, standardized to the percentile of it's mean.

To assess whether these GRF-based groupings aligned with labels formed from kinematic methods, a confusion matrix compared cluster assignments with expert-defined foot strike labels from kinematic methods of classification.

## Results

A total of 1,979 non-zero-variance features were extracted from the right-foot GRF signals and 1,981 from the left-foot signals. For both sides, the first 52 principal components—capturing 90% of the total variance—were retained as inputs to the HAC algorithm. The resulting dendrograms, shown in Figure 1, indicate five distinct profiles for the right-foot GRF data and four for the left-foot GRF data.

<table align="center">
  <tr>
    <td align="center"><img src="plots/left_dend.png" width="1000px"><br><em>Left GRF Division</em></td>
    <td align="center"><img src="plots/right_dend.png" width="1000px"><br><em>Right GRF Division</em></td>
  </tr>
</table>

_**Figure 1**. Hierarchical clustering trees (dendogram) showing division of runners into distinct clusters from extracted left and right GRF featuers._

#### *Foot Strike Cluster Profiles*

Spider plots for the five right-foot strike clusters (Figure 2) visualize how each group differs across a set of externally selected, biomechanically meaningful GRF features associated with running-related injury risk. Each of the five clusters demonstrates a unique biomechanical running profile, indicating that the clusters formed caputer meaningful differences in how athletes load and interact with the ground during stance beyond the traditional RFS, MFS, and FFS categorizations.

<table align="center">
  <tr>
    <td align="center"><img src="plots/right_cluster_1_spider_plot.png" width="600px"><br><em>Cluster 1 Running Profile</em></td>
    <td align="center"><img src="plots/right_cluster_2_spider_plot.png" width="600px"><br><em>Cluster 2 Running Profile</em></td>
    <td align="center"><img src="plots/right_cluster_3_spider_plot.png" width="600px"><br><em>Cluster 3 Running Profile</em></td>
  </tr>
  <tr>
    <td align="center"><img src="plots/right_cluster_4_spider_plot.png" width="600px"><br><em>Cluster 4 Running Profile</em></td>
    <td align="center"><img src="plots/right_cluster_5_spider_plot.png" width="600px"><br><em>Cluster 5 Running Profile</em></td>
  </tr>
</table>

_**Figure 2**. Spider plots illustrating the biomechanical running profiles for the five right-foot strike clusters._

Spider plots for the four left-foot strike clusters (Figure 3) visualize how each group differs across a set of externally selected, biomechanically meaningful GRF features associated with running-related injury risk. Each of the four clusters demonstrates a unique biomechanical running profile, indicating that the clusters formed caputer meaningful differences in how athletes load and interact with the ground during stance beyond the traditional RFS, MFS, and FFS categorizations.

<table align="center">
  <tr>
    <td align="center"><img src="plots/left_cluster_1_spider_plot.png" width="600px"><br><em>Cluster 1 Running Profile</em></td>
    <td align="center"><img src="plots/left_cluster_2_spider_plot.png" width="600px"><br><em>Cluster 2 Running Profile</em></td>
    <td align="center"><img src="plots/left_cluster_3_spider_plot.png" width="600px"><br><em>Cluster 3 Running Profile</em></td>
  </tr>
  <tr>
    <td align="center"><img src="plots/left_cluster_4_spider_plot.png" width="600px"><br><em>Cluster 4 Running Profile</em></td>
  </tr>
</table>

_**Figure 3**. Spider plots illustrating the biomechanical running profiles for the five left-foot strike clusters._

#### *Relationship Between Data-Driven Clsuters and Kinematic Foot Stirek Pattern*

Confusion matrices comparing cluster assignments with the kinematic labels (RFS, MFS, FFS) for both the left and right foot strikes are provided in Figure 4, highlighting areas of agreement as well as divergence between force-based and kinematic categorizations.

<table align="center">
  <tr>
    <td align="center"><img src="plots/left_confusion_matrix.png" width="600px"><br><em>Left Foot Strike Comparison</em></td>
    <td align="center"><img src="plots/right_confusion_matrix.png" width="600px"><br><em>Right Foot Strike Comparison</em></td>
  </tr>
</table>

_**Figure 4**. Spider plots illustrating the biomechanical running profiles for the five left-foot strike clusters._

## Acknowledgements

I would like to thank **Dr. Song Chen**, **Dr. Thomas Kernozek**, **Dr. Nathan Vannetta**, and **Dr. Drew Rutherford** for the opportunity to contibribute to this project.

## References

1. Gruber, A. H., Umberger, B. R., Braun, B., & Hamill, J. (2013). Economy and rate of carbohydrate oxidation during running with rearfoot and forefoot strike patterns. Journal of Applied Physiology, 115(2), 194–201. https://doi.org/10.1152/japplphysiol.01437.2012.
2. Hasegawa, H., Yamauchi, T., & Kraemer, W. J. (2007). Foot strike patterns of runners at the 15-km point during an Elite-Level half marathon. The Journal of Strength and Conditioning Research, 21(3), 888. https://doi.org/10.1519/r-22096.1.
3. Lieberman, D. E., Venkadesan, M., Werbel, W. A., Daoud, A. I., D’Andrea, S., Davis, I. S., Mang’Eni, R. O., & Pitsiladis, Y. (2010). Foot strike patterns and collision forces in habitually barefoot versus shod runners. Nature, 463(7280), 531–535. https://doi.org/10.1038/nature08723.
4. Cavanagh, P. R., & Lafortune, M. A. (1980). Ground reaction forces in distance running. Journal of Biomechanics, 13(5), 397–406. https://doi.org/10.1016/0021-9290(80)90033-0.
5. Altman, A. R., & Davis, I. S. (2012). Barefoot running. Current Sports Medicine Reports, 11(5), 244–250. https://doi.org/10.1249/jsr.0b013e31826c9bb9.
6. Ferber, R., Osis, S. T., Hicks, J. L., & Delp, S. L. (2016). Gait biomechanics in the era of data science. Journal of Biomechanics, 49(16), 3759–3761. https://doi.org/10.1016/j.jbiomech.2016.10.033.
7. Halilaj, E., Rajagopal, A., Fiterau, M., Hicks, J. L., Hastie, T. J., & Delp, S. L. (2018). Machine learning in human movement biomechanics: Best practices, common pitfalls, and new opportunities. Journal of Biomechanics, 81, 1–11. https://doi.org/10.1016/j.jbiomech.2018.09.009.
8. Leporace, G., Guadagnin, E. C., Carpes, F. P., Gustafson, J., Gonzalez, F. F., Chahla, J., & Metsavaht, L. (2025). The search for the holy grail in running biomechanics: Is there an ideal movement profile for minimizing mechanical overload? Sports Health a Multidisciplinary Approach, 19417381251338267. https://doi.org/10.1177/19417381251338267.
9. Martin, J. A., Stiffler-Joachim, M. R., Wille, C. M., & Heiderscheit, B. C. (2022). A hierarchical clustering approach for examining potential risk factors for bone stress injury in runners. Journal of Biomechanics, 141, 111136. https://doi.org/10.1016/j.jbiomech.2022.111136.
10. Hamill, J., & Gruber, A. H. (2017). Is changing footstrike pattern beneficial to runners? Journal of Sport and Health Science/Journal of Sport and Health Science, 6(2), 146–153. https://doi.org/10.1016/j.jshs.2017.02.004.
11. Almeida, M. O., Davis, I. S., & Lopes, A. D. (2015). Biomechanical Differences of Foot-Strike Patterns during Running: A Systematic Review with meta-analysis. Journal of Orthopaedic and Sports Physical Therapy, 45(10), 738–755. https://doi.org/10.2519/jospt.2015.6019.
12. Stiffler-Joachim, M. R., Lukes, D. H., Kliethermes, S. A., & Heiderscheit, B. C. (2020). Lower Extremity Kinematic and Kinetic Asymmetries during Running. Medicine & Science in Sports & Exercise, 53(5), 945–950. https://doi.org/10.1249/mss.0000000000002558.
13. Boyer, S. L., Edmondson, D. R., Artis, A. B., & Fleming, D. (2013). Self-Directed Learning. Journal of Marketing Education, 36(1), 20–32. https://doi.org/10.1177/0273475313494010.
14. Malisoux, L., Delattre, N., Meyer, C., Gette, P., Urhausen, A., & Theisen, D. (2020). Effect of shoe cushioning on landing impact forces and spatiotemporal parameters during running: results from a randomized trial including 800+ recreational runners. European Journal of Sport Science, 21(7), 985–993. https://doi.org/10.1080/17461391.2020.1809713.
15. Jauhiainen, S., Pohl, A. J., Äyrämö, S., Kauppi, J., & Ferber, R. (2020). A hierarchical cluster analysis to determine whether injured runners exhibit similar kinematic gait patterns. Scandinavian Journal of Medicine and Science in Sports, 30(4), 732–740. https://doi.org/10.1111/sms.13624.
16. Mahoney, J. M., Rhudy, M. B., Outerleys, J., Davis, I. S., & Altman-Singles, A. R. (2024). Identification of footstrike pattern using accelerometry and machine learning. Journal of Biomechanics, 174, 112255. https://doi.org/10.1016/j.jbiomech.2024.112255.
