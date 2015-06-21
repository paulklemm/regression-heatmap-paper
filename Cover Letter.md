This cover letter is written in Markdown

<!--TOC-->

Cover Letter
============

At first, we'd like to thank all reviewers for the detailed feedback on this paper. The work underwent substantial changes and enhancements. We extended the Regression Cube to display various descriptive metrics for regression models, empahsized how expert feedback influenced the design choices, revised all figures and included previously missing important related work.

This cover letter is divided into two parts. The first highlights major changes to the paper. The second part covers the reviewer feedback with our inline comments to the individual reviews, which are for the most parts pointers to the first section to reduce redundancy.

*All changes can be found on the running instance of the Cube under [regressioncube.herokuapp.com](regressioncube.herokuapp.com)*.
Code changes can be tracked in the GIT repositories [of the R back-end package](https://github.com/paulklemm/regression-cube-r-package/commits) and [the Javascript/HTML5/CSS front-end and Node back-end](https://github.com/paulklemm/regression-cube-prototype/commits).

Changes
=======

Regression Metrics
------------------

One large complaint was the focus on R² values only for representing linear regression models. Therefore, we reworked this to include a variety of different variables, which put emphasis on different aspects of the data.

* [Reviewer 1] We added a new select interface element for selecting the regression metric used to colorize the mosaic plot and regression cube. It contains the following new metrics:
  * Adjusted R²: This is basically the R² term, but with a penalty term, which leads to lower R² values, if a added dimension contains little entropy w.r.t. the target variable.
  * F-statistic: The f statistic determines how much improvement the independent variables will add to the model compared to them being not considered at all. The F-statisic is scaled between 0 and 1 based on the largest f-statistic in a cube slice.
    * **We did implement a visual comparison of f-statisic, but decided against it**. The resulting plot is misleading. f-statistic are based on their degrees of freedom, which are determined by the number of independent features (equal in the cube, which is good) and the number of elements (unequal with very high differences). The cube would visually compare values, which are inherently not comparable, as many features are sparse. We therefore decided to restrict f-statisic as contextual information for each model.
  * Akaike Information Criterion (AIC), which acts similar as the R² by preferring simpler models based on occams razor.
  * Adjusted R² and f-statistic are implemented for linear regression models, since they lack a counter part for logistic regression models. For those, the standard Nagelkerke R² values are used.
* [Reviewer 1] The context information for regression models was enhanced according to the suggestions made by the reviewers
  * A scatter plot shows the distribution of the residuals of the model.
  * All p-values for each dimension are shown.
  * The f-statistic is additionally represented as table, which covers its degrees of freedom.
  * The Akaike Information Criterion (AIC) as well as the adjusted R² can also be found in the context information.

The sections revised using this feedback are:

* *2.3 Regression Analysis* - explained the new metrics and their usage
* *4.3 Abstracting Regression Results using R²* is now renamed into  *4.3 Abstracting Regression Results* and covers the new metrics.
* *5.2 Regression Cube Visualization* contains *Selecting and Scaling the Descriptive Regression Metric*, a new paragraph explaining the selection and scaling of the regression metrics
* Paragraph *Mosaic Plot Slice Visualization* summarizes the features appearing as context information including the residual plot.

Related Work
------------

The reviewers suggested several works, which need to be discussed as part of the Section **Related Work**. Hence, we added:

* Z.Guo,M.O.Ward,andE.A.Rundensteiner.ModelSpaceVisualization for Multivariate Linear Trend Discovery. In Proc. of IEEE VAST, pages 75–82, 2009.
* T. Mühlbacher and H. Piringer. A Partition-based Framework for Build- ing and Validating Regression Models. IEEE Trans. on Visualization and Computer Graphics, 19(12):1962–1971, 2013.
* A. Maries, N. Mays, M. Hunt, K. F. Wong, W. Layton, R. Boudreau, C. Rosano, and G. E. Marai. GRACE: A Visual Comparison Framework for Integrated Spatial and Non-Spatial Geriatric Data. IEEE Trans. on Visualization and Computer Graphics, 19(12):2916–2925, 2013.
* M. Sedlmair, C. Heinzl, S. Bruckner, H. Piringer, and T. Mo ̈ller. Visual Parameter Space Analysis: A Conceptual Framework. IEEE Trans. on Visualization and Computer Graphics, 20(12):2161–2170, 2014.

As the **Related Work** section became too lengthy with these changes, we cut the description of the following papers:

* A. Rind, T. D. Wang, W. Aigner, S. Miksch, K. Wongsuphasawat, C. Plaisant, and B. Shneiderman. Interactive Information Visualization to Explore and Query Electronic Health Records. Foundations and Trends in Human-Computer Interaction, 5(3):207–298, 2013.
* T. Schreck and D. Keim. Visual Analysis of Social Media Data. Com- puter, 46(5):68–75, 2013.
* B. Shneiderman, C. Plaisant, and B. W. Hesse. Improving Healthcare With Interactive Visualization. Computer, 46(5):58–66, 2013.


User Interaction
----------------

* [Reviewer 1],[Reviewer 3] As suggested, we implemented a slider to adjust the transfer function of the selected metric. It is applied both on the 2D heatmap as well as the 3D cube. It can therefore be also used to filter for specific values, such as regression models with very high R².
  * The figures are updated to cover the new UI elements.
  * *5.2 Regression Cube Visualization* contains *Selecting and Scaling the Descriptive Regression Metric*, explaining the functionality of the slider

Support Design Decisions with Expert Feedback
---------------------------------------------

One main complaint was the lack of supporting design decisions using expert feedback ([Reviewer 4 - Primary],[Reviewer 2]). We revised Section *4 Regression Cube Analysis of Cohort Study Data* and Section *5 System Design* as well as the contributions with this feedback in mind. We focused on telling the story on how different elements of the project were derived from joint analysis sessions and which purpose they serve.

Details on the changes are as follows:

  * [Reviewer 2] Following Munzners "A Nested Model for Visualization Design and Validation" as suggested, we revised the contributions in the **Introduction**
  * *4 Regression Cube Analysis of Cohort Study Data*
    * Added new subsection *Iterative Design Based on Expert Feedback* to explain how expert feedback was incorporated in the design
    * Subsection *Abstracting Regression Results*: Explained how expert feedback is included in selecting the respective regression metrics
    * Paragraph *Hypothesis-Free and Hypothesis-Based Analysis*: Motivated the different approaches with examples from the epidemiological application domain
    * [Reviewer 2] Justified selection of colour and object size parameters for the visualization with expert feedback
  * *5 System Design*
    * Section starts with a motivation on suitability of web-based techniques for the epidemiological application domain
    * Added expert input in Subsection *System Paradigm and Components*
    * Created new paragraph Selecting and Scaling the Descriptive Regression Metric
    * Paragraph *3D Prism as Data Mini-Map* goes into details on early prototypes of the 3D prism and why these designs were discarded
    * [Reviewer 2] Justified selection of interaction techniques
    * [Reviewer 3] The paragraph **Cube Slice Selection** of Section **5.2 Regression Cube Visualization** was revised to be more precise. The area below the prism is in fact be used to identify the correct position of the current slice.

Additional Changes
------------------

  * [Reviewer 1] It was criticised, that it is not clear how the found models are investigated further. Therefore, we clarified this in the introduction of Section *4 Regression Cube Analysis of Cohort Study Data* as well as in the introduction of Section *5 System Design*
  * [Reviewer 1] Elaborate more on the limitation of having only three dynamic variables. We discussed this limitation in Section *8 Summary and Outlook* by suggesting 3D projections of hypercubes spanned by more than 3 dynamic regression variables.
  * [Reviewer 2] Security issues are now indicated at the beginning of Section **4 Regression Cube Analysis of Cohort Study Data** as well as Section **5 System Design** and discussed in Subsection **5.1 System Paradigm and Components**
  * [Reviewer 2] We revised a large number of long sentenced to either split them up or to simplify them.
  * [Reviewer 2] Citations are now treated as gramatically invisible
  * [Reviewer 3] Discussed limitations of CFS algorithm in Section **4.3 Target-Variable-Dependent Dimension Reduction** and how we tackle them in Section **4.4 Abstracting Regression Results**.
  * [Reviewer 3] We added a check box as part of the file-upload step, which allows to skip the CFS preprocessing step. It is noted in Section **5.1 System Paradigm and Components**
  * [Reviewer 3] Fixed errors in Figure 1
  * [Reviewer 3] Removed paragraph **Encoding via CSV Files**

# VAST'15 Reviews "Regression Cube Analysis of Cohort Study Data "

# Reviewer 4 - Primary

- Overall Rating: 4: Good contribution
- Topic Classification
- Type: System Type: Application
- Topic: Visual representation and interaction technique
- Topic: Data handling and knowledge representation
- Topic: Model visualization and optimization
- Best Paper Award: Maybe
- Contribution to the field of Visual Analytics: This is an application paper, and the main contribution is in its satisfaction of the requirements of domain expert analysts as they address real problems.
- Expertise: 3 (Knowledgeable)

### The Review
The strength of the submissions is that the application is an important one and the program actually works. It appears that it meets the requirements of the expert users.The weakness of the paper is that the text is dense and a challenge to read.
This submission is flagged as an application paper, and so it should show evidence of Impact in solving real world problems, Novelty in extending into an application area, Innovative reuse and adaptation of existing techniques or Insight into the experience design, engineering, evaluation and deployment.
In my estimation the case for accepting this paper is primarily in its potential for impact on a real-world application. It is also in a subject domain where there are not many VA applications, and it reuses and adapts existing techniques. This in my opinion makes a prima-facie case for acceptance. The argument for not accepting the paper would be that it fails in enough of these criteria that it would fall below threshold, or that it has technical flaws that are severe enough that its acceptance could cause others to make similar errors.While I am not an expert in epidemiological statistical analysis the compromises that are made appear to be reasonable. I see nothing in the paper that would give me a reason not to accept it.

*Main Recommendation: Acceptable for presentation
*Additional Recommendation about TVCG Publication: This paper is potentially acceptable to TVCG but authors may need more revision time (> 3 weeks).*

### The Summary Review

Reviewers agree that the paper addresses an important problem, and the high level of contact with experts makes this a good application paper. They are concerned in the general sense that linear regression modelling experts need to assess more criteria in order to select best models. There are a matrix of measures such as adjusted R square, F statistic, p-values etc. that are often used to understand a multiple regression. Other measures such as the Akaike Information Criterion can help analysts to compare models with different power e.g. number of variables. Other metrics such as the distribution of residuals can also be useful (and sometimes essential) to make decisions about models.

<i><font color='green'>

  * See [Regression Metrics] for detailed changes in the paper with this feedback in mind. To summarize:
    * The Regression Cube can now be displayed w.r.t. different descriptive metrics other than the R² (adjusted R², Akaikes Information Criterion)
    * Additonally, all suggested features are included into the context information attached to each regression model, including a resdiual scatter plot
    * The changes are made apparent in the paper in the respective sections (see [Regression Metrics])

</i></font>

Some of this might be dealt with by pointing out how user input was used to select the measures used, and to make it clear that the system is intended for expert users who have sufficient understanding of regression and how it should be interpreted that they are able to use the system wisely.

The paper has aspects of a design study and of a system paper. For a design study the contributions would need to be revised, or better supported by evidence in the methods and results. It would be good to know how the authors made the decision what to include in the system. Did the users consider these factors important, in which case they may be added later, or were they not of interest to them? This may explain some of the design decisions that are not obvious to readers.

<i><font color='green'>

  * See [Support Design Decisions with Expert Feedback] for details
    * The design decisions were integrated in Sections 4 and 5 to state how user feedback influences the final result.
    * now we focus more on telling the story behind the design, rather then just presenting the final product

</i></font>

It was suggested that the manuscript could be further strengthened by better structuring the domain requirements to include the web and security issues.

<i><font color='green'>

  * Advantages of the web-based approach regarding the epidemiological application domain is covered as part of [Support Design Decisions with Expert Feedback] by discussing it at the beginning of the *System Design* section
  * Security issues are now indicated at the beginning of Section **4 Regression Cube Analysis of Cohort Study Data** as well as Section **5 System Design** and discussed in Subsection **5.1 System Paradigm and Components**

</i></font>

A common concern was that relevant works in visual analytics area should be referenced. See individual reviews for specifics.

<i><font color='green'>

  * The related work was substantially revised with the reviewers feedback in min. For details, please see [Related Work].

</i></font>

Reviewer 1
----------

- Reviewer: secondary
- Overall Rating: 2.5
- Topic Classification
- Type: Application
- Best Paper Award: No
- Expertise: 4 (Expert)
Contribution to the field of Visual Analytics: The paper addresses an important problem – finding the best linear regression model to model a target variable using a set of potential variables. The authors calculate all possible combinations of models and present the results to the user with help of a heatmap - matrix/cube representation of Rsquared quality criterion. The approach has been defined and evaluated in close cooperation with medical experts. It helps them to choose suitable models from a large set of potential models. The problem tackled can be found across many application areas so the potential for such solutions is large. The paper is very well written and the authors have put a lot of effort into tackling this problem. The paper takes a simplified approach focusing only on Rsquared criterion, which enables them to use a “simple” heatmap for showing the results. The authors provide a tool that allows for creating varous variants of models and exploring the resulting Rsquared values for all combinations. This approach provides an overview of good/bad possible models using this criterion. I see several problems with this approach. Mainly, in reality, linear regression modelling experts need to assess much more criteria in order to select best models. Second, in case the focus is only on Rsquared, it is not clear to me how these particular visualizations bring value added beyond simple spotting of large Rsquare values.

With respect to related works, several important and very relevant works in visual analytics area have not been referred to.

### The Review

This paper addresses an important problem. Modelling and parameter setting (parameters in this case are the variables of the model) is a well-known problem in many application areas. So the potential of tools supporting modelling is large. Recently, a wealth of literature in visual analytics area has started to look at parameter steering and modelling and to provide tools for various selected problems. This paper focuses on linear regression model. The problem stems from medicine/health analysis of real large scale data. The paper is very well written, easily readable and well structured. Introduction motivates the work well and supports reader in wanting to read more. Related work covers many works from medical analysis and information visualization. This is a broad overview of literature. Nevertheless, I still miss several important works from visualization/visual analytics are that focus on modelling and visual parameter analysis (model variables can be seen as parameters). This is the core of the paper. An overview of visual parameter analysis is given in a recent Sedlmeier et al. paper. Especially, it would be needed to mention

- 1) Zhenyu Guo, Matthew O Ward, and Elke A Rundensteiner. Model space visualization for multivariate linear trend discovery. In Visual Analytics Science and Technology, 2009. VAST 2009. IEEE Symposium on, pages 75–82. IEEE, 2009.
- 2) Muhlbacher, Thomas, and Harald Piringer. "A partition-based framework for building and validating regression models." Visualization and Computer Graphics, IEEE Transactions on 19.12 (2013): 1962-1971.

