# Getting Started with Openshift

## Architecture

<p align="center"> 
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194984201-c7158bf9-5b94-450c-855b-ec966214661e.png">
</p>

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194984455-56846284-4545-455b-83b1-b5fc0c3f051b.png">
</p>

--------

## Deployment Options

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194984585-e6d33dac-58f4-4918-8c9b-e79175e85146.png">
</p>

- [ ] [`CodeReady Containers`](https://github.com/rodriggj/openshift/tree/master/02_GettingStarted#demo-environment-with-codeready-containers)
- [ ] [`Minishift`](https://github.com/rodriggj/openshift/tree/master/02_GettingStarted#demo-environment-with-minishift) coupled with a Hypervisor

-------

## Demo Environment with `CodeReady Containers`

> Due to Openshift versions and open source packages for installation of Openshift, there are multiple ways to deploy a local test environment. The Minishift option is discussed below, but has several dependencies to 3rd party applications and container versions that make the installation and subsequent troubleshooting -- difficult. A more streamlined an error free installation procedure is to utilize `CodeReady Containers` which will be the focus of this procedure walkthrough. 

Steps: 
1. Navigate to the github repository for `minishift` [here](https://github.com/minishift/minishift)
2. Scroll down the readme file and you will see a link to `CRC` 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195121485-80ca2731-e949-4382-854d-03f462a765db.png">
</p>

3. When the page redirects you will find yourself in Redhat Hybrid Cloud Console. Here you will be required to do 2 things: 
- [ ] Download the binaries for your local OS 
- [ ] Download the Pull Secret that will be used to authenticate to the Openshift cluster

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195122523-7425eaf3-d1d1-46d1-838b-56b1b26becbc.png">
</p>

+ Start by downloading the binanries, and saving to your `Desktop`. Double click on the file and the installer will go through its install process. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195122928-efc8ced1-c7f7-4ff7-8cbc-50a63194d71d.png">
</p>

+ Run the following command: 

```s
crc setup
```

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195132271-eb1db4f8-f41f-44af-ad08-f98ec35b2391.png">
</p>

+ During the course of the `crc setup` process you will be prompted for an input of your _Pull Secret_.

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195132948-6494bf31-3e4e-4b94-830f-87bcd0efae38.png">
</p>

Which comes from the Redhat page 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195133376-14771c6d-824a-486b-a928-5cb43f2c5c79.png">
</p>

4. When this configuration is provided and the installation completes, you will need to run the following command

```s
crc start
```

5. You will be presented with credential information, and a URL to access the Openshift console. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195134351-0e53039f-4225-4233-b46f-01777133b4d8.png">
</p>

6. If the browser doesn't automatically populate you can simply navigate to a web browser and input the URL. Here you can enter the credentials and login to an Openshift instance. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195135085-a49623a5-5b06-4c2e-9ddd-701342e8a269.png">
</p>

> NOTE: If there is an error, resolve the error and repeat the `crc setup` and then `crc start` process. 

> Troubleshooting: There was only one instance of troubleshooting required which was a blocking port. The process to rectify this _"...port in use..."_ error was to kill the blocking process. A helpful article to debug this was found [here](https://stackoverflow.com/questions/11583562/how-to-kill-a-process-running-on-particular-port-in-linux). 

Here is a view of the error and the resolution in the terminal: 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195136390-85b549a6-569d-409d-b9b6-46466608f1fe.png">
</p>

7. Now that the setup is complete, there are several functions that Openshift can perform. The documenation can be found [here](https://access.redhat.com/documentation/en-us/red_hat_openshift_local/2.5/html/getting_started_guide/using_gsg) & [here](https://crc.dev/crc/). Additional walkthroughs will be provided in subsequent folders in the root directory. 

<sub><sub>[Back to the Top](https://github.com/rodriggj/openshift/tree/master/02_GettingStarted#deployment-options)</sub></sub>

------

## Demo Environment with `Minishift`

If you were to setup a production cluster there are several things that need to be configured to get Openshift up and running. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194984946-3419c896-3542-45f2-91d5-8c8f60ec1386.png">
</p>

For Demo purposes, Openshift packages all these components into a single `.iso` image and makes available as an executable that will run on a hypervisor, in this case we'll use Virtualbox. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194985211-5670d61f-93fd-4b59-8e87-3563480c3bd1.png">
</p>

> NOTE: A Containerized environment can also be deployed without Minishift as an An alternative method. The architecture would look something like this. This is not done for this demo environment. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194985340-b41cd986-c301-4299-b329-7b38f4e14a8b.png">
</p>

------

## Configure Minishift

Steps: 
1. Navigate to `Minishift` website [here](https://docs.okd.io/3.11/minishift/getting-started/installing.html)

2. Navigate to the `Getting Started with Minishift` documenation [here](https://docs.okd.io/3.11/minishift/getting-started/index.html). This documentation will outline the following highlevel activities. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194987721-b616eaee-923f-470a-92d2-f96728767df1.png">
</p>

3. Depending on your Operating System, you have a pre-requisite step to complete which is to ensure there is a hypervisor installed. For macOS, you will need to ensure `hyperkit` is installed. If you navigate to the `Setting Up Your Virtual Environment` documentation [here](https://docs.okd.io/3.11/minishift/getting-started/setting-up-virtualization-environment.html), and scroll down to the macOS section, you can see that **IF** you have `Docker Desktop` installed, you will have automatically installed the `hyperkit` hypervisor. If you have not downloaded `Docker Desktop` you can do so [here](https://www.docker.com/products/docker-desktop/). If you have downloaded `Docker Desktop` ensure that it is running. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194988123-53135426-58ce-4b61-a2ce-a2d8c9294e43.png">
</p>

4. Even if you have installed `Docker Desktop` you should still install the latest version of the `docker-machine-driver-hyperkit`. You may get an error that looks like the following if you try to use Homebrew to install the `hyperkit`. 

```s
$ brew install docker-machine-driver-hyperkit
```

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194989199-10c4e71d-f8f8-44ae-9f82-56cbe2050948.png">
</p>

If an error does render, then attempt to download the binaries directly to your `/usr/localbin` folder. 

```s
sudo curl -L  https://github.com/machine-drivers/docker-machine-driver-hyperkit/releases/download/v1.0.0/docker-machine-driver-hyperkit -o exp
```

The result should look like the following: 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194989444-93244b1d-3bfe-455e-b6f3-9cf6e56b782c.png">
</p>

You may still have an issue per this [ticket](https://github.com/kubernetes/minikube/issues/5231). Try running 

```s
brew install hyperkit
```

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194992220-5b491973-bf42-4682-a0d0-85bb2aa61d10.png">
</p>

5. Configure your `PATH` variable to point to these binaries and 

```s
export PATH=$PATH:/usr/local/bin/docker-machine-driver-hyperkit
sudo chown root:wheel /usr/local/bin/docker-machine-driver-hyperkit
sudo chmod u+s,+x /usr/local/bin/docker-machine-driver-hyperkit
```

6. Utilize Homebrew package manager for minishift installation

```s
brew install minishift
brew install --force minishift
```

Results in...

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194987040-e44b6cdd-b04b-4e95-91c2-7709a62bf448.png">
</p>

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194990700-c0f95d42-d39f-443e-94d4-7155f4650dbb.png">
</p>

7. Navigate to the `Minishift Quickstart` section of the documentation [here](https://docs.okd.io/3.11/minishift/getting-started/quickstart.html)

```s
minishift start
```

> NOTE: If you receive an error _"Minishift cannot be opened because ..."_ then follow this [link](https://github.com/minishift/minishift/issues/3500) whic effectively says to run the following command. 

```s
brew reinstall minishift --no-quarantine
```

Which results in ... 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194991296-7837e6af-f49c-405a-9d67-a68d5fe1519f.png">
</p>

If incurring an error see this [ticket](https://github.com/minishift/minishift/issues/3529), which suggest you elevate privledges and run `minishift setup`. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194992604-13b596b8-4535-45bd-81cc-e9147f495aaf.png">
</p>

Exit from `sudo` privledges and then retry `minishift start` command

```s
exit
minishift start
```

Results in 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/194992846-b62a5e64-48d6-4e03-81da-4a0652865005.png">
</p>

Stopped ... there were several errors with the versioning of the Minishift image, the `hyperkit` installation, & the credential availablity of the minishift image once running in Virtualbox. I ultimately deleted the box and simply used `CRC` process. 

<sub><sub>[Back to the Top](https://github.com/rodriggj/openshift/tree/master/02_GettingStarted#deployment-options)</sub></sub>

-------

