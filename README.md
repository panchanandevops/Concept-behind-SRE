

# Table of Content

- [Table of Content](#table-of-content)
  - [What Do We Mean by Reliability?](#what-do-we-mean-by-reliability)
  - [What is Site Reliability Engineering?](#what-is-site-reliability-engineering)
    - [Importance of SRE in Modern IT Landscape](#importance-of-sre-in-modern-it-landscape)
  - [Key Pillars of SRE](#key-pillars-of-sre)
  - [Error Budget:](#error-budget)
    - [How Do We Implement An Error Budget:](#how-do-we-implement-an-error-budget)
    - [How Can We Spend Our Left Over Error Budget:](#how-can-we-spend-our-left-over-error-budget)
  - [Service Level Indicators (SLIs):](#service-level-indicators-slis)
    - [Formula:](#formula)
    - [How To Choose A Good SLI?](#how-to-choose-a-good-sli)
      - [Based on user requests:](#based-on-user-requests)
      - [Based On Data Processing:](#based-on-data-processing)
      - [Based On Storage:](#based-on-storage)
    - [Measurement Strategies SLI Metrics?](#measurement-strategies-sli-metrics)
  - [Service Level Objectives (SLOs):](#service-level-objectives-slos)
    - [How To Set A Good SLO Target Based On SLI?](#how-to-set-a-good-slo-target-based-on-sli)
  - [Service Level Agreements (SLAs):](#service-level-agreements-slas)
    - [Best Practices:](#best-practices)
  - [Final Thoughts](#final-thoughts)


## What Do We Mean by Reliability?

Reliability in IT refers to the ability of a system or service to consistently perform its intended functions without errors or interruptions. It means that users can depend on the technology to work as expected, providing a smooth and predictable experience. 

## What is Site Reliability Engineering?

Site Reliability Engineering (SRE) is a discipline that merges software engineering with IT operations, focusing on creating scalable and highly reliable software systems. SREs aim to balance service reliability, system efficiency, and rapid innovation in the development and operation of large-scale, distributed systems.

### Importance of SRE in Modern IT Landscape

1. **Reliability as a Competitive Edge:** SRE ensures systems remain dependable, fostering customer trust and satisfaction, critical for competitiveness in the market.

2. **Resilience Amid Complexity:** In today's intricate IT environments, SRE provides a structured approach to manage complex systems while maintaining reliability.

3. **Balancing Innovation with Stability:** SRE empowers teams to innovate without compromising system stability, facilitating a balance between agility and dependability.

4. **Cost-Efficiency through Automation:** By automating repetitive tasks and focusing on error reduction, SRE minimizes downtime, saving both time and resources.

5. **Enhanced Incident Response:** SRE's proactive approach to incident management enables quick response, minimizing the impact of failures and reducing recovery time.


## Key Pillars of SRE
The foundational elements of SRE, encompassing Service Level Indicators (SLIs), Objectives (SLOs), and Agreements (SLAs), along with the crucial concept of Error Budget, form the key pillars that drive reliability and performance in modern IT operations.

Lets understand them one by one.

## Error Budget:

Error Budget represent the permissible margin of errors or disruptions in a system's reliability over a specific time frame. SREs use Error Budget to strike a balance between innovation and reliability, allowing a controlled level of incidents while maintaining service performance.

### How Do We Implement An Error Budget: 

- Set clear reliability targets and acceptable levels of errors or downtime.
- Implement robust monitoring systems for real-time performance tracking and alerts for approaching Error Budget depletion.
- Encourage cross-team collaboration between development and operations.
- Continuously monitor service performance and make adjustments to stay within the allocated Error Budget, slowing down deployment when necessary.
- Conduct regular reviews to assess the impact of Error Budget utilization and learn from incidents, iterating to improve processes and infrastructure.


### How Can We Spend Our Left Over Error Budget:
- Release new features.
- Expected system changes.
- Inhabitable failure in hardwares, networks, etc.
- Planned downtime
- Risky experiments



## Service Level Indicators (SLIs):
Service Level Indicators (SLIs) are metrics that quantify the performance of a service, reflecting its behavior or characteristics. They provide a clear, measurable understanding of how well a service is operating, often based on user experience or system behavior.


### Formula:
\[ SLI = \frac{\text{Number of Successful Events}}{\text{Total Number of Events}} \]

This formula provides a ratio indicating the proportion of successful events, serving as a key metric to assess the reliability and performance of a service.

### How To Choose A Good SLI?

- Identify critical aspects of your service that directly impact user experience.
- Choose metrics that are measurable, relevant, and align with user expectations.
- Prioritize simplicity and clarity in defining SLIs, ensuring they reflect essential user interactions.
- Collaborate with stakeholders to gain a comprehensive understanding of user priorities and concerns.
- Regularly review and update SLIs to adapt to changing user needs and service characteristics.

> "**100%** is the **wrong** reliability target for basically everything."
> > **`- Betsy Beyer`**, Site Reliability Engineering: How Google Runs Production Systems

Lets understand good SLIs through some examples.

#### Based on user requests:

1. **Latency SLI:**
   - **Metric:** Response time for user requests

2. **Availability SLI:**
   - **Metric:** System uptime and availability

3. **Error Rate SLI:**
   - **Metric:** Percentage of failed requests

4. **Quality SLI:**
   - **Metric:** User satisfaction ratings


#### Based On Data Processing:

1. **Coverage SLI:**
   - **Metric:** Percentage of data processed compared to the total incoming data.
   
2. **Correctness SLI:**
   - **Metric:** Percentage of accurate results compared to the expected outcomes.
  
3. **Freshness SLI:**
   - **Metric:** The time it takes for the system to process and make data available for consumption.
  
4. **Throughput SLI:**
   - **Metric:** The number of data records processed per unit of time.
   

#### Based On Storage:

1. **Latency SLI:**
   - **Metric:** Time taken for storage operations to be completed.
   
2. **Throughput SLI:**
   - **Metric:** Rate of data transfer to and from the storage system.
   
3. **Availability SLI:**
   - **Metric:** Percentage of time the storage system is available for read and write operations.

4. **Durability SLI:**
   - **Metric:** Assurance that data written to the storage system is not lost.
   

**NOTE:** We have to define clearly what is **success** and **failure** for our **SLI**.

### Measurement Strategies SLI Metrics?

Measurement strategies for SLI (Service Level Indicator) metrics involve systematic approaches to gather and assess data at various levels of a system. Here are common measurement strategies:

1. **User-Centric Measurement:**
   - **Strategy:** Directly measure metrics that impact the end-user experience, such as page load times, response times, and error rates during real user interactions.
   - **Tools:** Use real user monitoring (RUM) tools to capture data from actual user sessions and experiences.

2. **Instrumentation in Application Code:**
   - **Strategy:** Embed instrumentation within the application code to capture SLI metrics related to critical functionalities and operations.
   - **Tools:** Leverage application performance monitoring (APM) tools and custom logging to collect data directly from the codebase.

3. **Infrastructure and Server Monitoring:**
   - **Strategy:** Implement monitoring tools to track resource utilization, response times, and error rates at the server and infrastructure levels.
   - **Tools:** Use server monitoring solutions, log analyzers, and infrastructure monitoring platforms.

4. **Database Query and Transaction Monitoring:**
   - **Strategy:** Monitor SLI metrics related to database operations, including query performance, transaction times, and error rates.
   - **Tools:** Employ database monitoring tools and query performance analyzers.

5. **API Endpoint Monitoring:**
   - **Strategy:** Monitor SLI metrics at API endpoints, capturing response times, error rates, and data transfer efficiency.
   - **Tools:** Utilize API monitoring tools and endpoint-specific metrics.

6. **Microservices Interaction Analysis:**
   - **Strategy:** Assess SLI metrics at points of interaction between microservices to identify latency issues and error rates.
   - **Tools:** Leverage distributed tracing tools and microservices observability platforms.

7. **Load Balancer Effectiveness Assessment:**
   - **Strategy:** Monitor SLI metrics at load balancers to evaluate their efficiency in distributing traffic and maintaining system stability.
   - **Tools:** Load balancer logs, analytics, and dedicated monitoring tools.


## Service Level Objectives (SLOs):

Service Level Objectives (SLOs) are specific, **measurable targets set** for Service Level Indicators **(SLIs)** to quantify the **desired** performance and **reliability** of a system. SLOs act as a **bridge** between high-level business expectations and concrete technical metrics.

By defining SLOs based on SLIs, organizations can establish **clear** objectives for aspects such as latency, throughput, availability, and **correctness**, providing a tangible **framework** for assessing and maintaining the quality of their services. The alignment of SLOs with SLIs ensures a **focused** and **measurable** approach to meeting **user expectations** and delivering a reliable **user experience**.


### How To Set A Good SLO Target Based On SLI?

- Understand user expectations and critical service aspects.
- Review historical performance data for patterns and improvements.
- Align SLO targets with broader business goals.
- Consider dependencies on other services or components.
- Involve stakeholders, including product owners and end-users.
- Prioritize SLIs with a significant impact on user satisfaction.
- Set realistic yet challenging SLO targets.
- Embrace an iterative approach for refinement over time.

Here are some real-world examples of **Service Level Objectives (SLOs)** based on various **Service Level Indicators (SLIs)**:


1. **E-commerce Platform - Latency:**
   - **SLI:** Time taken to load product pages.
   - **SLO:** Ensure that **90%** of page loads occur within **3 seconds**.
   - **Alert:** Trigger an alert if the page load time exceeds **4 seconds** for more than **5 minutes**. Notify the on-call engineer via **Slack**.

2. **Cloud Storage Service - Availability:**
   - **SLI:** Percentage of time the storage service is accessible.
   - **SLO:** Maintain an availability of **99.99%** over a **monthly** period.
   - **Alert:** Send an alert and create a high-priority **JIRA ticket** if the availability falls below **99.95%** in a given month. Notify the **operations team**.

3. **Video Streaming Service - Buffering Rate:**
   - **SLI:** Percentage of video playback without buffering interruptions.
   - **SLO:** Limit buffering interruptions to less than **1%** of total viewing time.
   - **Alert:** Trigger an alert, escalate to video streaming engineers, and create a critical incident in **PagerDuty** if the buffering rate exceeds **1.5%** during **peak hours**.

4. **Financial Transactions - Error Rate:**
   - **SLI:** Percentage of error-free financial transactions.
   - **SLO:** Keep the error rate below **0.1%** for all monetary transactions.
   - **Alert:** Issue an alert, notify the **security team**, and initiate a forensic analysis if the error rate surpasses **0.2%** in a given day.

5. **Healthcare Application - Response Time:**
   - **SLI:** Time taken to process and display patient records.
   - **SLO:** Ensure that **95%** of requests for patient records are served within **2 seconds**.
   - **Alert:** Send an alert, notify the **support team**, and create a ticket for the **development team** if the response time for patient records exceeds **2.5 seconds** for more than **2 hours**.

6. **Social Media Platform - Throughput:**
   - **SLI:** Number of user posts processed per second.
   - **SLO:** Maintain a throughput of at least **1000 posts per second** during **peak usage**.
   - **Alert:** Trigger an alert, notify the **performance team**, and create a **post-incident report** if the throughput falls below **900 posts per second** for more than **10 minutes**.

7. **Online Learning Platform - Uptime:**
   - **SLI:** Percentage of time the platform is operational.
   - **SLO:** Achieve an uptime of **99.9%** throughout the **academic year**.
   - **Alert:** Issue an alert, notify the **operations team**, and engage incident response if the platform's uptime drops below **99.5%** within a **24-hour period**.

8. **Telecommunications Network - Call Drop Rate:**
   - **SLI:** Percentage of completed phone calls without dropping.
   - **SLO:** Keep the call drop rate below **1%** during **peak hours**.
   - **Alert:** Send an alert, escalate to **network operations**, and initiate a **bridge call** with the **engineering team** if the call drop rate exceeds **1.2%** during **peak hours** for more than **15 minutes**.


## Service Level Agreements (SLAs):

Service Level Agreements (SLAs) are **formal** **agreements** between **service providers** and **customers** that outline the expected level of service, including performance metrics, responsibilities, and **guarantees**.

SLAs establish a contractual framework, specifying the **minimum standards** that the service provider commits to meet, and they often include **consequences** for **failing** to meet these standards, such as **penalties** or **compensations**. SLAs serve as a crucial component in ensuring **transparency**, **accountability**, and the overall quality of services provided.

### Best Practices:
- Set SLOs **slightly** **above** the contracted SLA to provide a buffer, avoiding user dissatisfaction.
  
- Ensure SLIs **should not** fall **below** the SLA, maintaining a commitment to agreed-upon service levels.


## Final Thoughts
As we conclude our journey through the realm of Site Reliability Engineering, remember that SRE is not just a set of practices; it's a mindset that fosters reliability, collaboration, and continuous improvement. May your systems be resilient, your incidents be few, and your services be reliable. Happy engineering!