<i><font color='green'>

  * The mentioned work is now integrated into the related work discussion.

</i></font>

Approach: The authors focus on linear regression models with one target variable (quantitative or discrete). The approach is restricted to 3 variables including the target. The authors calculate all possible models and support finding best models using only Rsquared measure. This is where my problem with the approach is. In reality, modeling experts need to assess a wealth of quality criteria in order to find a suitable model. RSquared is only one indicator of good models. One usually also needs to assess adjustedRsquare, F statistic, p-values for all model variables, akaike criterion etc. Moreoever one has to inspect the distribution of residuals in order to verify the independency condition of linear models. Simple Rsquared measure can be largely misleading, especially in cases of multicollinearity. Then the Rsquared is very high but the model is wrong. Moreover, there may be spurious regressions. This requires a very sophisticated system for analyzing models.

<i><font color='green'>

  * Reply
    * We agree with this argument. As this was also identified as major critique point by the summary review, we put much effort to include additional metrics into the analysis. Please see [Regression Metrics] for details on these changes.
    * Some of these features (such as f-statistic) are not comparable between regression models with different degrees of freedom. Hence, they are included as supplemental information in the details on demand step
    * In contrast to the reviewers statement, we do not only focus on linear regression, but also on logistic regression. This restricts the list of regression metrics used for comparisons to those shared by both regression types, such as R² or Akaike Information Criterion. The other features are, as mentioned before, implemented and shown as part of the details on demand

