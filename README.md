# QR King
#### Video Demo:  https://www.youtube.com/watch?v=u8P66bdpu1o
#### Description:

Introduction:

The name of my project is QR King. It is a web-based application that allows users to register, log-in; and then create, delete, and
load/view QR codes. I contemplated many different projects that I could do, and which problems they could solve. For example, first,
I was going to work on an informative page that provides reliabe visa information for tourists in Thailand. Then, after speaking with
my family and friends, we thought of perhaps making a social media website that connects lyricists and instrumental musicians. After some
more contemplation, I thought of the 'QR code' part of the lecture by professor David in Week 6, and thought that it was so cool. I then
thought of an instance when I tried to create a QR code for one of my projects at university, but it was very difficult to find a
service that was free. I didn't have to think any further -- This is the problem that I want to solve. After a good month of working on
my project, low and hgbehold, QR King came to life.

Developmemt Process:

Though I met plenty of challenges when developing QR King, I learned a lot from it. First of all, there was no specification like there
is in each problem set. I actually had to sit down and plan out step by step what I wanted to do. That was the first challenge.
Here is the "blueprint" that I wrote out and followed:

Pseudocode / To do:
1. Build the project
    1. Create folder
    2. Adding files
    3. Connecting files

2. Theres a nav bar so…
    1. Create qr code
    2. My qr codes (history)
    3. About/homepage

3. Register, login
    1. Login and register similar to CS50 Finance,
    2. Perhaps add more styles with CSS

4. Store your previous QR codes in a flask template. (like history page from finance)

Simplicity & Functionality is priority, Not necessarily style.

Must have table to store QR codes in a database
Note to self: I have to create them (STORE IN THE TABLE), show them (AS PER mycoses.html)
and delete them (DELETE FROM THE TABLE.)

After creating the blueprint, I followed it step by step; creating all of the necessary folders, organizing the files, and then
finally moving on to writing the code. In writing the code, there is one main challenge that I want to speak about. It was not only
the main challenge, but also the major lesson that shifted my way of thinking. The challenge was storing the QR code into the
sqlite database. Initally, I tried to store the QR image encoded as a Base64 string into the database. This process was quite
challenging and I couldn't quite get it right. After failing many times and being frustrated for many days, I suddently thought:
"Why don't I just store the link of the QR code in the database and then generate it on demand?" I did that, and it worked like magic.
Now I just had to figure out where to store the qr code once it was generated. I wanted to create a folder to store all of the created
files, but that would take up too much space, thus I decided to create just one image in the static folder called "new.png" that would
be replaced each time a QR code is created. This works, but I suspect that if many more users would register and generate
QR codes simultaneously, the server will overload cause bugs. I don't yet know how to solve this problem, but at least I am learning
about the challenges that that maybe faced if we want to scale applications.

The different folders and files:

Just like in CS50 finance, since I used Flask, I created a static folder and a templates folder as well as a few different extra
files such as "app.py", "helpers.py"(borrowed from CS50 finance) and "project.db"

In the static folder I included one "new.png" and one "styles.css" as well as a "qr.png" which is a randomly generated qr code that
acts as a background for the website logo.

In the "templates" folder I included 9 html templates: apology.html, create.html, delete.html, index.html, layout.html, login.html
mycodes.html qrcode.html, register.html. All of the files are extensions of "layout.html", vis-a-vis Flask Jinja templates.

1. apology.html was borrowed from CS50 finance, to return an apology if there is any error.
2. create.html allows a user to input data as to which link they want a QR code for, and what they want to call it. The data will be
stored in a sqlite database, "project.db".
3. delete.html allows users to delete QR codes they created by a dropdown list and a button.
4. index.html is the welcome page that welcomes the user and communicates the inspiration behind the project.
5. layout.html is the "mother" html file and extends all of the other jinja templates.
6. login.html allows users to login
7. mycodes.html allows users to select which QR code they want to load via a dropdown bar.
8. qrcode.html is the html file that shows the QR code once it is selected in myqrcodes.html.
9. register.html allows users to register for an account. The password must include special character.

The "app.py" file is where all of the functionality takes place. It contains 7 Flask "functions" that mainly serve the purpose
of connecting the users data into the sqlite database, and rendering that data to achieve the desired output.

"helpers.py" is simply borrowed from CS50 finance, and includes the "apology()" function and a "login_required()" function.

project.db is the sqlite database, containing 2 tables:
1. users: stores user data (id, username, password hash)
2. mycodes: stores the qr code data (id, QR link, designated name)

Summary:

QR King is a project that I am super proud to present. Along the way of developing QR King, I met plenty of obstacles and challenges,
but ultimately it was a fun experience which I learned a lot from and will surely help me in my aspirations of becoming a developer.
The project solves the problem of not being able to generate lasting QR codes for free. I will definitely use my own website if
I ever need a QR code; and that really does feel so rewarding to say. Thank you.