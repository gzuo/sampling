# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Qingfeng(George) Zuo

```
Please write your explanation here...


### 1
Stage 1 - Event Simulation
Sampling Frame: The entire population attending events, divided into 200 attendees at weddings and 800 at brunches.
Sample Size: 1000 people (200 at weddings, 800 at brunches).

Stage 2 - Infection Assignment
Procedure: Randomly infect 10%(ATTACK_RATE) of the population.
Underlying Distribution: Binomial distribution, where each individual has a 10% chance of being infected.

Stage 3 - Primary Contact Tracing
Procedure: Randomly determine which infected individuals are successfully traced with a 20%(TRACE_SUCCESS) success rate.
Underlying Distribution: Binomial distribution, where each infected individual has a 20% chance of being traced.

Stage 4 - Secondary Contact Tracing
Procedure: If at least 2(SECONDARY_TRACE_THRESHOLD) infections are traced back to the same event, trace all infections from that event.
Sampling Frame: Events where primary tracing identified at least two infections.

### 2
The outcome of running 'whitby_covid_tracing.py' is different from the graphs in the original blog post.

### 3
In comparing the data in props_df between 1000 and 50000 repetitions as following, it looks the first 1000 rows are the same. 
My understanding is that since we have set the random seed for reproducibility (np.random.seed(10)) so the outcome would be the same every time I run it.


	Infections	Traces
0	0.18	0.012048
1	0.26	0.260000
2	0.13	0.130000
3	0.18	0.180000
4	0.17	0.170000
...	...	...
995	0.20	0.200000
996	0.29	0.290000
997	0.19	0.190000
998	0.23	0.230000
999	0.20	0.200000
1000 rows × 2 columns


	Infections	Traces
0	0.18	0.012048
1	0.26	0.260000
2	0.13	0.130000
3	0.18	0.180000
4	0.17	0.170000
...	...	...
49995	0.29	0.290000
49996	0.15	0.150000
49997	0.16	0.011765
49998	0.17	0.170000
49999	0.26	0.260000
50000 rows × 2 columns


### 4
When I remove the code of setting random seeds, the data in props_df is different every time I run the code. 
The followings are the data in props_df of running the code 3 times with 1000 repetitions.  The outcomes are different every time I run the code.
Once I set the random seeds to 10 again, the result got back to the same as before.


1st time
	Infections	Traces
0	0.30	0.300000
1	0.17	0.170000
2	0.12	0.011236
3	0.21	0.012500
4	0.22	0.220000
...	...	...
995	0.25	0.250000
996	0.18	0.180000
997	0.18	0.012048
998	0.17	0.170000
999	0.22	0.220000
1000 rows × 2 columns

2nd time
	Infections	Traces
0	0.18	0.180000
1	0.22	0.220000
2	0.22	0.220000
3	0.13	0.000000
4	0.21	0.210000
...	...	...
995	0.18	0.180000
996	0.18	0.012048
997	0.23	0.230000
998	0.25	0.250000
999	0.22	0.220000
1000 rows × 2 columns

3rd time
	Infections	Traces
0	0.22	0.220000
1	0.18	0.012048
2	0.20	0.200000
3	0.18	0.180000
4	0.25	0.250000
...	...	...
995	0.18	0.180000
996	0.22	0.220000
997	0.15	0.011628
998	0.19	0.190000
999	0.24	0.240000
1000 rows × 2 columns




```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `HH:MM AM/PM - DD/MM/YYYY`
* The branch name for your repo should be: `sampling-and-reproducibility`
* What to submit for this assignment:
    * This markdown file (sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `sampling-and-reproducibility`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
