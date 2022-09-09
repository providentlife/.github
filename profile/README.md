<!-- ## Hi there 👋 -->

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

**![](https://lh5.googleusercontent.com/gAshYUM0T4w8x5NkrtfiJTFNLr8JA3V3xsFQ591Hc4qxxgtbCDjJSKLs5oKn7bvWPXx4WEef6IQlnxBal775v26oGBD4Z85-a7_nheoflhVKqehFNZ7s_keJat6OyVSQJ5AyJRnBOvVk4lIKukfTPxbxB15VAMAbTo-1Hs8cRUF6-LTKXQ6b4jo6xw)**
# Provident Life Case Study

### By [Jason Padilla](https://www.linkedin.com/in/jason-padilla-8294bb1a7/) and [Matthew Tan](https://www.linkedin.com/in/matthewtan15/)

## *Project Overview*
Provident Life is a thoughtful and accountable approach to health and fitness by providing users an alternative to navigating their weight gain/loss journey. This is done by calculating a user's total daily maintenance calories and macros, informing them of their food consumption, and thereby helping the user create a balanced food habit with the help of one of our FAQ cards. Furthermore, the users have a visual representation of their journey through the use of charts.

### **Problems To Solve**
Young adults today have insecurities about their bodies. According to [NOW](https://now.org/now-foundation/love-your-body/love-your-body-whats-it-all-about/get-the-facts/#:~:text=Body%20Image,the%20time%20girls%20reach%20seventeen.&text=When%20asked%20%E2%80%9CAre%20you%20happy,their%2060s%20answered%20%E2%80%9Cyes%E2%80%9D.), 50% of teens are "self-conscious" about their bodies, with 26.2% reporting being "dissatisfied." Furthermore, the internet being a vast source of information overwhelms them. As a result, many go down an unfavorable path that leads to unwanted results. Through our web application, we will create a better alternative to navigating their weight journey. We plan to allow young adults to learn about choosing the right path in their journey through a TDEE (Total Daily Energy Expenditure). Similarly, we want to become an acceptable and engaging source of information that not only piques interest; but also supports the users in wanting to continue their progression through additional information & resources.
### **Motivations**
We were inspired to build this project because we want to help people reach their weight loss/gain goals. The primary motivator for this app is to create a platform that guides users using TDEE numbers to track their weight loss/gain journey, with charts being a visual representation of the said journey. We also wanted to challenge ourselves to use technologies that we haven’t used yet such as NestJS and Chart.js. In addition, we wanted to improve in technologies that we have had previous struggles in such as React.js. This project will give users an effective method of losing weight while still being able to enjoy the foods that they like by tracking their calories with precision. We want to help as many people as we can to transform their body and live a healthier and happier life.
### **TDEE Concepts**
What is TDEE? TDEE stands for Total Daily Energy Expenditure (aka your maintenance calories). TDEE is the total energy needed daily to maintain body weight after factoring in all activities after 24 hours. Knowing TDEE will help the user understand how many calories are needed to eat to maintain, lose, or gain weight. The calculations are done by multiplying the user's BMR (Basal Metabolic Rate). BMR is a component of the user's TDEE and the number of calories the body needs to continue to operate. Regardless, it is NOT the number of calories a user may need to eat to lose/gain weight. Be that as it may, figuring out a user's TDEE is enough to track a weight loss/gain journey.

## *Design Overview*
ProvidentLife is built using the RNPN (React, NestJS, PostgreSQL, Node.js) stack.

  

Why we used RNPN stack:

-   React (Frontend)
    

	-   Build encapsulated components that manage their own state, then compose them to make complex UIs.
    
	-   Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes.
    

-   Nest.js (Backend)
	-   Uses OOP concepts which can help you understand things better.
	-   Built on top of express.
	-   Uses progressive JavaScript, is built with and fully supports TypeScript
	-   A better choice than ExpressJS since it is built on a clear design with a few simple components (controllers, modules, and providers).
	-   Responsible for allowing the database and front end to communicate.
    
-   PostgreSQL (Database)
	-   For the context of our application, using relational databases was the optimal choice
	
-   Node.js
	-   Build scripts to run terminal commands and run applications


Why we used other technologies:

-   JWT (Backend)
	-   Creates a JSON web token and encodes, sterilizes, and adds a signature with a secret key that cannot be tampered with.
	-   Used for user login feature.
    

-   Chart.js (Frontend)
    
	-   Easy to set up charts.
   	-   Easy Learning Curve.
  
### **TDEE Formula Implementation**
The process of finding out a user’s TDEE formula stems from calculating a user’s BMR first. With that in mind, extensive research was done, scouring through multiple health apps, testing them out, and finding the formula used to calculate BMR. There were two formulas we had found and had tried testing. The first formula was [Harris-Benedict Equation](https://en.wikipedia.org/wiki/Harris%E2%80%93Benedict_equation), developed in 1919 and revised for accuracy in 1984, which is immensely popular and is used in many health apps today. The second formula, the Mifflin-St Jeor Equation, was a more optimal choice for us, as the calculations to the TDEE are raised in accuracy by 5% compared to the Harris-Benedict Equation. The Mifflin-St Jeor formula we have implemented with imperial metrics (lbs, in) is calculated by (4.536 * weight) + (15.88 * height) - ( 5 * age)  + 5 or - 161 depending on the user’s gender, once added is then multiplied by the user’s activity level to get their TDEE.

### **Data Model**
**![](https://lh6.googleusercontent.com/8LoBfwtPN4yikIeAtVKubb896zyAItdDD7E9gdEY3yBf5TF2d-CG2A_rPUoSwfeR_I-MdT2J9AHvIq60KnMxPqoH_6E0xSysUDi5oZBfmA3F2aBssrxXUeizj7iUMIFkYA4u9Tvq9YeKWIry7yXehg)**

We built an entity relationship diagram to model our database where a user can have many starting metrics (user_starting_metrics) to start their weight journey anytime because at each point in time when a user created a new starting metric, their measurements are different from the last time they had created one and they will most likely have a different goal to either lose or gain weight the next time. Our starting metrics also have many weight entries to record their weight loss/gain that will then be depicted on a chart.

### **API Layer**
Through the use of NestJS’ controllers and services class, we created 3 controllers for specific routes (user, user-starting-metrics, and weight-entries), and in each controller we built APIs for that route. Afterwards, we built methods for 3 services in accordance with our controllers. For each of our controllers, we thought about our approach to our user flow in the front end, and as a user, you should be able to sign up, log in, create user starting metric sessions, select the sessions they have created, and post weight entries to those sessions. So we created endpoints that call methods from our services class that utilized TypeOrm’s repository API to handle all incoming requests from our client.

### **User Interface & Charting Library**
ProvidentLife's design was mocked up in Figma and built using Tailwind/Flowbite (free tailwind component library) to build clean and visually appealing components at rapid succession. Using pre-built charts, we also implemented chart.js to display a user's weight gain/loss journey visually. Similarly, we built two color schemes around giving users a straightforward yet simple path on our website.

**![](https://lh5.googleusercontent.com/hTUTEAJbXKBatGz9lMJf0ZNckdloQE-UEsQDkZpBRyLcZ6y9PjB2hlYh4mjT7RbO8vqsGI6WBkwy7TjqmxI_kdm7yzjNQbMsQlCaeZGdCzKUf32ap8ELNd4hN4LfYPsXu_3QbJawd6G577DYW3fYNmtP_mVFyBghjXmTNFcvbnnwJM5fj9K2VP130g)**

### **User Authentication**
To ensure that our users can safely sign up, log in, and start their weight journey progress, we needed a way to secure their credentials. We came up with using JWT (JSON Web Token), a compact URL-safe means of representing claims to be transferred between two parties, which handles user authentication when they log in, and password hashing using Bcrypt, used to hash and salt passwords securely, which safely secures our user’s password in the database and uses to compare hashed passwords when a user logs in. We chose to use JWT and Bcrypt because we had learned about these technologies from The Marcy Lab School but were not comfortable with them at the time as we had difficulty using them. We wanted to use this project as an opportunity to improve our familiarity and implementation of these technologies.

## *Challenges*
In every project, there are glows and grows; areas we excelled in and areas that required more effort and time invested. In this section, we will be talking about the challenges we faced throughout our project build because no project is ever linear.

### **Weight Entry Sessions**
The first time we created our ERD for ProvidentLife had some challenges, our ERD had gotten too complex and very difficult to navigate through if we had committed to that design, the original ERD had an issue with creating multiple user starting metric sessions because the user table contained not just login credentials, but all user metrics too. We later realized that while creating different sessions, a user’s body metrics could be different with each time, with that realization it meant updating the user’s metrics each time a session is created and there had to be a better way. After a day of brainstorming, we came up with an idea which we’ve ended up following through, which was to build only 3 tables, one for users that consists of user credentials, a user starting metrics table to store their metrics each time they create a session, and a weight entries table to store weight entries for each session.

### **Connecting NestJS to Postgres via TypeORM**
Learning NestJS, a framework we had never used, was a fun challenge and very intuitive when it comes to creating controllers, and services. But connecting to Postgres had thrown us deep into a rabbit hole, with many resources out there, like the NestJS documentation and YouTube tutorials, it became very inconsistent as each resource we had checked out connected to Postgres differently. We tried multiple attempts to connect to Postgres through these resources but weren't able to succeed in connecting to Postgres. After a few days of attempting to follow the same resources again, we dug deeper into NestJS documentation and read about TypeORM. With another attempt following the documentations, we were able to create tables for our database and connect with it.

### **Stateless Charting**
**![](https://lh5.googleusercontent.com/oYMeRLbrSqR1X8fy7g4QoEauK11X36aIYtSyEDxWBq1BngAUcW-e_zswqHfjFN2OmKghr_5APfNEtnYwbWNS6ecQnV6pXOnCMifPT-9JK2fxZGYbI4s7rPj8gS3ySSwtxQiHi6MhCpe-zZzOYBa7l-o)**

Chart.js renders data given to it in the dataset property in a chart. This process happens immediately upon the component rendering to the web. This resulted in the chart trying to display data that did not exist yet, throwing an error. The first approach was to create a button that turns off/on the charts, believing that if the charts were off upon the component being rendered, no error would be thrown. However, we still had the same issues. After coming together, doing peer programming, and asking for help, we concluded to create a dummy chart object that would render nothing upon page loading. However, upon a user selecting a session, it will supply the dataset property with the necessary information for the chart to be rendered. Afterward, a member refactored and cleaned it up while at the same time enlightening his fellow member.

### **ORM vs. Raw Queries**
Before we built out queries for our endpoints, we discussed our decision between raw queries or using an ORM with a list of pros and cons for each of them.

ORM cons:

-   Obscures the underlying database operations
    
-   Could be making inefficient queries without you realizing, e.g. using the incorrect index on a table.
    
-   Slow, if you compare the performance between writing raw SQL or using ORM, you will find raw much faster as there is no translation layer.
    

  

ORM pros:

-   Nesting of data, in case of relationships, the ORM layer will pull the data automatically for you.
    
-   Single language, you don't have to know SQL language to deal with the database.
    
-   Adding is like modifying, most ORM treat adding new data (SQL insert) and updating data (SQL Update) in the same way, this makes writing and maintaining code a piece of cake.
    
-   Eliminating repetitive coding tasks, primarily assigning many object properties from the columns of a single row of a query result set.
    

  

After carefully considering the pros and cons of using an ORM, the cons of using an ORM usually doesn't pop up for more straightforward applications such as ProvidentLife, so the speed & convenience that the ORM gives us makes this not as much of a concern when compared to the benefits.

### **Chart.js vs D3.js**
We decided to implement a data visualization library to display users' weight entries as they document their journeys. We came across two prevalent ones, D3.js and Chart.js, both equally having their advantages and disadvantages. Chart.js provides pre-built charts, from bar to pie charts. Chart.js excels at setting up charts with quick successions and having a short learning curve. However, their greatest asset is also their most significant liability. Because charts are pre-built, it does not add much to customization and complete manipulation of visualized data. Though changes to their configurations and settings are enabled, there are still many restrictions.

Unlike Chart.js, D3.js provides more creative freedom as we can manipulate and display data to our absolute liking. D3.js allows engineers to create visually appealing graphs. Nevertheless, this comes at the cost of an extreme learning curve, as since there is more freedom than Chart.js, more knowledge is required to use D3.js. After researching both libraries' pros and cons and considering our team's scope, the group concluded that Chart.js would be the best course of action. Though D3.js reflects our project's mission of creating engaging content, the cost of added workload and, with our deadline being in four weeks, could result in a member burning out quicker than expected.

## ***Extension Opportunities***
If given more time, we would have liked to add:

### Expected Weight Loss/Gain Trajectory Plotting

One feature we would have liked to add was an expected weight loss/gain trajectory plotting on a chart. When a user creates a session and starts adding weight entries, they would see their estimated growth in accordance with each week and compare it with the user’s actual growth when they plot their weight entries on their chart so they can see if they are on track.

### **Conclusion & References**
Provident Life is a website that guides people in their weight loss/gain journey. We hope you enjoy it as much as we did making it. Here are some links to resources that assisted us and our project artifacts.

-   [GitHub Organization](https://github.com/providentlife)
    
-   [Official Website](https://6307e5e3c37bbe0009ac8af7--nimble-dolphin-b10546.netlify.app/chart)
    
-   [Mockup #1](https://www.figma.com/file/klQWSPvbk0PvDs9l2Wzi5c/Project-Health?node-id=1%3A470)
    
-   [Mockup #2](https://www.figma.com/file/UIyyFAsXpHsVyJ83gfuIlb/Interface-Design?node-id=0%3A1)
### Articles on TDEE

-   [Brief explanation of TDEE](https://www.musclehacking.com/calorie-calculator/#tdee)
    
-   [Usage of BMR and TDEE](https://chomps.com/blogs/news/what-is-bmr-tdee)
    

### Official Technolgies Docs

-   [React Chart.js](https://react-chartjs-2.js.org/)
    
-   [Chart.js](https://www.chartjs.org/docs/latest/)
    
-   [Tailwind Css](https://tailwindcss.com/)
    
-   [Flowbite](https://flowbite.com/)
    
-   [React](https://reactjs.org/)
    
-   [Netlify](https://docs.netlify.com/?utm_source=google&utm_term=&utm_campaign=DSA-Nonbrand-MaxC-US&utm_medium=ppc&hsa_acc=3888979506&hsa_cam=15837178031&hsa_grp=140563434428&hsa_ad=573752505767&hsa_src=g&hsa_tgt=aud-951962601295%3Adsa-1287291258367&hsa_kw=&hsa_mt=&hsa_net=adwords&hsa_ver=3&gclid=CjwKCAjwpKyYBhB7EiwAU2Hn2dhoko0JYHD0ZfSyPct9wAvyZXaHcHo4J5wPepH4awtA7DQ8H1vLPhoC_-8QAvD_BwE)
    
-   [D3.js](https://d3js.org/)
    
-   [NestJs](https://docs.nestjs.com/)
    
-   [TypeORM Repository API](https://typeorm.io/repository-api)






