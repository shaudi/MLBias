# Bias throughout the Pipeline

In this section presents a high-level view of AI/ML bias, as might be encountered by a typical government practitioner. To this end, this section walks the reader through common sources of bias along the length of the machine learning pipeline, extended here to include composition of research and development and implementation teams before development even begins, and application of results to inform policies or programs at the tail end of the process. 


![image](https://user-images.githubusercontent.com/80533280/113006618-89764d00-9143-11eb-8081-29350ac93ca1.png)


Source of the above image: https://arxiv.org/pdf/1901.10002.pdf 


In this section, we walk through common sources of bias along the machine learning pipeline, to prepare users for a later discussions of how to assess and mitigate bias along the workflow. 

- [Institutional Knowledge and Configuration](#institutional-knowledge-and-configuration) 

https://static1.squarespace.com/static/5b5df2f5fcf7fd7290ff04a4/t/5b8d79a81ae6cf1d7dfb19a4/1535998377033/04+Artificial+Intelligence+Policy+-+A+Primer+and+Roadmap+%28Calo%29.pdf

-  [Vendor or software selection](#vendor-selection)

- Data Collection

- Data Preparation

- Model Selection/Development/Training

- Model Deployment

- Model Evaluation

- Model Post-processsing

- Application of Bias, Including Even Distribution of Benefits and Risks First, Quotation from paper to include: "**what constitutes best practice in minimizing discriminatory bias and by what mechanism (antidiscrimination laws, consumer protection, industry standards) does society incentivize development and adoption of best practice?62 And second, how do we ensure that the risks and benefits of artificial intelligence are evenly distributed across society? Each set of questions is already occupying considerable resources and attention, including within the industries that build AI into their products, and yet few would dispute we have a long way to go before resolving them.**." "https://static1.squarespace.com/static/5b5df2f5fcf7fd7290ff04a4/t/5b8d79a81ae6cf1d7dfb19a4/1535998377033/04+Artificial+Intelligence+Policy+-+A+Primer+and+Roadmap+%28Calo%29.pdf


### Institutional Knowledge and Configuration 

[As noted in Engstrom et al. (2020)](https://law.stanford.edu/wp-content/uploads/2020/02/ACUS-AI-Report.pdf), agencies lack protocols around ensuring diversity of AI/ML practitioners, and none of the largest federal agencies with active AI programs had any working protocols and processes to assess the potential impact of bias, as of 2020. The lack of practical tools and guidance to complement high-level recommendations like the [OMB](https://www.omb.gov) Guidance for Regulation of Artificial Intelligence Applications, which recommends agencies employ a tiered AI/ML risk management approach, suggests that agency workforces are not currently best configured to plan to navigate the bias landscape. Compounding this is lack of sufficiently diverse AI/ML, across demographic and other classficiations, which is troubling when studies suggest that the identity-based experiences of vulnerability resulting from diverse lived experiences have been associated [in recent research (McDonald and Pan, 2020)](https://dl.acm.org/doi/abs/10.1145/3415218) with complex thinking about AI, such as a heightened ability to reason about fairness across groups as well bias. 

### Vendor selection

A significant proportion of AI/ML progress in government is fueled by agency acquisitions of off-the-shelf software, and/or building of tools by outside vendors. Whether these software is trained and developed with data or even methods well-understood to the agency or the build and training process is less transparent, the vendor selection and software acquisition can be rife with sources of bias, leading to eventual unfairness. As recent work [from the RAND Institute](https://www.rand.org/content/dam/rand/pubs/perspectives/PEA800/PEA862-1/RAND_PEA862-1.pdf) suggests, language in vendor solicitation or criteria for selection could discourage diverse vendors, or unintentionally promote certain classes of applicants over others. The paper suggests assessment criteria should be in some fashion validated for equity, as it relates to both applications or respondents and solution proposals.  Another relevant source of bias could be selection of a vendor that is not equipped, or is not instructed by the proposal, to develop a bias assessment, monitoring, or mitigation. A third possible source of bias at this stage is incomplete or misguided articulation of agency goals for the potential acquisition, which could guide vendors to develop products that are developed for a different application entirely.





 1) increase racial diversity in AI designers, 2) implement AI impact assessment, 3) establish procedures for staff to contest automated decisions. Each proposal addresses a different stage in the lifecycle of AI used by federal agencies and helps align US policy with the Organization for Economic Co-operation and Development (OECD) Principles on Artificial Intelligence.


