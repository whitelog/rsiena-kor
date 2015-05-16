Manual for RSiena
Ruth M. Ripley Tom A.B. Snijders Zso ́fia Boda Andra ́s Vo ̈r ̈os Paulina Preciado
University of Oxford: Department of Statistics; Nuffield College February 17, 2015

Abstract
SIENA (for Simulation Investigation for Empirical Network Analysis) is a computer pro- gram that carries out the statistical estimation of models for the evolution of social networks according to the dynamic actor-oriented model of Snijders (2001, 2005), Snijders et al. (2007), and Snijders et al. (2010a). This is the manual for RSiena, a contributed package to the statistical system R. It complements, but does not replace the help pages for the RSiena functions! It also contains contributions written earlier, for the manual for SIENA version 3, by Mark Huisman, Michael Schweinberger, and Christian Steglich.
This manual is frequently updated, mostly only in a minor way. This version was renewed for RSiena version 1.1-283.

Contents
	•	General information 6 

Part I. Introduction 8
	•	1. Minimal Intro
	⁃	1.1 Giving references..................................... 8
	•	2. Getting started with SIENA 9
	⁃	2.1 The logic of Stochastic Actor-Oriented Models .................... 9
	⁃	2.1.1 Types of Stochastic Actor-Oriented Models . . . . . . . . . . . . . . . . . . 10
	⁃	2.1.2 Data, variables and effects............................ 11
	⁃	2.1.3 Outline of estimation procedure......................... 15
	⁃	2.1.4 Further useful options in RSiena ........................ 16
	⁃	2.2 Installing R and SIENA ................................. 16
	⁃	2.3 Using SIENA within R .................................. 17
	⁃	2.4 Example R scripts for getting started.......................... 19
	⁃	2.5 Steps for looking at results: Executing SIENA...................... 19
	⁃	2.6 Getting help with problems ............................... 20

