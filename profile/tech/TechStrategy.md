
## High level goals


- Minimize dependencies on 3rd party cloud providers such as AWS, Azure, or Google Cloud Platform.
- Use open source technology when possible.
- The platform should use the [ActivityPub](https://activitypub.rocks/) protocol.
- Minimize the number of libraries or frameworks that are dependencies.
- All code is written by a developer without the help of generative AI tools.
- AI should not be used to support any website functionality such as a group search.

## Key priorities to consider when implementing changes.


To support the goal of encouraging more in person interaction, the following things should be prioritized

### Focus on the long term over taking shortcuts.

While taking shortcuts might help productivity in the short term, it is likely to be detrimental in the long term. Shortcuts
can create significant amounts of technical debt that causes long term challenges in terms of adding new features or fixing
bugs.

Shortcuts can also affect learning. People working on this project should be developing skills to write good software and not
just focus on getting things done. Good software means something that is well-designed from a technical perspective. It also
means providing a good user experience. For the purposes of this platform, this means making it easy for users to use it 
to find in person events, and make connections that allow them to independently schedule their own events.

However, there should be a limit. For example, programming the entire website in assembly code would be great for learning 
how a computer works and how memory is managed. However, programming in assembly language would make the website take a 
very long time and add a significant amount of complexity to development. Also, the fact that assembly requires writing
more code would mean additional bugs and maintenance would be more difficult.


### Prioritize user experience.

 - User experience will be very important. In addition to regularly asking users for feedback, the following metrics should be used.
   - All user actions on the website generate a visual response within 100 milliseconds.
   - If a user action is going to take more than 100 milliseconds to resolve, then a loading indicator should be shown.
 - User actions should not take more than 100 milliseconds to show a result when no API call is necessary.
 - Users should be encouraged to make decisions on their own about events they should attend. As a result, suggested groups or events will not be presented.
   Users will be able to search for events by time, location, or by using tags associated with an event. Every user who uses the same search query will 
   see the same results instead of attempting to customize results based on user activity on the site.

### Minimize tech debt

#### Reasons why minimizing tech debt is important

- Less tech debt->Costs don’t rapidly increase->Less need for donations and requiring users to pay. High tech debt increases
  costs, which will mean more focus on raising money over improving the platform.
- Less tech debt makes it easier to address user feedback regarding bugs or site enhancements.

#### Ways tech debt will be minimized.

##### Prioritize readability

If code is complex, then developers will spend too much time trying to understand the code. Also, too much complexity will 
add risk that developers accidentally make a change that adds a bug or makes a change that adds even more complexity. 

#### Minimize the number of libraries and frameworks that will need to be used.

- Minimizing the usage of libraries and frameworks will help reduce complexity and simplify dependency management.
- Choosing a library and learning how to use it can be a time-consuming process. People will recommend different 
    solutions for the use case a library is going to address. For example, when looking at recommendations for React state
management, some people recommended Redux Toolkit. Other people recommended another library such as Zustand or MobX. Trying to decide what
 solution to use takes time. 
- Upgrading a library would be a challenge While staying with an older version of a library is possible, it can cause challenges.
  For example, class components were recommended for use in React in older versions. Later, functional components were recommended, 
   and most of the documentation online was for functional components

### Decoupled backend and frontend

The backend should be decoupled from the front end. While there are many powerful frameworks which rely on coupling the 
frontend and the backend, and there could be performance or speed benefits from the coupling, it is best to avoid the 
coupling for this platform. 

Flexibility is helpful in case it is decided that a different backend technology should be
used. Also, the backend will support custom frontends.

## Notes on tech used


### Vanilla JavaScript with an internal framework.

 - Less dependence on Internet to look up documentation, which helps with focus. Many websites that answer technical questions about frameworks
have other distractions even though they are also giving useful information. For example, answers to React questions can often be found
on online forums. However, there is often unhelpful, misleading, or inaccurate information that needs to be parsed through.
 - The codebase and documentation can be implemented in a way that anyone familiar with JavaScript can understand the UI code without needing
to look up documentation in the Internet.
 - Fewer challenges with attempts to use patterns from outside a framework or library due to a lack of experience with it  For example, here are some 
issues I ran into when working with React.
   - Trying to conditionally call a hook within a React component in React 16, and doing so in a way that was not supported in React 16.
   - Managing complex state in a React context that was constantly changing. I did not realize that every component subscribed to the context
   was re-rendered, and this causes significant performance slowdowns. As a result, the user experience was negatively affected.
 - Some additional difficulty with implementing UI changes isn't a major concern. If UI changes are quicker to implement, that incentivizes
   more UI changes to be done. The site should only focus on features that are essential for people to find or host in person events
 - An internal framework can be easily customized to enforce development patterns that are good for the platform because of internal knowledge. Also,
   the internal knowledge helps developers use the framework more effectively.


### Using a multiple page application instead of a SPA(Single page application)

- Using a SPA is likely to make the user experience slightly better. However, correctly creating a SPA will add a significant 
 amount of complexity and time needed to maintain the code. 

### Java

The main reason Java is backend was my experience using it compared with the fact that I prefer using it over Node.js. 
The experience will help me improve quality and minimize tech debt.

Here are reason why I prefer using Java.

- Dependency management in Node.js is challenging.  A large number of dependencies are necessary for handing important 
  tasks such as configuring API endpoints, authentication, and database access in an efficient manner. Keeping these
  dependencies up to date is challenging. On the other hand, I've found that dependency management in Java is less of a challenge
  due to a larger standard library and more mature 3rd party tools.
- In Node.js, I found unit testing to be a challenge with mocking. Jest mocking is challenging to use. They are multiple ways 
  to mock, and trying to configure each mocking method to work the way you want is hard. I have found that Mockito
  for Java unit tests is much easier to use.
- There is a long track record of successful projects that were built in Java and these were products that had a great customer experience. Node.js 
   doesn't have that long track record because it is newer.
- Java seems to scale more effectively for platforms that have a large number of active users. While there is more upfront complexity
  with a Java project compared to a Node.js project, I think the complexity is not an issue given the goal of focusing on the long term


There are many other programming languages such as Go, PHP, or Python that are suitable for a complex backend. However, I
have less experience with these languages compared to Java.

