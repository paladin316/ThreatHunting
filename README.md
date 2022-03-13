# ThreatHunting
This repo is where I store my Threat Hunting ideas/content

Below are the use cases and file descriptions for the items in this repo:

Before going into what the files are, I will describe my lab setup:

**Lab Ingredients:**

1. Win10 Guest VM configured with Olaf Hartong's sysmon-modular (https://github.com/olafhartong/sysmon-modular)
2. Splunk Enterpirse Evaluation https://www.splunk.com/en_us/download/splunk-enterprise.html installed on Host Linux System
3. Atomic Red Team script to generate the data (https://github.com/redcanaryco/invoke-atomicredteam)



**Use Cases:**

Splunk queries are designed to score LOLBINs activity using a scoring method that bubbles up the most egregious activity to the top of the list based on MITRE techniques. The Scoring model uses four numbers (1,4,7,10) to represent the level of seriousness of the activity seen. The sum of all of the activity is added together to create a total score for each of the MITRE techniques, then added together to create an overall score for each system. Before implementing the scoring system its a good idea to perform some frequency analysis on LOLBINs usage within your environment. Build out the scoring model according to what you know about your environment (Priciple: Know You Environment). This scoring model will be unique to your environment since no two companies are the same. 

The primary goal here is to identify areas where security products can't alert on due to the high rate of false positives. Basically searching between data elements to pick up on malicious behaviors.


**Scoring Model (Base):**

Base score + Each MITRE Technique Score = Overal Score

1  = (Low) LOLBINs activity that is frequent in your environment and may be used by some of your Server and Workdstation Support Teams

4  = (Med) LOLBINs activity that is less frequent in your environment and may be used by some of your Server and Workdstation Support Teams

7  = (High) LOLBINs activity is not frequent in your environment and may be used by some of your Server and Workdstation Support Teams

10 = (Critical) LOLBINs activity should never be seen in your environment and is not used by your Server and Workdstation Support Teams


**Scoring Model with Threat Count:**

Base score + Each MITRE Technique Score X The number of occurences for each event = Overal Score 


[**See the ThreatHunting Wiki for hunt details and info**](https://github.com/paladin316/ThreatHunting/wiki/Threat-Hunting-Wiki)
