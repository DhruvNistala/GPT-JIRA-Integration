# GPT-JIRA Integration

## Introduction
-  GPT-JIRA Integration is an app designed listen in during standup meetings, detect any discussions relevant to JIRA board, and make updates accordingly. The intention is for the updates to happen automatically while keeping the flow of conversation seamless.

- This project is a tool created by the Alpha Dev Interns in Summer 2023. It is by Dhruv Nistala and Parth Patki.

## Objective 
- During standup meetings, a lot of time is spent updating JIRA boards. Also, some inaccuracies may result due to the high volume of tasks.

## Implementation/Workflow Structure
- 
    1. Voice Classification
        - Run the classifier, which uses WhisperAI and embeddings libraries, to train a model on the voices of the members of the standup meeting.
    2. Speech Processing
        - Using WhisperAI, the script transcribes the meeting audio and using the pretrained classifier, labels the speakers on the transcript.
    3. JIRA Context Retrieval
        - Using some functions for the JIRA API, the script receives information about the context of the JIRA board at the present time.
    4. GPT Interpretation
        - Using the contexts obtained by the speech processing and JIRA API, GPT determines whether an update to the JIRA board is warranted given the current state and discussions taken place in standup meeting.
    5. JIRA API Output
        - Using the conclusions of GPT, a file called updates.py is created and running it will update the JIRA board accordingly.

# Running the workflow

- The file requires 3 things: assigneeId.txt, containing the assignee Ids of each member. It also requires Recording.mp4, which is a recording of the standup meeting. Finally, it contains a voice classifier that is pretrained using the voices of the members of the standup meetings.

# Limitations

- Currently, due to computational limitations, the workflow does not run real-time during standup meetings; instead, an mp4 of the meeting should be fed in as input. Ideally the script should be modified to interpret the part of the meeting that has been heard so far and re-listen and interpret after some more intervals.

- The updates.py file must automatically be run each time the scipt is finished running.
