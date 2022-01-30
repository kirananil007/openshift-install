### Install a customized OpenShift cluster on AWS 

##### 1. Generate a key pair for cluster node SSH access

```
$ ssh-keygen
```



##### 2. Add key to ssh-agent		

```
$ eval "$(ssh-agent -s)"
```



##### 3. Add ssh private key to ssh-agent;

```
$ ssh-add <path>/<file_name> 
```



##### 4. Download the installation program and command line interface (OC) from [here](https://console.redhat.com/openshift/install/aws/installer-provisioned).

```
$ mkdir ocp

$ cd ocp

$ tar zxvf openshift-install-linux.tar.gz -C /usr/bin

$ tar zxvf openshift-client-install-linux.tar.gz -C /usr/bin
```



##### 5. Download the [awscli](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) and configure [aws credentials](https://docs.aws.amazon.com/cli/latest/reference/configure/)

​		Note: OCP requires administrator privileges for cluster install which can be revoked after successful installation.



##### 6. Create the install-config.yaml file for custom installation. 	

```
$ mkdir ~/ocp-install

$ vi install-config.yaml
```

  * Make necessary modifications to the file such as domain name, cluster name, region, ssh public key and pull secret.

  * Create a copy of the **install-config.yaml** for future use.

    

##### 7. Run the install

```
$ cd ocp

$ openshift-install create cluster --dir=../ocp-install --log-level=info 
```

 * Takes around 30 minutes to bring up a cluster

   

##### 8. Destroy cluster

```
$ openshift-install destroy cluster --dir=../ocp-install --log-level=info
```

