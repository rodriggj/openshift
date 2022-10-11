# Openshift Management Options 

There are 3 types of management solutions built for Openshift management. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195142855-f673d062-7802-4685-a156-0d3fa3e9ad4a.png">
</p>

-------

## Web Console Option 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195143687-dcea847f-c16a-4c29-beed-ab9e19a0482e.png">
</p>

-------

## Command Line Interface (CLI) Option

### Options
> Realize there is not just one but many CLI tools available to support Openshift management. 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195149063-a179d219-6f3b-41ff-97ac-d13d99992d62.png">
</p>

For the purpose of our installation we will simply configure the `oc` CLI tooling. 

### Installation

1. The documentation for CLI documenation for your platform can be found [here](https://docs.openshift.com/container-platform/4.7/cli_reference/openshift_cli/getting-started-cli.html)

2. Download the binaries to your Desktop and unzip. 

3. Move the downloaded files to a location on your source PATH. 

```s
mv oc-4.11.7-macosx /usr/local/bin
```

4. Add the path to your local PATH variable 

```s
export PATH=$PATH:/usr/local/bin/oc-4.11.7-macosx
```

5. Validate that the pathname was entered to your PATH variable

```s
echo $PATH
# or simply run the oc command 
oc
```

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195148107-b7904d2f-d830-4b5d-80ea-b8261b2ad8e1.png">
</p>

### Use of CLI

> The documenation and available list of commands can be found [here](https://docs.openshift.com/container-platform/4.7/cli_reference/openshift_cli/getting-started-cli.html#cli-getting-started) or via the console by entering `oc --help`.

-------

## REST API

> The Openshift platform has a REST API that will allow an Admin or User to access information about the Openshift cluster via API endpoints. The documenation for this API can be found [here](https://docs.openshift.com/container-platform/4.7/rest_api/index.html)

1. If you start by attempting to curl the REST API 

```s
curl https://api.crc.testing:6443/oapi/v1/projects
```

You will get a certificate error... 

<p align="center">
<img width="694" alt="image" src="https://user-images.githubusercontent.com/8760590/195150839-4bf023b6-e7b1-40e8-8e96-efcf058207b7.png">
</p>


2. You can bypass this error by using the `-k` option.

```s
curl -k https://api.crc.testing:6443/oapi/v1/projects
```

But now you get another error ... 

<p align="center">
<img width="350" alt="image" src="https://user-images.githubusercontent.com/8760590/195151126-525fa92e-d5b3-408d-9cd9-d04192cb2731.png">
</p>


3. To bypass this error we need to pass a curl request with a `-H` header option and provide a `Bearer Token` in our Authorization request. But where does the token come from? 

```s
curl -k https://api.crc.testing:6443/oapi/v1/projects -H "Authorization: Bearer <token?"
```

4. To  get the token we need to utilize the `oc` CLI and provide the following command: 

```s
oc login -u developer -p developer    # to login to the OS cluster via CLI
whoami                                # to identify the user 
whoami -t                             # to receive the token
```

> You will receive an error indicating that the x509 certificate is not valide for CLI access.  You will have to create a Service Account and Namespace before adding/receiving a token. [here](https://access.redhat.com/solutions/2972601)

> I have not configured TLS Certificates for this demo envrionvment so REST API access is not available at the moment. 
---------

