```
$ docker run hello-world
```

```
$ docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
29202e855b20: Pull complete 
Digest: sha256:e6173d4dc55e76b87c4af8db8821b1feae4146dd47341e4d431118c7dd060a74
Status: Downloaded newer image for ubuntu:latest

root@38974ab2b70b:/# ls  
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

root@38974ab2b70b:/# rm -rf /
rm: it is dangerous to operate recursively on '/'
rm: use --no-preserve-root to override this failsafe

root@38974ab2b70b:/# rm -rf / --no-preserve-root
.
.
.

root@38974ab2b70b:/# ls
bash: ls: command not found

root@38974ab2b70b:/# exit
exit

$ docker run -it ubuntu bash

root@5563522cadb9:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
```

```
$ docker run -it python:3.9
Unable to find image 'python:3.9' locally
3.9: Pulling from library/python
1b13d4e1a46e: Pull complete 
1c74526957fc: Pull complete 
30d855997954: Pull complete 
ad5739181616: Pull complete 
75e2b45cbee5: Pull complete 
2085960a02e9: Pull complete 
5e8caa1d5d83: Pull complete 
0cd6f205cb3b: Pull complete 
Digest: sha256:3d9dbe78e1f45ed2eb525b462cdb02247cc0956713325aeeffa37cb5f2c8c42e
Status: Downloaded newer image for python:3.9
Python 3.9.18 (main, Jan 17 2024, 07:02:31) 
[GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print('hello world')
hello world
>>> import pandas
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'pandas'
```

```
$ docker run -it --entrypoint=bash python:3.9
root@a93818531d45:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@a93818531d45:/# pip install pandas
Collecting pandas
  Downloading pandas-2.2.0-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (13.0 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 13.0/13.0 MB 5.6 MB/s eta 0:00:00
Collecting python-dateutil>=2.8.2
  Downloading python_dateutil-2.8.2-py2.py3-none-any.whl (247 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 247.7/247.7 kB 3.0 MB/s eta 0:00:00
Collecting pytz>=2020.1
  Downloading pytz-2023.3.post1-py2.py3-none-any.whl (502 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 502.5/502.5 kB 4.2 MB/s eta 0:00:00
Collecting tzdata>=2022.7
  Downloading tzdata-2023.4-py2.py3-none-any.whl (346 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 346.6/346.6 kB 3.4 MB/s eta 0:00:00
Collecting numpy<2,>=1.22.4
  Downloading numpy-1.26.3-cp39-cp39-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (18.2 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 18.2/18.2 MB 2.0 MB/s eta 0:00:00
Collecting six>=1.5
  Downloading six-1.16.0-py2.py3-none-any.whl (11 kB)
Installing collected packages: pytz, tzdata, six, numpy, python-dateutil, pandas
Successfully installed numpy-1.26.3 pandas-2.2.0 python-dateutil-2.8.2 pytz-2023.3.post1 six-1.16.0 tzdata-2023.4
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv

[notice] A new release of pip is available: 23.0.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip

root@a93818531d45:/# python
Python 3.9.18 (main, Jan 17 2024, 07:02:31) 
[GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pandas
<stdin>:1: DeprecationWarning: 
Pyarrow will become a required dependency of pandas in the next major release of pandas (pandas 3.0),
(to allow more performant data types, such as the Arrow string type, and better interoperability with other libraries)
but was not found to be installed on your system.
If this would cause problems for you,
please provide us feedback at https://github.com/pandas-dev/pandas/issues/54466
        
>>> pandas.__version__
'2.2.0'
```

```
$ docker run -it --entrypoint=bash python:3.9
root@c9d014c14da9:/# python
Python 3.9.18 (main, Jan 17 2024, 07:02:31) 
[GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pandas
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'pandas'
```

Despues de generar el Dockerfile con python 3.9 y dentro de la carpeta
```
~/dtc-dez/01-docker-terraform/docker_sql$ docker build -t test:pandas .
[+] Building 29.7s (6/6) FINISHED                                                                     docker:default
 => [internal] load .dockerignore                                                                               0.3s
 => => transferring context: 2B                                                                                 0.0s
 => [internal] load build definition from Dockerfile                                                            0.2s
 => => transferring dockerfile: 97B                                                                             0.0s
 => [internal] load metadata for docker.io/library/python:3.9                                                   0.0s
 => [1/2] FROM docker.io/library/python:3.9                                                                     0.3s
 => [2/2] RUN pip install pandas                                                                               25.8s
 => exporting to image                                                                                          2.9s 
 => => exporting layers                                                                                         2.9s 
 => => writing image sha256:d0d0ada8980a97f3df980ebb560e243d624631882a02bca016d104300837ea32                    0.0s 
 => => naming to docker.io/library/test:pandas                                                                  0.0s 
                                                                                                                     
What's Next?                                                                                                         
  View a summary of image vulnerabilities and recommendations → docker scout quickview
```

