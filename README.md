# lt
Spaced repetition shell scripts based on the SM2 algorithm (it's old but it works (for me)).

## Usage

Clone this repository, write your flashcards then simply run `./lt <deck>` to study flashcards in `<deck>`. Files containing flashcards (decks) must have the following structure:

```
<question>;<answer>;<e-factor>;<repetition-date>;<repetition-number>;<current-interval>
<question>;<answer>;<e-factor>;<repetition-date>;<repetition-number>;<current-interval>
<question>;<answer>;<e-factor>;<repetition-date>;<repetition-number>;<current-interval>
.
.
.
```

as you can imagine each line represent a flashcard and some information about it. To add a flashcard just substitute `<question>` and `<answer>` accordingly and give the other fields the standard values as in the following example:

```
Definition of a fiel;A field is a commutative division ring;2.5;mm-dd-yyyy;1;0
```

usually you'll want to substitute `mm-dd-yyyy` with today's or tomorrow date but if you're making flashcards in advance you can also schedule them for later my writing a future date. You should not put any line that is not of the above format in a deck file nor use the `;` character in your questions or answers. **If you do not respect those simple rules lt will probably fail potentially deleting part (if not all) of your flashcards** thus is good practice to back up your decks.

### Using cram
In the spirit of spaced repetition lt does not allow you to study again your deck if no card is scheduled for the current day but sometimes a cram session is needed. To run a cram session on a deck you can use the cram script. By running `./cram <deck>` it will allow you to review all the flashcards in `<deck>` ignoring their scheduled dates. cram also does not collect nor update flashcards data and thus do not require you to score your review.

## Known bugs and strange "features"
* lt does not allow you to quit a session nor saves any progress to the deck file until the session is over. If you quit from lt for any reason it is possible to recover the lost progress in the `/tmp/tmpdeck` file and merge them back into the deck file.
* running more than one instance of lt will probably mess up your decks since lt saves progress in temporary file `/tmp/tmpfile`
* if you're manually editing your decks do not expect them to be well-ordered; lt literally shuffles them every time

## TODO
* [ ] add functionality to add flashcards to a deck without having to operate the deck file directly
* [ ] merging cram into lt and make it available with an option