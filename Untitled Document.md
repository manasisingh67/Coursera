# IEEE STANDARD 1016: Software Design Specification

The Software Design Specification (SDS) sections provide you with guidelines related to the structure and the contents of SDS document. The Software Design Specification document includes at least these sections.

For the project, your team may have good reasons for wanting to deviate from this proposed outline. If a section is not applicable in your case, do not delete it; instead, give the topic heading and write "Not applicable".

You will note that there is some overlap in the content between different documents (i.e. the User Requirements Specification Document and the Software Design Specification Document.) This redundancy allows each document to stand on its own.

# The Software Design Specification Outline

## Introduction
### 1.1 Purpose of this document

This SDS document contains all the features and procedures that how we are going to develop our Exam-cell system (Web app). We explained the working of our system using Use-case diagram, Sequence diagram and also class diagram.

### 1.2 Scope of the development project

The primary purpose of our web app is to make the work of exam cell easier by generating an automatic exam schedule, seating allotment, invigilation schedule and the secondary purpose is toSend emails to the students, faculty, staff their individual exam schedule, seating allotment, invigilation schedule respectively.

Our database will be able to access the data from the Faculty and students ERP and admin will be able to add the schedule-time and available class rooms. Basically we want to decrease the burden of our Exam cell and also to give user friendly output to students and faculty.

### 1.3 Definitions, acronyms, and abbreviations

HTML: Hyper text Markup language

OS: Operating System.

### 1.4 References

NA

### 1.5 Overview of document

NA

## System architecture description
### 2.1 Overview of modules / components

The various modules of our system are explained here:

 Module 1: Authentication

Attributes: 1. User id

                2. Password
Methods: 1. Log in ( );

             2. Verify ( );
.Module 2: Exam-cell (Home page)

Methods: 1. Faculty ( );

            2. Student ( );

               3. Log out ( );
. Module 3: Student details

** ** Attributes: 1. S.name

                      2. S.roll no

                                         3. Batch

                                         4. E-mail

                      5. Branch

                          6. Subjects enrolled in
Methods: 1. Submit ( );

                 2. Logout ( );
. Module 4: Exam Hall

Attributes:

CR's needed

LT's needed

Labs needed

Methods: 1. Submit ( );

Log out ( );
. Module 5: Faculty details

Attributes: 1. F.name

               2. E-mail

               3. F.id

               4. Subjects handled
Methods: 1. Submit ( );

             2. Log out ( );
. Module 6 : Student display

Inherits the functions from its base class Student details and exam hall

Functions: 1. Sallot ( );

 2. Log out ( );
. Module 7: Faculty display
Inherits the functions from its base class Faculty details and exam hall

Functions: 1. Fallot ( );

    2. Log out ( );
Module 8: Exam schedule

Inherits the functions from student details.

Attributes:

     1. from date

     2. To date

     3. Time slot

     4. from time

     5. to time

     6. Exam type.
Methods: 1. Generate schedule ( );

. Module 9: S-mail
It inherits the functions from the student display and exam schedule.

Methods:

      1. E\_schedule mail ( );

      2. S\_allotment mail ( );

      3. Log out ( );
. Module 10: F-mail
Inherits the functions from the faculty display and exam schedule

Methods:

     1. E-schedule mail ( );

     2. I\_allotment mail ( );

     3. Log out ( );
2.2 Structure and relationships

Make clear the interrelationships and dependencies among the various components. Structure charts can be useful here. A simple finite state machine can be useful in demonstrating the operation of the product. Include explanatory text to help the reader understand any charts.

2.3 User interface issues

Error messages display : To prevent errors various precautions will be taken while writing an effective algorithm but still if there are some errors then we will generate a warning message, after which the user has to correct the error for going to the next step.

Database : The database we will be using is the NIIT nucleus for students and staff and moreover we will access the class room data and labs data. The server will have to be updated regularly so that no wrong data is available for processing.

3 . Consistency in command is applied throughout our software.

Standard buttons like "Back" "Refresh" and "Home" will appear on every page except the login page.

-.Layout- The system will have a login page wherein admin has to enter his credentials and login.
-.Then various function options will appear and the user has to choose the one he wants and click next.
-. The bottom will always have print command after a function has been performed.

Detailed description of components

