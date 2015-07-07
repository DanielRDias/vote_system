# Vote System

The vote system is an application that allows for participants vote on a
proposal with time limit. The objective is to promote progress when a group of
participants do not seem to agree on something. The time limit should not
mandatory but it is recommended to avoid abstention on purpose.

## Design

A proposal contains a title, description and available options. A title is a
summary of the proposal and should transmit clearly in few words what the
proposal is about. The description are the details of the proposal and should
tell give the advantages and disadvantages of each option. The options are the
possible choices that each participant can make in a proposal. For example:

 * Title: "Red or Green?"
 * Description: "Should we paint our car in red or green? Green promotes calm
   feelings but also envy. Red promotes aggressive nature but also courage."
 * Options: "Red" or "Green"

A participant is any entity that can vote on a proposal. Each participant must
have a unique identifier (e.g., email) and can only vote on one choice. If the
time limit ends, the participant cannot vote anymore.

When the time limit reaches the end each participant is informed of the voting
results.

## Implementation

The initial implementation should be fully local and terminal based. That way
the focus is the core itself, not the interface or network mechanism.


An administrator is allowed to register users on the terminal, as such:

    > register <name> <email>

Each user can then login:

    > login <email>

For now there is no security. A user can create a proposal and then will be
asked to fill the proposal data:

    > create proposal

    Input the title:
    Red or Green?

    Input the description:
    Should we paint our car in red or green? Green promotes calm feelings but
    also envy. Red promotes aggressive nature but also courage.

    Options:
    Red
    Green

    Time limit:
    24h

    Proposal #1 created.

Afterwards the user may invite participants, including himself:

    > invite <user> <proposal_id>

Each participant can then vote:

    > list proposals

    1) Red or Green?

    > show 1

    Title:
    Red or Green?

    Description:
    Should we paint our car in red or green? Green promotes calm feelings but
    also envy. Red promotes aggressive nature but also courage.

    Options:
    1) Red
    2) Green

    Time left:
    23h30
      
    > vote 1 2

    Successfuly voted "Green".

After the time ends, each participant is notified when logins:

    > login <user>

    Hello <user>. Proposal <proposal_id> finished.
