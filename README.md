# Hello World — Jenkins GCC Pipeline

A minimal C project used as a playground to validate the Jenkins CI/CD pipeline with the GCC agent.

## What it does
The pipeline runs on the `gcc` agent and executes four stages:
1. **Checkout** — pulls the code from GitHub
2. **Build** — compiles `hello.c` with GCC (`-Wall -O2`)
3. **Test** — runs the compiled binary
4. **Archive** — stores the `hello` binary as a build artifact

## Requirements
- A running Jenkins instance with the `gcc` labeled agent (see [jenkins-casc](https://github.com/marcocastellari/jenkins-casc.git))

## Run locally
```bash
gcc -Wall -O2 -o hello gcc/hello.c
./hello
```