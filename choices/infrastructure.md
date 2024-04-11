# Focus: Infrastructure

This choice focuses on infrastructure. After reading through the background and scenario below, please implement a solution to the prompt that follows.

The programming language we prefer you use is: **JavaScript**. You may use any open sourced materials you'd like.

## Background

When we run interactive online network experiments, we often recruit a group of participants to synchronously complete a sequence of tasks together over a fixed duration of time. These tasks may be at the level of individuals (e.g., filling out questionnaires), dyads (e.g., two-person chat), or groups (e.g., collaborative document editing). However, before participants can begin an experiment’s tasks, we must (a) have a minimum number of participants to join the experiment, then (b) randomly assign them to network positions (nodes). Depending on the experiment, we manipulate which network ties (edges) exist between different participants over time.

## Scenario

We want to run an experiment with a 6-person network where every participant completes a sequence of two unique 5-minute-long dyadic conversations. At least 6 participants must be available at the time of starting an experiment. We then must assign exactly 6 participants to positions in a predefined network structure where each participant is tied to two other participants—each tie results in a dyadic conversation. Once assigned, participants complete their first 5-minute conversation with their first-tie partners; then, they complete their second 5-minute conversation with their second-tie partners. Unfortunately, we are beholden to all 6 participants staying in the experiment for both conversations over the full 10 minutes, which doesn’t always happen. Participant attrition is commonplace, and we need a way to make sure that participants always have a conversation partner—if someone drops out before the first conversation ends, they must be replaced by another participant before the second conversation starts. How do we handle participant replacements before the second conversation starts?

## Prompt

Suppose we recruited 8 participants who are waiting in a lobby to join an experiment. We have a [list of those participants](#participants), including unique alphabetical identifiers A, B, …, G, H and the time they were created. To start the experiment, we need to randomly select and assign participants to a predefined lattice network with 6 nodes and 6 edges, where each node is connected to only two unique others. This structure enables an experiment that includes two “rounds” (labeled 0 and 1) of three unique dyadic conversations in each.

**Your task is to implement a collection of methods that enable a complete experiment to run even when one of the participants drops out in the first round of conversations**. You should try to accomplish the following in your solution:

1. Select the 6 earliest-created participants from the lobby and randomly assign them to positions in the network, using the nodes as defined in the [network data structure](#network-structure) below. (This is similar to the output of [NetworkX](https://networkx.org/documentation/stable/) graph generators that we use to model more complex network structures for our experiments.)
2. Split the rounds of conversation into separate objects that demonstrate (a) which participants are in that round and (b) who their conversation partners are.
3. Remove a participant at random from the first round so only five positions are filled in the network.
4. Replace the removed participant with the earliest-created participant remaining in the lobby in the second round of conversations.
5. Return data for the experiment showing which participants had conversations in each round and with whom.

### Participants

```json
[
    {
        "id": "A",
        "created_at": "24-04-10T17:41:40.122225Z"
    },
    {
        "id": "B",
        "created_at": "24-04-10T17:42:03.651453Z"
    },
    {
        "id": "C",
        "created_at": "24-04-10T17:41:20.033491Z"
    },
    {
        "id": "D",
        "created_at": "24-04-10T17:42:04.949927Z"
    },
    {
        "id": "E",
        "created_at": "24-04-10T17:41:21.333795Z"
    },
    {
        "id": "F",
        "created_at": "24-04-10T17:41:06.274596Z"
    },
    {
        "id": "G",
        "created_at": "24-04-10T17:41:52.891564Z"
    },
    {
        "id": "H",
        "created_at": "24-04-10T17:41:26.043611Z"
    }
]
```

### Network Structure

```json
{
  "nodes": [
    {
      "id": 0
    },
    {
      "id": 1
    },
    {
      "id": 2
    },
    {
      "id": 3
    },
    {
      "id": 4
    },
    {
      "id": 5
    }
  ],
  "links": [
    {
      "source": 0,
      "target": 1,
      "round": 0,
    },
    {
      "source": 0,
      "target": 5,
      "round": 1,
    },
    {
      "source": 1,
      "target": 2,
      "round": 1,
    },
    {
      "source": 2,
      "target": 3,
      "round": 0,
    },
    {
      "source": 3,
      "target": 4,
      "round": 1,
    },
    {
      "source": 4,
      "target": 5,
      "round": 0,
    }
  ]
}
```