PartII Users’ Manual
	•	3. Steps of modeling 22
	•	4. Input data 23
	⁃	4.1 Data types ........................................ 23
	⁃	4.1.1 Network data................................... 23
	⁃	4.1.2 Transformation between matrix and edge list formats . . . . . . . . . . . . 25
	⁃	4.1.3 Behavioral data.................................. 26
	⁃	4.1.4 Individual covariates............................... 26
	⁃	4.1.5 Dyadic covariates................................. 27
	⁃	4.2 Internal data treatment ................................. 28
	⁃	4.2.1 Interactions and dyadic transformations of covariates . . . . . . . . . . . . . 28
	⁃	4.2.2 Centering ..................................... 28
	⁃	4.2.3 Monotonic dependent variables ......................... 30
	⁃	4.3 Further data specification options............................ 30 
	⁃	4.3.1 Structurally determined values .........................
	⁃	4.3.2 Missing data ................................... 32 
	⁃	4.3.3 Composition change: joiners and leavers.................... 33
	•	5. Model specification 35
	⁃	5.1 Definition of the model.................................. 35 
	⁃	5.1.1 Specification in SIENA ............................. 37 
	⁃	5.1.2 Mathematical specification ........................... 38
	⁃	5.2 Important structural effects for network dynamics: one-mode networks.................................... 39
	⁃	5.3 Important structural effects for network dynamics: two-mode networks.................................... 42
	⁃	5.4 Effects for network dynamics associated with covariates . . . . . . . . . . . . . . . 43
	⁃	5.5 Cross-network effects for dynamics of multiple networks . . . . . . . . . . . . . . . 45
	⁃	5.6 Effects on behavior evolution .............................. 46
	⁃	5.7 Model Type: non-directed networks .......................... 47
	⁃	5.8 Additional interaction effects .............................. 48
	⁃	5.8.1 Interaction effects for network dynamics.................... 49
	⁃	5.8.2 Interaction effects for behaviordynamics.................... 49
	⁃	5.9 Time heterogeneity in model parameters........................ 50
	⁃	5.10 Limiting the maximum outdegree............................ 51
	⁃	5.11 Goodness of fit with auxiliary statistics ........................ 52
	⁃	5.11.1 Treatment of missing data and structural values in siena GOF . . . . . . . . 52
	•	6 Estimation 54
	⁃	6.1 The estimation function siena07............................. 54 
	⁃	6.1.1 Initial Values ................................... 56 
	⁃	6.1.2 Convergence Check................................ 57
	⁃	6.2 What to do if there are convergence problems..................... 58 
	⁃	6.2.1 Pressing on .................................... 60
	⁃	6.3 Some important components of the siena Fit object . . . . . . . . . . . . . . . . . . 61
	⁃	6.4 Algorithm......................................... 62
	⁃	6.5 Output .......................................... 63 
	⁃	6.5.1 Convergence check ................................ 64 
	⁃	6.5.2 Parameter values and standard errors ..................... 64 
	⁃	6.5.3 Collinearity check ................................ 65
	⁃	6.6 Maximum Likelihood and Bayesian estimation .................... 66
	⁃	6.7 Other remarks about the estimation algorithm .................... 68
	⁃	6.7.1 Conditional and unconditional estimation ................... 68
	⁃	6.7.2 Fixing parameters ................................ 69
	⁃	6.7.3 Automatic fixing of parameters......................... 69
	⁃	6.7.4 Required changes from conditional to unconditional estimation . . . . . . . 69
	⁃	6.8 Using multiple processes................................. 70
	•	7 Standard errors 71 
	⁃	7.1 Multicollinearity ..................................... 71 
	⁃	7.2 Precision of the finite differences method........................ 72
	•	8 Tests 73
	⁃	8.1 Wald-type tests...................................... 73 
	⁃	8.1.1 Standard errors of linear combinations..................... 75
	⁃	8.2 Score-typetests...................................... 76
	⁃	8.3 Example: one-sided tests, two-sided tests, and one-step estimates . . . . . . . . . . 77 
	⁃	8.3.1 Multi-parametertests .............................. 78
	⁃	8.4 Alternative application: convergence problems..................... 79
	⁃	8.5 Testing differences between independent groups.................... 79
	⁃	8.6 Testing time heterogeneity in parameters ....................... 80
	•	9 Simulation 82 
	⁃	9.1 Accessing the generated networks............................ 83 
	⁃	9.2 Conditional and unconditional simulation ....................... 84
	•	10 Getting started 85 
	⁃	10.1 Modelchoice ....................................... 86
	•	11 Multilevel network analysis 87
	⁃	11.1 Multi-group Siena analysis................................ 88
	⁃	11.2 Meta-analysis of Siena results.............................. 89
	⁃	11.2.1 Meta-analysis directed at the mean and variance of the parameters . . . . . 90 
	⁃	11.2.2 Meta-analysis directed at testing the parameters . . . . . . . . . . . . . . . 92 
	⁃	11.2.3 Contrast between the two kinds of meta-analysis . . . . . . . . . . . . . . . 93
	⁃	11.3 Random coefficient multilevel Siena analysis...................... 93 
	⁃	11.3.1 Which data sets to use for siena Bayes ..................... 94 
	⁃	11.3.2 Models pecification................................ 95 
	⁃	11.3.3 How to enter your data in siena Bayes ..................... 95 
	⁃	11.3.4 How to choose the parameter settings for siena Bayes . . . . . . . . . . . . . 96 
	⁃	11.3.5 Prior distributions ................................ 96 
	⁃	11.3.6 Operation of sienaBayes()............................ 98 
	⁃	11.3.7 Assessing convergence .............................. 98 
	⁃	11.3.8 Interpreting results of sienaBayes........................ 98
	•	12 Formulas for effects 100 
	⁃	12.1 Networkevolution .................................... 100 
	⁃	12.1.1 Network evaluation function........................... 101 
	⁃	12.1.2 Multiple network effects ............................. 116 
	⁃	12.1.3 Network creation and endowment functions . . . . . . . . . . . . . . . . . . 123 
	⁃	12.1.4 Network rate function .............................. 124 
	⁃	12.2 Behavioral evolution ................................... 126 
	⁃	12.2.1 Behavioral evaluation function ......................... 126 
	⁃	12.2.2 Behavioral creation function........................... 134 
	⁃	12.2.3 Behavioral endowment function......................... 135 
	⁃	12.2.4 Behavioral rate function............................. 135
	•	13 Parameter interpretation 137 
	⁃	13.1 Networks ......................................... 137 
	⁃	13.2 Behavior.......................................... 138 
	⁃	13.3 Ego–alter selection tables ............................... 139 
	⁃	13.4 Ego–alter influence tables ............................... 145
	•	14 Error messages 149 
	⁃	14.1 During estimation .................................... 149 
	⁃	14.2 As result of a score-type test (including time test) . . . . . . . . . . . . . . . . . . 150 
	⁃	14.3 In sienaGOF ....................................... 150

Part III Programmers’ manual 152 
	•	15 Get the source code 152 
	•	16 Other tools you need 152 
	•	17 Building, installing and checking the package 153
	•	18 Understanding and adding an effect 154 
	⁃	18.1 Example: adding the truncated out-degree effect ................... 156 
	⁃	18.2 Notes for effects for two-mode networks ........................ 160
Back Matter
	•	A List of Functions in Order of Execution 161
	•	B Changes compared to earlier versions
	•	C References