</i></font>

The authors say that the models found with Rsquared measure need to be further inspected. I fully agree, however the paper does not mention what happens then.

<i><font color='green'>

  * Reply
    * The focus of the paper is providing overview visualizations based on regression analyses. It is not suited for detailed regression analyses producing final statements about the statistical validity of a hypothesis. This step incorporates including confounding features and requires a sound statistical background of the user. These calculations are carried out using statistical processors, such as SPSS or STATA.
    * We agree with the feedback that the further analysis steps were not clear. Hence, we revised the introduction of Section *4 Regression Cube Analysis of Cohort Study Data* as well as in the introduction of Section *5 System Design*
    * The lesson learned **Extracted Hypotheses Have to be Investigated Further** is solely focused on how the analysis can be carried out

</i></font>

When looking at the visualization: The authors propose a regression matrix/cube depending on the dimensionality of the model. It provides an overview of good/bad possible models using this criterion. It allows the users to spot models with large Rsquared. The dimensionality of the matrix/cube is reduced by pre-processing which filters out irrelevant variables. This is a positive side of the approach. The user inspects the matrix in order to find “hotspots” – variable combinations with high Rsquared values. It would be nice to include support for this, e.g. by filtering/guidance. It may be already implemented, but it is not clearly described in the paper.

<i><font color='green'>

  * We approached this crituque in context with [Reviewer 3], who suggested a method for scaling the transfer function used to specify ranges of interest. This led to the implementation of a range-slider. Details can be found under [User Interaction]. Using this technique, the user can filter for very high R² values in both the 2D and 3D view.

