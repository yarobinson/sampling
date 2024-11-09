# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 1000 (from the original 50000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Yasmine Robinson

```
Question 1: At what stages did sampling occur?

Sampling occurred three times within the model: first, during the stage where a random subset of attendees was chosen to be infected; then, during the primary contact phase, where infected people are traced; and finally, during the second contact tracing, which is based on event attendance.

Question 2: What is the sampling procedure for each stage?

Random subset of attendees - Using np.random.choice along with the attack rate of 10% of attendees are randomly selected to be infected
Primary contact phase - Among the 10% randomly chosen to be infected, 20% are successfully traced to a source event (Trace_Success)
Second contact tracing - Based on event size and if an infected person is already identified at the event, secondary tracing is completed on source events with at least two infections (

Question 3: What is the sample size for each stage?

Random subset of attendees - 10% of the 1000 attendees across both events (100)
Primary contact phase - 20% of the infected attendees that are successfully traced (20)
Second contact tracing - Any infected attendees who attended an event where 2 or more people were infected and the infected attendees are fully traced

Question 4: What is the sampling frame for each stage?

Random subset of attendees - Attendees of brunches and weddings
Primary contact phase - Identified infected attendees of the brunches and weddings
Second contact tracing - Attendees who attended an event where 2 or more people were infected

Question 5: How do the above answers relate to the procedure used in Whitby's blog post?

Sampling procedures were pulled from Whitby's procedure in the blog post. Our code utilized random 10% infection of attendees, 20% successfully traced infections and the threshold for second contact tracing. Taking these sampling procedures allows us to replicate Whitby's model as closely as possible. 

Question 6: Does the original code reproduce the graphs in Whitby's blog post?

Yes, the code reproduces graphs similar to the one in Whitby's blog post. The graphs produced through our Python code show that more cases are traced to weddings than have occurred. Proving Whitby's theory that contact tracing can give a biased view of the actual infections that have occurred. 

Question 7: After changing the repetitions to 1000, what is the reproducibility of the results?

While the overall graph still shows that more cases are traced to weddings than have occurred. There are slight differences in the graph using 5000 repetitions vs 1000 repetitions (shape, distribution, etc). The difference in the graph due to the number of repetitions could signify limited reproducibility of our results. 

Question 8: What changes can be made to the code to make it reproducible and how does this affect the reproducibility?

To make our code more reproducible, we can set a random seed which will run along with each of our repetitions.

For example, np.random.seed(seed number) can be used to ensure that the random sampling for infection and tracing returns the same results every time despite the number of repetitions. 

This change will make our results more stable even if the number of repetitions changes. It will not completely replicate Whitby's graph but will still show the bias of contact tracing. 

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
