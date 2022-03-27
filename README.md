# Learning Kubernetes Log

Random notes while learning Kubernetes.

TODO: make my Anki Flashcard desk available for everyone.

TODO: my questions in #kubernetes-users

# March 2022


kubernetes.io is great. There are several small tasks which explain how to configure a cluster:

https://kubernetes.io/docs/tasks/administer-cluster/


---

You want to learn Kubernetes? 

You can read the Kubernetes docs from top to buttom. But you should not follow the confusing links in the text. On the left side of [kubernetes.io](https://kubernetes.io/docs/home/) is a nice table of content. Follow this from top to bottom, and you need no additional book or course. Don't follow the "What's next" at the bottom of the page.

And the slack channel #kubernetes-users is very helpful. 

---

[What Kubernetes is not](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/#what-kubernetes-is-not)

---

There are several ways for the inner development loop, if you want to develop an application
on kubernetes:

* https://skaffold.dev/
* https://tilt.dev/
* https://www.telepresence.io/

# February 2022


I use kind (kubernetes in docker) to play around with Kubernetes on my desktop.

I create the cluster like this
```
kind create cluster --image kindest/node:v1.23.3 --config multi-node-config-kind.yaml 
```

With this config:
```
# multi-node-config-kind.yaml 
# three node (two workers) cluster config
# https://kind.sigs.k8s.io/docs/user/quick-start/#multinode-clusters
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
```

Working with `kubectl` works, but connecting to the nodes in the Kubernetes cluster does not work.

The simples solution to connect to nodes in my kind cluster is via the docker container which is called `kind-control-plane`.

You can access this node via:

```
me@pc> docker container exec -it kind-control-plane bash 
```

Then you can execute commands:

```
root@kind-control-plane:/# kubectl get nodes -o=wide
NAME                 STATUS   ROLES                  AGE   VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE       KERNEL-VERSION      CONTAINER-RUNTIME
kind-control-plane   Ready    control-plane,master   22h   v1.23.3   172.18.0.3    <none>        Ubuntu 21.10   5.13.0-28-generic   containerd://1.5.9
kind-worker          Ready    <none>                 22h   v1.23.3   172.18.0.2    <none>        Ubuntu 21.10   5.13.0-28-generic   containerd://1.5.9
kind-worker2         Ready    <none>                 22h   v1.23.3   172.18.0.4    <none>        Ubuntu 21.10   5.13.0-28-generic   containerd://1.5.9
```

`kubectl` works directly from your PC, too. But from inside the cluster you can access the nodes of the cluster, which you can't from your PC. At least I found no way to do it. Please tell me if you found a way.

You need to install some packages:

```
apt update
apt install iputils-ping dnsutils vim bash-completion less wget
```

And then bash-completion: https://kubernetes.io/docs/tasks/tools/included/optional-kubectl-configs-bash-linux/

---

off-topic: As a developer, how can I define a dependency between my app and a service which
my app needs? AFAIK there is no solution yet.

Defining dependencies between an app and a library is easy. But between services .... I have no clue (although this
is a very basic question)

---

You want to use a managed kubernetes, but you are unsure which provider to choose? Kubernetes is an open source project.
I think it makes sense to choose a provider who contributes much to it.

Here is a chart of contributions per company: https://k8s.devstats.cncf.io/d/9/companies-table?orgId=1

Conclusion: I think I will use Google (GKE) or Azure (AKE). Not AWS.


---

The #kubernetes-users Slack channel is great. You get profound answers during several minutes (not always, but often).
From time to time I try to answer questions, too. Although I don't know much yet, sometimes I can help.

---

Wow, three great books about SRE are available for free: https://sre.google/books/ (I read the first one in 2018)

---


I see experienced people struggling with Kubernetes. They have 20 years experience in IT. This means they
were able to do their IT work 20 years without kubernetes. They are experts, but they struggle to 
except/adapt/enbrace Kubernetes.

Young people are more open to now things. This is normal for mammals.

---


Some years ago, while fighting with config-management with SaltStack I had a "vision": Config-management
with SaltStack, Ansible ... is nice, but it would be much better if you had a relational database schema, and
instead of writing YAML files, you could use SQL (or a web-GUI) to define your desired state. I am happy that
I never started to implement this "vision". Because Kubernetes is this vision. Except that it is not SQL, but nevertheless
Kubernetes provides this well defined schema. I like it.

---

---

vscode has Kubernetes YAML support. Even with auto-complete. Nice.

---

Which network plugin to use? I think Cilicum is the best solution. It will be used in GKE.

Ansible/Terraform usualy run once. The operator pattern of K8s is better: it brings
the current state into the desired state over and over again.

[Parca](//parca.dev) looks cool: sampling profiling of a whole cluster without modifying the code!

Startup dependencies between containers is not solved yet: https://github.com/kubernetes/kubernetes/issues/65502 (this is the issue with 2nd most number of up-votes of all)


What are the do's and don'ts of cloud-native applications? I think an application should not need a block device. This means you don't need things like Ceph or Longhorn. And I think an app should not need any persistent volumne. Write the data to a s3 like object store (like minio).

This means PersistentVolumne and PVC exist, but this is not needed if you write cloud-native applications.



# January 2022

[Stackoverflow: kube-apiserver: constantly 5 to 10% CPU: Although there is no single request](https://stackoverflow.com/questions/70592752/kube-apiserver-constantly-5-to-10-cpu-although-there-is-no-single-request)

How to enable the audit log?

Are your allowed to use https://github.com/ahmetb/kubectl-aliases during the exam?

bash completion works very cool: https://kubernetes.io/docs/reference/kubectl/cheatsheet/

jsonpath: https://kubernetes.io/docs/reference/kubectl/jsonpath/ nice

[kustomize](https://kubectl.docs.kubernetes.io/guides/introduction/kustomize/) nice: template-free. Instead: overlays.

More than 20 years ago someone complained about Linux. He argued that MS-Windows has
a central registry. The registry was like a central config database. But on Linux
every server had its own config. And most config files had a different syntax. I agreed (althoug I prefered Linux),
that a central registry would be nice. Now I see Kubernetes, and here it is. The central
registry database of your data center. K8s has well defined, self documenting configuration. Nice.

I like this audiobook:
> The Kubernetes Book
> Author: Nigel Poulton
https://www.audible.de/pd/The-Kubernetes-Book-Hoerbuch/B07Q4FPNX7

Great video of Zalando (Henning Jacobs) "how to crash your cluster"
https://youtu.be/6sDTB4eV4F8

---

Why tool for playing around? minikube, kind, ... I will use "kind".

---

minikube start --driver=docker

---

Kubernetes Fundamentals (LFS258). This course of the Linux-Foundation looks outdated. The instructions
are in a PDF which you see inside the html page. This gives you two scroll-bars. If I try to scroll, then the scroll-event usually gets
to the wrong scroll-bar. The text is talks about Ubuntu 18.04. I think the next time I will use a
different organization for the course.

[KodeKloud](<a href="https://kodekloud.com/) looks better. If you book for one year, then you can do CKA and additional other courses. 


---

From time to time I look at https://stackoverflow.com/questions/tagged/kubernetes?tab=Newest and see if I can already
answer some question. Although K8s is still very new to me, I can already answer some questions.

---

json-path vs go-template. Both are new to me. Which one to learn?


Which tool for logging? Current choice: fluent-bit (smaller memory footprint)

http://sotagtrends.com/?tags=fluentd+logstash+filebeat+promtail+fluent-bit

---

The text of the "Kubernetes Fundamentals (LFS258)" course of the Linux-Foundation is outdated.
I go through it page by page and for every new term I check the official docs at kubernetes.io.
Then I usually create a card in Anki for this term.

---

The Slack Channel [#cka-exam-prep](https://kubernetes.slack.com/archives/CA0HH2XTJ) is a great ressource. Searching in the channel helps to
find solutions to common issues while learning. You have no access to the channel during the exam.

---



