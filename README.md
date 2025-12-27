# AI SOC Agents

<img width="524" height="524" alt="image" src="https://github.com/user-attachments/assets/de5b7986-9114-4d3a-af30-3c308f8ae7a1" />

**Overview**  
Tackling one of the most critical challenges in cybersecurity operations: context gathering (correlation between various data sources) and alert fatigue. Context gathering is a fundamental part of detection and response; most of the time it is also tedious and repetitive, making it well-suited for handling by AI agents. PoC of 'Tier 1 SOC Analyst' tasks (Ip check, web searches, determine true or false positive) done using LangChain/LangGraph in a Google Colab notebook.

<img width="1184" height="464" alt="image" src="https://github.com/user-attachments/assets/ebc38a85-77c3-45b3-a770-b6b8fbc8e221" />  


**Versus current automation (SOAR)**

| Capability | SOAR Playbook | AI Agent |  
| -------- | ------- | ---------|
| Planning  | Fixed script | Dynamic planning    |  
| Scenarios | Anticipates specific cases     | Adapts to novel situations    | 
| Edge cases| Breaks when off-script    |  Re-plans when unexpected    | 
| Context  | No understanding    | Reasons about business/threat context    |  
| Integration | Rigid API calls     | Flexible tool use    | 
| Maintenance| Rewrite scripts    |  Update goals/tools/knowledge    | 

**Versus Agentic SOC**  
AI SOC Agents: AI tools or models deployed within a SOC (Security Operations Center) that assist analysts. They are generally task-specific and reactive, performing functions like alert triage, log correlation, or threat enrichment.  

Agentic SOC: A SOC framework where AI operates more autonomously as “agents” with goals, decision-making ability, and the capacity to orchestrate actions across multiple systems. Think AI-driven SOC operations rather than AI-assisted SOC operations.  

**Sample PoC Results**  
Incoming Alert:
```
Alert: High volume of traffic detected from source 185.220.101.1 to internal database.
```

