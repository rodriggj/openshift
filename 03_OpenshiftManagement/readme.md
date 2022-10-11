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

-------

## REST API
