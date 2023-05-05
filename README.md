Download Link: https://assignmentchef.com/product/solved-cse5306-lab1-client-server-architecture
<br>
<strong><u>Objectives</u></strong>:

<ol>

 <li>An introduction to sockets.</li>

 <li>Exposure to thread management.</li>

</ol>

<strong><u>Project Specification</u></strong>:

These will be <strong>individual</strong> projects. You may write the program in any language that is supported under any Integrated Development Environment (IDE). Keep in mind that available controls, objects, libraries, et cetera, may make some of these tasks easier in one language than in another. Finally, because of the lack of restrictions on IDEs, you will have to have that IDE available to demo to the TA (e.g., you will demo the program on your own laptop).

All components should be managed with a <em>simple</em> GUI.  The GUI should provide a way to kill the process without using the ‘exit’ button on the window.

You will write a system consisting of a server and three client processes.  Each client process will connect to the server over a socket connection and register a username at the server. The server should be able to handle all three clients simultaneously and display the names of the connected clients in real time.

Two or more clients may not use the same username simultaneously.  Should the server detect a concurrent conflict in username, the client’s connection should be rejected, and the client’s user should be prompted to input a different name.

Every ten seconds, the server will randomly select a connected client and send that client an integer between 3 and 9.  Upon receiving the integer, the client will pause (e.g., sleep or otherwise suspend) the thread managing the connection to the server for a period equaling the value received from the server, in seconds.  The client’s GUI will maintain a decrementing countdown timer indicating when the thread will resume, as well as a button to skip the wait and resume the thread’s operation immediately.

When the client thread is finished waiting, it will reply to the server with a message stating, “Client &lt;name&gt; waited &lt;#&gt; seconds for server.”  The server will display this message on its GUI.  This sequence will be repeated until the components are manually terminated by the user.

<strong><u>Client</u> </strong>




<strong>Startup: </strong>

<ol>

 <li>Prompt the user to input a username.</li>

 <li>Connect to the server over a socket and register the username.

  <ol>

   <li>When the client is connected, the user should be notified of the active connection.</li>

   <li>If the provided username is already in use, the client should disconnect and prompt the user to input another username.</li>

  </ol></li>

 <li>Proceed to accept commands received from the server until manually terminated by the user.</li>

</ol>




<strong>Receiving Pause Commands</strong>:

<ol>

 <li>The client will wait for ‘Pause’ commands from the server.</li>

 <li>Upon reception of a ‘Pause’ command, the client will suspend the thread managing the connection to the server for the indicated period.</li>

 <li>The client will display a counter on its GUI which decrements in accordance with the number of seconds remaining until the thread resumes.</li>

 <li>The thread will resume when either:

  <ol>

   <li>The timer expires; or,</li>

   <li>The user manually resumes the thread by pressing a button on the GUI.</li>

  </ol></li>

 <li>Return to <strong>Receiving Pause Commands: Step 1</strong> until manually killed by the user.</li>

</ol>




<strong><u>Server</u> </strong>




The server should support three concurrently connected clients.  The server should indicate which of those clients is presently connected on its GUI.  The server will execute the following sequence of steps:

<ol>

 <li>Startup and listen for incoming connections.</li>

 <li>Print that a client has connected, and:

  <ol>

   <li>If the client’s username is available (e.g., not currently being used by another client), fork a thread to handle that client; or,</li>

   <li>If the username is in use, reject the connection from that client.</li>

  </ol></li>

 <li>Every ten seconds, the server should randomly select a connected client, then:

  <ol>

   <li>Randomly choose and integer between 3 and 9; and,</li>

   <li>Send that integer to the selected client.</li>

  </ol></li>

 <li>The server will then wait for a reply from that client.</li>

 <li>Upon receiving a reply from a client, the server will print the reply to its GUI.</li>

 <li>Return to <strong>Step 1</strong> until manually killed by the user.</li>

</ol>




<strong>Notes: </strong>

<ul>

 <li>All three clients and the server may run on the same machine.</li>

 <li>The server must correctly handle an unexpected client disconnection without crashing.</li>

 <li>When a client disconnects from the server, the server GUI must indicate this to the user in real time.</li>

 <li>The program must operate independently of a browser.</li>

</ul>

<strong> </strong>

<strong><u>Citations</u></strong>:

You may use open source code found on the Internet in your program.  When citing this code:

A full list of your source URLs should be included in your writeup file.  Including generic citations (for instance, simple listing “StackOverlow.com” without additional details) will result in a ten (10) point deduction in your lab grade, per instance.