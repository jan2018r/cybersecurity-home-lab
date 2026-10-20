# Lab 04 — Linux Processes and System Monitoring

## Objective
Practice viewing Linux processes, monitoring resource usage, and safely stopping a background process that I created.

## Environment
- Ubuntu virtual machine
- Bash terminal
- Working directory: `~/cyber-labs/lab04-processes`

## Expectations vs Results
I expected this lab to be a little difficult because I had never worked with Linux processes before. During the lab, I used `ps`, `jobs`, and `top` to view processes. I also started background processes and successfully stopped my practice process.

## Steps and Results

### 1. Prepare the lab folder
```bash
mkdir -p ~/cyber-labs/lab04-processes
cd ~/cyber-labs/lab04-processes
pwd
whoami
```
I confirmed that I was in the lab folder and using my own account.

### 2. View terminal processes
```bash
ps
```
The output showed `bash` and `ps`. I learned that a PID is a process identification number.

### 3. Start a background process
```bash
sleep 120 &
ps
```
The `&` ran the waiting process in the background while I continued using the terminal. The process appeared in the `ps` output.

```bash
jobs
```
After the wait finished, Bash reported `Done`.

### 4. Monitor processes live
```bash
top
```
I viewed running processes and CPU and memory usage. I exited the live monitor with `q`.

### 5. Identify and stop my practice process
```bash
sleep 600 &
jobs -l
```
I confirmed that job 1 was my `sleep 600` process, with PID 3962.

```bash
kill %1
jobs -l
```
`kill %1` sent the default termination signal, SIGTERM, to job 1 in my current shell. Bash reported `Terminated`, and the final job check returned no jobs.

Job numbers and PIDs can change between sessions. I checked the target before stopping it.

## Challenges and Troubleshooting
I entered `jobs -1` using the number one instead of `jobs -l` using a lowercase L. Bash reported an invalid option. I corrected the character and successfully displayed the job and its PID.

I also entered `q` after I had already left `top`. Bash reported that the command was not found. I learned that `q` is a keyboard shortcut inside `top`, rather than a command to run at the Bash prompt.

## Personal Reflection
I enjoyed every part of this lab, including learning from my mistakes. It showed me how small typing errors can affect a command. Going forward, I want to slow down, proofread what I enter, and pay closer attention to similar-looking characters.

## Skills Practiced
- Viewing processes with `ps`
- Running a process in the background
- Checking shell jobs and process IDs
- Monitoring CPU and memory usage with `top`
- Identifying and terminating my own practice job
- Reading errors and correcting command syntax
