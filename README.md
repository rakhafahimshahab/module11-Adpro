## Reflection

### 1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
<img src = "images/image1.png">
When you access the application through the proxy into the Service, each access should generate a log entry if the application logs such requests. Therefore, you would expect to see the number of log entries increase with each request you make to the application. The logs might show incoming traffic, the source of the requests such as HTTP GET in the screenshot, and other details depending on how verbose the logging is configured in the application.

### 2. Notice that there are two versions of kubectl get invocation during this tutorial section. The first does not have any option, while the latter has -n option with value set to kube-system. What is the purpose of the -n option and why did the output not list the pods/services that you explicitly created?
The -n option with kubectl get command is used to specify the namespace in which to look for resources. Namespaces in Kubernetes are used to organize resources in a cluster and can be thought of as a virtual cluster within a cluster. They help different teams or projects to use the same cluster without interfering with each other, by isolating their resources.

Why the output did not list the pods/services that you explicitly created:

If the resources (pods, services, etc.) you created are in a different namespace than kube-system, they will not appear when you run kubectl get with -n kube-system. The default namespace for resources is default unless specified otherwise during their creation.
When you use kubectl get without specifying -n, it defaults to the default namespace, or the namespace set in your Kubernetes context. Thus, it only lists resources in that specific namespace.