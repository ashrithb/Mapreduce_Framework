# Mapreduce_Framework
The framework executes MapReduce programs with distributed processing on a cluster of computers. This project includes MapReduce program execution, basic distributed systems, fault tolerance, OS-provided concurrency facilities (threads and processes), and networking (sockets). All of this is built in Python!!

This project consists of two major pieces of code. A manager that listens for user-submitted MapReduce jobs and distributes the work among Workers. Multiple Worker instances receive instructions from the Manager and execute map and reduce tasks that combine to form a MapReduce program. Here is a basic rundown of what my program looks like: 
![flowchart excalidraw](https://github.com/ashrithb/Mapreduce_Framework/assets/92128095/67808b2f-53d0-415b-bb66-3dac353b6dc6)
