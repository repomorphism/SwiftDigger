# SwiftDigger

Applying MCTS to Tetris dig challenge.  This is an ongoing personal side project.

[Notebook on Google Colab](https://colab.research.google.com/drive/1h0KF2E4jErjFsNvfW21AZSwzAgN0cZ-8)

## Problem Description

Most AI work on Tetris is done using more traditional rules.  Personally I'm interested in the problem of downstacking challenge with modern Tetris rules, SRS with hold and multiple previews.

The downstacking challenge is commonly called dig race, dig challenge (as in Nullpomino), or cheese race (in [Jstris](https://jstris.jezevec10.com/)).  There are several variations of the same theme, with different numbers of fixed garbage, infinite garbage, or garbage with different shapes.

I'll mostly refer to it/them generally as dig race.

Proficiency in dig race can be measured in different ways, most commonly real-time downstacking speed, but what I'm only interested in the other metric: efficiency, as in the ratio between the number of lines cleared, vs. the number of pieces placed.  It could vary a lot between players and even between different games by the same player, and for years, it has been a mystery to me.

For example, I consider myself not a terrible downstacker, but in Jstris 100L cheese race, I use anywhere between 250~350 pieces, while below 300 is a pretty good run for me.  Meanwhile, the top 100 least blocks on the leaderboard are all in the low 200s.

## Current State

A basic single-threaded MCTS routine has been implemented, but that combined with simple evaluation did not work well for me.

To help with that, I implemented a more traditional field evaluation as in the paper, Building Controllers for Tetris, by Thiery and Scherrer.  Evaluation functions like this were not originally intended to be used in MCTS, but it does seem to greatly help my MCTS.

There are a few places I could tune here and there, but at the moment I don't have a solid idea of what works best.

The downstacking performance is occassionally excellent, other times not so much, on average I'd say it is still quite a bit worse than myself.

## Future

The ultimate vision is to have a bot that can consistently perform better than myself in a 100L dig, using <300 pieces most of the time, hopefully getting to 250 with ease.  Best if it doesn't take too long to think and can play in real time, say at most 2~3 seconds per move.

To get there, I'd like to try the AlphaZero approach, i.e. deep reinforcement learning.  Things to do include:

- Tighten loose ends, e.g. allow SRS twist moves, code organization
- Learn to implement a combined value & policy network, using Swift for TensorFlow
- Make MCTS parallelizable, using virtual loss to allow selecting multiple positions to evaluate in one batch
- Devise a scheme that is as light as possible in terms of human domain knowledge, yet possible for the algorithm to converge
- Try things out, work out challenges like data management and computation resource
- Learn more about reinforcement learning


