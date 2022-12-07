# CS 411 Project Report

[Link to Project 1 Track](https://canvas.illinois.edu/courses/30041/pages/fa22-project-track-1)

### Authors:

- Rustom Ichhaporia (rustomi2)
- Ayan Mallik (amallik2)
- Alec Chen (acc11)

# Changes in Direction

One change of direction that we had is removing our implementation of the payments and bank accounts tables. We originally included these in our project proposal and database design, because we were planning on allowing the users of our application to connect their bank accounts so that the members of a gamily could pay the family leader for their portion of the monthly subscription service price; their payments would then be tracked to ensure that all members are paying their share. However, we realized that implementing a full payment solution securely is quite difficult and time consuming, so we focused our efforts on implementing the CRUD and efficiency operations for the joining and managing of family and user settings. These still meet the requirements for the number of tables and queries. 

# Discuss what you think your application achieved or failed to achieve regarding its usefulness.

Barring the note above, we believe we were able to achieve everything that we set out to complete at the beginning of the project. We implemented all important CRUD features for our schema, as well as secure authentication and efficient and accessible interfaces to access and edit data. We did not fail to achieve any meaningful features that were discussed. 

# Discuss if you changed the schema or source of the data for your application

We kept the majority of our schema and source of data of our application the same. Regarding the source of data, the process of mocking out data for user, families, and the memberships connecting those two entities ended up being more difficult than expected because of the interaction between those tables. Since memberships rely on user and family ID’s as foreign keys to connect the two entities, translating that many-to-many relationship from our database schema to mock data was a complex yet interesting process that built the foundation for our data source across the application.

# Discuss what you change to your ER diagram
and/or your table implementations. What are some differences between the original design and the final design? Why? What do you think is a more
suitable design?

The only major change we made to our table implementation was to add auto-increment functionality to the ID fields in our tables, so that we did not manually have to increment IDs from inside the application. Serialized transactions in the SQL implementation will ensure that there are no ID collisions. Some of the field names may also have been slightly tweaked during creation. 

# Discuss what functionalities you added or removed. Why?

We added auto-join functionality. We define auto-join as the ability to join a family without having to manually search through the table of available families. Instead you select the subscription service you’re looking for, and click on the auto-join button. This will automatically find an available family and add the user to the group. 

# Explain how you think your advanced database programs complement your application.

The advanced databases programs that we wrote for FamilyHub include the 2 advanced queries involving site statistics, our trigger upon new family creation, and and our auto-join transaction. 

The site statistics are valuable to new users because they can learn about the activity and popularity of FamilyHub at their respective university. For example, the second site statistic revolving popularity of various streaming services at a user’s university can help recommend what families a user creates based on what other people at their college tend to gravitate towards

Our trigger, which automatically marks a user as a leader of any family they create, streamlines the creation process for new families and ensures that each family has a leader.

Finally, our auto-join transaction adds a nice quality of life feature for users who want to join a family but don’t prefer a specific group. Rather than facing the discomfort of specifically requesting a group of strangers, the auto-join functionality eliminates that issue by smoothly matching members with the services they want to consume.

# Each team member should describe one technical
challenge that the team encountered. This should be sufficiently detailed such that another future team could use this as helpful advice if they were to start a similar project or where to maintain your project.

Rustom: One challenge we faced was figuring out how to implement fake data to use for our database. We did this using python, because creating fake data in the SQL console itself is difficult and inefficient. This can be done using a popular Python library called Faker. Faker offers a variety of dummy data such as fake names, emails, and randomizers that we could use to determine the fake student’s attributes such as their university. By leveraging the power and flexibility of Faker, we were able to populate our User and Family tables with relevant mock data that populated FamilyHub as if it is was released live to students across the nation.

Alec: One challenge we faced was when our SQL didn’t work in the GCP console, for certain features you have to look outside just the SQL syntax and need to sometimes configure features in the GCP setup. Sometimes also depending on your tech stack, the SQL written in your frontend/backend may not be being directly executed on the GCP console. The takeaway here to to look beyond just the SQL to figure out where the origin of the bug when it comes to the queries.

Ayan: One technical challenge I encountered was determining how to integrate SQL functionality into the user interface of our React frontend. When developing clean and reusable code, it’s important to abstract logic and complex functionality from the portion of user interaction. With websites however, the logic itself is couple so strongly with the user interface that maintaining that separation becomes more difficult. However, I believe we attained a strong level of abstraction by building various routes in our `/api` folder to manage the various CRUD operations and advanced queries that we wrote in SQL. Upon a fresh set of eyes navigating our codebase for the first name, they should easily be able to follow the various operations we run thanks to a strong abstraction and integration between SQL logic and frontend interaction.

# Are there other things that changed comparing the final application with the original proposal?

One thing we integrated into our final application that we didn’t cover in our original proposal was the inclusion of site statistics for new users to view the popularity of FamilyHub at various universities. Like we mentioned earlier, this added functionality enables users to see which types of streaming services are popular at their university or just gain a general sense of the activity of FamilyHub in the community around them.

# Describe future work that you think, other than the interface, that the application can improve on

Our current application is generally tailored towards to course requirements for this project, however we think our application could extend to be a useful tool in the real world. The main feature that need to be implemented for this to be brought to the masses is to integrate our apps with the actual services. We haven’t done a lot of research into how accessible the services’ APIs are for this kind of tool, however we imagine we’d be able to integrate each services such that members of families wouldn’t have to interact with the services at all besides the actual usage. They would be able to create an account, join a family plan, and pay the monthly subscription service through our service, without needing to interact with their family either. This would be purely to reduce the friction between consumers and the wholesale market price, which is exactly what we imagine as the ideal experience for a user: seamless experience, reduced cost!

Our current tech stack and architecture could remain similar, but a lot of our functionality would be refactored. We would want to simplify the app to be focused around automating the whole process of finding families, and removing the manual work of actually registering together as a family on the services.

# Describe the final division of labor and how well you managed teamwork.

Coming into this project as roommates, we were able to conduct most of our ideation and work in-person which led to greater collaboration and a stronger sense of teamwork as we tackled this project together. Nevertheless, we did each specialize in various aspects of the project given our various backgrounds. Rustom led our SQL integration process by choosing an innovative tech stack in Next.js that manages how content is served and how we connect with the MySQL instance on GCP. Alec led our frontend development process by proposing designs for the look and feel of FamilyHub and converting those visions into reality through the use of a material design library called Chakra UI. Ayan led our database design process by helping ideate many of the advanced queries that we would end up building together and illustrating our ERM diagram and helping convert that into the schema structure. 

Like we mentioned though, the majority of this work was collaborative attributing to greater ownership from all 3 of us and ensuring that we could all contribute our ideas to all facets of the final product that we’ve hosted to Vercel: [https://familyhub.vercel.app/](https://familyhub.vercel.app/)

After this class concludes and break begins, we plan to continue working together on FamilyHub because we all see value in the platform we built and truly believe that many college students across the nation could benefit from connecting with those around them.