

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE, warning = FALSE, message = FALSE)

# https://dktanwar.github.io/CV/ds.html
# https://fontawesome.com/v4.7.0/icons/
# https://github.com/jienagu/Jiena_McLellan_CV


DOI_link <- function(doi, sci_hub = TRUE){
  host <- if (sci_hub) "sci-hub.se" else "doi.org"
  
  glue::glue("[DOI:{doi}](https://{host}/{doi})")
}

count_students <- readxl::read_xlsx("count_students.xlsx")

n_students <- count_students |> 
  dplyr::summarise(
    n = sum(מספר), 
    .by = תואר
  ) |> 
  dplyr::pull(n, name = תואר)

n_courses <- count_students |> 
  # dplyr::group_by(מוסד) |> 
  dplyr::distinct(קורס) |> 
  dplyr::count() |> 
  dplyr::pull() |> 
  sum()

dozen_courses <- floor(n_courses / 12)
dozen_courses_txt <- ifelse(dozen_courses == 1, "a", insight::format_number(dozen_courses))

years_teaching <- difftime(Sys.Date(), as.Date("2015-09-30")) / lubridate::dyears()
```

Aside
================================================================================

<center>
<img src="headshots/JSF_9523.png" style="width:100%; border-radius: 50%;"/>
</center>

Contact Info {#contact}
--------------------------------------------------------------------------------

<i class="fa fa-envelope"></i> mattansb@msbstats.info  
<!-- <i class="fa fa-phone"></i> +972 50-837-1566   -->
<!-- <i class="fa fa-home"></i> 5 Dunash st., apt 27, Ramat-Gan   -->
<i class="fa fa-globe"></i> [Home Page](https://home.msbstats.info) | 
<i class="fa fa-rss"></i> [Blog](https://blog.msbstats.info/)  
<i class="fa fa-brands fa-bluesky"></i> [BlueSky](https://bsky.app/profile/mattansb.bsky.social) |
<i class="fa fa-brands fa-linkedin"></i> [LinkedIn](https://www.linkedin.com/in/mattan-s-ben-shachar)  
<i class="fa fa-brands fa-github"></i> [GitHub](https://github.com/mattansb)  
<i class="fa fa-brands fa-orcid"></i> [ORCID](https://orcid.org/0000-0002-4287-4801) |
<i class="fa fa-brands fa-google-scholar"></i> [G-Scholar](https://scholar.google.co.il/citations?user=Vrbic5QAAAAJ)  

Languages {#languages}
--------------------------------------------------------------------------------

English - native language  
Hebrew - native language  

Technical Skills
--------------------------------------------------------------------------------

**Programming:** R, Matlab, SQL, Stan, Python, Git(Hub) (See my [github profile](https://github.com/mattansb)).  

**Documentation:** Office Suites, (R)Markdown/Quatro, Google Docs/Sheets.  

Disclaimer {#disclaimer}
--------------------------------------------------------------------------------

See [short resume](https://mattansb.github.io/CV/resume).

Last updated on `r Sys.Date()`.

Main
================================================================================

Mattan S. Ben-Shachar, PhD {#title}
--------------------------------------------------------------------------------

As a freelance [research analyst and statistical consultant](#stats-analyst) specializing in the social sciences, I offer comprehensive guidance throughout all stages of the research process, having provided support and consultation in these areas to numerous researchers, across several institutions. Holding a [PhD in neurocognitive psychology](#education) from Ben-Gurion University, I am deeply rooted in theoretical and applied statistics, and am committed to the principles of data analysis, inferential statistics, and reproducible research.

Concurrently, I am a [statistics educator](#teaching) at both Ben-Gurion University and Tel-Aviv University, teaching bachelor- and graduate-level statistics, research methods, and R programming, ranging from introductory statistics to applied machine learning. I supplement my goal of making statistics more accessible as an active [`R` developer](#R-dev), creating tools that aid in understanding statistical models.

Education {data-icon=graduation-cap data-concise=true #education}
--------------------------------------------------------------------------------

### Ph.D. in Psychology

Ben-Gurion University

Be'er Sheva, Israel

2023

**Title:** *The Electrophysiological Basis of Processing Speed*  
([Download dissertation (pdf) <i class="fa fa-download"></i>](https://drive.google.com/uc?export=download&id=10NbOvivBrRQiCiioiR4g4X3xk3Msp0G_) | [Audio overview <i class="fa fa-circle-play"></i>](https://drive.google.com/file/d/14u6hj1nqUKCrQQEhsjl_LSnvWecxv0aj/view))  
**Supervisor:** Prof. Andrea Berger  

<!-- **Courses:**   -->

<!-- ::: concise -->
<!--  - Advanced EEG Methods -->
<!--  - Hierarchical Linear Models -->
<!--  - Linear Algebra for Neuroscience -->
<!--  - Machine Learning -->
<!-- ::: -->

### M.A. in Experimental Cognitive Psychology

Ben-Gurion University

Be'er Sheva, Israel

2017

**Title:** *Electrophysiological Evidence for the Role of Processing Speed and Attentional Control in Visual Recognition Tasks.*  
**Supervisor:** Prof. Andrea Berger

### B.A. in Behavioral Sciences

Ben-Gurion University

Be'er Sheva, Israel

2015

Graduated *Magna Cum Laude*

<!-- ### Entrance Test for Advanced Degrees in Psychology (MITAM) -->

<!-- N/A -->

<!-- N/A -->

<!-- 2014 -->

<!-- Received 138 (92th percentile) -->

<!-- ### Psychometric Entrance Test (PET) -->

<!-- N/A -->

<!-- N/A -->

<!-- 2011 -->

<!-- Received 727 (94th percentile) -->

<!-- ### Israeli Matriculation Certificate (Te'udat Bagrut) -->

<!-- N/A -->

<!-- N/A -->

<!-- 2008 -->

<!-- ::: concise -->
<!-- - 5-unit level in English -->
<!-- - 4-unit level in Mathematics -->
<!-- - 5-unit elective in geography -->
<!-- ::: -->

Professional Experience {data-icon=laptop}
--------------------------------------------------------------------------------

### Statistical Consultant & Research Analyst {#stats-analyst}

N/A

N/A

Since 2016

I am deeply rooted in theoretical and applied statistics, and am committed to the principles of data analysis, inferential statistics, and reproducible research, while also mindful of the practical needs of researchers and academics. I provide guidance throughout all stages of the research process and decision-guided statistical analyses. I specialize in the following methods:

::: concise
- Generalized linear models (regression, AN(C)OVA)  
- Generalized mixed effects models (HLM, LMM)   
- Missing data analysis and treatment  
- Structural equation modeling (SEM)  
- Factor analysis and clustering
- Bayesian modeling and inference  
- Nonlinear models (NLM)  
:::

*For more info and client testimonials, see [my home page](https://home.msbstats.info/stats-consultation).*

### Statistics Lecturer

N/A

N/A

Since 2015

My teaching and instructing are focused on undergraduate- and graduate-level statistics, research methods, and R programming. Over the last `r scales::comma(years_teaching)` years I have taught over `r scales::comma(n_students["1"], 10)` undergraduate students and over `r scales::comma(n_students["2"], 10)` graduate students across over `r dozen_courses_txt` dozen courses. See [*Teaching Experience*](#teaching) section.

### R Developer {#R-dev}

N/A

N/A

Since 2016

Core developer of the [*easystats* eco-system of packages](https://easystats.github.io/easystats/) --
an [award-winning](#awards) collection of R packages,
which aims to provide a unifying and consistent framework to tame, discipline and harness the scary R statistics and their pesky models (e.g., [*parameters*](https://cran.r-project.org/package=parameters), [*performance*](https://cran.r-project.org/package=performance), and more).

- Developer and maintainer of [***effectsize***](https://easystats.github.io/effectsize/) for 
estimating indices of effect size and standardized parameters.  
- Developer of [***bayestestR***](https://easystats.github.io/bayestestR/), a package for describing and testing posterior distributions and Bayesian models.

*See my full [github profile](https://github.com/mattansb).*

:::aside
List of additional packages I have contributed to: [`afex`](https://cran.r-project.org/package=afex), [`brms`](https://cran.r-project.org/package=brms), [`ggeffects`](https://cran.r-project.org/package=ggeffects), [`semTools`](https://cran.r-project.org/package=semTools).
:::


### Neurocognitive Researcher

N/A

N/A

2015 - 2022

My research focused on differential cognitive psychology using behavioral and physiological methods, occasionally collaborating with international research groups. I have experience designing computerized tasks that evoke individual differences in an array of cognitive abilities. I have also led and managed research projects, including teams of graduate students and research assistants.

***Neurophysiological Signal Processing***: I have collected and analyzed multi-channel electroencephalography (EEG) data using `eeglab`. My experience with signal pre-processing includes noise "cleaning" methods as well as dimension reduction tools (PCA, ICA); I specialize in latency measurement of event-related potentials (ERPs).

- Developed Matlab toolboxes for artifact removal ([TBT](https://github.com/mattansb/TBT), an eeglab plugin) and for plotting and extracting measurements for processed EEG/ERP/wavelet data ([EPP-TB](https://github.com/mattansb/EPP-TB)).
- Instructed workshops for pre-processing of experimental EEG.

### MITAM Exam Developer

National Institute for Testing and Evaluation

N/A

Since 2020

I am a developer and reviewer of the MITAM exam (entrance test for advanced degrees in psychology - equivalent to the GRE).

<!-- ### Member of Editorial Board -->

<!-- N/A -->

<!-- N/A -->

<!-- N/A -->

<!-- - (2020 - Present) Review Editor for *Frontiers in Applied Mathematics and Statistics* and *Frontiers in Psychology*.   -->
<!-- - Ad hoc reviewer: *British Journal of Mathematical and Statistical Psychology*, *Cerebral Cortex*, *Frontiers in Psychology*, and *Advances in Methods and Practices in Psychological Science*. -->


<!-- ### Research Assistant -->

<!-- ERP Lab for Developmental Studies -->

<!-- Ben-Gurion University -->

<!-- 2013 - 2015 -->

<!-- ::: concise -->
<!-- - EEG data acquisition on preschool children. -->
<!-- - Behavioral game-like tasks with children. -->
<!-- ::: -->

<!-- ### Quality Assurance Manager -->

<!-- Groupon, Israel -->

<!-- N/A -->

<!-- 2012 - 2013 -->

<!-- ::: concise -->
<!-- - Established the quality assurance division. -->
<!-- - Examination of all daily deals.   -->
<!-- - Checked for compliance with consumer protection laws.   -->
<!-- ::: -->

<!-- Research Topics {data-icon=flask #topics} -->
<!-- -------------------------------------------------------------------------------- -->

<!-- ### Processing Speed -->

<!-- Ben-Gurion University -->

<!-- Be'er Sheva, Israel -->

<!-- N/A -->

<!-- Focusing on individual differences in processing speed and its relation to higher cognitive abilities, using indirect measures of processing speed, such as: sensitivity to implicit temporal information, ERP latency, and EEG phase synchronicity. -->

<!-- ### Fetal Alcohol Spectrum Disorder -->

<!-- University of Cape Town -->

<!-- Cape Town, South Africa -->

<!-- N/A -->

<!-- Research focused on the effects of prenatal alcohol exposure on the ability to detect mathematical errors in basic arithmetic equations in infancy and adolescence, using EEG/ERP paradigms. -->

<!-- *In collaboration with Andrea Berger, Michael Shmueli, Sandra Jacobson, and Joseph Jacobson* -->

<!-- ### Numerical Cognition -->

<!-- Ben-Gurion University -->

<!-- Be'er Sheva, Israel -->

<!-- N/A -->

<!-- Research automatic processing of quantities and numbers among adults and children, and the development of numerical cognition before formal mathematical education, using both behavioral and electro-physiological (EEG) measures. -->

<!-- *In collaboration with Andrea Berger, Shachar Hochman, Avishai Henik, and Minna Hannula-Sormunen.* -->

\pagebreak

Teaching Experience {data-icon=chalkboard-teacher #teaching}
--------------------------------------------------------------------------------

### Lecturer & Teaching Fellow

N/A

N/A

Since 2018

:::aside
*\* Denotes upcoming courses.*
:::

#### School of Psychological Sciences, Tel-Aviv University

Graduate level courses:  
- [Data Science Lab for Psychologists](https://github.com/mattansb/Machine-Learning-foR-Psychologists) (Annually, since 2023)  
- [Hierarchical Models](https://github.com/mattansb/Hierarchical-Linear-Models-foR-Psychologists) (Annually, since 2023)  


#### Department of Psychology, Ben-Gurion University

Graduate level courses:  
- [Hierarchical Linear Models](https://github.com/mattansb/Hierarchical-Linear-Models-foR-Psychologists) (Biannually, since 2022)  
- [Machine Learning for Psychologists](https://github.com/mattansb/Machine-Learning-foR-Psychologists) (Annually, since 2022)  
- Essential Data Science Skills (Annually, since 2022)  
- [Practical applications in R](https://github.com/mattansb/Advanced-Research-Methods-foR-Psychologists) (Fall 2019--2021)  
- [Structural equation modelling in R](https://github.com/mattansb/Structural-Equation-Modeling-foR-Psychologists) (Spring 2020--2021)  
- [Analysis of factorial designs in R](https://github.com/mattansb/Analysis-of-Factorial-Designs-foR-Psychologists) (Spring 2019)  
  
Under-graduate level courses:  
- Regression and Multi-Variables Analysis (Fall 2022--2023)  
- Experimental Psychology (Fall 2018)

#### Statistics and Data Program, Ben-Gurion University of the Negev

Under-graduate level courses:  
- Introduction to Data Science (Annually, since 2023)  
- Bayesian Statistics and Modeling (Annually, since 2023)  

#### School of Cognitive Sciences, Ben-Gurion University of the Negev

Under-graduate level courses:  
- Inferential Statistics for Cognitive Sciences (Fall 2022)  

### Workshops

N/A

N/A

N/A

- *Bayesian Statistics: So Much More Than Just the Bayes factor.* (2 days; Aug 2024)  
- [*Evaluating Evidence and Making Decisions using Bayesian Statistics*](https://mattansb.github.io/bayesian-evidence). Workshop at the The 8th Conference on Cognitive Research of the Israeli Society for Cognitive Psychology, Israel.  

Traveling workshops:

::: concise
- *Pre-Processing EEG Data* (12h; Oct-Nov 2020, Jan-Feb 2020)  
- *Intro to the R Programming Language* (7h; Jan 2021)  
- *Trends in Open Science* (2h; Nov 2019, May 2019, Dec 2018) 
- [*ANOVA and Contrasts in R*](https://github.com/mattansb/ANOVA-and-Contrasts-in-R) (2h; May 2018)  
:::
 
### Teaching Assistant & Instructor

Ben-Gurion University  

N/A

2015 - 2018

#### Department of Psychology, Ben-Gurion University

Under-graduate level courses:  
- Experimental Psychology (Fall 2017; Summer 2017)  
- Inferential Statistics (Spring 2017--2018)  
- Introduction to Statistics (Fall 2015)  


#### Department of Health Systems Management

Graduate level courses:  
- Research Seminar (*for Graduate Students*) (Fall 2016--2017)  
  
<!-- ### Mitam Instructor -->

<!-- Ofek Mitam -->

<!-- N/A -->

<!-- 2016 -->

<!-- MITAM Prep Course -->




<!-- Military Service {data-icon=fighter-jet} -->
<!-- -------------------------------------------------------------------------------- -->

<!-- ### Discharged with Honor -->

<!-- Israeli Air Force -->

<!-- N/A -->

<!-- 2011 -->

<!-- Staff Sgt. -->

<!-- ### Technical Translator -->

<!-- Depot 22, Israeli Air Force -->

<!-- N/A -->

<!-- 2008 - 2011 -->

<!-- ###  -->

<!-- Technical Studies School, Israeli Air Force -->

<!-- N/A -->

<!-- 2008 -->


Awards and Scholarships {data-icon=star-o #awards}
--------------------------------------------------------------------------------

### SIPS Mission Award

Society for Improving Psychological Science (SIPS)

N/A

2023

[Awarded to the `easystats` project](http://improvingpsych.org/mission/awards/) for improving the training and research practices of psychological scientists.

### Full academic scholarship for graduate studies

Humanities and Social Sci Faculty, Ben-Gurion University

Be'er Sheva, Israel

2015 - 2022

### Negev Mid-Way Scholarship

Kreitman School of Advanced Graduate Studies

Be'er Sheva, Israel

2020 - 2021

### SIPS Commendation

Society for Improving Psychological Science (SIPS)

N/A

2020

[Awarded to the `bayestestR` package](http://improvingpsych.org/mission/awards/) for improving the training and research practices of psychological scientists.

### M.H.R Publication Award

Humanities and Social Sci Faculty, Ben-Gurion University

Be'er Sheva, Israel

2020

For *Ben-Shachar et al. (2020). `r DOI_link("10.1111/acer.14244")`*

### Erasmus+ EU Travel Grant

EU programme for education, training, youth and sport in Europe

N/A

2018

### Radboud Summer School Scholarship

Radboud University

Nijmegen, Netherlands

2018

:::aside
Studied Linear Algebra for Neuroscience with Prof. Mike X. Cohen
:::

### Award for Academic Distinction

Dep. of Sociology and Anthropology, Ben-Gurion University

Be'er Sheva, Israel

2014

\pagebreak
