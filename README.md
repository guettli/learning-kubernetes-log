# Learning Kubernetes Log

Random notes while learning Kubernetes.

TODO: make my Anki Flashcard desk available for everyone.

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

Which tool for logging? Current choice: fluent-bit (smaller memory footprint)

http://sotagtrends.com/?tags=fluentd+logstash+filebeat+promtail+fluent-bit

---

