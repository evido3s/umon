# umon

## Pre-requisites
* Install gnuplot on the server running umon
```bash
# Ubuntu
> sudo apt-get install gnuplot

# Fedora/CentOS/RedHat
> sudo yum install gnuplot
```

* Install dstat on the servers to monitor
```bash
# Ubuntu
> sudo apt-get install dstat

# Fedora/CentOS/RedHat
> yum install dstat
```

* Setup SSH keys to connect to all the servers without password

## Configuration file
```bash
{
    "servers":[
        {
            "hostname": string,
            "devices": [string],
            "interfaces": [string]
        }
    ]
}
```

### hostname
Type: String
Hostname of a server to monitor
### devices
Type: Array of strings

List of devices to monitor, e.g "sda", "sdb", "nvme0n1"
### interfaces
Type: Array of strings

List of interfaces to monitor, e.g. "eth0", "eth1"

## Run 
```bash
> python umon.py -r 5 -s 1 -t 10 -c sample_conf

> python umon.py --help
Usage: umon.py [options] arg

Options:
  -h, --help            show this help message and exit
  -r TIME, --runtime=TIME
                        Monitoring time (in seconds)
  -c CONF, --conf=CONF  Path to a configuration file
  -s SAMPLING, --sampling=SAMPLING
                        Sampling time (time between two dots, in seconds)
  -t TIMEOUT, --timeout=TIMEOUT
                        SSH connection timeout (in seconds)
  -d, --debug           Enable debug logs
```

## Output
![alt text](https://github.com/nmotte/umon/blob/master/screenshot/example.png)
