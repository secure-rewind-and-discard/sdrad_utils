
## SDRaD Evaluations 

This repository contains useful scripts and commands for evaluating SDRaD


### Memcached 

To measure the restart time of a Dockerized Memcached, use the following commands:
##### Measuring Docker Restart Time

```bash 
docker run  -d --restart unless-stopped  -p 11211:11211 memcached

docker system events --filter 'event=start' --filter 'event=die' | cut -d : -f 3
```

##### Resident Set Size
To monitor the Resident Set Size (RSS) used by Memcached, execute:

`/usr/bin/time -v memcached ...`

`Maximum resident set size (kbytes)`


##### Reproducing CVE

* [CVE-2011-4971](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-4971) can be reproducible using [this script](./CVE-2011-4971.sh)


##### Memcached-User Interface with TELNET

This example demonstrates how to store and retrieve a simple value.

```plaintext
telnet 127.0.0.1 11211
set test 0 100 5
sdrob
get test
```

### NGINX

##### Reproducing CVE

* [CVE-2009-2629](https://cve.mitre.org/cgi-bin/cvename.cgi?name=cve-2009-2629)

    * PoC-implementation can be found [this script](./CVE-2009-2629.sh), originally sourced from [this external repository](https://github.com/badd1e/Disclosures/blob/master/CVE-2009-2629_nginx_http/testcase/testcase.sh)

* [CVE-2022-3786](https://nvd.nist.gov/vuln/detail/CVE-2022-3786) 

    * PoC-implementation can be found [here](./nginx_openssl/security-labs-pocs/proof-of-concept-exploits/openssl-punycode-vulnerability/malicious_client/)
    * generate the key and malicious cert `./client/gen.sh`
    * run the `./client/run_client.sh`






