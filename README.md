Download Link: https://assignmentchef.com/product/solved-2110215prog-final-quiz-1
<br>



<h1>1.    Instruction</h1>

<ul>

 <li>Create a Java Project named “<strong>2110215_Final_Q1</strong>”.</li>

 <li>Copy all folders in <strong>“toStudent/Q1”</strong> to your project directory src folder.</li>

 <li>You are to implement the following classes (detail for each class is given in section 2 and</li>

</ul>

3.

<ol>

 <li><strong>Ordinary</strong> (package role.derived)</li>

 <li><strong>Master </strong>         (package role.derived)</li>

 <li><strong>Seer</strong>      (package role.derived)</li>

 <li><strong>Gambler</strong> (package role.derived)</li>

 <li><strong>Player</strong> (package game.object)</li>

</ol>

<ul>

 <li>Make UML class diagram for classes in package role.base and role.derived, using ObjectAid or another UML generator program. Save its picture file in your role.derived folder.</li>

 <li><strong>JUnit for testing is in a package test.</strong></li>

 <li><strong>To submit: </strong>

  <ul>

   <li><strong>go to src folder that you actually do the coding for this question. </strong></li>

   <li><strong>Zip this question’s src folder. Name it YOUR-ID_Q1.zip (for example, 6332112121_Q1.zip) </strong></li>

   <li><strong>Submit the zipped file as an assignment on MyCourseville. </strong></li>

  </ul></li>

</ul>







<h1>2.   Problem Statement: Marble Master</h1>







In Marble Master, a group of <strong>4</strong> <strong><em>players</em></strong> is playing a game of fortune. At the start, each player initially has <strong>20 <em>marbles</em></strong>, and is randomly assigned to one of the following <strong>4 <em>roles</em></strong>: <strong>Master</strong>, <strong>Seer</strong>, <strong>Gambler</strong>, and <strong>Ordinary</strong> (every player has a distinct role and <u>does not know</u> the role of each other).

The game is played in <strong><em>rounds</em></strong>. At the beginning of each round, there are <strong>7</strong> <strong><em>cards</em></strong> to be chosen and picked up by the players. Each card has its own <u>hidden</u> value, called <strong><em>multiplier</em></strong>. The cards are placed in <strong><em>slots</em></strong>, numbered from 0, 1, 2, 3, 4, 5, 6. The <strong>Master</strong> is the one who decides where to place them; thus, only the <strong>Master</strong> knows which cards are placed in which slots. Then the players take <strong><em>turns</em></strong> to play by following some specific <strong><em>order</em></strong>, which is determined by the <strong>Gambler</strong>.

The order of playing is numbered as follows: 0, 1, 2, 3. That is, the player who takes the first turn of each round is in order number 0. For each player, when it is in his/her turn, the player chooses one of the remaining slot numbers and picks up the card in that slot. The information of the chosen card will be announced to every player, e.g., the slot number and the multiplier of that card.

However, some players have an extra action <u>before</u> playing his/her turn. Firstly, the <strong>Seer</strong> can <u>secretly</u> choose two cards to see their multiplier and <u>swap</u> them before returning them to the slots. It is possible that the card he will choose and pick up in his/her normal playing turn is not from the two cards he/she viewed earlier. Moreover, the <strong>Gambler</strong> can <u>secretly</u> choose <strong><em>two target players</em></strong>. It is possible that the <strong>Gambler </strong>may choose him/herself as one of the targets.

At the end of the round, i.e., after every player has played their turn, the <strong><em>two target players</em></strong> (chosen by the <strong>Gambler</strong>) will have to <em><u>swap their role and card</u></em>. Then every player will gain or lose some number of marbles, which is determined by the product of the multiplier and the slot number of their chosen card. The first player who successfully collects at least <strong>100</strong> marbles wins and becomes the <strong>Marble Master</strong>! If there is a <u>tie</u>, an <u>extra round</u> will be played until the tie is broken.




<h1>3.   Implementation Detail</h1>

The class package is summarized below.

<strong>* In the following class description, only details of IMPORTANT</strong> <strong>fields and methods are </strong>

<strong>given.</strong><strong>*</strong>




3.1 Package role.base

3.1.1 abstract class Role  <strong>/* ALREADY PROVIDED */</strong>

<strong> </strong>

This class is an abstract class and also a <strong>base class </strong>for <strong>all roles</strong> of Player. It contains all common actions which each role must do.










3.1.2. Interface PreRoundActable <strong>/* ALREADY PROVIDED */</strong>

<em>Method </em>

<table width="629">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="383"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">+ abstract voidpreRoundActs(GameAction action)</td>

   <td width="383">Method to take an action before entering each round.</td>

  </tr>

 </tbody>

</table>




3.1.3. Interface PreturnActable <strong>/* ALREADY PROVIDED */</strong>

<em>Method </em>

<table width="631">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="384"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">bstract void preTurnActs(GameActionction)</td>

   <td width="384">Method to take an action before entering each turn.</td>

  </tr>

 </tbody>

</table>




3.2 Package game.logic

3.2.1. class GameAction  <strong>/* ALREADY PROVIDED */</strong>

This is a wrapper class for the action’s information. The information is an array of <strong>GameObject</strong>s. The type and the length of <strong>GameObject</strong>s are dependent on the <strong>role </strong>of the player and when the action takes place (pre-round or pre-turn). For more details, see the description of each role. <em>Fields </em>

<table width="629">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="383"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">+ final int length</td>

   <td width="383">The number of GameObjects related to this action.</td>

  </tr>

  <tr>

   <td width="247">– ArrayList&lt;GameObject&gt; info</td>

   <td width="383">A list of GameObjects related to this action.</td>

  </tr>

 </tbody>

</table>

<em>Method</em>

<table width="635">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="389"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">+GameAction(ArrayList&lt;GameObject&gt; info)</td>

   <td width="389">This is the Constructor. Initialize the GameAction by setting length and info</td>

  </tr>

  <tr>

   <td width="247">+ ArrayList&lt;GameObject&gt; getInfo()</td>

   <td width="389">This method return the ArrayList of GameObject</td>

  </tr>

  <tr>

   <td width="247">+ GameObject getInfo(int slot)</td>

   <td width="389">This method return GameObject at index slot</td>

  </tr>

 </tbody>

</table>




3.2.2. class GameLogic  <strong>/* ALREADY PROVIDED */</strong>

3.2.3. class GameRound  <strong>/* ALREADY PROVIDED */</strong>




3.3 Package role.derived <strong>/* You must implement this ENTIRE package from scratch */ </strong>

3.3.1. class Ordinary <strong>/* You must implement this class from scratch */ </strong>

<strong>Ordinary</strong> is a <strong>Role</strong> with no special actions.




<em>Method </em>

<table width="641">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="395"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">+ String toString()</td>

   <td width="395"><strong>/* FILL CODES */</strong>This method return “Ordinary”</td>

  </tr>

 </tbody>

</table>













3.3.2. class Gambler <strong>/* You must implement this class from scratch */</strong>

<strong>Gambler </strong>is a <strong>Role</strong> which has to set the playing order of all the players <u>before the round</u> <u>starts</u>. Thus, the <strong>GameAction </strong>that Gambler will work on will contain <strong>4</strong> GameObjects where each <strong>GameObject </strong>is a <strong>Player</strong>. These Players are stored in the specific playing order. For example, if the GameAction contains 4 players: &lt;<strong>a</strong>, <strong>b</strong>, <strong>c</strong>, <strong>d</strong>&gt;, then <strong>a</strong> is the first player to play in this round. You have to set the order of player <strong>a</strong> as <strong>0</strong>, set the order of player <strong>b</strong> as <strong>1</strong>, and so on.

Also, <u>before playing his/her turn</u>, the <strong>Gambler </strong>has to choose two target players. The target players will have to swap their role and their card at the end of the round. For the purpose of testing, the system has already chosen the two players for you. Hence, the <strong>GameAction parameter </strong>will contain <strong>2</strong> GameObjects where each <strong>GameObject </strong>is a <strong>Player</strong>. Then, you only have to set these two players as to-be-swapped.

<em> </em>

<em>Method </em>

<table width="647">

 <tbody>

  <tr>

   <td width="281"><strong>Name</strong></td>

   <td width="366"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="281">+ void preRoundActs(GameAction action)</td>

   <td width="366"><strong>/* FILL CODES */</strong>Use this method to shuffle the order of all the players by setting each Player’s order based on the given action’s info.<u>HINT</u>:Use the method <strong>action.getInfo(i)</strong> to get the i<sup>th</sup> <strong>GameObject </strong>of this action. For each <strong>GameObject</strong>, consider it as a <strong>Player</strong>, and use the method <strong>setOrder(i)</strong> from the class <strong>Player </strong>to set the playing order of this player as <strong>i</strong>. </td>

  </tr>

  <tr>

   <td width="281"> </td>

   <td width="366"><u>Noted</u>: <strong>order</strong> starts with<strong> 0</strong> and ends with <strong>action.length-1</strong></td>

  </tr>

  <tr>

   <td width="281">+ void preTurnActs(GameAction action)</td>

   <td width="366"><strong>/* FILL CODES */</strong>Use this method to mark 2 players in the given GameAction as to-be-swapped.<u>HINT</u>:Use the method <strong>action.getInfo(i)</strong> to get the i<sup>th</sup> <strong>GameObject </strong>of this action. For each <strong>GameObject</strong>, consider it as a <strong>Player</strong>, and use the method <strong>setToBeSwapped(true)</strong> from the class <strong>Player </strong>to set this player as to-be-swapped. <strong> </strong></td>

  </tr>

  <tr>

   <td width="281">+ String toString()</td>

   <td width="366"><strong>/* FILL CODES */</strong>This method return “Gambler”</td>

  </tr>

 </tbody>

</table>




























3.3.3. class Master <strong>/* You must implement this class from scratch */</strong>

<strong>Master </strong>is a <strong>Role</strong> which has to decide where to place all the cards <u>before the round starts</u>. Thus, the <strong>GameAction </strong>that it works on will contain <strong>7</strong> GameObjects where each <strong>GameObject </strong>is a <strong>Card</strong>. These Cards are stored in the specific slot. For example, if the GameAction contains 7 cards: &lt;<strong>c4</strong>, <strong>c2</strong>, <strong>c1</strong>, <strong>c3, c5</strong>, <strong>c0</strong>, <strong>c6</strong>&gt;, you have to set the slot of card <strong>c4</strong> as <strong>0</strong>, set the slot of card <strong>c2</strong> as <strong>1</strong>, and so on.




<em>Method </em>

<table width="647">

 <tbody>

  <tr>

   <td width="281"><strong>Name</strong></td>

   <td width="366"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="281">+ void preRoundActs(GameAction action)</td>

   <td width="366"><strong>/* FILL CODES */</strong>Use this method to set the cards’ slot in the given GameAction  <u>HINT</u>:Use the method <strong>action.getInfo(i)</strong> to get the i<sup>th</sup> <strong>GameObject </strong>of this action. For each <strong>GameObject</strong>, consider it as a <strong>Card</strong>, and use the method <strong>setSlot(i)</strong> from the class <strong>Card </strong>to set the slot number of this card as <strong>i</strong>.   <u>Noted</u>: <strong>slot</strong> number start with<strong> 0</strong> and ends with <strong>action.length-1 </strong></td>

  </tr>

  <tr>

   <td width="281">+ String toString()</td>

   <td width="366"><strong>/* FILL CODES */</strong>This method return “Master”</td>

  </tr>

 </tbody>

</table>




3.3.4. class Seer  <strong>/* You must implement this class from scratch */</strong>

<strong>Seer</strong> is a <strong>Role </strong>which has to secretly choose two cards to see their multiplier and swap them <u>before playing his/her turn</u>. For the purpose of testing, the two cards are already chosen for you. Thus, the <strong>GameAction </strong>will contain <strong>2</strong> GameObjects where each <strong>GameObject </strong>is a <strong>Card</strong>. Then, you only have to swap them.




<em>Method </em>

<table width="653">

 <tbody>

  <tr>

   <td width="269"><strong>Name</strong></td>

   <td width="384"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="269">+ void preTurnActs(GameAction action)</td>

   <td width="384"><strong>/* FILL CODES */</strong>Use this method to swap 2 Cards in the given GameAction.<u>HINT</u>:Use the method <strong>action.getInfo(i)</strong> to get the i<sup>th</sup><strong>GameObject </strong>of this action, and consider it as a <strong>Card.</strong> Then, Swap them by using the method from package game.logic<strong>GameLogic.<em>getInstance</em>().getCurrentRound().swapCard s(</strong><strong>…, </strong><strong>…) </strong></td>

  </tr>

  <tr>

   <td width="269">+ String toString()</td>

   <td width="384"><strong>/* FILL CODES */</strong>This method return “Seer”</td>

  </tr>

 </tbody>

</table>
















3.4 Package game.object

3.4.1. class Card <strong>/* ALREADY PROVIDED */</strong>

Card is a GameObject that every role has to pick one and gain (or lose) marbles from it. The cards are placed in slots, numbered from 0, 1, 2, …, 6. This class contains the method which will be used in role.derived

<em>Fields </em>

<table width="641">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="395"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">– String id</td>

   <td width="395">id of the Card</td>

  </tr>

  <tr>

   <td width="247">– int slot</td>

   <td width="395">slot number of the Card (0,1,2,…,6)</td>

  </tr>

  <tr>

   <td width="247">– int multiplier</td>

   <td width="395">Each card has its own hidden value, called multiplier</td>

  </tr>

  <tr>

   <td width="247">– boolean pickedUp</td>

   <td width="395">True if the Card is picked up</td>

  </tr>

 </tbody>

</table>

<em> </em>

<em>Method </em>

<table width="641">

 <tbody>

  <tr>

   <td width="247"><strong>Name</strong></td>

   <td width="395"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="247">+ Card(String id, int multiplier)</td>

   <td width="395">This is the Constructor.Initialize the card by setting slot to -1, set id, setting multiplier, and setting pickedUp as false</td>

  </tr>

  <tr>

   <td width="247">+ String toString()</td>

   <td width="395">Return Card’s id and its multiplier Ex. [C001: -2]</td>

  </tr>

  <tr>

   <td width="247">+ String getStatus()</td>

   <td width="395">This method return only Card slot if it’s not picked up, otherwise return Card slot and its multiplier (Calling revealInfo())</td>

  </tr>

  <tr>

   <td width="247"> </td>

   <td width="395">Ex. [S0|####] or [S1| -2 ]</td>

  </tr>

  <tr>

   <td width="247">+ String revealInfo()</td>

   <td width="395">Return Card slot and its multiplier Ex.  [S1| -2 ]</td>

  </tr>

  <tr>

   <td width="247">getter/setter for all fields</td>

   <td width="395"> </td>

  </tr>

 </tbody>

</table>




3.4.2. class abstract GameObject  <strong>/* ALREADY PROVIDED */</strong>

<strong>GameObject </strong>is the abstract base class for <strong>Player </strong>and <strong>Card</strong>.

3.4.3. class Player <strong>/* You must implement some methods of this class*/</strong>

Player is GameObject. This class represents a player. It contains player information and status.  <em>Fields </em>

<table width="615">

 <tbody>

  <tr>

   <td width="317"><strong>Name</strong></td>

   <td width="298"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="317">– String name</td>

   <td width="298">The name of the player</td>

  </tr>

  <tr>

   <td width="317">– int order</td>

   <td width="298">The order to play in each round</td>

  </tr>

  <tr>

   <td width="317">– Role role</td>

   <td width="298">The role of the player in each round</td>

  </tr>

  <tr>

   <td width="317">– int marblesEarned</td>

   <td width="298">Amount of the marble that player has earned during the game. At the start, each player has <strong>20</strong> marbles.</td>

  </tr>

  <tr>

   <td width="317">– boolean toBeSwapped</td>

   <td width="298">True when the player is chosen to be swapped role with another player by the Gambler</td>

  </tr>

 </tbody>

</table>

<em>Method </em>




<table width="624">

 <tbody>

  <tr>

   <td width="276"><strong>Name</strong></td>

   <td width="348"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="276">+ Player(String name, Role role)</td>

   <td width="348">This is the Constructor. Initialize all fields of Player</td>

  </tr>

  <tr>

   <td width="276">+ void doPreRoundAction(GameAction action)</td>

   <td width="348"><strong>/* FILL CODES */</strong>This method is called to do an action before entering each round.If the player’s role has the action to do before entering each round, you have to consider the player’s role as <strong>PreRoundActable</strong>, and then call the method   <strong>role.preRoundActs(</strong><strong>…) </strong> </td>

  </tr>

  <tr>

   <td width="276">+ void doPreTurnAction(GameAction action)</td>

   <td width="348"><strong>/* FILL CODES */</strong>This method is called to do an action before entering each turn.If the player’s role has the action to do before entering his/her turn, you have to consider the player’s role as <strong>PreTurnActable</strong>, and then call the method<strong>role.preTurnActs(</strong><strong>…)</strong></td>

  </tr>

  <tr>

   <td width="276">+ int getRoundRewards()</td>

   <td width="348">Return the marbles that player’s going to receive calculated by slot number multiply by multiplier of the chosen Card</td>

  </tr>

  <tr>

   <td width="276">+ void takesRoundRewards()</td>

   <td width="348">This method set Player’s marblersEarned at the end of each round</td>

  </tr>

  <tr>

   <td width="276">+ String toString()</td>

   <td width="348">Return player’s name and his/her marblesEarned  Ex. [Anny: 20]</td>

  </tr>

  <tr>

   <td width="276">getter/setter for all fields</td>

   <td width="348"> </td>

  </tr>

 </tbody>

</table>

3.5 Package main

3.5.1 class Main <strong>/* ALREADY PROVIDED */</strong>

This class is the main program. You don’t have to implement anything in this class. You can test the program by running this class.




3.6 Package test <strong>/* ALREADY PROVIDED */</strong>

<table>

 <tbody>

  <tr>

   <td width="139"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

This package provides JUnit test for each of your class.




<h1>4.   Finished Code Run Example (this is one of possible runs)</h1>




Just run and the game logic will do everything at random. You don’t have to interact with anything after running the code.




4.1. Start the game

4.3 Pre round interface  be able to set cards’ slot and players’ order

4.4 Pre turn interface

<table>

 <tbody>

  <tr>

   <td width="96"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

Be able to view and swap the slot of the card.

Be able to swap the role and card of the players

4.5. Round summary

4.6. Game Ending

<h1>5</h1>