6
1 General information
SIENA1, shorthand for Simulation Investigation for Empirical Network Analysis, is a set of methods implemented in a computer program that carries out the statistical estimation of models for repeated measures of social networks according to the Stochastic Actor-oriented Model (‘SAOM’) of Snijders and van Duijn (1997), Snijders (2001), Snijders et al. (2007), Snijders et al. (2010a), and Greenan (2015); also see Steglich et al. (2010). A tutorial for these models is in Snijders et al. (2010b).
A website for SIENA is maintained at http://www.stats.ox.ac.uk/~snijders/siena/ . At this website (‘publications’ tab) you shall also find references to introductions in vari- ous other languages, as well as the file Siena algorithms.pdf which gives a sketch of the main algorithms used in RSiena. The website further contains references to many pub- lished examples, example scripts illustrating various possibilities of the package, course announcements, etc.
This is a manual for RSiena, which also may be called SIENA version 4.0; the manual is provisional in the sense that it is continually being updated, taking account of updates in the package. RSiena is a contributed package for the R statistical system which can be downloaded from http://cran.r-project.org. For the operation of R, the reader is referred to the corresponding literature and help pages.
RSiena was originally programmed by Ruth Ripley and Krists Boitmanis, in collab- oration with Tom Snijders. Since May 2012 the maintainer is Tom Snijders. Further contributions were made by Josh Lospinoso, Charlotte Greenan, Christian Steglich, Jo- han Koskinen, Mark Ortmann, Nynke Niezink, and Robert Hellpap.
In addition to the ‘official’ R distribution of RSiena, there is an additional distribution at R-Forge, which is a central platform for the development of R packages offering facilities for source code management. It is quite usual that later versions of RSiena are available at http://r-forge.r-project.org/R/?group_id=461 before being incorporated into the R package that can be downloaded from CRAN. In addition, at R-Forge there is a package RSienaTest which may include additional options that are still in the testing stage. Some of the options described in this manual may apply to RSienaTest only, with the plan to transfer this to RSiena in the future.

———
1 This program was first presented at the International Conference for Computer Simulation and the Social Sciences, Cortona (Italy), September 1997, which originally was scheduled to be held in Siena. See Snijders and van Duijn (1997).



7
We are grateful to NIH (National Institutes of Health, USA) for their funding of programming RSiena. This was done as part of the project Adolescent Peer Social Network Dynamics and Problem Behavior, funded by NIH (Grant Number 1R01HD052887-01A2), Principal Investigator John M. Light (Oregon Research Institute).
For earlier work on SIENA, we are grateful to NWO (Netherlands Organisation for Scientific Research) for their support to the project Models for the Evolution of Networks and Behavior (project number 461-05-690), the integrated research program The dynamics of networks and behavior (project number 401-01-550), the project Statistical methods for the joint development of individual behavior and peer networks (project number 575-28- 012), the project An open software system for the statistical analysis of social networks (project number 405-20-20), and to the foundation ProGAMMA, which all contributed to the work on SIENA.





1.1 Giving references
When using SIENA, it is appreciated that you refer to this manual and to one or more relevant references of the methods implemented in the program. The reference to this manual is the following.
Ruth M. Ripley, Tom A.B. Snijders, Zs ́ofia Boda, Andr ́as V ̈or ̈os, and Paulina Preciado, 2014. Manual for SIENA version 4.0 (version February 17, 2015). Oxford: University of Oxford, Department of Statistics; Nuffield College. http://www.stats.ox.ac.uk/siena/
A tutorial is Snijders et al. (2010b). A basic reference for the network dynamics model is Snijders (2001) or Snijders (2005). Basic references for the model of network-behavior co-evolution are Snijders et al. (2007) and Steglich et al. (2010). A basic reference for the Bayesian estimation is Koskinen and Snijders (2007) and for the maximum likelihood estimation Snijders et al. (2010a).
More specific references are Schweinberger (2012) for the score-type goodness of fit tests and Schweinberger and Snijders (2007b) for the calculation of standard errors of the Method of Moments estimators. For the model for diffusion of innovations in dynamic networks, please refer to Greenan (2015). For assessing and correcting time heterogene- ity, and goodness of fit assement and associated model selection considerations, refer to Lospinoso et al. (2011) and Lospinoso (2012).

There may be various strategies for getting acquainted with RSiena. In any case, it is a good idea to study the tutorial Snijders et al. (2010b). Two recommended options for learning the ‘how to’ are the following:
	•	1. One excellent option is to read the User’s Manual from start to finish (leaving aside the Programmer’s Manual).
	•	2. A second option is to read this Minimal Introduction, to get a sense of the rest by looking at the table of contents, and then follow the references to specific sections of your interest. The searchable pdf file makes it easy to look for the relevant words.
This Minimal Introduction explains the basics of Stochastic Actor-Oriented Models and gives practical information on running RSiena. We start with section 2.1 which gives a brief and non-technical introduction to the types of Stochastic Actor-Oriented Models, to the most important concepts related to them, to the data required to apply SIENA, and to further features of the program. In Section 2.2 we explain how to install and run SIENA as the package RSiena from within R. Section 2.4 and Section 2.5 provide example R scripts and guidance for understanding the results. If you are looking for help with a specific problem, read Section 2.6.

