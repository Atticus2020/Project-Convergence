Introduction
           Project Convergence is a project that uses the Unity Game Engine, WordPress, an SQL database hosted through Laragon, PHP code, and C# in Visual Studio to create a video game that changes when interacting with an external website in real time.

MAMP & Unity to Database
           The first challenge in this sprint was getting the Unity Game Engine to work with a database. However, that brings up a significant issue: what device would I run the database on? I knew I didn’t have the funds to buy a server rack, but I 
           needed a database, or the project would fall flat. That’s where the temporary gift of MAMP would come into play. MAMP is a program that allows you to run a SQL server for free, merely running the application on your device. It wouldn’t be 
           a permanent solution, but it would suffice for the project.
           <img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/be56bcc3-1024-40d8-859a-4655eeff5e22" />

 
MAMP uses MySQL server through PhpMyAdmin to host the database, which the whole project would revolve around, and where we’d insert, update, and grab the data when needed.   
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/ab20aa49-4ee5-4cb1-a730-3b20a139d9e4" />

Now we have a Unity Project and a functioning database, both separately, 
so to finish the sprint, all that needs to be done is connect the two and have Unity confirm that tangibly. Then Unity should grab the data in the database and use it in the engine. The solution was PHP scripting. Still, in the learning process, 
unsure of how to work with PHP, I covered YoutTuber BoardToBits’s series on Unity with PHP. Even though I would later write my code to connect to the database, this code written by the YouTuber gave me a good grasp of PHP scripting.
<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/404923df-ea4d-4cbd-a25f-f0f901179f38" />

These PHP scripts poll the database for data, create users in the database, encrypt the passwords for security, and then poll the user data to be used in Unity. We use C# scripting in Unity through Visual Studio to make use of these PHP scripts 
to connect the two platforms.
<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/088759ab-89a3-4529-a5d2-60cf571f82c4" />

 
These scripts have Unity use the PHP scripts to create users, send them to the database, and log in to users- which some of them in Unity UI collaborate with. 
 <img width="975" height="485" alt="image" src="https://github.com/user-attachments/assets/661743bd-7b35-4045-8df0-b8f0f12c23a3" />
<img width="975" height="479" alt="image" src="https://github.com/user-attachments/assets/d4ea93d0-6a9f-46b1-8538-065e332b0a0b" />

Now we have a database that Unity connects to and uses that data tangibly; with the first sprint done, we now move on to the next sprint, where we need to create a website.

WordPress To Database
           Now we come to the Second & Third sprint, building the website and connecting it to the database. This project, being a hybrid between a Game and a website, needs a website that connects to a database. Around this time, I used MAMP 
           to do this; however, later on in the project, MAMP became unusable because I changed my database password in the wrong place and got locked out of the database and website. I spent two hours of troubleshooting for nothing, so I switched 
           to Laragon as MAMP’s replacement. Laragon has all the same functionality I needed for the project but more. To have a website with MAMP, you need the paid version, but Laragon would set up both the database and the website and connect 
           the two with minimal effort.
 <img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/998b519e-50a5-4456-916e-760ef2bfce85" />

WordPress was easy to install, the Website is now running on my Unity PHP database, but I needed to build an HTML page that I could do PHP scripting with HTML forms. I used the Courses Tab in WordPress to create a custom HTML template that became 
the end result.

Here is the code: 
<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/2c2272aa-7cb4-4de3-8bf3-c02dff303b4f" />

Here is the result:
 <img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/5a20936a-2550-4790-bcab-9c04e13919c7" />

In action, clicking the “give in to the love” button form would create an entry into a table, and clicking the “remove the love” will update a specific entry in the table. However, the two forms used in the final product, “True” and “False,” 
change a bool to true or false; Unity will soon, later down in this paper, check if the value if it is true. If the bool is true, other code will cause a door to open. In this sprint’s conclusion, our website is functional and interacting with 
the database as intended.

To Unity, Open The Door
           On the final sprint is the last connector. We have Unity which connects to the database, and a website that does the same. Now, all we need is to have a game in Unity react to changes in the website. Most of the hard code is done, 
           and now only the implementation is left.
 <img width="975" height="479" alt="image" src="https://github.com/user-attachments/assets/0d8551c3-fd35-461f-8ff9-3a892c6b249f" />

First, we have a table in our database that has a bool that will be used to determine if the door should be ready to be opened. Our Unity code will rely on this table to tell when to do so. Then we have the PHP we’ll use to poll that table.
 <img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/977f233a-fc36-48db-a4d7-16379391dc58" />

This PHP code connects to the database, checks the table’s bool value, and echoes that to the code we use in Unity. Unity uses this code to catch that bool value we need to check and sends it into a variable we can use.
 <img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/4294e137-2d6b-4d0f-a383-eb098b84332f" />

The code will also check if the bool’s value is 1 or true; if it is, the door in-game is ready to open. This code is called not on the game start but when the player in-game tries to open the door. In more detail, when the player interacts
with the in-game object’s collider highlighted in red. 
<img width="974" height="456" alt="image" src="https://github.com/user-attachments/assets/a0dea4e1-1813-4572-9f53-dac88930dc8e" />

It runs the OnTriggerEnter code, which runs the ”StartCoroutine(LoginPlayer());” function call, which runs code checking if the bool in the database is 1. If it is 1, the door opens.
If the bool s false, or 0, in the database, after pressing the “False” button on the website. 
<img width="460" height="89" alt="image" src="https://github.com/user-attachments/assets/91ec1e29-93b9-44a5-a264-a2edbb834d93" />

The door won’t open in game, and a “0” will be printed on the console.
<img width="975" height="455" alt="image" src="https://github.com/user-attachments/assets/015dd7ec-a80c-469a-b609-00732098193d" />

To make the door open while the game is running, all that needs to be done is press the “True” button on the website, walk out of the collider’s range, then walk back into it and the door will open!
<img width="975" height="476" alt="image" src="https://github.com/user-attachments/assets/6914abce-32c5-49f1-a15b-994ea29ba7b2" />

There we have it; we have a game that changes in real time when interacting with a website.

Why should you care?
           Internet-only video games, or live service games, are mainstream now. However, the concept of using a website simultaneously with a game is not on the market. I have seen web browsers within games for logging into accounts
           before entering the game, but this implementation is seldom, if not used at all. Players are looking for unique experiences, and ARGs are ever popular now. ARGs are extensions of video games where developers give players 
           cryptic data to sift through using different programs and methods to get desired results. These desirable results can be hidden lore, a website with more lore, etc. The games market isn’t alien or detached from this meta 
           form of gaming and interaction. My implementation could well be used to create a legitimate product on global markets people would enjoy. The concept of sifting through an ARG website that would literally change the game 
           they are playing in real-time would be addicting for the next hidden unlock in-game when they find the code in the website. I believe this implementation would be profitable and eye-catching to a decent market segment.

Conclusion
           I showed you how I connected Unity to a database, connected a website to the same database, and used the connections to make a unique product that, to my knowledge, is seldom done in the video game market. With this 
           implementation, it only works on one device. Still, all that needs to be done to make the project work on modern platforms is to, instead of using Laragon to host the database, get a dedicated server to connect to the 
           current database. I also explained to you that this implementation is a viable business model in the current gaming 
market, and how it is not so far off than ARGs which are incredibly popular. I believe this implementation might just become an actual product in the gaming market.
