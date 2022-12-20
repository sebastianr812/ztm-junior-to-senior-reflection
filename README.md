Today is 12-19-2022 and I have completed the ZTM junior to senior course by Andrei. Here are the topipcs which I learned: 

1. SSH - this is a secure connection that is used to access other computers around the world - if we were to have a server somewhere else we can go into the computer and run commands on it to see what info it has or debug things. This secure connection is established using public and private keys - we use the public key as well as another hashed data to demonstrate the user is the correct one and establ9ish the secure connection. There are different ways of using encryption for the connection but the most common nowadays is the public/private key pair - use the public key to encrypt the message and then the private key to decrypt it 

2. Performance pt 1 - Briefly learned about CDN's and how to optimize files and images for best transferign thru the wire. We learned the critical render path which allows us to understand where we can improve things. Import CSS as quick as possible and js as late as possible, minimize dom manipulation because this makes our app have to re render. We can also change the rel of links in order to pre fetch the data or wait until their needed, pre render, dns, etc

3. React, Hooks, Redux - hooks were integrated to have pure functions for all of our components - pure functions are easier to test by a landslide because we can give it inputs and expect the same output every time, they also produce no side effects and hooks are used for state management inside of functional components. useState is used set the state of something - this produces an array of 2 things [stateName, setStateName]- setStateName() pass into it what we want to change the state to - useEffect is another common react hook - this is a function that is run every time the state of something is changed, this is defined by adding the state variables as the other parameter for the functon ... for example if we leave it as useEffect(()=> { [code to run ]}, [variables inserted and the callback func will run every time the state of the variable chnages]) ... so if its left as [] it will only run once on initial rendering. 
    
    Redux - state management tool that is used mostly on big projects (need a refresher) - in principle it consists of actions that trigger a reducer function which make changes to the state or store - this store lives in a level above the app so any time a component needs to access the state, it just needs to be connected to the store and it can pass it down as props to the component. Action takes place by user, gets sent to reducer function that takes the action and outputs the brand new state of the store (the store is just a big object describing the state of your app). We can also add middleware for logging purposes or adding other things we want to happen between the state change and the action being taken place. use thunk to set the state of something asynchronously like when doing fetch calls 

    Module buundlers - webpack vs parcel vs roll up - do the same thing, webpack needs configurations that is done by CRA but we can configure it if we want to they can convert our modern js to js that all browsers can understand and bundle them all into 1 big file that then gets sent to the client.

4. Perfromance part 2 - code splitting - the practice of sending js when a certain button is hit, or when a certain view is present - minimizing what js gets sent to just complete the functionality needed in the moment and periodically import more and more js as needed. Lazy load allows us to import js dynamically ... keep in mind this is all for CSR. We can also import JS files when a certain route is hit by adding it to the logic of the render method. •	In essence – all codesplitting is moving the import statements from the top of the code – to inside some logic so that it will only trigger if that condition is met – reducing the amount of code having to be ran to the browser and only sending it when the condition is met. The most common way of doing code splitting in react is to use react.lazy - this uses Suspense to wrap the component that is going to be lazy loaded. 

    PWA - progressive web apps are a type of web appplication that can be ran offline, be shown as an app of a mobile user for both ios and android AND avoid having to go thru the hassle of apple and android requirements for native apps. Makes the UX better for mobile users which is a browser user base, and generally we should implement it in all of our webaps to have it accessible / good UX for all users regardless of device. HTTPS is needed for PWA, as well as app manifest and service worker. The app manifest is seen in the public folder in CRA and describes how the app will look on mobile devices, what is the title going to be, different images for our logo on different native sizes, Service Worker is used to have the app working offline because it caches static files from the server that way if the connection is lost or subsequest requests for the same static file is made instead of doing another request to the server, it is already memory of the browser. Use lighthouse extension / website to check the performance of our web app and see where we can imporve, we can also use pagespeed test and other services found online