SIENA (Simulation Investigation for Empirical Network Analysis) is a statistical tool de- veloped for the analysis of longitudinal network data, collected in a network panel study with two or more ‘waves’ of observations. It incorporates different variants of a dynamic network model family: the Stochastic Actor-Oriented Model (SAOM). In this section, we give a very concise introduction to how these models work in principle and what type of data they are suitable to analyze. For sake of simplicity, SAOMs implemented in SIENA are often referred to as ‘SIENA models’. In this subsection, we only consider the case of network evolution; see below for the more complex cases of coevolution. For a further in- troduction, consult Snijders et al. (2010b). An introduction for applications in the context of adolescent development is Veenstra et al. (2013).
The defining characteristic of Stochastic Actor-Oriented Models is their ‘actor-oriented’ nature which means that they model change from the perspective of the actors (nodes). That is, Stochastic Actor-Oriented Models always “imagine” network evolution as indi- vidual actors creating, maintaining or terminating ties to other actors. When thinking about network dynamics, researchers usually assume that these decisions (conscious or subconscious) of actors are influenced by the structure of the network itself and the char- acteristics and behaviors of the focal actor (ego) who is making a decision and those of other actors in the network (alters). Stochastic Actor-Oriented Models provide a means to quantify the ways, the extent and the uncertainty with which these factors are associated with network evolution between observations.
The Stochastic Actor-Oriented Modelcan be regarded as an agent-based (‘actor-based’) simulation model of the network evolution; where all network changes are decomposed into very small steps, so-called ministeps, in which one actor creates or terminates one outgoing tie. These ministeps are probabilistic and made sequentially. The transition from the observation at one wave to the next is done by means of normally a large number of ministeps. The actors respond to the network in the sense that the probabilities of these changes depend on the current (unobserved) state of the network. Each further ministep changes the network state and therefore the actors are each others’ ever changing context (Zeggelink, 1994). This allows the model to represent the feedback process that is typical for network dynamics. These changes are not individually observed, but they are simulated; what is observed is the state obtained at the next observation wave.
This simulation model implements the statistical model for the network dynamics. The statistical procedures utilize a large number of repeated simulations of the network evolution from each wave to the next. They estimate and test the parameters producing a probabilistic network evolution that ‘could have’ brought these observations to follow one another.
To avoid misunderstandings, two notes have to be made about the meaning of actor “decisions” and the role of Stochastic Actor-Oriented Models in causal inference. First, the fact that SIENA models are actor-oriented does not imply the assumption that the actors take decisions in any real sense. It means that the changes in the network are organized, so to say, by the nodes in the network. This aligns very well with a substantive standpoint where the nodes have agency (Snijders, 1996) but it does not necessarily reflect a commitment to or belief in any particular theory of action elaborated in the scientific disciplines. In fact, the purpose of SIENA in this matter is to assist substantive researchers in further developing their theories of action by e.g. exploring the relative importance of individual, contextual, and social factors in network change. The second, and related, point is that, like other generalized regression models, SIENA does not by itself solve all causal questions. When inferring causality from model results, one has to face difficulties very similar to those with other statistical methods; see, e.g., Lomi et al. (2011) and Goldthorpe (2001). In any case, causal interpretations should be backed by further results from the discipline the explanations originate in. However, Stochastic Actor-Oriented Models do allow research to profit from a longitudinal design – therefore, they may be helpful in tackling some issues related to causality, like the selection-influence problem (Steglich et al., 2010; Lomi et al., 2011).

So far, we have mostly talked about SIENA as a tool to analyze the evolution of a single network. However, there are different variants of Stochastic Actor-Oriented Models that can be applied to more complex data structures. The availability of these options depends on the research question and the quantity and type of data one has. In this section, we briefly discuss the currently implemented model types, which will help researchers determine what kind of analyses they are able to carry out with Stochastic Actor-Oriented Models given the data at hand.
A minimal dataset suitable for analysis with SIENA consists of two observations of a single network defined on the same set of nodes. In this case, one is able to test how the structure of the network contributes to its own evolution. However, depending on the data available, further modeling options may be applicable. Currently, the implemented Stochastic Actor-Oriented Models are suitable for the analysis of
	•	1. the evolution of a directed or undirected one-mode network (e.g., friendships in a classroom) (Snijders, 2001);
	•	2. the evolution of a two-mode network (e.g., club memberships in a classroom: the first mode is constituted by the students, the second mode by the clubs) (Koskinen and Edling, 2012);
	•	3. the evolution of an individual behavior (e.g., smoking), and
	•	4. the co-evolution of one-mode networks, two-mode networks and individual behaviors (e.g., the joint evolution friendship and smoking; or of friendship and club member- ship) (Steglich et al., 2010; Snijders et al., 2013).
