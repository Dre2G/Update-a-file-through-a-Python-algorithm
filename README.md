# Update-a-file-through-a-Python-algorithm
<h1>Update a file through a Python algorithm</h1>

<h2>Description</h2>
This is a project that I completed regarding updating a file through a Python algorithm. The scenerio is based on a fictional company.
The Python elements are completed within a shell environment.

<br />

<h2>Scenerio</h2>

In this scenerio, I am security professional working at a health care company. As part of my job I am required to reqularly update a file that
identifies the employees who can access restricted content. The contents of the file are based on who is working with personal patient records.
Employees are restricted access based on their IP address. There is an allow list for IP addresses permitted to sign into the subnetwork.
There's also a remove list the identifies which employees I must remove from this allow list.

I am tasked with creating an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list.
If so, you should remove those IP addresses from the file containing the allow list.

At my organization, access to restricted content is controlled with an allow list of IP addresses. The <em>"allow_list.txt"</em> file identifies these
IP addresses that should no longer have access to this content. I created an algorithm to automate updating the <em>"allow_list.txt"</em> file and remove
these IP addresses that should no longer have access.

<p >
<h3> Open the file that contains the allow list </h3>
For the first part of the algorithm, I opened the <em>"allow_list.txt"</em> file. First, I assigned this file name
as a string to the <em>"import_file"</em> variable:
  
<br align="center"/>
<img src="https://imgur.com/CLqvhQ0.png" height="80%" width="80%" alt="Control Categories"/>
<br />

Then, I used a <em>with</em> statement to open the file:

<br align="center"/>
<img src="https://imgur.com/G27SCfI.png" height="80%" width="80%" alt="Control Categories"/>
<br />
 
<h3> Describe the permissions string </h3>

The 10-character string can be deconstructed to determine who is authorized to access the
file and their specific permissions. The characters and what they represent are as follows:
- <b>1st character</b>: This character is either a <em>d</em> or hyphen <em>(-)</em> and indicates the file type. If it’s
a <em>d</em>, it’s a directory. If it’s a hyphen <em>(-)</em>, it’s a regular file.
-   <b>2nd-4th characters</b>: These characters indicate the read <em>(r)</em>, write <em>(w)</em>, and execute <em>(x)</em>
permissions for the user. When one of these characters is a hyphen <em>(-)</em> instead, it
indicates that this permission is not granted to the user.
-   <b>5th-7th characters</b>: These characters indicate the read <em>(r)</em>, write <em>(w)</em>, and execute <em>(x)</em>
permissions for the group. When one of these characters is a hyphen <em>(-)</em> instead, it
indicates that this permission is not granted for the group.
-   <b>8th-10th characters</b>: These characters indicate the read <em>(r)</em>, write <em>(w)</em>, and execute <em>(x)</em>
permissions for other. This owner type consists of all other users on the system apart
from the user and the group. When one of these characters is a hyphen <em>(-)</em> instead,
that indicates that this permission is not granted for other.

For example, the file permissions for <em>project_t.txt</em> are <em>-rw-rw-r--</em>. Since the first
character is a hyphen <em>(-)</em>, this indicates that <em>project_t.txt</em> is a file, not a directory. The
second, fifth, and eighth characters are all <em>(r)</em>, which indicates that user, group, and other all have
read permissions. The third and sixth characters are <em>(w)</em>, which indicates that only the user and
group have write permissions. No one has execute permissions for <em>project_t.txt</em>.

<br />

<h3>Change file permissions</h3>

The organization determined that other shouldn't have write access to any of their files. To
comply with this, I referred to the file permissions that I previously returned. I determined
<em>project_k.txt</em> must have the write access removed for other.

The following code demonstrates how I used Linux commands to do this:

<br/>
<img src="https://imgur.com/uEcfgI7.png" height="80%" width="80%" alt="Control Categories"/>
<br />

The first two lines of the screenshot display the commands I entered, and the other lines
display the output of the second command. The <em>chmod</em> command changes the permissions on
files and directories. The first argument indicates what permissions should be changed, and
the second argument specifies the file or directory. In this example, I removed write
permissions from other for the <em>project_k.txt</em> file. After this, I used <em>ls -la</em> to review the
updates I made.


<br />

<h3>Changing file permissions on hidden file</h3>

The research team at my organization recently archived project_x.txt. They do not want
anyone to have write access to this project, but the user and group should have read access.

The following code demonstrates how I used Linux commands to change the permissions:

<br/>
<img src="https://imgur.com/OUoRCU8.png" height="80%" width="80%" alt="Compliance Checklist choices"/>
<br />

The first two lines of the screenshot display the commands I entered, and the other lines
display the output of the second command. I know <em>.project_x.txt</em> is a hidden file because
it starts with a period <em>(.)</em>. In this example, I removed write permissions from the user and
group, and added read permissions to the group. I removed write permissions from the user
with <em>u-w</em>. Then, I removed write permissions from the group with <em>g-w</em>, and added read
permissions to the group with <em>g+r</em>.


<br />

<h3>Change directory permissions</h3>

My organization only wants the <em>researcher2</em> user to have access to the <em>drafts</em> directory
and its contents. This means that no one other than <em>researcher2</em> should have execute
permissions.

The following code demonstrates how I used Linux commands to change the permissions:


<br/>
<img src="https://imgur.com/VGs0H0M.png" height="80%" width="80%" alt="Risk Assessment"/>
<br />

The first two lines of the screenshot display the commands I entered, and the other lines
display the output of the second command. I previously determined that the group had
execute permissions, so I used the <em>chmod</em> command to remove them. The <em>researcher2</em> user
already had execute permissions, so they did not need to be added.

<br />

<h3>Summary</h3>

I changed multiple permissions to match the level of authorization my organization wanted for
files and directories in the <em>projects</em> directory. The first step in this was using <em>ls -la</em> to
check the permissions for the directory. This informed my decisions in the following steps. I
then used the <em>chmod</em> command multiple times to change the permissions on files and
directories