.3.1 Authentication
Identification	First user interface that user will see
Type	Module
Identification	Home page of the App.
Purpose	It gives access to the web application
Function	User will log in using his User name and password and `then verify( ) will check whether the user provided the correct details which are already entered in the database and if the entered details are correct then the user gets access to use the web application..
Subordinates	The functional components are:
Log in ( );
Verify ( );
Attributes are:Username - Primary key.Password |
| Dependencies | Without specifying the User name and the password by the users, he cannot access the application and so every other module of the application is dependent on this module. |
| Interfaces | Details entered by the user will be authenticated by comparing the same values with the values present in the database. If the user provides incorrect data, then an error message will be displayed and he would not be allowed to access the application and for the encryption of the data, password attribute is useful. |
| Resources | We need a device with any operating system, web browser, memory, ERP database. |
| Processing | Log in ( ) will accept the user id and password in the string format , returns it to Verify ( ) , then it compares the values with the values of the database and if both the values match, it returns true and then user will be able to access the app and if do not match it returns false and so the user will not be able to access the application |
| Data | Both User id and password entered by the user will be in the form of text boxes. |

.3.2 Exam Cell
Type	A module
Purpose	Function and performance requirements implemented by the design component, including derived requirements. Derived requirements are not explicitly stated in the SRS, but are implied or adjunct to formally stated SDS requirements.
Function	This module is an home page of our web app. Here User will see 3 options called student ( ), Faculty( ) and logout ( ).He can click on any of them as per his requirements. This is possible only if the user enters proper Username and password.
Subordinates	Functional components are;1.Student( );2.Faculty ( );3.Logout ( );
Dependencies	This module is just to take users to student details and faculty details page
Interfaces	Home page contains 3 buttons named Students ,faculty and it will take users to the Student details page on clicking student button and faculty details page on clicking faculty button.
Resources	We need a device with any operating system, web browser, and memory.
Processing	If user clicks student button, then he will reach a page called student details and if he clicks faculty button, he will reach an another page called faculty details.
Data	The page contains three buttons named:
Students
Faculty and
Logout. |
3.3 Student details

Identification	
Type	A module
Purpose	For seating allotment, we need the details of a student and the subjects in which he has enrolled. This module is for fetching the details of the student from ERP database.
Function	When user reaches this student details page, only thing he has to do is to click submit button to give the details to the allot function.
Subordinates	Attributes:
Sname
Enrollment no
Batch
Branch
Email
Subjects Methods:
Submit ( );
Logout ( ); | | Dependencies | Student display function is dependent on this module as student display module will be inherited from this module. | | Interfaces | Two options are displayed in the form of buttons:
Submit
Logout | | Resources | We need a device with any operating system, web browser, memory, ERP database. | | Processing | If the user clicks submit button, then the details fetched from the ERP will be sent to the fallot function in the student display module.. | | Data | Both Submit and Logout options will be in the form of buttons. |
3.4 Exam Hall

Identification	
Type	A module.
Purpose	This module is to add the details about the module rooms and this data is helpful to generate the seating allotment and invigilation schedule.
Function	When the user will reach to this page, he have to enter all the details about the examination hall and then he has to click the submit button and so that entered details will be accessed by the Exam schedule function in the Exam timetable module.
Subordinates	Attributes:1.Hall Id (primary key)2.CR's available.3.LT's available.4.Labs available.5.capacity Methods:
Submit ( );
Logout ( ); | | Dependencies | Student display, faculty display and exam schedules are inherited by this Exam hall module and so the above mentioned modules are dependent on this module. | | Interfaces | Hall id , CR , LT and Labs available are entered by the user in the provided drop down menu of the text boxes. Submit and the logout are the buttons. | | Resources | We need a device with any operating system, web browser, and memory. | | Processing | User will enter all the details of the exam cell at first and then click submit button. By clicking on submit button, all the details will get stored in the Exam hall database and then the other methods will access the details from the database whenever required. | | Data | All the attributes mentioned will be entered by the user in the provided text box by using the drop down menu and the methods submit and logout will be represented in the form of buttons. |
3.5 Faculty details

Identification	
Type	A module.
Purpose	For invigilation schedule, we need the details of a faculty and the subjects which he is teaching. This module is for fetching the details of the faculty from ERP database.
Function	When user reaches this Faculty details page, only thing he has to do is to click submit button to give the details to the fallot function in the Faculty display function.
Subordinates	Attributes:
Fname
Fid
Department
Sub handle Methods:
Submit
Logout. | | Dependencies | Faculty display function is dependent on this module as Faculty display module will be inherited from this module. | | Interfaces | Two options are displayed in the form of buttons:1.Submit 2.Logout | | Resources | We need a device with any os, web browser, memory and ERP database. | | Processing | If the user clicks submit button, then the details fetched from the ERP will be sent to the allot function in the faculty display module. | | Data | Both the submit and logout buttons will be in the form of buttons. |
3.6 Student display

Identification	
Type	A module.
Purpose	For seating allotment and exam schedule, we need the details of the students.
Function	When user reaches this Faculty details page, only thing he has to do is to click submit button to give the details to the fallot function in the Faculty display function.
Subordinates	Attributes:1.Fname2.Fid3.Department4.Sub handle Methods:1.Submit2.Logout.
Dependencies	Faculty display function is dependent on this module as Faculty display module will be inherited from this module.
Interfaces	Both submit and logout buttons will appear in the form of buttons.
Resources	We need a device with any os, web browser, memory, ERP database.
Processing	If the user clicks submit button, then the details fetched from the ERP will be sent to the fallot function in the faculty display module.
Data	Both the submit and logout buttons will be in the form of buttons.
3.7 Faculty display

Identification	
Type	A module.
Purpose	For invigilation schedule, we need the details of the faculty
Function	When user reaches this Faculty details page, only thing he has to do is to click submit button to give the details to the fallot function in the Faculty display function.
Subordinates	Attributes:
Fname
Fid
Department
Sub handle Methods:
Submit
Logout. | | Dependencies | Faculty display function is dependent on this module as Faculty display module will be inherited from this module. | | Interfaces | Two options are displayed in the form of buttons:1.Submit 2.Logout | | Resources | We need a device with any os, web browser, memory and ERP database. | | Processing | If the user clicks submit button, then the details fetched from the ERP will be sent to the allot function in the faculty display module. | | Data | Both submit and logout buttons will be in the form of buttons. |
3.8 Exam schedule

Identification	
Type	A module.
Purpose	To generate the exam schedule and is inherited from its base module Student details.
Function	When user reaches this page, he has to submit all the details of the exam and then if he clicks generate schedule, as this module is inherited from the student details module, it uses the subjects that students has enrolled from the base module and then it will generate exam schedule.
Subordinates	Attributes:
from date
To date
Time slot
From time
To time
Exam type Methods:1.submit ( );2.generate schedule ( );3.Logout ( ); | | Dependencies | S mailing and F mailing modules are dependent on this module as both are inherited from this Exam schedule module. | | Interfaces | All the attributes mentioned will be entered by the users in provided text boxes.Logout, submit and generate schedule options will appear in the form of buttons. | | Resources | We need a device with any os, web browser, memory and ERP database. | | Processing |
user enters the details of the exam hall
User will click the submit button
User will choose generate schedule option and thus the schedule is generated. | | Data | All the attributes mentioned will be the inputs from the user and Submit, generate schedule and logout options will be appeared in the form of buttons. |
3.9 S-mailing:

Identification	
Type	A module.
Purpose	To send the individual exam schedule and seating allotment to the students mail.
Function	When the user reaches this page,
Subordinates	Attributes: Methods:1.submit ( );2.generate schedule ( );3.Logout ( );
Dependencies	S mailing and F mailing modules are dependent on this module as both are inherited from this Exam schedule module.
Interfaces	Logout, submit and generate schedule options will appear in the form of buttons.
Resources	We need a device with any os, web browser, memory, ERP database.
Processing	
Data	Both submit and logout buttons will be in the form of buttons.
4.0 Reuse and relationships to other products

Our web application can be reused and extended to the larger extent but the efficiency cannot be assured as we are solving for an NP-hard problem.

But As the data like number of students, invigilators, subjects, class rooms are not constant and they will be increased in future. To some extent with the same efficiency, Exam cell can use this app and if the data will become too large, then efficiency will get decreased.

5.0 Design decisions and tradeoffs

We use the HTML, CSS and bootstrap for the front end and PHP for back end.

Exam hall





Student



Admin



6.0 Pseudocode for components

7.0 Appendices (if any)

SDS component template

The template given below suggests a reasonable structure for giving a thorough description of each component described in Part 3 of the SDS. The specific information depends in part on the design approach. Your team must adapt this template to your needs and describe it in section 3.1 of your SDS.

Identification	
Type	A module, a subprogram, a data file, a control procedure, a module, etc
Purpose	Function and performance requirements implemented by the design component, including derived requirements. Derived requirements are not explicitly stated in the SRS, but are implied or adjunct to formally stated SDS requirements.
Function	What the component does, the transformation process, the specific inputs that are processed, the algorithms that are used, the outputs that are produced, where the data items are stored, and which data items are modified.
Subordinates	The internal structure of the component, the constituents of the component, and the functional requirements satisfied by each part.
Dependencies	How the component's function and performance relate to other components. How this component is used by other components. The other components that use this component. Interaction details such as timing, interaction conditions (such as order of execution and data sharing), and responsibility for creation, duplication, use, storage, and elimination of components.
Interfaces	Detailed descriptions of all external and internal interfaces as well as of any mechanisms for communicating through messages, parameters, or common data areas. All error messages and error codes should be identified. All screen formats, interactive messages, and other user interface components (originally defined in the SRS) should be given here.
Resources	A complete description of all resources (hardware or software) external to the component but required to carry out its functions. Some examples are CPU execution time, memory (primary, secondary, or archival), buffers, I/O channels, plotters, printers, math libraries, hardware registers, interrupt structures, and system services.
Processing	The full description of the functions presented in the Function subsection. Pseudocode can be used to document algorithms, equations, and logic.
Data	For the data internal to the component, describes the representation method, initial values, use, semantics, and format. This information will probably be recorded in the data dictionary.