</i></font>

The approach provides several features which could be better explained and their need/usage documented. For example, the difference matrix seems like a nice tool to compare models for two targets. However, the authors also state that Rsquared values cannot be compared across targets. It is somewhat confusing. The use case also does not seem to rely on this visualization.

<i><font color='green'>

  * The use case for the cube comparison is now explained in more detail by adding the expert feedback which led to its implementation (Paragraph *Cube Comparison*, Section *4.5 Analysis Workflow*)
  * R² values *can* be compared between targets as long as they rely on the same regression type. This argument is made in Section *4.4 Abstracting Regression Results*, Paragraph *3D (Cube) View*. We added feedback from the epidemiological statistician, which led to the design decision of incorporating different colors for each regression type.

</i></font>

A very positive side of the work is the close cooperation with medical experts and application of the tool in real scenarios. Two use cases are also described in the paper.

Some more questions

- Limitations: only three features including target. Although it may cover many cases, it is still very restrictive. Could you please detail on this aspect more? How could the approach be extended to more variables?

<i><font color='green'>

  * We discussed this limitation in Section *8 Summary and Outlook* by suggesting 3D projections of hypercubes spanned by more than 3 dynamic regression variables. Note that by including static features using the formula input, more than three features can already be considered. The whole idea of the difference cube relies on this concept.
  * The epidemiological statistics domain expert argued that their regression models rarely contain more than 4 features.
  * Additionally it is possible that the target is fixed, which leaves all three variables for independent features.

