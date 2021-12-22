# QuintrisAI

## Simple

### Successor function creation

For successor function, I started with a simple logic which was rotating the piece in each possible rotation(with and without horiontal flip) and placed it on the board. Then, I calculated the cost of the those boards using a myriad of evaluation functions such as counting holes, blocks above the hole ,column height difference, empty columns and full rows completed. Using these, I took the minimum cost state and played my moves.

Then I tried to implement expectimax but it was taking a considerable amount of time to return the optimal move so I decided to modify my greedy approach I mentioned above instead. One modification I made was after placing the current piece on the board, instead of calculating the cost of the current piece, I called a `Successor()` to generate successors and calculated the cost for the next piece. Then, I returend the minimum cost value and considered the `move_string` with the lowest cost value.   

## Animated

### Successor function creation

For animated version, I have used greedy approach considering each rotation, hflip and rotation and calculating the cost and placing it where the cost is lowest. Before this, I was using the same approach I was using for simple version. While it was running fine on my local machine, it was taking quite a lot of time to run on Silo so I was not able to get the optimal placement of the piece before it hit the board. So I revert it back to the one I mentioned. I have used the same evaluator functions for animated version as I did for simple version. 

### Evaluation functions

1) Counting holes created: here I was checking if there were any 'x' surrounding empty blocks, and when I find these empty holes, I add them to cost function.
2) Counting Column height difference: Calculating the column height heights and taking `max() - min()`
3) Almost Game over cost: Assigned a large cost if the column height was greater than (board height - 1)
3) Full rows completed: Subtracted a substantially large value from total cost if one row was getting completed to encourage the given move
4) Empty Columns: I noticed that my pieces were being placed around one corner in the beginning of the game so to avoid that, I added a small cost for each empty column found in the board
5) Blocks above empty holes: I analyzed that there were a lot of empty holes getting created so I wanted to add substantial cost when pieces were placed on top of the empty blocks
