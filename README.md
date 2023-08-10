# MapReduce Framework (Inspired by Google's Model)

## Overview
This MapReduce framework aims to bring the powerful distributed data processing capabilities, similar to those of Google, to any cluster of computers. By using this framework, you can process vast amounts of data using the MapReduce paradigm with ease and reliability. It includes MapReduce program execution, basic distributed systems, fault tolerance, OS-provided concurrency facilities (threads and processes), and networking (sockets). This was inspired by [Google’s original MapReduce paper](https://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf), and all of this is built in Python!!

This project consists of two major pieces of code. A manager that listens for user-submitted MapReduce jobs and distributes the work among Workers. Multiple Worker instances receive instructions from the Manager and execute map and reduce tasks that combine to form a MapReduce program. Here is a basic rundown of what my program looks like: 
![flowchart excalidraw](https://github.com/ashrithb/Mapreduce_Framework/assets/92128095/67808b2f-53d0-415b-bb66-3dac353b6dc6)



### Features

- **Distributed Processing**: Harness the power of multiple computers to process data concurrently.
- **Fault Tolerance**: The framework ensures that tasks are recovered and re-executed in case of failures.
- **Networking**: Seamless communication between the Manager and Worker nodes through efficient socket implementation.
- **Concurrency**: Utilizes the OS-provided facilities (threads and processes) to achieve high-level concurrency and parallelism.

## Architecture

- **Manager**: The central node listens for user-submitted MapReduce jobs and efficiently distributes the work among Workers.
- **Worker Instances**: Multiple worker nodes receive instructions from the Manager and execute the map and reduce tasks that form a MapReduce program.

## Usage (Hypothetical)

\```bash
# Start the Manager node
python manager.py start

# Submit a MapReduce job (example)
python submit_job.py --input data.txt --map mapper.py --reduce reducer.py
\```

(Note: Since the actual code isn't provided, this usage section is hypothetical and for illustrative purposes only.)

## Learning Goals Achieved

- **MapReduce Execution**: Gained deep insights into the inner workings of the MapReduce paradigm and its execution.
- **Distributed Systems**: Developed understanding and practical experience with basic distributed systems.
- **Fault Tolerance**: Implemented mechanisms to handle node failures gracefully.
- **Concurrency**: Leveraged OS facilities for managing threads and processes.
- **Networking**: Implemented socket programming to ensure seamless communication between different components of the framework.

## Future Improvements

- Implement data shuffling and sorting between the map and reduce stages.
- Enhance fault-tolerance mechanisms to handle large-scale cluster failures.
- Introduce a user-friendly GUI for monitoring job progress and node status.

## Acknowledgements

Inspired by Google's original MapReduce paper. The project served as an excellent opportunity to delve deep into distributed systems and large-scale data processing.