</i></font>

- It would be good to explain when happens that the user does not know the target and thus needs to examine all possible targets. This use case seems to me rather unrealistic. In my experience, the experts already know which target variables they wish to examine. If there is a real need for such tools, it would be good to document it better.

<i><font color='green'>

  * The use-case is part of the hypothesis-free analysis approach. Our observation was that the domain experts often have a set of features, which act as targets. They might contain different abstraction levels (e.g. dichotomous feature chest pain and the more granular feature chest pain levels) or a set of variables describing a condition (e.g. features describing image-derived data). The formula `Z ~ X + Y` allows to quickly assess these features, which can the be analyzed in detail by putting them as static target.
  * The other use-case we observed was to check the system for logical validty. Domain experts used `Z ~ X + Y` to analyze potentially uninteresting targets for correlations they would expect to check if the system works as intended

</i></font>


## Reviewer 2

- Reviewer: external
- Overall Rating 4: Good contribution
- Topic Classification Type: Design study
- Type: Application Topic: Visual representation and interaction technique
- Best Paper Award: Maybe
- Expertise: 4 (Expert)
- Contribution to the field of Visual Analytics: This is an interesting paper in the tradition of visual analytics, at the fuzzy border between too computationally-complex statistics and visualization. The manuscript has multiple strengths. A first contribution is a description of the target domain data and tasks. The manuscript then presents a technique for knowledge discovery in cohort study data sets with user-defined target features (diseases). At the core of the technique is an overview 3D visual encoding of the whole dataset, followed by an interface for adjusting the regression model formulas. The heatmap solution may be simple, but the work features a useful application which relies on three domain experts, and there are at least two valuable design lessons learned. Last but not least, the system front-end is web based, and the entire system is publicly available, which facilitates broader use of this work. Overall, a good paper that within a review cycle can become an even more valuable contribution.

### The Review

This is an interesting paper in the best tradition of visual analytics, at the fuzzy border between too computationally-complex statistics and visualization. The manuscript needs a bit more editing work to find its legs, either as a system or a design study paper.

A first contribution is a description of the target domain data and tasks. The manuscript then presents a technique for knowledge discovery in cohort study data sets with user-defined target features (diseases). At the core of the technique is an overview 3D visual encoding of the whole dataset, followed by an interface for adjusting the regression model formulas. The solution may be indeed simple, but that is not necessarily a weakness: when working with domain experts, "complex" is not necessarily better. The work features a useful application which relies on three domain experts, and there are at least two valuable design lessons learned. Last but not least, the system front-end is web based, and the entire system is publicly available, which facilitates broader use of this work.

If the solution is not particularly striking or novel, the decision to do it in 3D is still interesting, and the manuscript still stands as a design study. For a design study the contributions, as stated in the paper introduction, would need to be either revised, or better supported by evidence in the methods and results. Munzner's Nested Design Model might be of help here -- are the contributions really visualization techniques (a visualization technique would have application across multiple domains), are they at the algorithmic level, or do they consist of selecting appropriate visual encodings from a possible array of options?

<i><font color='green'>

  * This feedback led to a substantial revision of Section **4 Regression Cube Analysis of Cohort Study Data** and **5 System Design** to incorporate how user feedback affected the design decisions. See [Support Design Decisions with Expert Feedback] for details.
  * Also, as suggested, the contributions were revised to capture the different levels of Munzners "A Nested Model for Visualization Design and Validation".

</i></font>

The manuscript could be further strengthened by better structuring the domain requirements to include the web and security issues which are currently discussed too late in the paper.

