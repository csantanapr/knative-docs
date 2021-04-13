Remember those super powers :rocket: we talked about? One of Knative Serving's powers is autoscaling. This means your Knative Service will only "spin up" to preform its job (in this case, saying "Hello world!") if it is needed, otherwise, it will spin down and wait for a new request to come in.

**Let's see this in action!** We're going to peek under the hood at the <a href= "https://kubernetes.io/docs/concepts/workloads/pods/" target="blank_">Pods</a> in Kubernetes where our Knative Service is running to watch our "Hello world!" Service scale up and down.


#### Check the Knative Pods
Let's run our "Hello world!" Service just one more time. This time, try the Knative Service `URL` in your browser or by using `open` instead of `curl` in your CLI.
```bash
open <service-url>
```
Where `<service-url>` is the URL where your Knative Service was deployed (same as the `<service-url>` in the last step).

You can watch the pods and see how they scale down to zero after http traffic stops to the url
```bash
kubectl get pod -l serving.knative.dev/service=hello -w
```

The output should look like this:
```bash
NAME                                     READY   STATUS
hello-xxxxx-1                           2/2     Running
hello-xxxxx-1                           2/2     Terminating
hello-xxxxx-1                           1/2     Terminating
hello-xxxxx-1                           0/2     Terminating
```

Try to access the url again, and you will see a new pod running again.
```bash
NAME                                     READY   STATUS
hello-xxxxx-1                           0/2     Pending
hello-xxxxx-1                           0/2     ContainerCreating
hello-xxxxx-1                           1/2     Running
hello-xxxxx-1                           2/2     Running
```

Some people call this **Serverless** 🎉 🌮 🔥