# Things I learnt for software engineering

1. System design 

***See backend notes in my repositories***

2. Test

Various types of tests:
- Unit test 
- Integration tests
- Widget tests
- End-to-end (E2E) tests
- User Testing (As opposed to the above automated testing)

**Unit testing** involves testing one individual piece of our code, such as a single function or a class, at a time. Unit tests are fully isolated and check that given an input, the output is what we expect it to be. The tests examines the reliability, quality, and logic of the function/method written. Aim is to check if the piece of code mathces its functionality and for pure functions, no side-effects is produced.

**Integration tests** focus on how the different functions written in a program interact with one another, which involves dependencies. Most of the time this testing involves not just functions, but also how the program interacts with the database and server. Usually they have a more complicated set up. 

**Widgets tests** are known as components testing, which tests how widgets interact with each other. This ensures the action, reaction and functionalities of the widgets used remains _predictable_. 

**E2E tests** look at the full flow of the code and imitates a real user experience. This involves looking at DOM manipulation based on what a user does on the screen. The process may still be automated (computer doing the test). 

Unit tests are less complicated, follow by integration/widgets testing (_tho some defines integration testing to be more complicated_), and E2E as the most complicated type of testing. 

For JS, we can use Jest, the testing framework, to write our tests. 

User testing involves working with personnels whose criteria meets the target audience and allows them to actually use the application. User testing is the process of having end users test and evaluate the product or feature. This testing is not automated and usually involves the interaction between a real user and the machine. A good guideline for user testing is the [seven questions postulated by Don Norman](https://uxdesign.cc/ux-psychology-principles-seven-fundamental-design-principles-39c420a05f84), which aims to enhance user interactability. Borrowing some insights from a [senior's work](https://drive.google.com/drive/u/1/my-drive) which flowed from that of Norman, the seven principles are essentially:
> 1. Discoverability: Allows the user to understand where to perform actions. 
> 2. Conceptual Models: Are simple explanations of how something works.
> 3. Affordance: Refers to the perceived properties of an object.
> 4. Mappings: Are the relationships between the controls and their effects.
> 5. Signifiers: Tell the user exactly where to perform an action.
> 6. Constraints: Restrict the interactions that can take place.
> 7. Feedback: Communicates the response of a user’s action.

Source/Reading:
- https://medium.com/swlh/testing-in-javascript-aa32e51d55ec
- Jest testing for JS: https://jestjs.io/
