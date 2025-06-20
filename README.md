# Update-a-file-through-a-Python-algorithm
<h1>Update a file through a Python algorithm</h1>

<h2>Description</h2>
This is a project that I completed regarding updating a file through a Python algorithm. The scenerio is based on a fictional company.
The Python elements are completed within a shell environment.

<br />

<h2>Scenerio</h2>

In this scenerio, I am a security professional working at a health care company. As part of my job I am required to reqularly update a file that
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
<img src="https://imgur.com/G27SCfI.png" height="80%" width="80%" alt="allow_list file"/>
<br />

Then, I used a <em>with</em> statement to open the file:

<br align="center"/>
<img src="https://imgur.com/NYadV0J.png" height="80%" width="80%" alt="with statement"/>
<br />

In my algorithm, the <em>with</em> statement is used with the <em>.open()</em> function is read mode to open the allow list
file for the purpose of reading it. The purpose of opening the file is allow me to access the IP addresses stored in 
the list file. The <em>with</em> keyword will help manage the resources by closing the file after exiting the <em>with</em> statement.
In the code <em>with</em> <em>open (import_file, "r") as file:</em>, the <em>open()</em> function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, <em>"r"</em> indicates that I want to read it. The code also uses the <em>as</em> 
keyword to assign a variable named <em>file</em>; <em>file</em> stores the output of the <em>.open()</em> function while I work within the <em>with</em> statement.

 
<h3> Read the file contents </h3>

In order to read the file contents, I used the <em>.read()</em> method to covert it into the string.
<br align="center"/>
<img src="https://imgur.com/VpUygtR.png" height="80%" width="80%" alt=".read() method"/>
<br />

When using an <em>.open()</em> function that includes the argument <em>"r"</em> for "read", I can call the <em>.read()</em>
function in the body of the <em>with</em> statement. The <em>read</em> method coverts the file into a string and allows
me to read it. I applied the <em>.read()</em> method to the <em>b</em> variable identified in the <em>with</em> statement.
Then, I assigned the string output of this method to the varible <em>ip_addresses</em>.

In summary, this code reads the contents of the <em>"allow_list.txt"</em> file into a string format that allows me to later use the 
string to organize and extract data in my Python program.

<br />

<h3>Convert the string into a list</h3>

In order to remove individual IP addresses from the allow list, I needed it to be in list format.
Therefore, I next used the <em>.split()</em> method to convert the <em>ip_addresses</em> string into a list:
<br/>
<img src="https://imgur.com/QaW8jVn.png" height="80%" width="80%" alt=".split() method"/>
<br />

The <em>.split()</em> function is called by appending it to a string variable. It works by converting the contents
of a string to a list. The purpose of splitting <em>ip_addresses</em> into a list is to make it easier to remove IP addresses
from the allow list. By default, the <em>.split()</em> function splits the text by whitespace into list elements. 
In this algorithm, the <em>.split</em> function takes the data stored in the variable <em>ip_addresses</em>, which is a string of IP addresses
that are each separated by whitespace, and it converts this string into a list of IP addresses. To store this list, 
I reassigned it back to the variable <em>ip_addresses</em>.


<br />

<h3>Iterate through the remove list</h3>

A key part of my algorithm involves iterating through the IP addresses that are elements in the <em>.remove_list</em>.
To do this, I incorporated a <em>for</em> loop:

<br/>
<img src="https://imgur.com/o7slN4o.png" height="80%" width="80%" alt="for loop"/>
<br />

The <em>for</em> loop in Python repeats code for a specified sequence. The overall purpose of the <em>for</em>
loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence.
The <em>for</em> keyword starts the <em>for</em> loop. It is followed by the loop variable <em>element</em> and the  key word <em>in</em>.
The key word <em>in</em>indicates to iterate through the sequence <em>ip_addresses</em> and assign each value to the loop variable <em>element</em>.


<br />

<h3>Remove IP addresses that are on the remove list</h3>

My algorithm requires removing any IP address from the allow list, <em>ip_addresses</em>, that is also
contained in <em>remove_list</em>. Because there were not any duplicates in <em>ip_addresses</em>, I was
able to use the following code to do this:


<br/>
<img src="https://imgur.com/u4v5WJW.png" height="80%" width="80%" alt="remove code"/>
<br />

First, within my <em>for</em> loop, I created a conditional that evaluated whether or not the loop
variable <em>element</em> was found in the <em>ip_addresses</em> list. I did this because applying
<em>.remove()</em> to elements that were not found in <em>ip_addresses</em> would result in an error.


Then, within that conditional, I applied <em>.remove()</em> to <em>ip_addresses</em>. I passed in the loop
variable <em>element</em> as the argument so that each IP address that was in the <em>remove_list</em>
would be removed from <em>ip_addresses</em>

<br />

<h3>Update the file with the revised list of IP addresses</h3>

As a final step in my algorithm, I needed to update the allow list file with the revised list of IP
addresses. To do so, I first needed to convert the list back into a string. I used the <em>join()</em>
method for this:

<br/>
<img src="https://imgur.com/PaO6iu6.png" height="80%" width="80%" alt="update allow list"/>
<br />

The <em>.join()</em> method combines all items in an iterable into a string. The <em>.join()</em> method is
applied to a string containing characters that will separate the elements in the iterable once
joined into a string. In this algorithm, I used the <em>.join()</em> method to create a string from the
list <em>ip_addresses</em> so that I could pass it in as an argument to the <em>.write()</em> method when
writing to the file <em>"allow_list.txt"</em>. I used the string <em>("\n")</em> as the separator to instruct
Python to place each element on a new line.


Then, I used another <em>with</em> statement and the <em>write()</em> method to update the file:

<br/>
<img src="https://imgur.com/ni22wmT.png" height="80%" width="80%" alt="with and write()"/>
<br />

This time, I used a second argument of <em>"w"</em> with the <em>open()</em> function in my <em>with</em> statement.
This argument indicates that I want to open a file to write over its contents. When using this
argument <em>"w"</em>, I can call the <em>write()</em> function in the body of the <em>with</em> statement. The
<em>write()</em> function writes string data to a specified file and replaces any existing file content.


In this case I wanted to write the updated allow list as a string to the file <em>"allow_list.txt"</em>.
This way, the restricted content will no longer be accessible to any IP addresses that were
removed from the allow list. To rewrite the file, I appended the <em>.write()</em> function to the file
object <em>file</em> that I identified in the <em>with</em> statement. I passed in the <em>ip_addresses</em> variable as
the argument to specify that the contents of the file specified in the <em>with</em> statement should
be replaced with the data in this variable.

<br />

<h3>Summary</h3>

I created an algorithm that removes IP addresses identified in a <em>remove_list</em> variable from
the <em>"allow_list.txt"</em> file of approved IP addresses. This algorithm involved opening the
file, converting it to a string to be read, and then converting this string to a list stored in the
variable <em>ip_addresses</em>. I then iterated through the IP addresses in <em>remove_list</em>. With each
iteration, I evaluated if the element was part of the <em>ip_addresses</em> list. If it was, I applied the
<em>.remove()</em> method to it to remove the element from <em>ip_addresses</em>.. After this, I used the
<em>.join()</em> method to convert the <em>ip_addresses</em> back into a string so that I could write over
the contents of the <em>"allow_list.txt"</em> file with the revised list of IP addresses.






