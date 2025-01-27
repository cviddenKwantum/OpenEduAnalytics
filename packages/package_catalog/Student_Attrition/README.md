(https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/)

# Student Attrition

The OEA Student Attrition Package provides a set of assets which support an education system in developing their own predictive model to address student retention. This package was developed in partnership between [Broward College](https://www.broward.edu/) and [Kwantum Analytics](https://www.kwantumedu.com/) using [Azure Machine Learning](https://azure.microsoft.com/en-us/products/machine-learning) and [Responsible AI](https://github.com/cviddenKwantum/ResponsibleAIAccelerator/tree/main) to identify key predictors of student attrition and provide data-driven, actionable strategies that will support students in achieving their academic goals. This package relies on three components:

1. Azure Machine Learning and the Responsible AI Accelerator
2. Azure Synapse Workspace
3. Power BI Insights

<ins>Use Case Documentation and Guidance:</ins> The OEA Student Attrition Package - [Use Case Documentation](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/OEA_Student_Attrition_Use_Case.docx/) provides guidance on the end-to-end process of developing a successful Student Attrition use case project, including how to engage stakeholders in the project, prior research on the use case problem domain and theory, how to map data sources to the theory of the problem, and how to implement Microsoft’s Principles of Responsible Data and AI in the process of predictive modelling. <em> It is highly recommended this document be reviewed by any education system considering using this package, and that the documentation be revised to the specific data and decisions for that system’s context.</em>

<ins>Technical Assets:</ins> Various assets are freely available in this package to help accelerate implementation of Student Attrition use cases. Assets include descriptions of data sources, notebooks for data processing, a pipeline for ML model building and deployment, and sample PowerBI dashboards. See descriptions of technical assets below.

<ins>Important Note:</ins> It is strongly recommended to education systems or institutions planning to use this package establish that they establish a process for obtaining student, family, guardian, teacher, faculty, and staff **consent for using this type of student data**. This consent should be part of the system or institution’s **broader data governance policy** that clearly specifies who can have access to what data, under what conditions, for what purposes, and for what length of time.

## Problem Statement

Broward College in Florida caters to a diverse student population of over 55,000 individuals, many of whom are first-generation college students or eligible for federal Pell Grants. The college takes pride in accepting every student and is committed to meeting their unique needs and challenges. Whether pursuing full-time degree programs or part-time certificates, each student comes with their own educational and career ambitions. To address the issue of student attrition, Broward College turned to data-driven solutions, aiming to decrease the rate at which students withdraw or leave before completing their course plans.

Broward College utilized Azure Machine Learning to identify five critical factors that predict student attrition: cumulative credit hours earned, cumulative GPA, high school degree and/or GED status, and course modality (in-person, blended, or online learning). Armed with these predictors, the college is now implementing data-driven student support strategies campus-wide and modifying course design, scheduling, and learning methods accordingly. The use of machine learning has significantly expedited data processing, enabling the team to swiftly respond to students' needs and isolate potential confounding variables, such as the impact of the pandemic on student retention.

With the actionable insights generated from machine learning, Broward College offers tailored and proactive interventions to support each student based on their specific requirements. For instance, through the "Take One More" campaign, students nearing the threshold of cumulative credit hours are encouraged to add another class, as this has been found to increase their chances of success. Broward College is committed to helping students complete their education successfully, using technology to predict and provide assistance, thus ensuring students' progress along their educational pathways.

## Package Impact

In general, this package can be used by system or institutional leaders, school, or department leaders, support staff, and educators to:
 - <em> accurately identify </em> which students are at risk
 - <em> quickly understand </em> what type of support resources or interventions might be most effective to support and retain students
 - <em> guide decision making </em> of school support staff by providing a real-time and detailed snapshot of student critical factors and enable actionable steps towards support

See below for examples of developed PowerBI dashboards (see also the [Power BI] folder).

## Package Setup Instructions

<ins><strong>Preparation:</ins></strong> This package currently leans on v0.8 of the OEA framework. Ensure you have proper [Azure subscription and credentials](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework) and setup of the [OEA framework](https://github.com/microsoft/OpenEduAnalytics/tree/main/framework#setup-of-framework-assets). This will include v0.8 of the [OEA python class](https://github.com/microsoft/OpenEduAnalytics/blob/main/framework/synapse/notebook/OEA_py.ipynb).

1. [Azure AI Machine Learning Studio](https://azure.microsoft.com/en-us/products/machine-learning): Run the [education_story model](https://github.com/cviddenKwantum/ResponsibleAIAccelerator/tree/main) in Azure AI Machine Learning Studio. For detailed steps on how to create an instance of the Azure AI Machine Learning Studio and stand up the model, see the [Responsible AI repository](https://github.com/cviddenKwantum/ResponsibleAIAccelerator/tree/main).
   ![](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/images/Azure_MachineLearning.png/)
2. Azure Synapse: Link the Azure AI Machine Learning resource to your Synapse environment through the Manage tab in your Synapse workspace. Ensure the resource is linked as well as the Azure Data Lake Storage that contains the data from Azure AI Machine Learning.
   ![](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/images/Azure_LinkedServices.png/)
   ![](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/images/Azure_LinkedStorage.png/)
3. Azure Synapse: Import the pipeline found in the pipeline folder within this package. By importing the .zip file, you will recieve all pipeline and notebook assets needed to consume the data. When importing the pipeline, connect it to the Azure Data Lake Storage you linked to the Azure AI Machine Learning Studio as well as to your OEA Azure Data Lake Storage previously created when standing up the OEA Framework.
   ![](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/images/Azure_PipelineParameters.png/)
4. Azure Synapse: Trigger the Student Attrition pipeline and verify the data was landed correctly into your OEA Azure Data Lake Storage under Stage 1 and Stage 2.

## Machine Learning Approach

View the [Responsible AI Accelerator documentation](https://github.com/cviddenKwantum/ResponsibleAIAccelerator/tree/main) to understand the key components of the Machine Learning Model and Approach used to support this package.

## Data Sources

This package relies on data sourced from School Information Systems. Once aggregated, this data can be fed through the Responsible AI Accelerator in Azure Machine Learning to provide key insights. See the complete data dictionaries outlining the necessary data in the [Data folder](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/data/) of the Student Attrition package.

It is critical that all end user identifiable information is pseudonymized to comply with GDPR and CCPA requirements (more details on the OEA pseudonymization process [here](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Predicting_Chronic_Absenteeism/data/README.md#pseudonymization-of-end-user-identifiable-information)).

## Package Components

This Predicting Student Attrition package was developed by [Kwantum Analytics](https://www.kwantumedu.com/) in partnership with [Broward College](https://broward.edu/). The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone, and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

Assets in the Student Attrition package include:

1. [Data](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/data/): For understanding the data relationships and standardized schema mappings used for certain groups of data.
2. [Documentation](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/):
     - [Use Case Documentation](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/docs/OEA_Student_Attrition_Use_Case.docx) developed in partnership with Broward College.
     - Resources and documentation for Machine Learning in Azure and Responsible AI Accelerator implementations.
3. [Notebooks](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/notebooks/): For cleaning, processing, and curating data within the data lake.
4. [Pipelines](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/pipeline/): For an overarching process used to support PowerBI dashboards.
5. [PowerBI](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Student_Attrition/powerbi/): For exploring, visualizing, and deriving insights from the data.

The Student Attrition package [welcome contributions.](https://github.com/microsoft/OpenEduAnalytics/blob/main/docs/license/CONTRIBUTING.md)

This package was developed by Kwantum Analytics in partnership with Broward College. The architecture and reference implementation for all modules is built on [Azure Synapse Analytics](https://azure.microsoft.com/en-us/services/synapse-analytics/) - with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) as the storage backbone,  and [Azure Active Directory](https://azure.microsoft.com/en-us/services/active-directory/) providing the role-based access control.

#### Additional Information

# Legal Notices

Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at <http://go.microsoft.com/fwlink/?LinkID=254653>.

Privacy information can be found at <https://privacy.microsoft.com/en-us/>

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
