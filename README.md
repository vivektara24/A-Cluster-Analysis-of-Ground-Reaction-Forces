# ML-FSP

#### Introduction

This repository contains work perfomred from Spring 2024 to Fall 2025. The primary motivation of the work was to explore the use of ML techniques to identify features of ground reaction forces (GRFs) of 103 cross country athletes exerted on the ground while running at moderate pace to see if could be extracted from the dataset discrete biomechanical groupings.

The ground reaction forces (GRFs) of the subjects were recorded along three components of with respect to the ground: The Vertical (V), Anterior-Posterior (AP), and Mediolateral (ML) compnents.

It has been suggested that higher magnitude and rates of change of V impact forces transmitted to lower limbs during running may contriubte to running-related injuries. Adopting different foot-strike patterns has been shown to differentiate chareactersitics of these vertical impact forces [[1]](#ref1).

Historically, runners have been classified into three foot strike categories: rearfoot strike (RFS), midfoot strike (MFS), and forefoot strike (FFS) according to the location of the center of pressure (CoP) at the time of first contact between foot and ground[[2]](#ref2). More recently, kinematic methods have been used for such classification [[3]](#ref3). However, recent advances in machine learning (ML) suggest that a comprehensive, data-drivenm classification system could caputre a continuous spectrum of foot strike behaviors, thereby offering deeper insight into biomechanical function during contact with the ground contact in stance which may have implications of mechanisms underlying injuries [[4]](#ref4).

#### Methods

*Participants*

This was a sub-analysis of an ongoing prospective trial of NCAA Division III Cross-country athletes. Incoming athletes were invited to participate during their first season from 2016-2023. Exclusion criteria included lower extremity surgery (last 12 months), current injury, or any condition precluding participation in running. Each provided informed consent to participate using a protocol approved by the university institutional review board.

*Procedures*

Overground running trials were collected on a 19.8 m runway using a force plate mounted flush with the surface. Several warm-up trials were allowed at each runner’s self-reported training pace. Running speed was monitored using photoelectric timing gates with a 2 m span centered on the plate to ensure that each trial was collected within ±5% of the participant’s training pace. Five trials were collected for each limb. Successful trials had the foot entirely on the force plate, no plate “targeting” was observed, and had a speed within the desired range.


## References

1. <a id="ref1"></a> Almeida, M. O., Davis, I. S., & Lopes, A. D. (2015). Biomechanical Differences of Foot-Strike Patterns during Running: A Systematic Review with meta-analysis. Journal of Orthopaedic and Sports Physical Therapy, 45(10), 738–755. https://doi.org/10.2519/jospt.2015.6019.
