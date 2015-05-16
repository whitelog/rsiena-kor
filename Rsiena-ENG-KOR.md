Manual for RSiena
Ruth M. Ripley Tom A.B. Snijders Zso ́fia Boda Andra ́s Vo ̈r ̈os Paulina Preciado
University of Oxford: Department of Statistics; Nuffield College February 17, 2015
RSiena 메뉴얼
Ruth M. Ripley Tom A.B. Snijders Zso ́fia Boda Andra ́s Vo ̈r ̈os Paulina Preciado
옥스포드 유니버시티: 통계학과 누필드 칼리지 2월 17일, 2015년 버전

Abstract
초록
SIENA (for Simulation Investigation for Empirical Network Analysis) is a computer pro- gram that carries out the statistical estimation of models for the evolution of social networks according to the dynamic actor-oriented model of Snijders (2001, 2005), Snijders et al. (2007), and Snijders et al. (2010a). 
SIENA (경험적 네트워크 분석을 위한 시뮬레이션 분석) 는 Snijders (2001, 2005), Snijders et al. (2007), and Snijders et al. (2010a)의 연구결과인 역동적 행위자기반 모델을 통해 사회연결망의 진화를 통계적 추론을 수행하는 프로그램이다.

This is the manual for RSiena, a contributed package to the statistical system R. 
이 문서는 통계시스템인 R에서 사용하는 RSiena 패키지를 위한 메뉴얼이다.

It complements, but does not replace the help pages for the RSiena functions! It also contains contributions written earlier, for the manual for SIENA version 3, by Mark Huisman, Michael Schweinberger, and Christian Steglich.
이 메뉴얼은 권장되나 RSiena기능 도움페이지를 대체하는것은 아니다. 이 문서에는 Mark Huisman, Michael Schweinberger, and Christian Steglich 가 기여한 초기 SIENA 버전3의 내용을 포함한다.

This manual is frequently updated, mostly only in a minor way. This version was renewed for RSiena version 1.1-283.
이 메뉴얼은 수시로 업데이트 되며 수시업데이트는 주로 마이너 업데이트가 주를 이룬다. 이 메뉴얼은 RSiena 버전 1.1-283을 기반으로 작성되었다.

Contents
목차
	•	General information 6 
	•	일반정보

Part I. Introduction 8
파트1. 소개
	•	1. Minimal Intro
	•	1. 소개
	⁃	1.1 Giving references..................................... 8
	⁃	1.1 참조문서와 항목들
	•	2. Getting started with SIENA 9
	•	2. SIENA 시작하기
	⁃	2.1 The logic of Stochastic Actor-Oriented Models .................... 9
	⁃	확률적 행위자 기반 모델의 로직
	⁃	2.1.1 Types of Stochastic Actor-Oriented Models . . . . . . . . . . . . . . . . . . 10
	⁃	확률적 행위자 기반 모델의 형식
	⁃	2.1.2 Data, variables and effects............................ 11
	⁃	자료, 변수, 영향
	⁃	2.1.3 Outline of estimation procedure......................... 15
	⁃	추정과정개요
	⁃	2.1.4 Further useful options in RSiena ........................ 16
	⁃	유용한 RSiena 옵션들
	⁃	2.2 Installing R and SIENA ................................. 16
	⁃	R 과 SIENA 설치
	⁃	2.3 Using SIENA within R .................................. 17
	⁃	R에서 SIENA 사용하기
	⁃	2.4 Example R scripts for getting started.......................... 19
	⁃	시작을위한 R 스크립트 예제
	⁃	2.5 Steps for looking at results: Executing SIENA...................... 19
	⁃	SIENA 실행: SIENA 시작에서 결과까지 과정
	⁃	2.6 Getting help with problems ............................... 20
	⁃	문제에 대한 도움얻기


