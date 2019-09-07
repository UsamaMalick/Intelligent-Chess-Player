# Intelligent-Chess-Player
Artificial intelligent Chess Player was build using Heuristics
Evaluation Functions Explored
1.	Material
2.	Piece square table
3.	Mobility
4.	Pawn formation
5.	Development

Material
Material equalization is a record of which pieces are on the board for each side. a ruler might be worth 900 points, a rook 500, a minister 325, a knight 300 and a pawn 100; the lord has vast esteem. Processing material equalization is in this manner a basic issue: a side's material esteem is equivalent to	

MB = Sum( Np * Vp )
Where Np is the quantity of bits of a specific sort on the board and Vp is that piece's esteem. Their corresponding piece number multiplies each piece value, and then we make a summation for all the products to get the material value of one side player. We give each kind of piece a weight to tune their material value.
On the off chance that you have more material on the board than your rival, you are fit as a fiddle. Controlling more squares than the opponent at the end of the game to win, but it is often better to limit his options by having as few pieces on the board as possible during the middle game.


Piece Square Table:
Piece Square Tables: The piece square tables is a two dimensional array, say PSQ[13][64]. For each kind of piece on each square, there is a corresponding value to describe the degree that a piece prefers to be placed to a square. Typically, this numbers are all less than 100. For example, king is encouraged to be stay in middle of the board rather than being at the board edge, because it will reduce the mobility of king, especially in ending games. Also, We give each kind of piece a weight to tune their PSQ value.
Mobility:
One of the characteristics of checkmate is that the victim has no legal moves left. Intuitively, it also seems better to have a lot of options available: a player is more likely to be able to find a good line of play if he has 30 legal moves to choose from than if he is limited to 3. In chess, mobility is easily assessed: count the number of legal moves for each side given the position, and you are done. However, this statistic has proven to be of little value. Why? For one thing, many chess moves are pointless. It may be legal to make your rook patrol the back rank one square at a time, but it is rarely productive. Still, a few sophisticated mobility evaluation features are always a good thing. This program penalizes "bad bishops" whose movement is hampered by a large number of pawns on squares of the same color, as well as knights sitting too close to the edges of the board.

Pawn Formation:
Chess grandmasters often say that pawns are the soul of the game. While this is far from obvious to the neophyte, the fact that great players often resign over the loss of a single pawn clearly indicates that they mean it! Chess literature mentions several types of pawn features, some valuable, some negative. My program looks at the following:
•	Doubled or tripled pawns. Two or more pawns of the same color on the same file are usually bad, because they hinder each other’s movement.
•	Pawn rams. Two opposing pawns "butting heads" and blocking each others forward movement constitute an annoying obstacle.
•	Passed pawns. Pawns, which have advanced so far that they can no longer be attacked or rammed, by enemy pawns are very strong, because they threaten to reach the back rank and achieve promotion.
•	Isolated pawns. A pawn, which has no friendly pawns on either side, is vulnerable to attack and should seek protection.
•	Eight pawns. Having too many pawns on the board restricts mobility; opening at least one file for rook movement is a good idea. A final note on pawn formations: a passed pawn is extremely dangerous if it has a rook standing behind it, because any piece that would capture the pawn is dead meat. My program therefore scores a passed pawn as even more valuable if there is a rook on the same file and behind the pawn.

Development:
This feature tells us the development of minor pieces in the opening games. We know that in the opening, a chess player should try to move the minor pieces and pawns to capture more territory and also prepare for moves of heavy piece in the middle games. First, it penalizes any position in which the King's and Queen's pawns have not moved at all. It also penalizes knights and bishops located on the back rank where they hinder rook movement, tries to prevent the queen from moving until all other pieces have, and gives a big bonus to positions where the king has safely castled (and smaller bonuses to cases where it hasn't castled yet but hasn't lost the right to do so) when the opponent has a queen on the board. the development factor is important in the opening but quickly loses much of its relevance; after 10 moves or so, just about everything.

Our Evaluation Function
On start of the game our evaluation function will choose randomly from predefined opening strategies. 
•	Ruy Lopez
1. e4, e5; 2. Nf3, Nc6; and 3. Bb5.

•	Italian Game
1. e4, e5; 2. Nf3, Nc6; and 3. Bc4.

•	Sicilian Defense
The Sicilian defense (1. e4, c5) is black's most popular response to e4, especially at the highest levels of chess. By playing c5, black immediately fights for the center and attacks d4 but avoids the symmetry of e5.

•	French Defense
The French defense (1. e4, e6) concedes central space to white and limits the scope of his king's bishop but prevents tactics against f7 while allowing black to have activity on the queenside and counter play in the center. After the most typical line of 2. d4, d5, white's "e" pawn is immediately pressured, and white must decide how to deal with this.

After 3-5 moves we will start using piece square table evaluation function.
