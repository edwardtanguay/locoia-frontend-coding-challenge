# CHALLENGE CONVERTED TO MY NOTES

- 1.5 hours
- single page 
- user enters name
  - enter has to be pressed
  - check if it is a "lucky name" list (via mock backend API: src\api\peopleApi.js)
  - if name is not in list
    - display "I'm sorry, {name} is not in today's list of lucky names." [OK]
    - when click [OK] then they can search again
  - if name IS in list
    - display "Congratulations, {name} is a lucky name! You've won a prize. Will you accept it?" [Accept] [Reject]
    - if Accept
      - name is added to list of winners (on same page)
      - input field is cleared
    - if Reject
      - name is NOT added
      - input field remains as is
- styling
  - scoped Sass styling in Home.vue
  - ElementPlus is also installed
    - https://element-plus.org/en-US/component/overview.html
    - e.g. <el-button type="primary">Primary Button</el-button>
- extras
  - validate input
    - only letters
    - no name smaller than 2 characters
  - send random mock error from API
    - deal with this gracefully on front end
  - add page "Winners"
    - shows same winners as on home page
  - once prize is accepted
    - don't allow it to win again
    - if typed in, show "I'm sorry, prize has already been won for {name}!"
  - persist all changed state in localstorage 
  - make limit of 10 guesses per day
    - enable user to "cheat" by clicking "next day" which changes the current day (displayed)
    - make it not allowed to give a guess from any previous day
  - refactor with TypeScript, Zod, Prettier, ESLint, make sure code is properly structured according to these tool's guidelines
  - create TODO.md and answer following questions:
    - plan an API an describe how you would implement it with
      - authentication
      - rate limiting 
      - error handling
      - API availability
      - retry strategies, e.g.
        - simply retry - 3 attempts then give up
        - expoential backoff - 5 attempts, multiply wait by 2
        - jitter - randomize the delay
        - conditional retry - only retry on 500, 502, 503, 504
        - circuit breaker - stop attempts if server is known to be down
    - how would you a protect the app from being abused? e.g.
      - implement a CAPTCHA to use the site
      - rate limiting and throttling (see above)
      - validation and sanitation
      - secure storage policies
      - use HTTPS
      - monitoring and logging
    - how to deploy in cloud environment
    - how to make sure app is running with latest version of code? e.g.
      - implement code versioning e.g. 1.0.0, 1.0.1
      - tag released in GitHub
    - how to ensure users are not disrupted when you make significant changes to code, e.g.
      - set up a work flow that developers follow which involves creating task branches, pushing to repository, merging, etc.
    - describe accessibility best practices for the site, e.g.
      - semantic HTML is used
      - ARIA roles and attributes
      - keyboard navigation
      - forms that use fieldset, legend, label, for
      - color and contrast
      - alt tags in images
      - responsive design
      - readability (make sure site works with larger fonts)
      - mangage focus on site, e.g. avoid focus traps
      - test site with screen readers
    - how to structure css to optimize reusability but decrease leakage between components (unintended impact styles from one component have on another)
      - Tailwind
      - Sass (variables, structure)
      - scoped-CSS or component encapsulation, e.g. in Vue
      - BEM
      - CSS modules (CSS files that are scoped by their names)
      - styled-components
      - atomic CSS (usability classes)
      - CSS variables


---

# Challenge (original)

This challenge is divided between the main task an additional stretch goals. All of those stretch goals are optional, but we would love to see them implemented. It is expected that you should be able to finish the chellenge in about 1.5 hours. If you feel you are not able to implement everything on time, try instead describing how you solve the points you didn't finish.

And also, please do not hesitate to ask any questions. Good luck!

## Do you have a lucky name?

Your task is to create a single page application that checks if a name the user enters is in the lucky names list for the day. If the name is lucky, then the person is a winner.
The user should be able to type in their name and submit it. You will have access to a mock api, which will provide you a list of people whose names are lucky. Once the application knows whether it is a lucky name or not, you should display that information back to the user.

If it's not a lucky name you should display a prompt with the message: "I'm sorry, {name} is not in today's list of lucky names."
Clicking "Ok" makes this message disappear and they can search for a different name.

If it's a lucky name then you should display a prompt with the message: "Congratulations, {name} is a lucky name! You've won a prize. Will you accept it?"
This prompts the user with two options:
* Accept: 
  * The name is added to the list of winners for the day.
  * The input field is cleared.
* Reject: 
  * The name is NOT added to the list of winners for the day.
  * The input field REMAINS with the inserted name.

The list of winners should be displayed in the same page.

Use your own judgement to make the user experience as pleasant as possible in your own terms, but don't spend much time on the visual, as the functionality is most important for the task.
You can use any UI libraries you're comfortable with to help completing this task, however, ElementPlus is already in the project for ease of use.

## Stretch goals

You may modify the "people" array to fit your needs. Some of these will also require the use of either the router and/or vuex store.

* Validate the input field to only accept letters and to not be smaller than 2 characters.
* Validate the api call by passing "canReturnError" as true and dealing with the error by displaying to the user a notification that an error occurred.
* Add a link that takes you to a dedicated page that shows only the list of people who have won. The winners should be the same as the list in the home page.
* Once the prize is "Accepted" for a name, don't allow it to win again. Displaying a message like "I'm sorry, {name} has already received their prize today!".
  * Persist this change through refreshing the page.
* Make a limit of 10 lucky names per day. Each day is arbitrary and the user can advance to the next day by clicking a button "Next day". Each subsequent day should not repeat a name from the previous day.
* Press enter to submit the name.
* Set up your favorite tools to measure and enforce code quality, apply linting rules, and format the code according to your preferred guideline.
* Prepare a TODO.md file describing possible further improvements to the architecture:
  * Assuming the list of names are fetched from an actual api, how would you implement authentication, rate limiting handling, error handling, api unavailability? - What kind of retry strategies you’d imagine implementing?
  * How can we protect the app from being abused?
  * How can we deploy the app into a cloud environment?
  * How can we be sure the app is running with the latest version of code?
  * What techniques you can employ to ensure users are not disrupted when you make significant changes to code?
  * What kind of accessibility best practices should we keep in mind?
  * How would you structure the css so that we have the most reusability but also the least leakage between components?
  * Any other improvements that you feel like could be added.
