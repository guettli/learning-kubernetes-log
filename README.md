# Learning Kubernetes Log

Random notes while learning Kubernetes.

TODO: make my Anki Flashcard desk available for everyone.

TODO: my questions in #kubernetes-users

# February 2022

Which network plugin to use? I think Cilicum is the best solution. It will be used in GKE.

Ansible/Terraform usualy run once. The operator pattern of K8s is better: it brings
the current state into the desired state over and over again.

[Parca](//parca.dev) looks cool: sampling profiling of a whole cluster without modifying the code!

Startup dependencies between containers is not solved yet: https://github.com/kubernetes/kubernetes/issues/65502 (this is the issue with 2nd most number of up-votes of all)


What are the do's and don'ts of cloud-native applications? I think an application should not need a block device. This means you don't need things like Ceph or Longhorn. And I have think an app should not need any persistent volumne. Write the data to a s3 like object store (like minio).

This means PersistentVolumne and PVC exist, but this is not needed if you write cloud-native applications.

---

vscode has Kubernetes YAML support. Even with auto-complete. Nice.

---

Some years ago, while fighting with config-management with SaltStack I had a "vision": Config-management
with SaltStack, Ansible ... is nice, but it would be much better if you had a relational database schema, and
instead of writing YAML files, you could use SQL (or a web-GUI) to define your desired state. I am happy that
I never started to implement this "vision". Because Kubernetes is this vision. Except that it is not SQL, but nevertheless
Kubernetes provides this well defined schema. I like it.

---

I see experienced people struggling with Kubernetes. They have 20 years experience in IT. This means they
were able to do their IT work 20 years without kubernetes. They are experts, but they struggle to 
except/adapt/enbrace Kubernetes.

Young people are more open to now things. This is normal for mammals.

---

Wow, three great books about SRE are available for free: https://sre.google/books/ (I read the first one in 2018)

---

The #kubernetes-users Slack channel is great. You get profound answers during several minutes (not always, but often).
From time to time I try to answer questions, too. Although I don't know much yet, sometimes I can help.

---

You want to use a managed kubernetes, but you are unsure which provider to choose? Kubernetes is an open source project.
I think it makes sense to choose a provider who contributes much to it.

Here is a chart of contributions per company: https://k8s.devstats.cncf.io/d/9/companies-table?orgId=1

Conclusion: I think I will use Google (GKE) or Azure (AKE). Not AWS.




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



