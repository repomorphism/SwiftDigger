# SwiftDigger

Applying AlphaZero's MCTS + Deep Learning techniques to Tetris dig challenge.  This is an ongoing personal side project.

[Notebook on Google Colab](https://colab.research.google.com/drive/1h0KF2E4jErjFsNvfW21AZSwzAgN0cZ-8)

## Problem Description

Most AI work on Tetris is done using more traditional rules.  Personally I'm interested in the problem of downstacking challenge with modern Tetris rules, SRS with hold and multiple previews.

The downstacking challenge is commonly called dig race, dig challenge (as in Nullpomino), or cheese race (in [Jstris](https://jstris.jezevec10.com/)).  There are several variations of the same theme, with different numbers of fixed garbage, infinite garbage, or garbage with different shapes.

I'll mostly refer to the game mode generically as dig race.

Proficiency in dig race can be measured in different ways, most commonly real-time downstacking speed, but I'm most interested in the other metric: efficiency, as in the ratio between the number of lines cleared, vs. the number of pieces placed.  It could vary a lot between players and even between different games by the same player, and for years, the key to efficient downstacking has been a mystery to me.

For example, I consider myself not a terrible downstacker, but in Jstris 100L cheese race, I mostly use between 250~350 pieces (fluctuating wildly), while below 300 is a pretty good run for me.  Meanwhile, the top 100 least-block records on the leaderboard are all in the low 200s.

## Current State

A basic MCTS player has been implemented.  It could use a traditional field evaluation method (referencing the paper: Building Controllers for Tetris, by Thiery and Scherrer) to play pretty reasonably.  It could sometimes finish a 10-line game in 25 moves or less.  I don't feel it does better than me yet, however.

A TensorFlow model is defined, and integrated with MCTS.  However, no training has been done yet, so it can only play random moves.

## Future

The ultimate vision is to have a bot that can consistently perform better than myself in a 100L dig, using <300 pieces most of the time, hopefully getting to 250 with ease.  Best if it doesn't take too long to think and can play in real time, say at most 2~3 seconds per move.

I still need to figure out model training, but before that, I'm stuck on the problem of model saving and loading.  It seems that this part of S4TF is still under construction.