5. Testing - there are different types of tests unit, integration and automation / UI tests - Unit tests the functions in our code, do imputs give the same output and classes the same concept - integration : how two functions or pieces of code worth WITH eachother / in conjunction of eachother. Automation / UI tests is where a real test user or automated both actually click and scroll thru our website to see how things are interacting / how the UX is and if any bugs arise from using the app. 

    Lots of packages that we can use - Jest is built into CRA and is really good for unit tests - tests are easy to write, we use describe(), expect(), it(), toBe(), toEqual(). We can mock functions to use inside of our tests like faking api calls. 

    Enzyone - most common way to do component tests. We can shallow render components which gives us a copy of the barbone component which we can compare to a snapshot to make sure things look correctly / renders correctly. Mount allows us to actually mount things to the DOM and we can also use a headless DOM to mount things to a fake dom. using shallow copies we can pass fake props down to run our tests efficiently, simulate events to make sure actions being taken are as they should. Tests get a lot more complicated for testing components connected to redux or with their own state. When using redux and wanting to integrate tests we can use redux mock store package to help with that. 

6. Typescript - allows us to add type safety to our project - very important when working on big teams because errors in types that variables are can cause the company a lot of money and headaches. Typescript tries to get us to a lower level programming language to ensure the write type of variables are being passed to functions. It adds complexity but makes it easier for new people to come to the team and understand the code / gives everyone a standard that the code should be written in. Using TS leads to less errors because of this. We NEED a ts compiler to change the code to regular js for the browser to run ** . TS has a bunch of different types like the primitive ones in JS and some added ones like Enums, tuples, Interface, types - these are used as a blueprint for objects

7. Client side rendering vs server side rendering:
    - SSR : static files are sent FROM the server which are already rendered and need to be hydrated (add JS to them) in order for the webpage to become responsive. SSR leads to quicker time to first paint (when we see the actual html elements on the webpage) but takes time to hydrate WHICH is ok because user is going to see something quicker --  leads to better UX. Every time a link is hit a new webpage is going to be requested for the server and thats going to get sent to the client. Frameworks like Next.js are great for integrating React into SSR. 

    - SPA: one html file that react connects to and uses JS to add elements, remove them, change the state etc. We dont need to request the server a bunch of times for new files to get sent. Client gets the static file which browser then sees the JS attached to it where it needs to be parsed and executed in order for things to be working properly / seen properly. In comparrison to SSR where the user can see the html right away and the JS gets downloaded in the background. * Time to interactivity is the exact same BUT to the USER SSR is faster than SPA / CSR

    In summary - both have their pros and cons: SPA have more rich interactions, feel like an APP, no hard reloads, no frequent requets to the server. But SPA are bad with SEO and web crawlers cannot get a good idea of what the webpage is about. The discussion of SPA vs SSR is something that comes entirely to the project itself, is it going to need good SEO, do you want to prioritize the speed of where users can see things, etc

8. Security - XSS vs CSRF : scripts that can be injected into your user inputs that will mess with the code and can be harmful to users or dummy inputs that get sent to a hacker for mal use. What to do to prevent - sanatize inputs: use JS logic to have if checks using regex and discard anything that does not match the type of input you are expecting. For SQL injection defense we need to change the statements to function type ones that way the user cannot insert what they want directly into the SQL script. Validate user inputs and build a way to turn a untrusted input to a trusted one. Logging tools like winston and morgan are very useful when developing. HTTPS certificate is NEEDED nowadays ... there are too many bad actors in the world. We can modify our apps content security policy to prevent our server from being hti from just anywhere. Set privacy rules for cookies which can contain user data. We can secure our headers with Helmet. Always encrypt user passwords and never store them as plain text. Have an authentication system set up for a way to make sure a user is the correct user. 

9. Docker - Docker is a way to create an environment for our app to live in that is independent from our local computer. We need to ensure that the app is able to get delivered in the same version every single time because if not it would depend on the node version of the user and other versions of different things. Docker uses a container which holds images of the tools we need: like node.js, reddis DB, postgresDB. Docker creates an environment for these services to live in that way we do not need to open the different services and connefct them to our local computer. Docker runs on top of the host machine meaning it does not need to share cpu and memory

10. Reddis - reddis is a memory based database that is very fast and most useful for storing data that is not that important meaning we can afford to lose it and being able to retrieve it quickly. In our case we used reddis to store the JWT token of a user and whenever we wanted to authenticate the user, we would look it up inside of the reddis database. 


