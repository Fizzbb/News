# A Look at Current State of Network Intelligence
Artificial intelligence plays an important role in the digital world. Almost all the industries have adopted some artificial intelligence technologies to improve their processes, efficiency, revenue, etc. The binding of artificial intelligence and network becomes more and more critical, with the ever-increasing network scale, demands and complexity.

1. Classic
* Root Cause Analysis 

Supervised learning is a well-known category in machine learning. The classification capability makes it a nature fit in root cause analysis in network system. When diagnostic records are available, those labeled cases can be used to train supervised model to diagnose root cause. One of the challenges here is labeling is costly, especially for today's data at scale. Fortunately, machine learning can be used for preparing training dataset as well, i.e., humans label a small portion of data, and machines learn from the labeled data and then label the remained dataset. [Amazone SageMaker Grouth Truth](https://aws.amazon.com/sagemaker/groundtruth/) is a fully managed labeling service. By leveraging automatic labeling technologies, the labeling cost can be significantly reduced. 

One trend is that many monitoring platforms start integrating root cause analysis features, since all the data are already collected in the platform. Recently, Moogsoft, AIOps platform vendor, consolidate monitoring, analysis and control together. In their latest release [Enterprise 8.0](https://www.moogsoft.com/blog/aiops/moogsoft-enterprise-8.0/), customers can create a [virtual Network Operations Center](https://www.infoq.com/news/2020/05/moogsoft-virtual-NOC/) using the Moogsoft situation room to collaborate throughout the incident management process, and diagnose and resolve issues quickly. Events are aggerated to alerts and situations. By analyzing the arrival time of events, related alerts and causal relationship can be identified. [Correlation](https://ieeexplore.ieee.org/document/8717853) has been considered as a critical step in the root cause analysis. Feature preprocessing and clustering algorithms need to be carefully designed. 

* Anomaly Detection 

Anomaly Detection can be temporal and spatial. In network O&M, monthly or yearly routine inspection collect metrics from large number of devices. To identify the outlier among a group of devices is more like a spatial problem. While some metrics are monitored at a high frequency forming a time series, the detection of spike, flapping or other patterns is a temporal problem. One main challenge in anomaly detection is the high false positive rate. The anomalies detected from a mathematic model often are not a problem in practical scenarios. Therefore, a user-friendly feedback portal for technicians to interact with system is very important. [Amazon Augmented AI](https://aws.amazon.com/augmented-ai/) is a good example when machine learning's decisions need human confirmation.

As for the temporal anomaly detection, [Anodot](https://www.anodot.com/blog/ai-analytics-5g/) has been a leading player. Through learning normal behavior and abnormal behavior, Anodot is able to predict a valid range for the metrics under monitoring. Once the new collected sample point falls out of the predicted normal range, an alert is triggered. To make customers' life even easier, Anodot provide automatic discovery on baseline, seasonality, etc., so fewer parameters need to be set up. 
Time series anomaly detection and forecasting are banded together. Forecasting plays importance role in network bandwidth dynamic control, especially with network slicing in 5G. Proactively adjusting bandwidth based on application can effectively optimize user experience and guarantee the critical application. Considering the temporal characteristics, some recurrent neural networks like LSTM have been studied for time series forecasting in both academia and industry.  However, LSTM has lots of hyperparameters to tweak and the performance is not often stable especially when dataset size is small. [Uber](https://eng.uber.com/m4-forecasting-competition/) has some interesting work in forecasting.

Another trend in the monitoring field is moving towards full stack observability. Most network vendors agree that network optimization is no more managing the box. It is about optimizing the end-to-end application experience. For example, Cisco fold [AppDynamic](https://www.appdynamics.com/product/application-performance-management/infrastructure-visibility) into its application centric infrastructure (ACI). By correlating ACI constructs, AppDynamics can show how network-configured policies are impacting application performance. Streamline collaboration across network and application teams to reduce time spent troubleshooting and focus on ensuring superior user experience. Similarly, Vmware's recent acquisition on a cloud-based network analytics startup, [Nyansa](https://www.nyansa.com/network-performance-analytics/), extends its SD-WAN platform and brings an end-to-end network visibility, monitoring and remediation solutions. Additionally, the container monitoring becomes increasingly important as with the shift to cloud-native paradigm. Full stack monitoring platform integrates Kubernetes events and metrics as well. Software intelligence company [Dynatrace](https://www.dynatrace.com/news/press-release/dynatrace-further-extends-kubernetes-support-for-full-stack-observability/) recently enhance its Kubernetes support. By ingesting additional Kubernetes metrics, it can deliver precise answers in real time about performance issues and anomalies across the full stack of Kubernetes clusters, containers, and workloads. 


2. Trending
* Close Loop Control 

Network automation and orchestration have a long history. Yet the meanings and actions behind it have always been evolving, like from zero touch provisioning to intent-based networking. Cisco, Juniper, VMware, [Anuta Network](https://www.anutanetworks.com/what-is-closed-loop-automation-and-how-to-achieve-it-in-networking/), [Apstra](https://apstra.com/intent-based-networking-examples-part-3-closed-loop-telemetry/) and other network vendors all have their advanced automation software in portfolio to solve customer challenges. Previously, automation is divided into different parts, like configuration, data collection, insights report, situation room etc. As machine learning advances, continuous optimization is an interesting target. Automation engine or traffic controller use advanced telemetry and analytics to improve network performance in real time without human intervention. Reinforcement learning (RL) is a perfect fit for this control problem. An agent takes an action based on the current observation/state, and then receives the rewards from the environment.  Iteratively, the agent learns the best policies through the environment's feedback. [Deep Mind](https://www.youtube.com/playlist?list=PLqYmG7hTraZDM-OYHWgPebj2MfCFzFObQ) has a very good series of lecture on reinforcement learning. 

Existing research demonstrates the feasibility of RL to control the infrastructure. Microsoft and MIT published a paper on [resource management with RL](https://dl.acm.org/doi/10.1145/3005745.3005750), which is able to continuously optimization job scheduling efficiency given CPU/memory/IO restrictions. Hebrew University and UC Berkeley published a paper on [learning to route with Deep RL](https://dl.acm.org/doi/10.1145/3152434.3152441). [VMware Project Magna](https://blogs.vmware.com/management/2019/08/tech-preview-project-magna.html) is to demonstrate the vision of self-driving data center. RL is integrated in the Magna engine, which makes performance tuning configurations by itself. With guard rails within the ML algorithms, it will not decrease performance by any means, but optimizes the desired read and write KPIs. Those use cases prove RL is capable for a specific performance tuning task. 

Reinforcement is still at its nascent stage, but it already starts disrupting many fields. It may not be able to do everything now, but we are confident that RL itself can figure out the best policies for a well-defined objective, given proper state space and rewards. With all the efforts from academia and industry, RL make its significant contributions in autonomous network.  


* Cloud, Edge, elastic infrastructure 

As more enterprise move to the clouds, network architecture keeps evolving. On-premise network needs cloud on-ramp to reach cloud services. Hybrid multi-cloud becomes the new norm. SD-WAN with security-as-a-service becomes secure access edge service (SASE). With all these excitements, new challenges are rising too, like multi-cloud network visibility, data governance and compliance, optimize hybrid-cloud connectivity, path selection, dynamic bandwidth, consistent network latency over internet, application-dependent network policies, security and more. Machine learning can help in these challenges. It is important to keep data and AI in mind while building all those new services, so the solutions are with built-in intelligence. 

Network vendors and cloud providers work closely more than ever. Recently, [Cisco SD-WAN use google backbone](https://searchnetworking.techtarget.com/news/252482016/Cisco-SD-WAN-to-use-Google-Cloud-backbone) to reduce latency variation in a global network, which is considered as the future direction for SD-WAN companies. DevOps also play an essential role in this marriage, efficiently convert application's network requirements into network policies through well-defined data structures. In addition, many startups build network services on top of AWS, Azure, GCP, etc. For example, [Aviatrix](https://aviatrix.com/cloud-network-platform/#multi-cloud-architecture) provides software defined cloud routing with a central controller that builds and manages multi-cloud and multi-account secure networks. [SilverPeak](https://www.silver-peak.com/company/tech-partners/cloud/aws) Unity EdgeConnect brings customer's VPC as just one more location on the SD-WAN.

 
3. Digital Life 

* Digital twin 

Digital twin has different meanings when it is placed in different contexts and fields. In the network world, one typical use case is for network validation. Before deploying the configuration into the real-world network, network engineers typically need to valid the correctness. Under this circumstance, a twin network with the same devices and topology is used for validation. The challenge is to determine how much details are needed to put into the twin. Accuracy and complexity have to be balanced. [Forward network](https://www.forwardnetworks.com/network-automation-software/) identify the fundamentals for modeling, one is configuration and the other is state. The model takes these two pieces of information to build the basic twin for verification. 

To make things more interesting, streaming data can be injected to the twin in real time. [ScaleOut](https://www.scaleoutsoftware.com/products/digital-twin-streaming-service/) provides digital twin streaming service. By their definition, a real-time digital twin model describes how to process incoming events for an object with a given state. To build a real-time digital twin platform, data ingestion and processing speed is the key. Most streaming platforms consider in-memory computing to host digital twins, so as ScaleOut. In addition, every digital twin is independently created, so it is easy to scale out. Ideally, digital twin is an accurate reflection of a real-world object, it offers situational awareness and real-time control. Yet due to the limited sensors and model accuracy, the digital twin still works on its way of maturing.

* Virtual Assistance

Virtual assistance has been a hot topic in many domains. In network world, it is more like a language wrapper added around the daily operation. Instead of reading logs and debug manuals, a chatbot or an interactive Q&A session can be leveraged in operations. Like Davis from [Dynatrace](https://www.dynatrace.com/support/help/how-to-use-dynatrace/davis-assistant/basic-concepts/get-started-with-davis-assistant/), on top of monitoring and analytics, Davis can communicate with you, and results can be queried. Early this year, [IPsoft](https://info.ipsoft.com/telco) release an even fancier assistant. Pre-trained assistant Amelia can take on real IT jobs. Besides the advanced natural language processing capability, robot process automation (RPA) is integrated as well. Another very important feature for virtual assistant is the online learning, which means through the interaction, she needs to learn answers to the new questions. Knowledge should be able to be added to the knowledgebase incrementally.  

Additionally, in some scenarios, virtual assistants need to provide explanations for their solutions, to earn human trusts, e.g., root cause identification, etc. IBM has been working on [explainable AI](https://www.ibm.com/blogs/research/2019/08/ai-explainability-360/), which provides some guidance in this field.

4. MLOps

As machine learning development mature, MLOps start emerging. Data scientist are not isolated in a Jupiter notebook. ML module is not just an executable file alienated from the whole advanced DevOps flow. Machine learning development starts joining the regular software development flow. Continues integration and continues delivery are required for ML module as well. ML will be part of software products, nothing special. [AWS Sage platform](https://aws.amazon.com/blogs/apn/how-slalom-and-wordstream-used-mlops-to-unify-machine-learning-and-devops-on-aws/) is leading the way. SageMaker studio provides a complete flow including, new data, build, train, deploy, monitor. The last stage monitor is for detecting data drift problem and continuously improving model accuracy. This is very important in ML service life cycle management.  

5. Data Foundation

Last but not least, data collection is the foundation of applied artificial intelligence. Without meaningful features and details, the good decision and resolution cannot be achieved. How to make networks report meaningful data is critical for future AI advance. For example, at the device level, [Mellnox demo](https://www.youtube.com/watch?v=xBOQX3_qVVc) a new feature (WJH) of sending detailed packet loss info in OCP virtual summit 2020. Once a packet loss, detailed info includes device IP, interface ID, port number will be reported to the OS, so it paves the way to fast fault isolation when packet loss happened. In addition, Alibaba published a Sigcomm 2020 paper on a vTrace platform, which simplifies in-band telemetry process, reports less data to minimize performance impacts. A new handshaking protocol is also implemented to accurately recording timestamps, so the event order is well observed in the large cloud networking environment.

In summary, root cause analysis, anomaly detection, and predictive analysis are relatively mature in the network field. Reinforcement learning and natural language processing are enabling the next level of network intelligence. Humans are putting more control and power into machines' hands, moving towards to an autonomous network era.