In all these cases, the data can also include covariates: observed variables that influence the dynamics, but of which the values are not themselves modeled.
In the first two cases, one can assess with SIENA the ways and the extent to which changes in a given one- or two-mode network depend on the network structure itself and on covariates. The third option, modeling changes in an individual behavior on its own, without reference to its embeddedness in a network, is rarely used. For this type of data numerous alternative longitudinal modeling techniques exist.
Accordingly, the fourth model type has been becoming widely used. Analyzing the joint evolution of networks and behavior allows researchers to address questions related to selection and influence processes, for example, whether smokers tend to become friends with each other or friends tend to become similar in their smoking habits. The strength of the SIENA co-evolution models is that one can simultaneously take into account the impact of network structure on network evolution, the actual level of a behavior on be- havior change, the network structure on behavior change, and the actual level of behavior on network evolution. Besides network and behavior co-evolution, this class of Stochastic Actor-Oriented Models also allow for the joint analysis of multiple networks (e.g. friend- ship and advice, friendship and dislike, or all three of them), and the analysis of ordered multiple networks (where the presence of a tie in one network presumes the existence of a tie in the other network, like in the case of friendships and best friend relations).


Now that we have discussed some core features of Stochastic Actor-Oriented Models and introduced the different implemented model types, we turn our attention, still just pre- senting an outline, to data types and the specification of a model. In general, the number of waves must be at least two in order to analyze a data set with Stochastic Actor-Oriented Models. In case of modeling evolution across more than two observations in time, esti- mated parameter values are assumed to be equal in all periods (unless time heterogeneity is specifically represented by changing parameters – see Section 5.9 for further details).
This section focuses on three related topics: the type of network and behavioral data SIENA works with, the meaning of explanatory variables, or so called effects, in Stochastic Actor-Oriented Models, and the different dependent variables with which SIENA captures network and behavior evolution.

Network data
Stochastic Actor-Oriented Models operate on binary networks, that is, on relations on a given set of actors, where tie variables between actors have two states: existent (1) or non-existent (0). Weighted networks are not allowed, but as mentioned above, it is possi- ble to define multiple networks representing discrete levels of relationships. It is possible to specify that some ties in the network are impossible (”structural zeros”) or necessary (“structural ones”) (see Section 4.3.1 for more details). For the network evolution, Stochas- tic Actor-Oriented Models how ties are being created, maintained or terminated by actors.

Behavioral data
Behavioral variables in Stochastic Actor-Oriented Models can be thought of as indi- cating the presence or intensity of a behavior. For example, behavioral data can represent whether an actor is a smoker or not, as well as a number of ordered categories express- ing the number of cigarettes usually smoked. The term “behavior” should not be taken literally here, it is possible to model changes in attitudes or other actor attributes. In the models, behavioral variables can be binary or ordinal discrete (the extension for con- tinuous behavioral data is currently being developed). The number of categories should be small (mostly 2 to 5; larger ranges are possible). In the case of behaviors, Stochastic Actor-Oriented Models express how actors increase, decrease, or maintain the level of their behavior.
A special case of the fourth type is the diffusion of innovations in dynamic networks (Greenan, 2015): here the behavior variable representing having adopted the innovation is binary, coded 0 or 1, and once an actor has the value 1 s/he is stuck with it. The only possible transitions are 0 ⇒ 1, representing that the actor adopts the innovation. See Section 12.2.4.

Covariates
In every model type, it is possible to define and use covariates, which are variables that are exogenous in the sense that their values are not modeled, but used to explain network or behavior change. Covariates can be dummy variables (e.g., sex) or continu- ous (e.g., attitudes or age). Also, they may have constant values across all observations or their value may change across time periods – this is the distinction between constant and varying covariates (e.g., sex and salary). Finally, there are individual (monadic) and dyadic covariates that refer, respectively, to characteristics of individual actors (e.g., sex) and to attributes of pairs of actors (e.g., living in the same neighborhood or kinship).

Missing data and composition change
Stochastic Actor-Oriented Models distinguish between two types of missing values: ab- sence of actors from the network and random missingness. The first case refers to changing composition: it is possible to specify that some actors leave or join the network between two observations (during the simulation process). This then applies to all dependent variables (networks, behaviors) simultaneously (see Section 4.3.3 for more details). In the second case, missing values are treated as randomly missing (see Section 4.3.2 for more de- tails). Stochastic Actor-Oriented Models can deal with some, but not too much, randomly missing data (as a rule of thumb, more than 20% is considered to be too much). With too many missing values, the simulation can become unstable, and also the estimated param- eters may not be substantively reliable anymore. And of course, missing data are likely to are caused by processes that are not totally random, and therefore risk to bias the resuls.

Explanatory variables: the effects
When defining Stochastic Actor-Oriented Models, we have to specify the exact ways in which current network structure or covariates may affect network or behavior change. This is defined by combinations of configurations (or situations) which are called “effects” in Stochastic Actor-Oriented Models. Effects can be treated as the explanatory variables of the models. Effects can be structural (depending on the network structure itself, also called endogenous), or covariate-related; also various combinations between structure and covariates are possible. Some examples for effects:
	•	structural effects: reciprocity, transitivity;
	•	covariate effects: sex of the tie sender, sex of the receiver, same sex, similarity in salary;
	•	combinations: average level of smoking of friends, interaction between sex of the sender and reciprocity.

