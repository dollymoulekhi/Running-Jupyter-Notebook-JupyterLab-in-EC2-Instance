# Running-Jupyter-Notebook-JupyterLab-in-EC2-Instance


## Setting Jupyter Notebook and Jupyter Lab in EC2 instance:

### Jupyter Notebook setup:
### Connecting to a EC2 instance:

`ssh -i "location\key.cer" ubuntu@IPaddress`

### Assigning a port to jupyter notebook:

`nohup jupyter notebook --no-browser --port=8888 &`
`nohup.out`

### Create SSH Tunnel Connection:

`ssh -NL 8833:localhost:8888 -i "location\key.cer" ubuntu@IPaddress`

## Jupyter Lab setup:

### Connect using ssh:

`ssh -i "location\key.cer" ubuntu@IPaddress`

### Download Anaconda to instance:

`https://repo.continuum.io/archive/Anaconda3-4.2.0-Linux-x86_64.sh`

### Installing required packages:

```pip install pandas scikit-learn numpy```
```pip install jupyterlab```

### Setting password for Jupyter-lab:

`jupyter-lab password`
`pwd`

### Making a directory ssl:
```mkdir ssl

cd ssl

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mykey.key -out mycert.pem


jupyter-lab --port=8890 --certfile=~/ssl/mycert.pem --keyfile=~/ssl/mykey.key
```

### Tunneling local to VM:
`nohup jupyter-lab --port=8890 --browser="no-browser %s" --certfile=~/ssl/mycert.pem --keyfile=~/ssl/mykey.key &`



 
## Connecting Azure to CMD:

### Getting error: Permission 0644 for keys are too open:

```
chmod 400 "key.pem"
ssh -i "key.pem" machineID

```


## How to download a folder from virtual machine

```
scp -i "key.pem" -r user_name@ip:/location_from_where_you_want_to_download/ /destination_location
```



