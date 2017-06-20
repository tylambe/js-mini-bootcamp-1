# Part V: Variables

Before getting started, make sure that you have a JavaScript console open (like <a href="http://www.repl.it/languages/javascript" target="_blank">repl.it</a>), so you can complete these exercises.

## Exercises

### Basic Requirements

1. Fix each of the following variable declarations in a console -- some are
   syntactically invalid, some are disobey style guidelines, and some are just
   weird.

   ```js
   var "animal" = "monkey";
   var "monkey" = animal;
   var x= 15;
   var y =10;
   var var = "huh?";
   var true = false;
   var isTenEven = 10 % 2 = 0;
   ```

2. Perform the following in the console:

   + Create a variable `firstName` and assign your first name to it.
   + Create another variable, `lastName`, and assign your last name to it.
   + Have a middle name? If so, repeat the process.
   + Now, create a variable `fullName` and assign your full name to it by using
     the above variables.

3. For each of the following code blocks, **use a whiteboard (or a piece of paper)** to reason about
   what the value of `x` is supposed to be on the last line. Once you have
   arrived at a conclusion that you are comfortable with, enter the lines into a
   console and check your answer. Was your hypothesis correct? If not, ensure
   that you understand why (talk with a classmate, or ask for help).

   ```js
   var x = 5;
   x + 10;
   x; // => ???
   ```

   ```js
   var x = 17;
   x = (x + 1) / 2;
   x * 4;
   x; // => ???
   ```

   ```js
   var x = 5;
   var y = 20;
   x = y;
   y = y + 7;
   x; // => ???
   ```

   ```js
   var x = 10;
   var y = 5;
   x = (x * 4) - 3;
   x + 17;
   x = x + y;
   x; // => ???
   ```

4. Write a function called `counter` that, when invoked, always returns a number
   that is *one more* than the previous invocation. For instance:

   ```js
   function counter() {
     // TODO: your code here
   }
   counter(); // => 1
   counter(); // => 2
   counter(); // => 3
   // etc.
   ```

   **HINT:** You'll need a variable for this. *Where* should the variable be
   declared?

### More Practice

**All of the following exercises involve augmenting the `guessMyNumber` function.**

1. In a previous module you wrote a function called `guessMyNumber` that
   simulated a guessing game: the idea is that the function picks a random
   number between `0` and `5`, and you invoke the function with your guess -- if
   you and the function are thinking of the same number, you win! Otherwise, the
   function informs you that your guess was incorrect. A version of this game
   might look like this (the `randInt` function is included for convenience):

   ```js
   function guessMyNumber(n) {
     if (n > 5) {
       return "Out of bounds! Please try a number between 0 and 5.";
     } else if (n === randInt(5)) {
       return "You guessed my number!";
     }
     return "Nope! That wasn't it!";
   }

   function randInt(n) {
     return Math.floor(Math.random() * (n + 1))
   }
   ```

   Read and test both of the functions in your console and
   affirm that you understand how they work; then, answer the following
   questions:

   + At present, the guess should be between `0` and `5`. We can think of `5` as
     the *upper bound* of the guess. How many times is the *upper bound*
     repeated? What if we wanted to change the upper bound to `6`? How many
     changes would be required?
   + Create a variable called `upperBound` to hold the upper bound, and then
     reference **it** instead of the number `5`. If you were asked to change the
     upper bound to some other number (*e.g.* `7`), you should only have to make
     *one* change.
   + Modify `guessMyNumber` so that if the guess is incorrect, `guessMyNumber`
     includes the correct guess in its output, *e.g.* `"Nope! The correct number
     was: X"` (where `X` would have been the correct number).

2. At present, the guessing game picks a new random number every time it is
   "played" (invoked). Now that you know how to make information *persistent*
   between function invocations, change the guessing game so that it picks a
   random number **once** and allows you to guess until you get the correct
   answer.

3. It would be really cool if, after the answer was guessed, the message
   included the number of guesses it had taken to find the answer; for example,
   "You guessed my number in 3 guesses."

   + **Tangent Problem:** What happens if you get the number right on the
     first try? Does it say, "You guessed my number in 1 guesses."? If so,
     perhaps the wording should be different? Some better ideas are:

     + "You guessed my number in 1 guess."
     + "Congratulations! You guessed my number on the first try!"

4. Implement a way to **limit** the number of guesses that can be made so that a
   player loses after exceeding the limit.

5. Keep track of a **high score** (the lowest number of guesses) between games,
   and, when the correct number has been guessed in a record number of times,
   include in the message something that indicates that a new high score has
   been set.

6. Whenever a player wins, **increase the difficulty** by increasing the
   `upperBound`; whenever a player loses, **decrease the difficulty** by
   decreasing the `upperBound`.

7. Implement a **high/low hinting system** to tell the the user that the guess
   is either too high or too low. You may want to increase the `upperBound` on
   the guess.

### Advanced

There is an optimal way to play this game that works like this, given
*upperBound* as the upper bound, *lowerBound* as the lower bound, and *guess* as
the guess:

1. Initialize the starting values:

   - *guess* as half of the *upperBound*
   - *lowerBound* as 0

2. Execute *guessMyNumber* with *guess*:

    + If the guess was **too high**, repeat (2) where:
      - the new *guess* is half of the difference of *guess* and *lowerBound*
      - the new *upperBound* is *guess*
    + If the guess was **too low**, repeat (2) where:
      - The new *guess* is half of the difference of *upperBound* and *guess*
      - The new *lowerBound* is *guess*
    + If the guess was **correct** stop.

**Your task** is to write a function that implements the above algorithm
to play the game on your behalf. The first thing that you will need to
do is create another version of `guessMyNumber` that returns output that
will be easier for another function to work with, *e.g.* use `1` for too
high, `-1` for too low, `0` for correct.

Relative to *upperBound*, how many guesses does it take on average to
guess correctly?

Some recommendations:

  + Make use of a whiteboard.
  + Play the existing game yourself using the above steps to get an
    idea of how the algorithm works.
  + Work with a partner.
  + Read about `console.log` on
    [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Console/log)
    and use it to help with debugging.