Dependent variables: network evaluation, creation and endowment functions
As we discussed earlier, SIENA is capable of analyzing and modeling the evolution of networks and behavior, jointly or separately. Consequently, a model may have more than one dependent variable. Here we introduce the ways network and behavior dependent variables can be defined in Stochastic Actor-Oriented Models. We start with network evolution.
Given two observations of a binary network, a single network tie variable can follow four patterns, as shown in Table 1. In Stochastic Actor-Oriented Models, however, tie change can be defined in three ways: we can model the creation of previously not exist- ing ties (creation), the maintenance of existing ties (endowment), or the presence of ties regardless of whether they were newly created or maintained (evaluation). These are the three possible values of the change in tie variables, constituting the dependent variables of the network evolution model. The effects model the odds (more precisely: they are components of the linear predictor for the log-odds) for the creation, maintenance or presence of network ties. Table 2 helps to imagine what the odds refer to in each case: we compare the probability of green cases to that of blue cases.

[Table 1]
￼

[Table 2]
￼

According to this distinction, network evolution may be modeled in SIENA by three functions: the evaluation, creation and endowment functions. Effects can appear as com- ponents of one or two of these functions in a single model, but never in all three (this would lead to perfect collinearity). Using only the evaluation effect assumes that the cre- ation and endowment effects are equal (and equal to the evaluation effect). The estimated parameters for each effect should be interpreted as log-odds ratios. From a practical point of view, it is meaningful to start modeling with evaluation effects, unless one has a clear idea about how tie creation and endowment may be different in the analyzed data set. Separating the contribution of an effect into two functions requires more of the data, and if a given effect is similarly strong for the creation and maintenance of ties the statisti- cal power will decrease by this split. For these reasons, most SIENA studies limit their attention to evaluation effects. However, if there is enough data, the distinction between creation and maintenance of ties can produce powerful insights (e.g., Cheadle et al., 2013).

Dependent variables: behavior evaluation, creation and endowment functions
The distinction between the different behavior evolution functions follows a logic sim- ilar to the case of network evolution. The three possibilities for change in behavior are increasing or decreasing the level of behavior by one unit, or maintaining its actual level. In case of the evaluation function, the model does not distinguish between upward and downward changes, only looks at the resulting level of behavior. By using the creation and endowment functions, we can obtain separate parameters (and assess the different impact) of effects for the increase and the decrease of behavior.

SIENA estimates parameters by the function siena07(), using the following procedure:
	•	1. Certain statistics are used that reflect the parameter values;
	⁃	the finally obtained parameters should be such that the expected values of the statis- tics are equal to the observed values.
	⁃	Expected values are approximated as the averages over a lot of simulated networks. Observed values are calculated from the data set. These are also called the target values.
	•	2. To find these parameter values, an iterative stochastic simulation algorithm is ap- plied. This works as follows:
	⁃	(a) In Phase 1, the sensitivity of the statistics to the parameters is roughly deter- mined.
	⁃	(b) In Phase 2, provisional parameter values are updated iteratively:
	⁃	this is done by simulating a network according to the provisional parameter values, calculating the statistics and the deviations between these simulated statistics and the target values, and making a little change (the ‘update’) in the parameter values that hopefully goes into the right direction. A lot of such updating steps are taken, each using the parameter that was produced in the preceding step.
	⁃	(Only a ‘hopefully’ good update is possible, because the simulated network is only a random draw from the distribution of networks, and not the expected value itself.)
	⁃	(c) In Phase 3, the final result of Phase 2 is used, and it is checked if the average statistics of many simulated networks are indeed close to the target values. 
	⁃	This is reflected in the so-called t statistics for deviations from targets. If some of these are too high (a threshold of 0.1 is used for the absolute value), the estimation must be repeated. Standard errors for the parameters are also estimated in this phase.
	⁃	If the estimation has to be repeated, this can be done by employing the argu- ment prevAns in the call of siena07(). See the help page for siena07().


• Checking for time heterogeneity (Sections 5.9 and 8.6) 
• Goodness of fit (Section 5.11)
• Meta-analysis of SIENA results (Section 11.2)
• Simulation without estimation (Section 9)

