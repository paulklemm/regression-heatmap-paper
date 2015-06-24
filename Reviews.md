# VAST'15 Reviews "Regression Cube Analysis of Cohort Study Data "

## Submission 175, Review 4 - Primary

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

Reviewers agree that the paper addresses an important problem, and the high level of contact with experts makes this a good application paper. They are concerned in the general sense that linear regression modeling experts need to assess more criteria in order to select best models. There are a matrix of measures such as adjusted R square, F statistic, p-values etc. that are often used to understand a multiple regression. Other measures such as the Akaike Information Criterion can help analysts to compare models with different power e.g. number of variables. Other metrics such as the distribution of residuals can also be useful (and sometimes essential) to make decisions about models.

Some of this might be dealt with by pointing out how user input was used to select the measures used, and to make it clear that the system is intended for expert users who have sufficient understanding of regression and how it should be interpreted that they are able to use the system wisely.

The paper has aspects of a design study and of a system paper. For a design study the contributions would need to be revised, or better supported by evidence in the methods and results. It would be good to know how the authors made the decision what to include in the system. Did the users consider these factors important, in which case they may be added later, or were they not of interest to them? This may explain some of the design decisions that are not obvious to readers.

It was suggested that the manuscript could be further strengthened by better structuring the domain requirements to include the web and security issues

A common concern was that relevant works in visual analytics area should be referenced. See individual reviews for specifics.

## Submission 175, Review 1

- Reviewer: secondary
- Overall Rating: 2.5
- Topic Classification
- Type: Application
- Best Paper Award: No
- Expertise: 4 (Expert)
Contribution to the field of Visual Analytics: The paper addresses an important problem – finding the best linear regression model to model a target variable using a set of potential variables. The authors calculate all possible combinations of models and present the results to the user with help of a heatmap - matrix/cube representation of Rsquared quality criterion. The approach has been defined and evaluated in close cooperation with medical experts. It helps them to choose suitable models from a large set of potential models. The problem tackled can be found across many application areas so the potential for such solutions is large. The paper is very well written and the authors have put a lot of effort into tackling this problem. The paper takes a simplified approach focusing only on Rsquared criterion, which enables them to use a “simple” heatmap for showing the results. The authors provide a tool that allows for creating varous variants of models and exploring the resulting Rsquared values for all combinations. This approach provides an overview of good/bad possible models using this criterion. I see several problems with this approach. Mainly, in reality, linear regression modelling experts need to assess much more criteria in order to select best models. Second, in case the focus is only on Rsquared, it is not clear to me how these particular visualizations bring value added beyond simple spotting of large Rsquare values.

With respect to related works, several important and very relevant works in visual analytics area have not been referred to.

### The Review

This paper addresses an important problem. Modelling and parameter setting (parameters in this case are the variables of the model) is a well-known problem in many application areas. So the potential of tools supporting modelling is large. Recently, a wealth of literature in visual analytics area has started to look at parameter steering and modelling and to provide tools for various selected problems. This paper focuses on linear regression model. The problem stems from medicine/health analysis of real large scale data. The paper is very well written, easily readable and well structured. Introduction motivates the work well and supports reader in wanting to read more. Related work covers many works from medical analysis and information visualization. This is a broad overview of literature. Nevertheless, I still miss several important works from visualization/visual analytics are that focus on modelling and visual parameter analysis (model variables can be seen as parameters). This is the core of the paper. An overview of visual parameter analysis is given in a recent Sedlmeier et al. paper. Especially, it would be needed to mention 1) Zhenyu Guo, Matthew O Ward, and Elke A Rundensteiner. Model space visualization for multivariate linear trend discovery. In Visual Analytics Science and Technology, 2009. VAST 2009. IEEE Symposium on, pages 75–82. IEEE, 2009. 2) Muhlbacher, Thomas, and Harald Piringer. "A partition-based framework for building and validating regression models." Visualization and Computer Graphics, IEEE Transactions on 19.12 (2013): 1962-1971.