Output Report:
```
--- Current Node: triage ---
Investigation Result: 🚨 Alert: IP 185.220.101.1 is MALICIOUS.
Malicious detections: 13 / 95 engines.
Suspicious detections: 1.

--- Current Node: researcher ---
Web Research Findings: [{'title': '185.220.101.1 reported for spam and brute force attacks - CleanTalk', 'url': 'https://cleantalk.org/blacklists/185.220.101.1', 'content': '| Date/time (GMT) | IP | Nickname | Event |\n ---  --- |\n| Dec 06, 2025 21:40:06 | 185.220.101.1 | devsign\\\\\\\\\\ | invalid\\_username |\n| Dec 06, 2025 14:31:46 | 185.220.101.1 | devsign\\\\\\\\\\ | invalid\\_username |\n| Dec 05, 2025 19:20:04 | 185.220.101.1 | devsign\\\\\\\\\\ | invalid\\_username |\n| Dec 05, 2025 14:12:05 | 185.220.101.1 | devsign\\\\\\\\\\ | invalid\\_username |\n| Dec 05, 2025 07:02:06 | 185.220.101.1 | devsign\\\\\\\\\\ | invalid\\_username |\n\n### 185.220.101.1 spam and brute force activity on date [...] Delete the record\n\n# 185.220.101.1 reported for spam and brute force attacks\n\nThe log shows up to 50 last spam activities.The address will be included in Security FireWall if it is present in SpamFireWall and the option "Use CleanTalk database of dangerous IP addresses" is turned on in Security settings.\n\n### Status [...] | Service | Status | Updated | Next steps |\n ---  --- |\n| Anti-Spam protection | Blacklisted | Dec 27, 2025 04:50:00 | Start protection |\n| SpamFireWall | Blacklisted | Dec 27, 2025 04:50:00 |\n| WordPress Security FireWall | Not in list  Start protection |\n| Type of attacks | Spam, BruteForce, Hacking   |\n\n### Details', 'score': 0.6350646}, {'title': '185.220.101.1 | Berlin, AS60729, & VPN Detected - IPinfo.io', 'url': 'https://ipinfo.io/185.220.101.1', 'content': 'This IP has been flagged as abusive — see AbuseIPDB for details. Berlin, State of Berlin, DE · Hosting Icon Hosting · Tor Icon Tor · VPN Icon', 'score': 0.49714416}, {'title': 'Cybersecurity Alerts & Advisories - CISA', 'url': 'https://www.cisa.gov/news-events/cybersecurity-advisories', 'content': 'Alert: Provides succinct information on recent, ongoing, or high-impact cyberthreats, plus associated mitigations, workarounds,and/or detections.Alertstypically include information on newly exploited or disclosed vulnerabilities, newly discovered cyberthreatcampaigns, severe denial-of-service events or widespread outages, or emerging', 'score': 0.25770947}]

--- Current Node: responder ---
# Security Operations Center Incident Report

**Incident Title:** Abuse and Brute Force Activities from IP Address 185.220.101.1

**Incident Date:** December 6, 2025

**Prepared By:** [Your Name]  
**Date of Report:** [Current Date]

---

## Executive Summary

This report outlines the incident regarding the IP address 185.220.101.1, which has been flagged for abusive behavior including spam and brute force attacks on multiple occasions. The analysis of several sources indicates that the IP is linked to significant cyber threats and should be addressed promptly to safeguard our network infrastructure.

## Analysis

### Findings

1. **Spam and Brute Force Attacks**
   - According to CleanTalk (report dated December 6, 2025), the IP address has been repeatedly reported for spam and brute force attacks. This includes multiple instances of invalid username attempts (see [CleanTalk report](https://cleantalk.org/blacklists/185.220.101.1)).
   - Notable timestamps reveal that the malicious activities occurred consistently over multiple days, indicating an ongoing threat.

2. **Abuse Report**
   - IPinfo.io has flagged IP 185.220.101.1 as abusive, linking it to a VPN and Tor services. Hosting details show it is primarily situated in Berlin, Germany ([IPinfo report](https://ipinfo.io/185.220.101.1)).
   - The abusive nature of this IP reinforces the need to take proactive security measures.

3. **CISA Cybersecurity Advisories**
   - While the latest updates from CISA do not directly mention this IP, they provide general alerts regarding ongoing cyber threats which may encompass attacks from such flagged IP addresses ([CISA advisory](https://www.cisa.gov/news-events/cybersecurity-advisories)).

### Severity Assessment

- **Severity Level:** High
  - The repeated attempts at unauthorized access and spam from this IP address warrant immediate attention and remedial action to prevent potential breaches and ensure the integrity of our systems.

## Recommendations

1. **Block the IP Address**
   - Immediately add 185.220.101.1 to the firewall blacklist to prevent any further unauthorized access attempts.

2. **Implement Security Measures**
   - Activate relevant settings in our Security FireWall, particularly those concerning CleanTalk’s database of dangerous IP addresses.
   - Ensure that anti-spam and brute force protection mechanisms are active and updated.

3. **Monitor Network Traffic**
   - Increase monitoring and analysis of network traffic originating from this IP and similarly flagged sources. This may include deploying intrusion detection systems (IDS) for real-time alerts.

4. **User Awareness Training**
   - Conduct training sessions for users to recognize signs of phishing and brute force attacks, emphasizing the importance of strong password policies and multi-factor authentication.

5. **Regular Review of Security Policies**
   - Schedule regular reviews of security policies to ensure they are updated against emerging threats and vulnerabilities.

## Conclusion

The activities associated with IP 185.220.101.1 clearly demonstrate an ongoing threat to network security. Immediate action should be taken to block this IP and strengthen our cybersecurity measures. Continuous monitoring and awareness are essential in preventing similar incidents in the future.

**Approval:**  
[Name, Title]  
[Signature]  
[Date]  
```