This and the next section give an overview of steps one needs to go through from installing R to running models in RSiena. Installing needs to be done only once (but should be repeated when next versions of the software appear).
	•	1. Install R.
	⁃	This can be done from http://cran.r-project.org/ .
	⁃	Many users prefer some kind of additional environment, such as RStudio, or the combination of Notepad++ with NppToR.
	•	2. Install the package RSiena or RSienaTest, with dependencies. The other packages used are tcltk, network, codetools, lattice, MASS, parallel, xtable, and tools. For goodness of fit testing it will be useful also to install sna and igraph. You can just install RSiena and the other packages in the regular way from CRAN. However, it is advisable to have the latest version of RSiena or RSienaTest from R- Forge or the SIENA website. You can go to http://r-forge.r-project.org/R/?group_id=461 or to http://www.stats.ox.ac.uk/~snijders/siena/siena_downloads.htm and there download the appropriate version of the package appropriate for your operation system (Windows, Mac, Unix). Installation can be done in various ways — by the function install.packages() in R, via the drop-down menu in the R console, or in command mode which for Mac is the ‘terminal’. If a binary file is available (.zip for Windows, .tgz for Mac), then using the binary is recommended. Installation from binary is much faster than installation from source.
	•	Installation from the R-Forge repository can be done as follows. In these commands, RSienaTest can be replaced by RSiena.
	⁃	for Windows:
	⁃	install.packages("RSienaTest", repos="http://R-Forge.R-project.org")
	⁃	for Mac the binary file code is not available on R-Forge, but the source code may also work:
	⁃	install.packages("RSienaTest", repos="http://R-Forge.R-project.org", type = "source")
	⁃	If this does not work, try one of the following methods.
	⁃	Installation from a downloaded file can be done as follows, assuming the root name of the file is RSienaTest 1.1-282, and filling in the correct path name. It will be convenient to first navigate to the directory containing the RSiena binary or source file so that this is the current directory. Then the pathname consists only of the filename.
	•	In R from binary:
	⁃	for Windows:
	⁃	install.packages("pathname to RSienaTest 1.1-282.zip", repos = NULL, type="binary")
	⁃	for Mac:
	⁃	install.packages("pathname to RSienaTest 1.1-282.tgz", repos = NULL, type="binary")
	•	In R from source:
	⁃	install.packages("RSienaTest 1.1-282.tar.gz", repos = NULL, type="source")
	•	In command.com or in batch mode (Windows) from binary: 
	⁃	R CMD INSTALL RSienaTest 1.1-282.zip
	•	In the terminal (Mac) from binary:
	⁃	R CMD INSTALL RSienaTest 1.1-282.tgz
	•	In command.com or in batch mode (Windows) or in the terminal (Mac) from source:
	⁃	R CMD INSTALL RSienaTest 1.1-282.tar.gz
	•	In drop-down menu in R:
	⁃	for Windows: go to Packages → Install package(s) from local zip file 
	⁃	for Mac: go to Packages & Data → Package Installer
	•	In RStudio:
	⁃	go to Tools → Install packages → Install From: Package archive file (zip; tar.gz)


	•	1. Load data (networks, behavior, covariates) into R (see Section 4.1):
	⁃	(a) Network data should be in objects of class matrix or sparse matrix (edgelist);
	⁃	(b) Behavioral data should be in objects of class matrix;
	⁃	(c) Individual constant covariates should be in objects of class vector or should be in columns or rows of a matrix;
	⁃	(d) Individual varying covariates should be in objects of class matrix;
	⁃	(e) Dyadic covariates should be in objects of class matrix.
	•	2. All missing data should be set to NA (see Section 4.3.2).
	•	3. Check whether your data objects meet the following criteria:
	⁃	(a) Each object contains the same nodes/actors;
	⁃	(b) Nodes are in the same order in each object;
	⁃	(c) Nodes are in the same order in rows and columns of matrix objects (in case of one-mode networks)2.
	⁃	If a two-mode network is studied, then of course there will be two node sets.
	•	4. Create SIENA objects for each data object using the appropriate functions (see Section 4.1):
	⁃	(a) sienaDependent() for networks and behavior variables;
	⁃	(b) only for two-mode networks, sienaNodeSet() for defining nodesets;
	⁃	(c) coCovar() and varCovar() for constant and changing/varying individual covari- ates respectively;
	⁃	(d) coDyadCovar() and varDyadCovar() for constant and changing/varying dyadic covariates respectively;
	⁃	(e) In case of two-mode networks, for each object it should be specified which nodeset it is defined on, using the nodeSets argument in the above functions.
	•	5. Create a SIENA data object containing all the SIENA objects specified above using the function sienaDataCreate() (see Section 4.1).
	•	6. Use getEffects() to create an effects object. This already gives a very simple model specification containing the outdegree and a reciprocity effects (see Section 5.2 - for two-mode networks see Section 5.3).
	•	7. Use sienaAlgorithmCreate() to create an algorithm object (see Section 5).
	•	8. Use print01Report() to produce an output file presenting some descriptive statistics for the objects included in the model.
	•	9. Use functions includeEffects(), setEffect() and includeInteraction() to further specify the model (see Sections 5.2 – 5.6).
	•	10. Use siena07() to run the estimation procedure.3
	•	11. Basic output is written to a log file in the actual working directory. The filename is the project name specified in the sienaAlgorithmCreate() function. Results can also be inspected in R using various functions.

The following scripts on the RSiena website go through the steps outlined in the previous
section, providing additional details and options:
	•	basicRSiena.r: a minimal example of a basic sequence of commands for estimating a
	•	model by function siena07() of RSiena.
	•	Rscript01DataFormat.R: gives a brief overview of R functions and data formats that
	•	are essential for using RSiena.
	•	Rscript02SienaVariableFormat.R: shows how to prepare data for a SIENA analysis,
	•	including the creation of RSiena objects; and how to specify effects for RSiena models.
	•	Rscript03SienaRunModel.R: shows how to carry out the estimation and look at the
	•	results;
	•	Rscript04SienaBehaviour.R:illustrates how to specify models for dynamics of networks and behaviour.
