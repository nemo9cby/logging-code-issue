# Logging Improvement
This repository hosts a collection of all research works related to improving logging code quality. Logging code refers to the code snippets that developers inserted into source code (e.g., `LOG.info("User " + userName + " logged in")`) to monitor the behavior of systems during runtime.

Execution logs, which are generated by logging code at runtime, are readily available in large-scale software systems for many purposes like system monitoring, problem degbugging, workload characterization, and business decision making. All these tasks require high quality logging code.

However, as logging code is a cross-cutting concern, it is hard to maintain and evolve logging code while the modern software development cycle increases. Hence, quite a few research works are proposed to tackle with this challenges and are published in top-ranked software engineering/system venues. This repository aims to summarize these works and present a complete catalog of logging code related research.

### Logging Issue Catalog (To be added)

| Category | Description | Example |
|-----------|-------------|---|
|Explicit Cast|Explicit casting informs the system to forcibly convert an object into a particular type. It might cause runtime type conversion errors and system crash.| DataNode.LOG.warn("Added missing block to memory " + (Block)diskBlockInfo);
|Logging Smells| Poor design and implementation choices when developing the logging code. | remoteAddress = s.getRemoteSocketAddress().toString();<br>LOG.warn("Invalid access token in request from " + s.getRemoteSocketAddress() + " for replacing block " + block);
|Malformed output|Some objects do not have a human readable format defined.| byte[] startRow;<br>LOG.debug("Creating scanner over " + Bytes.toString(tableName) + " starting at key '" + startRow  + "'");
|Nullable objects| The objects used in the dynamic contents can be null. | //proxy could be null<br>Log.error(... + proxy.getPort());|
| Wrong Verbosity Level | A problematic verbosity level for the logging code was chosen by developers |   LOG.info("DEBUG --- Container FINISHED: " + containerID);|
| Inadequate information in catch blocks | Duplicate logging statements in different catch blocks of the same try block | n/a
| Inconsistent error-diagnostic information  | Duplicate logging statements for documenting exceptions may contain inconsistent error-diagnostic information | n/a
| Log message mismatch | After developers copy and paste a piece of code to another method or class, they may forget to change the log message. | void scaleup() { <br> log.info("scaledown");
| Duplicate log in polymorphism | logs are same in classes implementing same interfaces, causing confusion | class A implements C {<br>   log.info("foo");}<br> class B implements C {<br> log.info("foo");}


### Papers on Improving Logging

#### Where-to-log
+ [**ICD '09**] A Logging Approach for Effective Dependability Evaluation of Complex Systems. Marcello Cinque, Domenico Cotroneo, and Antonio Pecchia.
+ [**OSDI '12**] Be Conservative: Enhancing Failure Diagnosis with Proactive Logging.Ding Yuan, Soyeon Park, Peng Huang, Yang Liu, Michael M. Lee, Xiaoming Tang, Yuanyuan Zhou, and Stefan Savage.
+ [**TSE '13**] Event Logs for the Analysis of Software Failures: A Rule-Based Approach. Marcello Cinque, Domenico Cotroneo, and Antonio Pecchia.
+ [**ICSE-C '14**] Where do developers log? an empirical study on logging practices in industry. Qiang Fu, Jieming Zhu, Wenlu Hu, Jian-Guang Lou, Rui Ding, Qingwei Lin, Dongmei Zhang, and Tao Xie.
+ [**ICSE '15**] Learning to Log: Helping Developers Make Informed Logging Decisions. Jieming Zhu, Pinjia He, Qiang Fu, Hongyu Zhang, Michael R. Lyu, and Dongmei Zhang.
+ [**ATC '15**] Log2: A Cost-Aware Logging Mechanism for Performance Diagnosis. Rui Ding, Hucheng Zhou, Jian-Guang Lou, Hongyu Zhang, Qingwei Lin, Qiang Fu, Dongmei Zhang, and Tao Xie.
+ [**COMPSAC '16**] LogOptPlus: Learning to Optimize Logging in Catch and If Programming Constructs. Sangeeta Lal, Neetu Sardana, and Ashish Sureka. 2016. 
+ [**ISEC '16**] LogOpt: Static Feature Extraction from Source Code for Automated Catch Block Logging Prediction. Sangeeta Lal and Ashish Sureka.
+ [**ISSREW '18**] Machine Deserves Better Logging: A Log Enhancement Approach for Automatic Fault Diagnosis. Tong Jia, Ying Li, Chengbo Zhang, Wensheng Xia, Jie Jiang, and Yuhong Liu. 2018.
+ [**HotOS '17**] The Game of Twenty Questions: Do You Know Where to Log? Xu Zhao, Kirk Rodrigues, Yu Luo, Michael Stumm, Ding Yuan, and Yuanyuan Zhou. 
+ [**SOSP '17**]  Log20: Fully Automated
Optimal Placement of Log Printing Statements under Specified Overhead Threshold. Xu Zhao, Kirk Rodrigues, Yu Luo, Michael Stumm, Ding Yuan, and Yuanyuan Zhou.
+ [**SANER '18**] SMARTLOG: Place error log statement by deep understanding of log intention. Zhouyang Jia, Shanshan Li, Xiaodong Liu, Xiangke Liao, and Yunhuai Liu. 2018.
+ [**ICPE '18**] Log4Perf: Suggesting Logging Locations for Web-based Systems’ Performance Monitoring. Kundi Yao, Guilherme B. de Pádua, Weiyi Shang, Steve Sporea, Andrei Toma, and Sarah Sajedi.

#### What-to-log

+ [**SLAML '10**] A Graphical Representation for Identifier Structure in Logs. Ariel Rabkin, Wei Xu, Avani Wildani, Armando Fox, David A. Patterson, and Randy H. Katz.
+ [**ASPLOS '11**] Improving Software Diagnosability via Log Enhancement. Ding Yuan, Jing Zheng, Soyeon Park, Yuanyuan Zhou, and Stefan Savage.
+ [**EMSE '17**] Which log level should developers choose for a new logging statement? Heng Li, Weiyi Shang, and Ahmed E. Hassan.
+ [**ASE '18**] Characterizing the natural language descriptions in software logging statements. Pinjia He, Zhuangbin Chen, Shilin He, and Michael R. Lyu. 


#### How-to-log
+ [**ICSE '12**] Characterizing logging practices in open-source software. Ding Yuan, Soyeon Park, and Yuanyuan Zhou.
+ [**ICSE '17**] Characterizing and detecting anti-patterns in the logging code. Boyuan Chen and Zhen Ming (Jack) Jiang.
+ [**APSEC '18**] An Automatic Approach to Validating Log Levels in Java. Tae-young Kim, Suntae Kim, Cheol-Jung Yoo, Soohwan Cho, and Sooyong Park. 
+ [**EMSE '17**] Towards just-in-time suggestions for log changes. Heng Li, Weiyi Shang, Ying Zou, and Ahmed E. Hassan.
+ [**EMSE '19**] Shanshan Li, Xu Niu, Zhouyang Jia, Xiang-Ke Liao, Ji Wang, and Tao Li. 2019. Guiding log revisions by learning from software evolution history. 
+ [**ICSE '19**] Zhenhao Li, Tse-Hsun (Peter) Chen, Jinqiu Yang, and Weiyi Shang. 2019. Dlfinder: characterizing and detecting duplicate logging code smells.
+ [**EMSE '19**] Extracting and studying the Logging-Code-Issue-Introducing changes in Java-based large-scale open source software systems. Boyuan Chen and Zhen Ming (Jack) Jiang.


#### Empirical Studies
+ [**ICSE '12**] Characterizing logging practices in open-source software. Ding Yuan, Soyeon Park, and Yuanyuan Zhou.
+ [**ICSE-C '14**] Where do developers log? an empirical study on logging practices in industry. Qiang Fu, Jieming Zhu, Wenlu Hu, Jian-Guang Lou, Rui Ding, Qingwei Lin, Dongmei Zhang, and Tao Xie.
+ [**ICSE '15**] Industry Practices and Event Logging: Assessment of a Critical Software Development Process. Antonio Pecchia, Marcello Cinque, Gabriella Carrozza, and Domenico Cotroneo.
+ [**MSR '16**] Logging library migrations: a case study for the apache software foundation projects. Suhas Kabinna, Cor-Paul Bezemer, Weiyi Shang, and Ahmed E. Hassan.
+ [**SANER '16**] Examining the Stability of Logging Statements. Suhas Kabinna, Weiyi Shang, Cor-Paul Bezemer, and Ahmed E. Hassan.
+ [**ICSE '16**] The bones of the system: a case study of logging and telemetry at Microsoft. Titus Barik, Robert DeLine, Steven M. Drucker, and Danyel Fisher.
+ [**EMSE '17**] Characterizing logging practices in Java-based open source software projects - a replication study in Apache Software Foundation. Boyuan Chen and Zhen Ming (Jack) Jiang.
+ [**ASE '18**] Characterizing the natural language descriptions in software logging statements. Pinjia He, Zhuangbin Chen, Shilin He, and Michael R. Lyu.
+ [**EMSE '19**] Studying the characteristics of logging practices in mobile apps: a case study on F-Droid. Yi Zeng, Jinfu Chen, Weiyi Shang, and Tse-Hsun Chen.

### Tools and Datasets
+ [**ICSE '17**] _Tool:_ LCAnalyzer ([Replication](https://nemo9cby.github.io/icse2017.html)) - [Characterizing and detecting anti-patterns in the logging code](./papers/icse_2017_chen.pdf). Boyuan Chen, Zhen Ming (Jack) Jiang.
+ [**ICSE '19**] _Tool:_ DLFinder - [DLFinder: Characterizing and Detecting Duplicate Logging Code Smells](./papers/icse_2019_li.pdf) Zhenhao Li, Tse-Hsun (Peter) Chen, Jinqiu Yang, Weiyi Shang.
+ [**EMSE '19**] _Dataset:_ Mobile Logging Practices([Replication](https://bitbucket.org/sense_concordia/mobilelogreplication/src/master/)) - [Studying the characteristics of logging practices in mobile apps: a case study on F-Droid](./papers/emse_2019_zeng.pdf) Yi Zeng, Jinfu Chen, Weiyi Shang, Tse-Hsun (Peter) Chen.
+ [**EMSE '19**] _Dataset:_ Logging-Code-Issue-Introducing(LCII) changes and fixes ([Replication](http://www.cse.yorku.ca/~zmjiang/share/replication_package/emse2018_chen/replication_package.zip)) - [Extracting and studying the Logging-Code-IssueIntroducing changes in Java-based large-scale open source software systems](./papers/icse_2019_li.pdf)