<i><font color='green'>

  * Advantages of the web-based approach regarding the epidemiological application domain is covered as part of [Support Design Decisions with Expert Feedback] by discussing it at the beginning of the *System Design* section
  * Security issues are now indicated at the beginning of Section **4 Regression Cube Analysis of Cohort Study Data** as well as Section **5 System Design** and discussed in Subsection **5.1 System Paradigm and Components**

</i></font>

In terms of related work, similar domain analysis and related visualization work, with epidemiology as the target domain, was featured here: http://www.computer.org/csdl/trans/tg/2013/12/ttg2013122916-abs.html and should be discussed in this context.

<i><font color='green'>

  * The mentioned work is now integrated into the related work discussion.

</i></font>

More details in the visual encoding are also necessary (color, size, interaction,...), and in particular a justification of the design choices available for these encodings. A videoclip demonstrating the system would further help.

<i><font color='green'>

  * Design decisions were explained in further detail and are supported with expert feedback as part of the revisions w.r.t [Support Design Decisions with Expert Feedback]

</i></font>

Overall, the manuscripts has multiple strengths, and within a review cycle could be improved.

Minor comments:
* Abstract and elsewhere: compound sentences run too long; consider splitting them, and moving the defined term to the start of a sentence, e.g.: not A 3D visualization of all combinations of two to three independent features towards a target acts as an overview of the whole data set, the Regression Cube. but The Regression Cube, a novel (?) 3D visual encoding, acts as an overview of the whole data set. The Cube shows all combinations of two to three independent features towards a specific target disease. (if “towards” is indeed the correct term here)

<i><font color='green'>

  * We revised a large number of long sentenced to either split them up or to simplify them.
  * "Towards" sounds odd indeed. We replaced it in all occurences.

</i></font>

* Confusing use of ‘Regression Cube’ term, already claimed by Chan et al. Why not rename this cube as something else (“Mosaic Cube” maybe or “Regression Mosaic”), for clarity?

<i><font color='green'>

  * TODO Discuss?

</i></font>

