# Automating-Software-Regression-Testing-through-Log-Analysis-NLP_Statistical-Comparison
Automating Software Regression Testing through Log Analysis A Statistical Comparison Approach using NLP Techniques
### <span style="color:yellow">**Background & Context:**<span style="color:lime">

The research presents important findings for the field of software regression testing. It introduces a new method that uses Natural Language Processing (NLP) and statistical techniques to automate the testing process.

What's great about this method is that it can quickly find errors, make tests more accurate, and better use resources. Understanding log data from regression testing can be quite tricky. However, by using NLP, this research tackles that problem. It's like using a new lens to view and analyze the data more clearly. On top of that, the research uses statistical tests, like the t-test, f-test, and ANOVA.

These tests make the results more trustworthy and even provide visual ways to see the outcomes. Why is this research so impactful? Because it can change how we approach software regression testing. It promises to make the testing process faster, more effective, and helps testers make better decisions. This study is timely and useful because the software industry is looking for 10ways to automate regression testing. Plus, it adds value to the methods used to ensure software
is of high quality.

### <span style="color:yellow">**About the Data**<span style="color:lime">

Android, an open-source mobile operating system (https://www.android.com), widely adopted across smart devices, lacks public availability of logs for research. We contribute Android log files derived from smartphones equipped with extensively instrumented modules. These logs encapsulate two distinct issue types, each with over 10 duplicate issue logs. Yet, the intricate nature of Android's multi-threading system poses challenges in precisely identifying abnormal log points. This unique dataset offers valuable insights into Android system behaviors, shedding light on issues that arise in real-world scenarios, fostering a deeper understanding of the platform's complexities for researchers and developers alike. Access to such data enhances opportunities for comprehensive analysis and improvements within the Android ecosystem.

Log level standards :
Though each of these standards have similar level construction, they vary in granularity. Approximate equivalents across the standards are as follows:

| Severity  | Description                  |
|-----------|------------------------------|
| Emergency | System is unusable           |
| Alert     | Action must be taken immediately |
| Critical  | Critical conditions          |
| Error     | Error conditions             |
| Warning   | Warning conditions           |
| Notice    | Normal but significant        |
| Info      | Information messaging        |
| Debug     | Debug-level messages         |

Our Focus will on the assesement of the Software verions using --> | Alert | Error | Warning | Critical |

Data Source : Jieming Zhu, Shilin He, Pinjia He, Jinyang Liu, Michael R. Lyu. Loghub: A Large Collection of System Log Datasets for AI-driven Log Analytics. IEEE International Symposium on Software Reliability Engineering (ISSRE), 2023.

https://github.com/logpai/loghub/tree/master/Android


### <span style="color:yellow">**Data Descriptions:**<span style="color:lime">

The final data format, after applying topic modeling and utilizing LLM, will be presented as follows:

##### Android Log to Dataframe :

| Variable            | Description                                                                                         |
|---------------------|-----------------------------------------------------------------------------------------------------|
| Date                | Date of the event occurrence in the log                                                            |
| Time                | Time of the event occurrence in the log                                                            |
| Hour                | Time in hours of the event occurrence in the log                                                   |
| Minute              | Time in minutes of the event occurrence in the log                                                 |
| PID                 | Unique numeric identifier assigned to each running process on the system                           |
| TID                 | Unique identifier assigned to each thread within a process                                         |
| Event_Type          | Severity level and type of the event: Info, Debug, Error, Warning                                  |
| Event_Owner         | Platform or the process responsible for the occurred event                                         |
| Events              | Description of the occurred event                                                                  |
| Processed_Events    | Description of the occurred event after applying NLP cleaning processes, removing stop words, and unnecessary elements |
| Processed_Events_POS| Description of the occurred event after applying NLP POS cleaning processes, eliminating Verbs, Numbers, ADJ |
| NLP_Topics          | Description of the occurred event after applying all NLP cleaning processes and using LLM for a more coherent short description |


### <span style="color:yellow">**Metric to measure:**<span style="color:lime">

In evaluating the interpretability and quality of the generated topics, our primary metric is the coherence score. A higher coherence score is indicative of clearer and more relevant topics. The subsequent step involves the use of statistical comparisons, utilizing Z-tests, T-tests, F-tests, and ANOVA on the transformed data.

Z-test = $Z = \frac{{\bar{X} - \mu}}{{\frac{\sigma}{\sqrt{n}}}}$

T-tests = $t = \frac{{\bar{x}_1 - \bar{x}_2}}{{\sqrt{\frac{{s_1^2}}{{n_1}} + \frac{{s_2^2}}{{n_2}}}}}$

F-test = $F = \frac{\text{Between-group variability}}{\text{Within-group variability}}$

ANOVA = $F = \frac{MS_{\text{between}}}{MS_{\text{within}}}$


- The primary objective is to unveil patterns, anomalies, or disparities in the distribution of topics.

This analysis informs the assessment of different versions of the software, enabling the acceptance or rejection of the Null Hypothesis, which posits that the various software versions exhibit similarity in sanity, considering logarithmic statistical values derived from 'Alert,' 'Error,' 'Warning,' and 'Critical' references.

**Null Hypothesis:**
$H_0:$ The different software versions are similar in sanity check, considering the logarithmic statistical values using 'Alert,' 'Error,' 'Warning,' and 'Critical' as references.

**Alternative Hypothesis:**
$H_A:$ There is a significant difference in sanity among the different software versions, as indicated by the logarithmic statistical values using 'Alert,' 'Error,' 'Warning,' and 'Critical' as references.
