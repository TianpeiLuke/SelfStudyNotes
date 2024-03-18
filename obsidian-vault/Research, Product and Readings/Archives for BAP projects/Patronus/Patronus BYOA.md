---
tags:
  - project
  - reference
  - wiki
  - customer_service_contact
aliases:
  - 1001cspatronus02
date of note: 2024-02-27
name: "Patronus: real time contact streaming"
---

- [Patronus Shared Service internal wiki](https://w.amazon.com/bin/view/Perfect_Order_Experience_Tech/DSPE/Projects/PatronusSharedService/#HBuildYourOwnApplication28BYOA29)

>[!quote]
> ### Build Your Own Application (BYOA)
> 
> We will make Patronus an integrated, full-stack, self-service application, which will allow business users to quickly build their own NLP solutions for customer feedback learning tasks. The application will be equipped with data generation tools, automatic model training, an interactive model iteration interface, one-click model deployment handler, and a model performance and business metrics monitor dashboard. For business teams with limited tech science capabilities, this enhancement will make ML model development extremely easy and smooth. Users will be able to complete a whole procedure of ML solution development from data collection, data enrichment, model selection, initial model training, model fine-tuning, customized business rules composition, to product launch and business metrics collection at one-stop, with minimal requirement on ML background knowledge, engineering support, and downstream product maintenance. As users will be freed from all the verbose technical details, they will purely focus on their specific business demands and obtain a solution with unprecedented efficiency. This is expected to yield savings of 1 science HC per model.
> 
> #### Self Service Tool Integrated with Easy Data Access, Fast Data Labeling and AutoML [(POC Demo Video](https://broadcast.amazon.com/videos/677776))
> 
> 
> We will build self-service capabilities in Patronus to allow users to easily access customer feedback data, conduct data annotation, train ML models and deploy them. Patronus will automate all phases of the ML solution development process through intuitive UIs that will offer the following advanced features:
> 
> 1. **Easy data access** Users will be able to select attributes from all feedback data sources available in Patronus and apply basic filtering rules and keywords searches to extract subsets that best fit their business domain.
> 2. **Fast data annotation** Users will be able to manually label data similar to how they would do it on a spreadsheet. Label storing and version control will allow for repeatable access to the newly labeled data. In addition to data available in Patronus, users will be allowed to upload their own datasets for annotation.
> 3. **ML model training with ease** After sufficient labels have been applied, users will trigger automatic ML model training with a single click. Feature engineering and hyperparameter tuning will be handled in the backend so that an optimal model based on the existing labeled data will be returned. Model performance metrics like accuracy and F1 score will be shown in real-time throughout the training process to help users understand the training trends and decide if a further model tuning or re-training will be preferred.
> 4. **Fast iteration and feedback loop** Patronus will enable a feedback loop to enable users to quickly iterate the model for improved model performance. Active learning will be used to identify which data should be labelled to yield the highest performance gain, thereby reducing human labelling cost.
> 5. **One-click deployment** We will develop an easy deployment mechanism that will allow users to move newly developed models in Patronus to URES once they have attained acceptable performance standards. The deployed model will generate predictions for real-time customer feedback events.
> 6. **Orchestrate existing components for each functionality using multiple team’s products** This self-service tool will not be built from scratch, but leverage existing tools built by multiple teams. For example, data collection and feedback loop is set up by Patronus; back-end models is comprised of existing NLP solutions such as Text Summarization, DeepReader; model deployment is through URES, etc. This self-service tool assembles mature tools built from multiple teams, which invent and simplify the development process.
> 