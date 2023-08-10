# MapReduce Framework (Inspired by Google's Model)

## Overview
This MapReduce framework aims to bring the powerful distributed data processing capabilities, similar to those of Google, to any cluster of computers. By using this framework, you can process vast amounts of data using the MapReduce paradigm with ease and reliability. It includes MapReduce program execution, basic distributed systems, fault tolerance, OS-provided concurrency facilities (threads and processes), and networking (sockets). This was inspired by [Google’s original MapReduce paper](https://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf), and all of this is built in Python!!

This project consists of two major pieces of code. A manager that listens for user-submitted MapReduce jobs and distributes the work among Workers. Multiple Worker instances receive instructions from the Manager and execute map and reduce tasks that combine to form a MapReduce program. Here is a basic rundown of what my program looks like: 
![flowchart excalidraw](https://github.com/ashrithb/Mapreduce_Framework/assets/92128095/67808b2f-53d0-415b-bb66-3dac353b6dc6)



### Features

- **Distributed Processing**: Harness the power of multiple computers to process data concurrently.
- **Fault Tolerance**: The framework ensures that tasks are recovered and re-executed in case of failures.
- **Networking**: Seamless communication between the Manager and Worker nodes through efficient socket implementation and TCP/UDP.
- **Concurrency**: Utilizes the OS-provided facilities (threads and processes) to achieve high-level concurrency and parallelism.

## Architecture

- **Manager**: The central node listens for user-submitted MapReduce jobs and efficiently distributes the work among Workers.
- **Worker Instances**: Multiple worker nodes receive instructions from the Manager and execute the map and reduce tasks that form a MapReduce program.

## Manager and Worker

These components play a crucial role in the functioning and orchestration of the MapReduce jobs.

### Manager Overview

The Manager module handles job submissions and coordination between Workers.

**Command-line options**:
- `host`: Host address to listen for messages.
- `port`: TCP port for messages and UDP port for heartbeats. (Note: TCP and UDP sockets are independent, hence we can use the same port number.)
- `logfile`: File path where logs are written. If not provided, stderr is used.
- `loglevel`: Severity level threshold for writing logs.
- `shared_dir`: Directory for a shared temporary space. If not provided, a directory chosen by the standard library is used.

**Startup Sequence**:
1. Spawn a new thread to listen for UDP heartbeat messages from Workers.
2. Initiate additional threads or setups as necessary. Consider another thread for fault tolerance.
3. Open a new TCP socket on the provided port and initiate listening.
4. Continuously listen for incoming messages, discarding invalid ones, especially those that fail JSON decoding. For instance:
5. The Manager constructor should not return until all its threads have concluded.

### Worker Overview

The Worker module is responsible for the actual data processing as instructed by the Manager.

**Command-line options**:
- `host`: Host address for message listening.
- `port`: TCP port for message listening.
- `manager-host`: Address for sending messages to the Manager.
- `manager-port`: TCP and UDP ports for Manager communication.
- `logfile`: File for logs. Defaults to `stderr` if not provided.
- `loglevel`: Determines the threshold for log severity levels.

**Initialization Sequence**:
1. Initiate a TCP socket on the designated port and commence listening. Ensure invalid messages, especially those failing JSON decoding, are discarded.
2. Dispatch a `register` message to the Manager. Ensure the Worker is listening before transmitting this message.
3. After receiving the `register_ack` message from the Manager, initiate a new thread for the sole purpose of sending heartbeat messages to the Manager.


## Usage

```bash
# Start the Manager node
python manager.py start

# Submit a MapReduce job (example)
python submit_job.py --input data.txt --map mapper.py --reduce reducer.py
```


## Learning Goals Achieved

- **MapReduce Execution**: Gained deep insights into the inner workings of the MapReduce paradigm and its execution.
- **Distributed Systems**: Developed understanding and practical experience with basic distributed systems.
- **Fault Tolerance**: Implemented mechanisms to handle node failures gracefully with Worker's heartbeat thread to send updates to the Manager via UDP. This allows the manager to maximize concurrency, but avoid duplication!
- **Concurrency**: Leveraged OS facilities for managing threads and processes.
- **Networking**: Implemented socket programming to ensure seamless communication between different components of the framework.

## Future Improvements

- Implement data shuffling and sorting between the map and reduce stages.
- Enhance fault-tolerance mechanisms to handle large-scale cluster failures.
- Introduce a user-friendly GUI for monitoring job progress and node status.

## Acknowledgements

Inspired by Google's original MapReduce paper. The project served as an excellent opportunity to delve deep into distributed systems and large-scale data processing.
