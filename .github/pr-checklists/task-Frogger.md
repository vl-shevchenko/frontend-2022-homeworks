## Frogger Arcade Game -- JS OO exercise check list

_Relates to [Object-Oriented JavaScript](https://github.com/kottans/frontend/blob/master/tasks/js-oop.md) task._

## Check-list - definition of done

* [ ] employ ES6 features like `const`, `let` etc. (with exclusion of ES6 `class` syntax)
* [ ] the code is very [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

* Requirements re **Constants**:
    * [ ] all numbers like block dimensions, initial locations are defined as named constants (e.g. `const STEP = 101;`) as otherwise numbers scattered across code base look cryptic; named constants add semantic meaning and improve readability
    * [ ] every number that has a semantic purpose (like those listed above) should be defined as constants; think of how your code **reads** - the closer to plain English the better
    * [ ] there are core constants and derived constants
      (e.g. derived constant `const FIELD_WIDTH = BLOCK_WIDTH * BLOCKS_NUMBER;`)
    * [ ] arrays of constants are also constants
      (e.g. `const INITIAL_POSITIONS = [1,2,3,4].map(rowNumber => rowNumber * BLOCK_HEIGHT);`)
    * [ ] const objects help organizing and structure const data even better
      (e.g. `const PLAYER_CONF = { initialPosition: {x: 1, y: 5}, sprite: '...', ...etc... };`
 
* Requirements re **OOP**:
    * [ ] OO is implemented using **JS prototype chain object model** (**not** ES6 classes syntax)
    * [ ] classes do not refer to any global variables, like global variable `player`, which is an instance of `Player` class
      (referring to global constants and globals provided by the gaming platform like `Resources` is OK);
      Hint: pass `Player` instance as an argument to every enemy
    * [ ] Separation of Concerns principle is followed
      (e.g. `update` method does only rendering and doesn't contain any unrelated **inline** code; for example collision check is defined as a dedicated method and only called from inside `update`)
    * [ ] Nice To Have: properties common for some classes are generalized into a base class
      (e.g. there is `Character` base class, which is extended by `Enemy` and `Player` classes)
    * [ ] class extension is implemented using `Subclass.prototype = Object.create(Superclass.prototype)`, not `Subclass.prototype = new Superclass(params);`; [Helpful resource](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* Most common mistakes
    * [ ] Make sure `target = condition ? valueWhenConditionTrue : valueWhenConditionFalse` is used instead of `condition ? target = valueWhenConditionTrue : target = valueWhenConditionFalse`; [Conditional (ternary) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
