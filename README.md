# Run CoreDns file plugin as user application in Kubernetes

The coredns file plugin run DNS service from a preloaded file.
Using the following yaml file, you can run a coredns DNS server as Kubernetes service.

How to run the DNS server ?

Download this yaml file
Edit the configmap with your DNS entries
Run:  kubectl apply -f <yaml file>

How to verify that server is responding?

First, retrieve the service's IP (or the Pod's IP) and the run:

$ dig -t srv moshe.example.org @10.0.0.80

; <<>> DiG 9.9.4-RedHat-9.9.4-72.el7 <<>> -t srv moshe.example.org @10.0.0.80
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5124
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;moshe.example.org. IN SRV

;; ANSWER SECTION:
moshe.example.org. 0 IN SRV 8080 10 10 example.org.

;; ADDITIONAL SECTION:
example.org. 0 IN A 192.168.11.11

;; Query time: 1 msec

;; SERVER: 10.0.0.77#53(10.0.0.77)

;; WHEN: Wed Dec 19 19:19:17 UTC 2018

;; MSG SIZE rcvd: 110

$
#