PartII Users’ Manual

	•	3. Steps of modeling 22
	•	모델링 과정
	•	4. Input data 23
	•	자료입력
	⁃	4.1 Data types ........................................ 23
	⁃	자료형식
	⁃	4.1.1 Network data................................... 23
	⁃	네트워크 자료
	⁃	4.1.2 Transformation between matrix and edge list formats . . . . . . . . . . . . 25
	⁃	행렬과 엣지리스트 형식간의 변환
	⁃	4.1.3 Behavioral data.................................. 26
	⁃	행위자료
	⁃	4.1.4 Individual covariates............................... 26
	⁃	개별 공변인
	⁃	4.1.5 Dyadic covariates................................. 27
	⁃	양자간 공변인
	⁃	4.2 Internal data treatment ................................. 28
	⁃	내부자료 처리
	⁃	4.2.1 Interactions and dyadic transformations of covariates . . . . . . . . . . . . . 28
	⁃	공변인의 상호작용과 양자간 변환
	⁃	4.2.2 Centering ..................................... 28
	⁃	센터링?
	⁃	4.2.3 Monotonic dependent variables ......................... 30
	⁃	단조? 종속 변수
	⁃	4.3 Further data specification options............................ 30 
	⁃	자료 명세 옵션들
	⁃	4.3.1 Structurally determined values .........................
	⁃	구조적으로 결정되는 변수들
	⁃	4.3.2 Missing data ................................... 32 
	⁃	결측데이터
	⁃	4.3.3 Composition change: joiners and leavers.................... 33
	⁃	구성요소의 변경 가입자들과 이탈자들 
	•	5. Model specification 35
	•	모델설정
	⁃	5.1 Definition of the model.................................. 35 
	⁃	모델의 정의
	⁃	5.1.1 Specification in SIENA ............................. 37 
	⁃	SIENA에서의 설정 
	⁃	5.1.2 Mathematical specification ........................... 38
	⁃	수학적 설정
	⁃	5.2 Important structural effects for network dynamics: one-mode networks.................................... 39
	⁃	네트워크 역동성에 대한 중요한 구조적 효과들 : one-mode 네트워크
	⁃	5.3 Important structural effects for network dynamics: two-mode networks.................................... 42
	⁃	네트워크 역동성에 대한 중요한 구조적 효과들 : two-mode 네트워크
	⁃	5.4 Effects for network dynamics associated with covariates . . . . . . . . . . . . . . . 43
	⁃	공변인과 연관된 네트워크 역동성에 대한 효과
	⁃	5.5 Cross-network effects for dynamics of multiple networks . . . . . . . . . . . . . . . 45
	⁃	다중네트워크의 역동성에 대한 교차네트워크 효과
	⁃	5.6 Effects on behavior evolution .............................. 46
	⁃	행동진화(변화?)에 대한 효과
	⁃	행동진화에 영향을 미치는 효과
	⁃	5.7 Model Type: non-directed networks .......................... 47
	⁃	모델형식 : 방향성없는 네트워크
	⁃	5.8 Additional interaction effects .............................. 48
	⁃	추가적 상효작용 효과
	⁃	5.8.1 Interaction effects for network dynamics.................... 49
	⁃	네트워크 역동성에 대한 상호작용 효과
	⁃	5.8.2 Interaction effects for behavior dynamics.................... 49
	⁃	행동 역동성에 대한 상호작용 효과
	⁃	5.9 Time heterogeneity in model parameters........................ 50
	⁃	모델 파라미터내 시간과 관련된 상이성
	⁃	5.10 Limiting the maximum outdegree............................ 51
	⁃	최대 out-degree 제한하기
	⁃	5.11 Goodness of fit with auxiliary statistics ........................ 52
	⁃	보조적 통계를 통한 모델 적합성
	⁃	5.11.1 Treatment of missing data and structural values in siena GOF . . . . . . . . 52
	⁃	결측데이터 처리와 Siena 모델적합성내 구조적 값
	⁃	결측데이터 처리와 Siena 모델적합성에 대한 구조적 변수값
	•	6 Estimation 54
	•	추정
	⁃	6.1 The estimation function siena07............................. 54 
	⁃	추정기능, siena07
	⁃	6.1.1 Initial Values ................................... 56 
	⁃	초기값
	⁃	6.1.2 Convergence Check................................ 57
	⁃	모델수렴확인
	⁃	6.2 What to do if there are convergence problems..................... 58 
	⁃	모델수렴에 문제가 있을때 해야할 것
	⁃	6.2.1 Pressing on .................................... 60
	⁃	그대로 진행하기
	⁃	6.3 Some important components of the siena Fit object . . . . . . . . . . . . . . . . . . 61
	⁃	
	⁃	6.4 Algorithm......................................... 62
	⁃	
	⁃	6.5 Output .......................................... 63 
	⁃	
	⁃	6.5.1 Convergence check ................................ 64 
	⁃	
	⁃	6.5.2 Parameter values and standard errors ..................... 64 
	⁃	
	⁃	6.5.3 Collinearity check ................................ 65
	⁃	
	⁃	6.6 Maximum Likelihood and Bayesian estimation .................... 66
	⁃	
	⁃	6.7 Other remarks about the estimation algorithm .................... 68
	⁃	
	⁃	6.7.1 Conditional and unconditional estimation ................... 68
	⁃	
	⁃	6.7.2 Fixing parameters ................................ 69
	⁃	
	⁃	6.7.3 Automatic fixing of parameters......................... 69
	⁃	
	⁃	6.7.4 Required changes from conditional to unconditional estimation . . . . . . . 69
	⁃	
	⁃	6.8 Using multiple processes................................. 70
	⁃	
	•	7 Standard errors 71 
	•	
	⁃	7.1 Multicollinearity ..................................... 71 
	⁃	
	⁃	7.2 Precision of the finite differences method........................ 72
	⁃	
	•	8 Tests 73
	•	
	⁃	8.1 Wald-type tests...................................... 73 
	⁃	
	⁃	8.1.1 Standard errors of linear combinations..................... 75
	⁃	
	⁃	8.2 Score-typetests...................................... 76
	⁃	
	⁃	8.3 Example: one-sided tests, two-sided tests, and one-step estimates . . . . . . . . . . 77 
	⁃	
	⁃	8.3.1 Multi-parametertests .............................. 78
	⁃	
	⁃	8.4 Alternative application: convergence problems..................... 79
	⁃	
	⁃	8.5 Testing differences between independent groups.................... 79
	⁃	
	⁃	8.6 Testing time heterogeneity in parameters ....................... 80
	⁃	
	•	9 Simulation 82 
	•	
	⁃	9.1 Accessing the generated networks............................ 83 
	⁃	
	⁃	9.2 Conditional and unconditional simulation ....................... 84
	⁃	
	•	10 Getting started 85 
	•	
	⁃	10.1 Modelchoice ....................................... 86
	⁃	
	•	11 Multilevel network analysis 87
	•	
	⁃	11.1 Multi-group Siena analysis................................ 88
	⁃	
	⁃	11.2 Meta-analysis of Siena results.............................. 89
	⁃	
	⁃	11.2.1 Meta-analysis directed at the mean and variance of the parameters . . . . . 90 
	⁃	
	⁃	11.2.2 Meta-analysis directed at testing the parameters . . . . . . . . . . . . . . . 92 
	⁃	
	⁃	11.2.3 Contrast between the two kinds of meta-analysis . . . . . . . . . . . . . . . 93
	⁃	
	⁃	11.3 Random coefficient multilevel Siena analysis...................... 93 
	⁃	
	⁃	11.3.1 Which data sets to use for siena Bayes ..................... 94 
	⁃	
	⁃	11.3.2 Models pecification................................ 95 
	⁃	
	⁃	11.3.3 How to enter your data in siena Bayes ..................... 95 
	⁃	
	⁃	11.3.4 How to choose the parameter settings for siena Bayes . . . . . . . . . . . . . 96 
	⁃	
	⁃	11.3.5 Prior distributions ................................ 96 
	⁃	
	⁃	11.3.6 Operation of sienaBayes()............................ 98 
	⁃	
	⁃	11.3.7 Assessing convergence .............................. 98 
	⁃	
	⁃	11.3.8 Interpreting results of sienaBayes........................ 98
	⁃	
	•	12 Formulas for effects 100 
	•	
	⁃	12.1 Networkevolution .................................... 100 
	⁃	
	⁃	12.1.1 Network evaluation function........................... 101 
	⁃	
	⁃	12.1.2 Multiple network effects ............................. 116 
	⁃	
	⁃	12.1.3 Network creation and endowment functions . . . . . . . . . . . . . . . . . . 123 
	⁃	
	⁃	12.1.4 Network rate function .............................. 124 
	⁃	
	⁃	12.2 Behavioral evolution ................................... 126 
	⁃	
	⁃	12.2.1 Behavioral evaluation function ......................... 126 
	⁃	
	⁃	12.2.2 Behavioral creation function........................... 134 
	⁃	
	⁃	12.2.3 Behavioral endowment function......................... 135 
	⁃	
	⁃	12.2.4 Behavioral rate function............................. 135
	⁃	
	•	13 Parameter interpretation 137 
	•	
	⁃	13.1 Networks ......................................... 137 
	⁃	
	⁃	13.2 Behavior.......................................... 138 
	⁃	
	⁃	13.3 Ego–alter selection tables ............................... 139 
	⁃	
	⁃	13.4 Ego–alter influence tables ............................... 145
	⁃	
	•	14 Error messages 149 
	•	
	⁃	14.1 During estimation .................................... 149 
	⁃	
	⁃	14.2 As result of a score-type test (including time test) . . . . . . . . . . . . . . . . . . 150 
	⁃	
	⁃	14.3 In sienaGOF ....................................... 150

Part III Programmers’ manual 152 

	•	15 Get the source code 152 
	•	
	•	16 Other tools you need 152 
	•	
	•	17 Building, installing and checking the package 153
	•	
	•	18 Understanding and adding an effect 154 
	•	
	⁃	18.1 Example: adding the truncated out-degree effect ................... 156 
	⁃	
	⁃	18.2 Notes for effects for two-mode networks ........................ 160
	⁃	
Back Matter

	•	A List of Functions in Order of Execution 161
	•	
	•	B Changes compared to earlier versions
	•	
	•	C References
	•	
