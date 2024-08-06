# Debug Container

This repository provides a debug container that can be attached to your pods for debugging purposes. If your primary container lacks certain debug binaries, you can use this container to access the necessary tools.

## Why Not Include Debugging Tools in Your Application Image?

Including debugging tools directly in your application image can lead to several issues:

1. **Increased Image Size**: Adding debugging tools significantly increases the size of the image, which can slow down deployment times and increase the storage requirements.

2. **Security Vulnerabilities**: Debugging tools may introduce additional security vulnerabilities. Each tool is another piece of software that could potentially be exploited.

3. **Exposure to Exploits**: The presence of debugging tools in a production environment can provide attackers with more options for exploitation if they gain access to your container.

4. **Performance Overhead**: Debugging tools can add unnecessary overhead to your running containers, potentially impacting performance.

5. **Best Practices**: It's a best practice to keep production images lean and only include what's necessary to run the application. Debugging tools should be kept separate to maintain a clean and secure environment.

Using a separate debug container, as provided by this repository, mitigates these risks while still allowing you to troubleshoot and diagnose issues effectively.


## Usage

You can attach this container as a [debug](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/) container to your pods using the following command:

```sh
kubectl debug -it ${pod_name} --image=ghcr.io/opentelekomcloud-community/debug-container:main -n ${namespace} 
```

## Features

- Contains a comprehensive set of debugging tools. EG: `tcpdump`, `bind-tools`, `curl`, `netcat`, `strace` just to name a few.
- Can be easily attached to any running pod.
- Helps in diagnosing issues without modifying the primary container image.

## Additional Resources

- [Kubernetes Debugging Documentation](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/)

Feel free to contribute or raise issues if you encounter any problems.