Approach: The authors focus on linear regression models with one target variable (quantitative or discrete). The approach is restricted to 3 variables including the target. The authors calculate all possible models and support finding best models using only Rsquared measure. This is where my problem with the approach is. In reality, modeling experts need to assess a wealth of quality criteria in order to find a suitable model. RSquared is only one indicator of good models. One usually also needs to assess adjustedRsquare, F statistic, p-values for all model variables, akaike criterion etc. Moreoever one has to inspect the distribution of residuals in order to verify the independency condition of linear models. Simple Rsquared measure can be largely misleading, especially in cases of multicollinearity. Then the Rsquared is very high but the model is wrong. Moreover, there may be spurious regressions. This requires a very sophisticated system for analyzing models. The authors say that the models found with Rsquared measure need to be further inspected. I fully agree, however the paper does not mention what happens then. When looking at the visualization: The authors propose a regression matrix/cube depending on the dimensionality of the model. It provides an overview of good/bad possible models using this criterion. It allows the users to spot models with large Rsquared. The dimensionality of the matrix/cube is reduced by pre-processing which filters out irrelevant variables. This is a positive side of the approach. The user inspects the matrix in order to find “hotspots” – variable combinations with high Rsquared values. It would be nice to include support for this, e.g. by filtering/guidance. It may be already implemented, but it is not clearly described in the paper. The approach provides several features which could be better explained and their need/usage documented. For example, the difference matrix seems like a nice tool to compare models for two targets. However, the authors also state that Rsquared values cannot be compared across targets. It is somewhat confusing. The use case also does not seem to rely on this visualization. A very positive side of the work is the close cooperation with medical experts and application of the tool in real scenarios. Two use cases are also described in the paper.

Some more questions -	Limitations: only three features including target. Although it may cover many cases, it is still very restrictive. Could you please detail on this aspect more? How could the approach be extended to more variables? -	It would be good to explain when happens that the user does not know the target and thus needs to examine all possible targets. This use case seems to me rather unrealistic. In my experience, the experts already know which target variables they wish to examine. If there is a real need for such tools, it would be good to document it better.


## Submission 175, Review 2

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

The manuscript could be further strengthened by better structuring the domain requirements to include the web and security issues which are currently discussed too late in the paper. In terms of related work, similar domain analysis and related visualization work, with epidemiology as the target domain, was featured here: http://www.computer.org/csdl/trans/tg/2013/12/ttg2013122916-abs.html and should be discussed in this context.

More details in the visual encoding are also necessary (color, size, interaction,...), and in particular a justification of the design choices available for these encodings. A videoclip demonstrating the system would further help.

Overall, the manuscripts has multiple strengths, and within a review cycle could be improved.