The website contains a lot of other scripts illustrating other functionalities of RSiena.




1. Look at the start of the output file obtained from print01Report() for general data description (degrees, etc.), to check your data input and get a general overview of the data set.

In this file, there is a section “Change in networks” which contains some basic descriptives. Some of these refer to the periods: these are the combinations of two successive waves. For example, a two-wave data set has one period, and a three- wave data sets has periods 1 ⇒ 2 and 2 ⇒ 3. The Distance mentioned there is the Hamming distance between successively observed networks, i.e., the number of tie variables that differ. The Jaccard index is the Jaccard distance between the successive networks:

[Equation]
￼

where Nhk is the number of tie variables with value h in one wave and value k in the next wave. The Jaccard index is a measure for stability; see Snijders et al. (2010b). Both for the Hamming distance and the Jaccard index, only those cells in the adjacency matrix are counted that have available data in the wave at the start and the wave at the end of the period concerned.
If Jaccard indices are very low while the average degree is not strongly increasing, this indicates that the turnover in the network may be too high to consider the data as an evolving network, and perhaps the SIENA method is not suitable for the data set. Jaccard values of .3 and higher are good; lower than .2 indicates that there might be difficulties in estimation; lower than .1 is quite low indeed. Using the SIENA method for two waves with an extremely low Jaccard index and average degrees that remain more or less constant will mean that the first wave hardly plays a role in the results, and for non-conditional estimation it will be close to treating the second wave as a sample from the stationary distribution of the network dynamics.
If Jaccard indices are low because the network is mainly increasing (creation of new ties) or decreasing (termination of ties), this is no problem for the SIENA method.

2. When parameters have been estimated, first look at the t ratios for deviations from targets. We say that the algorithm has converged if they are all smaller than 0.1 in absolute value, and that it has nearly converged if they are all smaller than 0.15. Results obtained for non-converged estimation runs may be misleading. (Very small deviations from these values are of course immaterial.) See Section 6.1.2.

3. In rare circumstances, when the data set leads to instability of the algorithm, the following may be of use. The Initial value of the gain parameter determines the step sizes in the parameter updates in the iterative algorithm. This is the parameter called firstg in function sienaAlgorithmCreate. A too low value implies that it takes very long to attain a reasonable parameter estimate when starting from an initial parameter value that is far from the ‘true’ parameter estimate. A too high value implies that the algorithm will be unstable, and may be thrown off course into a region of unreasonable (e.g., hopelessly large) parameter values. It usually is unnecessary to change this, but in some cases it may be useful.

4. If all this is to no avail, then the conclusion may be that the model specification is incorrect for the given data set.

5. Further help in interpreting output is in Section 6.5 of this manual.

For methodological help, consult the tutorial Snijders et al. (2010b) or this manual. The website, http://www.stats.ox.ac.uk/~snijders/siena/ , contains various further publica- tions (also in other languages than English) that may be helpful, as well as example scripts. There is a users’ group for SIENA to exchange information and seek technical advice; the address is http://groups.yahoo.com/groups/stocnet/ .

For technical problems running RSiena, follow the following points.

Help pages 
Study the R help page for the function you are using and that seems to give
the problems. This manual complements the help pages, but does not replace them!

Check your version of RSiena 
The ‘News’ page of the SIENA website gives information about new versions of RSiena. Details of the latest version available can be found at http://r-forge.r-project.org/R/?group_id=461. The version is identified by a version number (e.g. 1.1-283) and an R-Forge revision number. You can find both numbers of your current installed version by opening R , and typing packageDescription("RSiena"). The version is near the top, the revision number near the end. Both are also displayed at the start of SIENA output files produced by print01Report().

Check your version of R 
When there is a new version or revision of RSiena it will only be available to you automatically if you are running the most recent major version of R. (You can force an installation if necessary by downloading the tarball or binary and installing from that, but it is better to update your R.)

Check both repositories 
We have two repositories in use for RSiena: CRAN and R- Forge. The latest version will always be available from R-Forge. (Frequent updates are discouraged on CRAN, so bug-fixes are likely to appear first on R-Forge.)

Installation 
When using the repository at R-Forge, install the package rather than up- dating it. Then check the version and revision numbers.

Users’ group 
Consult the archives of the Users’ Group mentioned above, or post a mes- sage to the Users’ Group. In your message, please tell which operating system, which version of R, and which version of RSiena you are using.

R-Forge help list 
For technical questions about the RSiena code (as distinct from the methodology), you can send an email to rsiena-help@lists.r-forge.r-project.org, or post in the help forum for RSiena in R-Forge. You need to be a registered member of R-Forge (and possibly of RSiena) to post to a forum, but anyone can send emails (at present!). In your message, please tell us which operating system, which version of R, and which version of RSiena you are using.
