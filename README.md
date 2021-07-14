# WARNING: Telepresence examples is no longer actively maintained by VMware.

VMware has made the difficult decision to stop driving this project and therefore we will no longer actively respond to issues or pull requests. If you would like to take over maintaining this project independently from VMware, please let us know so we can add a link to your forked project here.

Thank You.


# Telepresence examples

This repository houses an example [Deployment](telepresence-test.yaml) to demo
[Telepresence](https://telepresence.io).

The Deployment uses an init-container to write data to an emptyDir volume, that
is then read out by the container in the Pod. In the demo, you can use
Telepresence to live-debug this Deployment:

```
$ telepresence --swap-deployment telepresence-test
# in telepresence shell:
$ ls # show that we're in the same directory on the local machine
$ cat $TELEPRESENCE_ROOT/data/random
$ env | grep SUPER_SECRET
```

The demo shows that Telepresence gives you access to the Pod's environment
variables and volumes, and allows you to leverage Kubernetes-specific features
such as init-containers.

Kubernetes Service Discovery is available to talk to other services running in
the cluster from the local machine. For example, we can query the [qotm
service](qotm.sh):

```
$ curl qotm:5000
```

## License

Copyright (c) 2018 Bitnami

Licensed under the Apache License, Version 2.0 (the "License"); you may not use
this file except in compliance with the License. You may obtain a copy of the
License at

http://www.apache.org/licenses/LICENSE-2.0 Unless required by applicable law or
agreed to in writing, software distributed under the License is distributed on
an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express
or implied. See the License for the specific language governing permissions and
limitations under the License.
