
# Collaborative Development Experience
## Demo Video
https://www.youtube.com/watch?v=zwGmCjEAcr0
## Qualitative Question Sample
We conducted semi-structured interview to address the following questions at research site.

- Q1: What is the day-to-day work routine for the specific role at SAP?
- Q2: What challenges did they encounter?
- Q3: What are the existing solutions or workarounds for these challenges?

## Qualitative Results:
### To summarize the results obtained from Q1, we use Collaboration Persona [1] to describe the research site.
Group goals:  Continuously refine and deliver product increments to customers while improving the collaboration process

Group work style: 
- Executives make decisions by evaluating teams through qualitative or quantitative data about product and process
- Program manager communicates group’s overall delivery plan and status regularly with six scrum teams across three time zones
- Developers work on artifact and communicate blockers, status, and needs with all the other roles
- Scrum masters work with developers to understand their sprint goal, status, manage and remove the blockers, escalate if necessary
- Product managers work with clients, designers, and developers to ensure everyone is aligned with the same goal

Collaboration needs: 
- Maintain awareness of group and sprint goals, blockers, and status across time zones and scrum teams.
- Obtain teams' overview to evaluate current process, practices, and artifact quality

### Q2: We summarized 6 challenges through thematic analysis
| Codes                            | Definitions                                                           |
|----------------------------------|-----------------------------------------------------------------------|
| Challenges: Management           | Challenges relevant to managing one or multiple teams                 |
| Challenges: Meetings             | Challenges relevant to hosting, arranging, or attending meetings      |
| Challenges: Tools                | Challenges relevant to the use of specific tools                      |
| Challenges: Hybrid/Remote work   | Challenges relevant to working in hybrid and distributed teams        |
| Challenges: Time zone difficulty | Challenges relevant to working with teams across different time zones |
| Challenges: Unclear roadmap      | Challenges relevant to unclear future direction                       |

### Q3: Solutions, workarounds, or wishes
Each challenge has its counter solutions, workarounds or wishes. Here we provide a sample of solutions to Challenges: Management.
| Codes | Sub-Codes |
|-------|-----------|
| Solution: Management |  Workaround: Invite experts to coach young team |
|  | Wish: people in scrum team can raise their challenges more proactively |
|  | Wish: Predictable progress |

## Implementation Details
### Implementation
Our tool consists of three components, as shown in below figure, which include 
1. a data engineering service in Python that monitors and updates data in real time, and particularly consumes data from two external data sources including Jira and GitHub;
2. a structured graph database that contains structured and formatted data entries;
3. a web server that queries and exposes these data as APIs including a dashboard frontend that visualizes the socio-technical dependencies and presents active work items for software developers.

<img width="457" alt="image" src="https://github.com/hank0982/collaborative-development-experience/assets/16849947/3e7902d3-c346-422b-a23b-38a498e2480f">

### Visualization of graph database Neo4j
Below visualization is generated by Neo4J when querying a specific team and its corresponding team members and their Jira Issue.

<img width="457" alt="image" src="https://github.com/hank0982/collaborative-development-experience/assets/16849947/2b0e7a22-3f2c-4ea6-abcd-1b6f01e96201">

### Graph Schema

![graph-schema-large-font](https://github.com/hank0982/collaborative-development-experience/assets/16849947/a665158e-df54-48b9-9ce1-fe32ba84643b)

### Basic statistics of Nodes and Edges extracted from 151 engineering teams with 1,730 members

| Edge Type               | Count   | Node Types            | Count   |
|-------------------------|---------|-----------------------|---------|
| CONTRIBUTES\_TO         | 7,642   | Team                  | 151     |
| HAS\_GITHUB             | 2,508   | Member                | 1,730   |
| JIRA\_ISSUE\_ACTION     | 871,150 | PullRequest           | 32,407  |
| CREATES\_PR             | 64,740  | PullRequestReview     | 40,081  |
| JIRA\_PROJECT\_LEAD\_BY | 176     | GitHubRepository      | 1,435   |
| JIRA\_BOARD\_LEAD\_BY   | 630     | JiraBoard             | 317     |
| PULL\_REQUEST\_TO       | 64,814  | ProgrammingLanguage   | 57      |
| CREATES\_PR\_REVIEW     | 77,902  | GitHubRepositoryTopic | 142     |
| HAS\_TOPIC              | 1,698   | JiraProject           | 90      |
| BELONGS\_TO             | 1,420   | JiraIssue             | 175,838 |
| BELONGS\_TO\_PROJECT    | 351,676 | GitHubAccount         | 1,254   |
| WRITTEN\_IN             | 8,392   |
| PR\_ACTION              | 80,166  |


DISCLAIMER: This is not an officially supported SAP product.

[1] Tara Matthews, Steve Whittaker, Thomas Moran, and Sandra Yuen. 2011. Collaboration personas: a new approach to designing workplace collaboration tools. In Proceedings of the SIGCHI Conference on Human Factors in Computing Systems (CHI '11). Association for Computing Machinery, New York, NY, USA, 2247–2256. https://doi.org/10.1145/1978942.1979272
