## How to deploy a service on k8s?

After your finished part1 and part2, you have make a docker image and build a kubenate environment. Unlike other teams did, we accomplish this task on a server rather than local host.

A docker image is one which copies the code of a service, say, a backend program. A k8s environment is an isolated container which avoids the influence from outsied.

In this project, I applied **Rancher**, a manager of k8s, to better   organize and manage k8s.

Now I'll introduce how I use racher and k8s to deploy a service.

**Step1:**

Login Rancher.

**Step2:**

Click **add cluster** button on the homepage. 

Choose **custom** and press next.

After configuration, you'll get the result like below.

Here we have a cluster with 3 nodes.

<img src="https://github.com/GEORGE5961/markdown_photos/blob/master/rr0.png?raw=true" width="60%"/>

<img src="https://github.com/GEORGE5961/markdown_photos/blob/master/rr3.png?raw=true" width="60%"/>



**Step3**

Enter the following command in the terminal.

```
sudo docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run rancher/rancher-agent:v2.1.5 --server https://rancher.jsznb.com --token 4j4v5b28f85n7d9jfntpx2dh7fxmffd2sj4h8h7nqlc494t4t7xfsm --ca-checksum 5169b181d4426c22c7acce42e27471b4e8c5ac2affe741a121c43935cf66f42d --node-name node1 --address 59.110.154.114 --internal-address 192.168.5.146 --etcd --controlplane --worker
```

Here we deploy a backend service and a mongodb service.

As you can see in the following images, an nginx service and a mongodb service are deployed.

<img src="https://github.com/GEORGE5961/markdown_photos/blob/master/rr1.png?raw=true" width="60%"/>

<img src="https://github.com/GEORGE5961/markdown_photos/blob/master/rr2.png?raw=true" width="60%"/>

<img src="https://github.com/GEORGE5961/markdown_photos/blob/master/rr4.png?raw=true" width="60%"/>

Rancher is really handy and highly recommended.