Minor comments:
* Abstract and elsewhere: compound sentences run too long; consider splitting them, and moving the defined term to the start of a sentence, e.g.: not A 3D visualization of all combinations of two to three independent features towards a target acts as an overview of the whole data set, the Regression Cube. but The Regression Cube, a novel (?) 3D visual encoding, acts as an overview of the whole data set. The Cube shows all combinations of two to three independent features towards a specific target disease. (if “towards” is indeed the correct term here)
* Confusing use of ‘Regression Cube’ term, already claimed by Chan et al. Why not rename this cube as something else (“Mosaic Cube” maybe or “Regression Mosaic”), for clarity?
* Page 2 no need for this statement “This section covers the epidemiological workflow and requirements.”
* Citations are grammatically invisible, and should not be used as nouns. Correct: "The PivotGraph system [13] features a derived aggregate network". Incorrect: "Aggregation is also used in [13]". (see https://www.cs.ubc.ca/~tmm/writing.txt) “In [22]...” “...in [29, 37].” “presented in [22]” etc. etc.
* Page 3, “Medical image data is “ Data is plural (singular is datum)
* Section 3 Related Work The purpose of the related work is to highlight the novelty of the presented work. It should contain one paragraph for each novel idea or component, and highlight at the end of the paragraph how that related body of work is different from, supports, or complements the present work. Some of the related work paragraphs follow this structure (the Statistical Analysis paragraphs in particular), but not all of them (e.g., the Visual Analysis in Public Health subsection). Please revise.
* a data scientists ---> a data scientist
* Typo (new paragraph)? . Extracted Hypotheses Have to be Investigated Further.
* a video demonstration would have been helpful (I gave up halfway through the git repo).

## Submission 175, Review 3

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
- Some design choices are questionable, and should at least be justified in more detail: 1) Regarding the ordering of features: the concept of ranking (combinations of) features is a proven means for guidance towards relevant features [SS04][MP13]. Without the option of ranking features in the plots, it is possible to visually miss less salient "hotspots". (e.g., Figure 3 or Figure 5 breast fat). What are the features ordered by in the current implementation? 2) The benefits of the 3D cube could be made more explicit. E.g., showing multiple slices at once in 3D makes sense to convey structure with respect to these dimensions, such as feature pairs being relevant for multiple targets in a row. Just for guiding users to slices with high R^2s, an ordered list of slices (e.g., targets in Z~X+Y) with respect to max. or avg. R^2 across the slice would be at least as effective.
- Regarding the color coding: A fixed linear scheme makes it very hard to discern small variations. Allowing the user to adapt the transfer function, e.g. adjusting the mapped range to enhance the contrast would help. Also, no legend is shown in the current implementation.
- Limitations of the approach are not discussed in enough detail in the paper: 1) I like the idea of CFS as a pre-filter for large numbers of features. However, I missed a discussion of possible drawbacks. Isn't it possible that interesting features are missed (e.g., features that are only relevant for a part of the data)? Besides, is it always desired to omit redundant but relevant features from this list? How does the user know whether a feature was omitted due to irrelevance or due to redundancy? Especially for smaller numbers of features, it would make sense to optionally turn this preprocessing step off. 2) What are the limits of hypothesis specification through the regression formula? For example: - is it possible to specify HOW feature interactions are taken into account mathematically, using the formula notation (or some other way in the implementation)? - is it possible to define feature transformations to be considered, such as X^2? I would expect things like this to be possible when you state "domain knowledge / hypotheses can be specified via the regression formula". But if not, please state such limitations.
- As this is a vis paper, another weakness in my opinion is the fact that details on demand for a cell are limited to statistical numbers. Adding some form of conditional distribution visualization could increase trust in findings further. It would be in accordance with the lesson learned regarding increased confidence in visually observed patterns as opposed to black box assessment.

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

*Is the exposition clear? How could the structure or style of the presentation be improved?*

It should be stated explicitly that the positioning of features in the cube takes all dimensions into account, i.e., the cube contains all features, and not only those selected by CFS for a given target.

*Should anything be deleted or condensed from the writeup?*

From a vis perspective, I think shortening or moving "Encoding via CSV Files" to supplemental material such as a manual of your implementation is also fine, if you need to gain space for modifications.

*Is the length of the paper appropriate for its contribution? Is it too long or too short?*

fine.

*Are the figures informative?*

In Figure 3, why do you show a blue (dichotomous) target in the 2D mosaic plot, while an orange (numerical) target slice is selected in the cube?

*Typos and other mistakes*
- Section 5.1. Usage of a Regression Prism for Information Reduction. "Figure 1 shows that all values are mirrored along the diagonal of the mosaic plot matrix" <- this is not shown in Figure 1.
- Section 7.1. "UN, a data scientists .."

*References*

- [KJ97] R. Kohavi and G. H. John. Wrappers for feature subset selection. Artificial Intelligence, 97(1):273–324, 1997
- [MP13] T. Mühlbacher and H. Piringer. A Partition-Based Framework for Building and Validating Regression Models. IEEE Trans. on Visualization and Computer Graphics (VAST ’13), 19(12):1962–1971, 2013
- [SS04] J. Seo and B. Shneiderman. A rank-by-feature framework for unsupervised multidimensional data exploration using low dimensional projections. In Proc. IEEE Symp. on Information Visualization 2004 (InfoVis 2004), pages 65–72, 2004.