Despues de generar el Dockerfile con python 3.9.1 y dentro de la carpeta
```
~/dtc-dez/01-docker-terraform/docker_sql$ docker build -t test:pandas .
[+] Building 136.5s (7/7) FINISHED                                                                    docker:default
 => [internal] load .dockerignore                                                                               0.2s
 => => transferring context: 2B                                                                                 0.0s
 => [internal] load build definition from Dockerfile                                                            0.3s
 => => transferring dockerfile: 99B                                                                             0.0s
 => [internal] load metadata for docker.io/library/python:3.9.1                                                 3.8s
 => [auth] library/python:pull token for registry-1.docker.io                                                   0.0s
 => [1/2] FROM docker.io/library/python:3.9.1@sha256:ca8bd3c91af8b12c2d042ade99f7c8f578a9f80a0dbbd12ed261eeba  91.0s
 => => resolve docker.io/library/python:3.9.1@sha256:ca8bd3c91af8b12c2d042ade99f7c8f578a9f80a0dbbd12ed261eeba9  0.3s
 => => sha256:ca8bd3c91af8b12c2d042ade99f7c8f578a9f80a0dbbd12ed261eeba96dd632f 2.36kB / 2.36kB                  0.0s
 => => sha256:2a7e1b9e632b7a3a967dbddbf8c80fff234f10f9cb647b253c6405252db41c9c 2.22kB / 2.22kB                  0.0s
 => => sha256:2a93c239d591553ed9c25ef20ed7c7a1542e8644f57d352e3a1446f0a5f0412d 8.33kB / 8.33kB                  0.0s
 => => sha256:7467d1831b6947c294d92ee957902c3cd448b17c5ac2103ca5e79d15afb317c3 7.83MB / 7.83MB                  5.8s
 => => sha256:feab2c490a3cea21cc051ff29c33cc9857418edfa1be9966124b18abe1d5ae16 10.00MB / 10.00MB                6.9s
 => => sha256:0ecb575e629cd60aa802266a3bc6847dcf4073aa2a6d7d43f717dd61e7b90e0b 50.40MB / 50.40MB               26.8s
 => => sha256:f15a0f46f8c38f4ca7daecf160ba9cdb3ddeafda769e2741e179851cfaa14eec 51.83MB / 51.83MB               28.4s
 => => sha256:937782447ff61abe49fd83ca9e3bdea338c1ae1d53278b2f31eca18ab4366a1e 192.33MB / 192.33MB             62.3s
 => => extracting sha256:0ecb575e629cd60aa802266a3bc6847dcf4073aa2a6d7d43f717dd61e7b90e0b                      11.4s
 => => sha256:e78b7aaaab2cfb7598d50ad36633611a75bff6116d6a0acc2d37df61b5c797be 6.15MB / 6.15MB                 29.4s
 => => sha256:06c4d8634a1a306e07412154f682d30988cee9a788c10563e0143279d23fa69b 19.12MB / 19.12MB               37.2s
 => => sha256:42b6aa65d161c7afc7d1b5741224751f55ea238144036e416037b02e22d73dff 231B / 231B                     30.1s
 => => sha256:f7fc0748308d6904bfdd5e91721ba058abdd1a415247a65089b44392f4be9fc9 2.16MB / 2.16MB                 32.7s
 => => extracting sha256:7467d1831b6947c294d92ee957902c3cd448b17c5ac2103ca5e79d15afb317c3                       1.3s
 => => extracting sha256:feab2c490a3cea21cc051ff29c33cc9857418edfa1be9966124b18abe1d5ae16                       1.0s
 => => extracting sha256:f15a0f46f8c38f4ca7daecf160ba9cdb3ddeafda769e2741e179851cfaa14eec                      11.0s
 => => extracting sha256:937782447ff61abe49fd83ca9e3bdea338c1ae1d53278b2f31eca18ab4366a1e                      21.4s
 => => extracting sha256:e78b7aaaab2cfb7598d50ad36633611a75bff6116d6a0acc2d37df61b5c797be                       1.0s
 => => extracting sha256:06c4d8634a1a306e07412154f682d30988cee9a788c10563e0143279d23fa69b                       2.2s
 => => extracting sha256:42b6aa65d161c7afc7d1b5741224751f55ea238144036e416037b02e22d73dff                       0.0s
 => => extracting sha256:f7fc0748308d6904bfdd5e91721ba058abdd1a415247a65089b44392f4be9fc9                       0.8s
 => [2/2] RUN pip install pandas                                                                               36.3s
 => exporting to image                                                                                          4.8s
 => => exporting layers                                                                                         4.7s
 => => writing image sha256:46ea48c04e265c521b4018821c528c37719bdc64d49cd5df9a6988295d3eb590                    0.0s
 => => naming to docker.io/library/test:pandas                                                                  0.1s

What's Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview
```
```
~/dtc-dez/01-docker-terraform/docker_sql$ docker run -it test:pandas
root@6ca0af2b0e70:/# python
Python 3.9.1 (default, Feb  9 2021, 07:42:03) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pandas
<stdin>:1: DeprecationWarning: 
Pyarrow will become a required dependency of pandas in the next major release of pandas (pandas 3.0),
(to allow more performant data types, such as the Arrow string type, and better interoperability with other libraries)
but was not found to be installed on your system.
If this would cause problems for you,
please provide us feedback at https://github.com/pandas-dev/pandas/issues/54466
        
>>> pandas.__version__
'2.2.0'
```