* Page 2 no need for this statement “This section covers the epidemiological workflow and requirements.”
* Citations are grammatically invisible, and should not be used as nouns. Correct: "The PivotGraph system [13] features a derived aggregate network". Incorrect: "Aggregation is also used in [13]". (see https://www.cs.ubc.ca/~tmm/writing.txt) “In [22]...” “...in [29, 37].” “presented in [22]” etc. etc.
* Page 3, “Medical image data is “ Data is plural (singular is datum)
* Section 3 Related Work The purpose of the related work is to highlight the novelty of the presented work. It should contain one paragraph for each novel idea or component, and highlight at the end of the paragraph how that related body of work is different from, supports, or complements the present work. Some of the related work paragraphs follow this structure (the Statistical Analysis paragraphs in particular), but not all of them (e.g., the Visual Analysis in Public Health subsection). Please revise.

<i><font color='green'>

  * TODO Put summary at the end of each paragraph, but first include the additional paper

</i></font>

* a data scientists ---> a data scientist
* Typo (new paragraph)? . Extracted Hypotheses Have to be Investigated Further.
* a video demonstration would have been helpful (I gave up halfway through the git repo).

Reviewer 3
----------

- Reviewer: external
- Overall Rating: 3: Sufficient contribution
- Topic Classification Type: Design study
- Type: Application
- Topic: Visual representation and interaction technique
- Topic: Analytical reasoning and decision support
- Topic: Model visualization and optimization
- Expertise: 4 (Expert)
- Best Paper Award: No

Contribution to the field of Visual Analytics:
The main contribution of the paper is an overview visualization showing the explanatory power of feature combinations for target variables. It is combined with an automatic feature pre-filtering that provides scalability up to hundreds of features. Interactive adaptation of the regression formula allows experts to specify hypotheses based on, e.g., previous findings or domain knowledge. This combination of interactive visualization and automatic analysis makes the approach suitable for a visual analytics paper.

Additional contributions include an open source implementation of the proposed system, two case studies based on the application of the system by domain experts in epidemiology, as well as generalizable lessons learned from these studies.

### The Review

The strenghts and weaknesses balance for this paper. On the one hand, it proposes a useful extension of feature space exploration frameworks, and is applicable to basically any domain. Writing style and structure are very good. The implementation is architecturally exemplary and accessible for everyone on the web, thus there is definitely value for the community. On the other hand, it ignores closely related work, presents some design choices that are not fully justified, and does not discuss limitations in enough detail. With all these points addressed, I might have returned a higher rating, but as of now, I consider it a borderline case.

*What are its strengths and weaknesses?*

*Strengths*
+ The paper is well-written and well-structured.
+ The system implementation is impressive due to its scalable and portable architecture. I also like the incremental result feedback. + Adopting the widely used regression formula notation strengthens the paper. It allows a very concise description of the possible cube configurations in the paper, and also makes the implementation intuitive for users already familiar with the notation.
+ The approach appears very scalable to large numbers of features (however, for small datasets it would make sense to have the CFS step only optionally, see below).
+ As opposed to previous approaches (e.g. [MP13]), the overview visualization is not limited to single input variables and pairs of variables, but supports combinations of 3 variable features at a time, and supports both numerical and categorical targets.
+ I like that the paper presents lessons learned that are applicable beyond the domain at hand.

*Weaknesses*

- Closely related work has not been taken into account: The partition-based regression framework paper [MP13] proposes an approach for ranking features and feature pairs for a target variable by R^2 of one model per feature combination, and uses a very similar matrix arrangement as this approach does for slices. Features and interactions can be iteratively added very similarly to hypothesis specification in the paper at hand. The paper at hand has benefits regarding scalability, categorical targets, and considers 3D combinations of features, but a thorough delimination is necessary to acceptance of this paper.

<i><font color='green'>

  * The mentioned work is now integrated into the related work discussion.

</i></font>

  - Some design choices are questionable, and should at least be justified in more detail:
    1. Regarding the ordering of features: the concept of ranking (combinations of) features is a proven means for guidance towards relevant features [SS04],[MP13]. Without the option of ranking features in the plots, it is possible to visually miss less salient "hotspots". (e.g., Figure 3 or Figure 5 breast fat). What are the features ordered by in the current implementation?
    2. The benefits of the 3D cube could be made more explicit. E.g., showing multiple slices at once in 3D makes sense to convey structure with respect to these dimensions, such as feature pairs being relevant for multiple targets in a row. Just for guiding users to slices with high R^2s, an ordered list of slices (e.g., targets in Z~X+Y) with respect to max. or avg. R^2 across the slice would be at least as effective.

  <i><font color='green'>

  1. The current ordering is based on the order of features in the CSV file. Ordering of features was discussed with the domain experts and ordering based on the regression metric is already implemented. Reorderings at the level of individual slices were discarded. Each slice ordering would be different, triggering a reordering of the cube on every slicing. On every slicing, the user had a different ordered list and searched all over again for parameters of interest.
    * We experimented with the new transfer function control, which was added to the prototype based on this review (see further below) and concluded that this tool is well suited for highlighting hot-spots by selecting a range of only high regression metrics.
    * The feedback is included in the revisions based on [Support Design Decisions with Expert Feedback].
  2. The cube acts as mini-map to spot hot-spots, which is now additionally supported additionally using the transfer function. Simple per-slice reorderings would, as argued in the prior bullet point, not be as effective, as it also introduces new problems, such as destroying the mental model of the feature order. A ordered list of slices with high average regression metrics will result in a ordering, where single features already have a strong explanatory power w.r.t. the target. We are, however, interested in strong combinations, which is one point made in Figure 5.
    * We emphasized more on the orderings as well as the limitations and advantages of the 3D view in Section **5.2 Regression Cube Visualization**

  </i></font>


- Regarding the color coding: A fixed linear scheme makes it very hard to discern small variations. Allowing the user to adapt the transfer function, e.g. adjusting the mapped range to enhance the contrast would help. Also, no legend is shown in the current implementation.

<i><font color='green'>

  * We completely agree with this comment. Therefore, we implemented a range-slider, which acts both as transfer function as well as caption
  * See [User Interaction] for details

</i></font>

  - Limitations of the approach are not discussed in enough detail in the paper:
    1. I like the idea of CFS as a pre-filter for large numbers of features. However, I missed a discussion of possible drawbacks. Isn't it possible that interesting features are missed (e.g., features that are only relevant for a part of the data)? Besides, is it always desired to omit redundant but relevant features from this list? How does the user know whether a feature was omitted due to irrelevance or due to redundancy? Especially for smaller numbers of features, it would make sense to optionally turn this preprocessing step off.
    2. What are the limits of hypothesis specification through the regression formula? For example: - is it possible to specify HOW feature interactions are taken into account mathematically, using the formula notation (or some other way in the implementation)? - is it possible to define feature transformations to be considered, such as X^2? I would expect things like this to be possible when you state "domain knowledge / hypotheses can be specified via the regression formula". But if not, please state such limitations.

  <i><font color='green'>

  1. We agree with the reviewers observations. The CFS filtering step, as most automatic preprocessings, add uncertainty into the analysis, as the user can not comprehend in detail, why certain features are removed.
    * We tackled this problem using the z-dimension of the cube. The CFS algorithm is applied per-slice depending on the target feature. In other words, there are always all features represented in z-dimension of the cube. This means, that for features with static a target (e.g., Cancer ~ X + Y + Z), the influence of each feature can be assessed by slicing through the cube.
    * We noted the limitation in Section **4.3 Target-Variable-Dependent Dimension Reduction** and how we tackled it in Section **4.4 Abstracting Regression Results**.
    * We added a check box as part of the file-upload step, which allows to skip the CFS preprocessing step. It is noted in Section **5.1 System Paradigm and Components**
  2. TODO: Wrote Till a Mail

  </i></font>

- As this is a vis paper, another weakness in my opinion is the fact that details on demand for a cell are limited to statistical numbers. Adding some form of conditional distribution visualization could increase trust in findings further. It would be in accordance with the lesson learned regarding increased confidence in visually observed patterns as opposed to black box assessment.

<i><font color='green'>

  * As part of the changes made regarding the [Regression Metrics], a additional scatter plot for analyzing the residuals was included.
  * Additionally, now different regression metrics can be visualized using the Regression Cube.

</i></font>

---

*Will this work inspire others in VAST research? Will it inform VAST practitioners? Is the work important and useful?*

Regarding architecture and accessibility, the implementation is impressive and inspiring to practitioners. The implementation is accessible for everyone on the web, thus there is definitely value for the community.

*Is this work novel, incremental, or previously published?*

Partly novel. I have not seen the cube visualization before, but very similar guidance mechanisms have been published before (see above, [MP13]).

*Is this work relevant for VAST? If not, what other venues would be appropriate?*

VAST is appropriate.

*Is related work adequately referenced and if not what citations should be added?*

As mentioned before, the partition based framework [MP13] must be considered in my opinion. - Another paper that could be cited is the Wrapper approach to feature selection by Kohavi and John [KJ97], to situate the feature assessments of the approach at hand with respect to the categories "filter" vs "wrapper" approaches to feature selection. In my opinion, both kinds of approaches are incorporated in the paper at hand, one for the CFS pre-filter, and the other (wrapper) for assessing the explanatory power given a particular regression formula. I would find this nice, but it is not a must.

*Are the technical results sound? Are the methods and techniques described in adequate detail?*

It is not clear how features are ordered in the plots. - Regarding the semi transparent representation of the current slice in the cube: From the figures/text in the paper, it is not clear how "data points are projected onto the currently selected plane". What data points? Projected how? From the implementation on the web it appeared to me as if the full slice of xy-feature pairs was shown instead of just the half above the diagonal.

<i><font color='green'>

  * The paragraph **Cube Slice Selection** of Section **5.2 Regression Cube Visualization** was revised with this critique in mind. The area below the prism is in fact be used to identify the correct position of the current slice. The observation of the reviewer regarding the projection is correct and is pointed out in the section.

</i></font>


*Is the exposition clear? How could the structure or style of the presentation be improved?*

It should be stated explicitly that the positioning of features in the cube takes all dimensions into account, i.e., the cube contains all features, and not only those selected by CFS for a given target.

<i><font color='green'>

  * This is now covered **3D (Cube) View** paragraph of Section **4.4 Abstracting Regression Results**

</i></font>

*Should anything be deleted or condensed from the writeup?*

From a vis perspective, I think shortening or moving "Encoding via CSV Files" to supplemental material such as a manual of your implementation is also fine, if you need to gain space for modifications.

<i><font color='green'>

  * The paragraph was removed in order to shorten the paper

</i></font>

*Is the length of the paper appropriate for its contribution? Is it too long or too short?*

fine.

*Are the figures informative?*

In Figure 3, why do you show a blue (dichotomous) target in the 2D mosaic plot, while an orange (numerical) target slice is selected in the cube?

<i><font color='green'>

  * Good catch, this is fixed now.

</i></font>

*Typos and other mistakes*
- Section 5.1. Usage of a Regression Prism for Information Reduction. "Figure 1 shows that all values are mirrored along the diagonal of the mosaic plot matrix" <- this is not shown in Figure 1.

<i><font color='green'>

  * Fixed as well

</i></font>

- Section 7.1. "UN, a data scientists .."

*References*

- [KJ97] R. Kohavi and G. H. John. Wrappers for feature subset selection. Artificial Intelligence, 97(1):273–324, 1997
- [MP13] T. Mühlbacher and H. Piringer. A Partition-Based Framework for Building and Validating Regression Models. IEEE Trans. on Visualization and Computer Graphics (VAST ’13), 19(12):1962–1971, 2013
- [SS04] J. Seo and B. Shneiderman. A rank-by-feature framework for unsupervised multidimensional data exploration using low dimensional projections. In Proc. IEEE Symp. on Information Visualization 2004 (InfoVis 2004), pages 65–72, 2004.
