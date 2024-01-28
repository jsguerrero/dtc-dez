<h1>Introduction to Docker</h1>

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

Despues de generar el archivo pipeline.py
```
~/dtc-dez/01-docker-terraform/docker_sql$ docker build -t test:pandas .
[+] Building 3.0s (10/10) FINISHED                                                                    docker:default
 => [internal] load build definition from Dockerfile                                                            0.1s
 => => transferring dockerfile: 142B                                                                            0.0s
 => [internal] load .dockerignore                                                                               0.1s
 => => transferring context: 2B                                                                                 0.0s
 => [internal] load metadata for docker.io/library/python:3.9.1                                                 2.2s
 => [auth] library/python:pull token for registry-1.docker.io                                                   0.0s
 => [1/4] FROM docker.io/library/python:3.9.1@sha256:ca8bd3c91af8b12c2d042ade99f7c8f578a9f80a0dbbd12ed261eeba9  0.0s
 => [internal] load build context                                                                               0.1s
 => => transferring context: 125B                                                                               0.0s
 => CACHED [2/4] RUN pip install pandas                                                                         0.0s
 => [3/4] WORKDIR /app                                                                                          0.1s
 => [4/4] COPY pipeline.py pipeline.py                                                                          0.1s
 => exporting to image                                                                                          0.2s
 => => exporting layers                                                                                         0.1s
 => => writing image sha256:d45b88f0bbe44e0a68e7c6a23037b8a28db265c591b1e8edb62983f3878d153d                    0.0s
 => => naming to docker.io/library/test:pandas                                                                  0.0s

What's Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview
```

```
~/dtc-dez/01-docker-terraform/docker_sql$ docker run -it test:pandas
root@6950c32a0a16:/app# ls
pipeline.py
root@6950c32a0a16:/app# pwd
/app
root@6950c32a0a16:/app# python pipeline.py 
/app/pipeline.py:1: DeprecationWarning: 
Pyarrow will become a required dependency of pandas in the next major release of pandas (pandas 3.0),
(to allow more performant data types, such as the Arrow string type, and better interoperability with other libraries)
but was not found to be installed on your system.
If this would cause problems for you,
please provide us feedback at https://github.com/pandas-dev/pandas/issues/54466
        
  import pandas as pd
job finished successfully
root@6950c32a0a16:/app# exit
```

Despues de agregar los parametros al pipeline
```
~/dtc-dez/01-docker-terraform/docker_sql$ docker build -t test:pandas .
[+] Building 1.5s (10/10) FINISHED                                                                                                                                          docker:default
 => [internal] load .dockerignore                                                                                                                                                     0.0s
 => => transferring context: 2B                                                                                                                                                       0.0s
 => [internal] load build definition from Dockerfile                                                                                                                                  0.0s
 => => transferring dockerfile: 159B                                                                                                                                                  0.0s
 => [internal] load metadata for docker.io/library/python:3.9.1                                                                                                                       1.3s
 => [auth] library/python:pull token for registry-1.docker.io                                                                                                                         0.0s
 => [1/4] FROM docker.io/library/python:3.9.1@sha256:ca8bd3c91af8b12c2d042ade99f7c8f578a9f80a0dbbd12ed261eeba96dd632f                                                                 0.0s
 => [internal] load build context                                                                                                                                                     0.0s
 => => transferring context: 191B                                                                                                                                                     0.0s
 => CACHED [2/4] RUN pip install pandas                                                                                                                                               0.0s
 => CACHED [3/4] WORKDIR /app                                                                                                                                                         0.0s
 => CACHED [4/4] COPY pipeline.py pipeline.py                                                                                                                                         0.0s
 => exporting to image                                                                                                                                                                0.0s
 => => exporting layers                                                                                                                                                               0.0s
 => => writing image sha256:622d265434e5775da70e6a39c3923a04bf7e89ca9d7e934eda82a6e47b977c55                                                                                          0.0s
 => => naming to docker.io/library/test:pandas                                                                                                                                        0.0s

What's Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview
```

```
~/dtc-dez/01-docker-terraform/docker_sql$ docker run -it test:pandas 2024-01-23
/app/pipeline.py:1: DeprecationWarning: 
Pyarrow will become a required dependency of pandas in the next major release of pandas (pandas 3.0),
(to allow more performant data types, such as the Arrow string type, and better interoperability with other libraries)
but was not found to be installed on your system.
If this would cause problems for you,
please provide us feedback at https://github.com/pandas-dev/pandas/issues/54466
        
  import pandas as pd
['pipeline.py', '2024-01-23']
job finished successfully for day = 2024-01-23

~/dtc-dez/01-docker-terraform/docker_sql$ docker run -it test:pandas 2024-01-23 123 hello
/app/pipeline.py:1: DeprecationWarning: 
Pyarrow will become a required dependency of pandas in the next major release of pandas (pandas 3.0),
(to allow more performant data types, such as the Arrow string type, and better interoperability with other libraries)
but was not found to be installed on your system.
If this would cause problems for you,
please provide us feedback at https://github.com/pandas-dev/pandas/issues/54466
        
  import pandas as pd
['pipeline.py', '2024-01-23', '123', 'hello']
job finished successfully for day = 2024-01-23
```

<h1>Ingesting NY Taxi Data to Postgres</h1>

```
~/dtc-dez/01-docker-terraform$ docker run -it \
>   -e POSTGRES_USER="root" \
>   -e POSTGRES_PASSWORD="root" \
>   -e POSTGRES_DB="ny_taxi" \
>   -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data:rw \
>   -p 5432:5432 \
> postgres:13 
Unable to find image 'postgres:13' locally
13: Pulling from library/postgres
.
.
.
/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

2024-01-28 03:56:51.793 UTC [50] LOG:  received fast shutdown request
waiting for server to shut down....2024-01-28 03:56:51.806 UTC [50] LOG:  aborting any active transactions
2024-01-28 03:56:51.818 UTC [50] LOG:  background worker "logical replication launcher" (PID 57) exited with exit code 1
2024-01-28 03:56:51.819 UTC [52] LOG:  shutting down
2024-01-28 03:56:51.884 UTC [50] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2024-01-28 03:56:51.967 UTC [1] LOG:  starting PostgreSQL 13.13 (Debian 13.13-1.pgdg120+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 12.2.0-14) 12.2.0, 64-bit
2024-01-28 03:56:51.968 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2024-01-28 03:56:51.968 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2024-01-28 03:56:51.998 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2024-01-28 03:56:52.012 UTC [65] LOG:  database system was shut down at 2024-01-28 03:56:51 UTC
2024-01-28 03:56:52.026 UTC [1] LOG:  database system is ready to accept connections
```

```
jguerrero@DESKTOP-FVK443T:~/dtc-dez$ virtualenv ~/venvs/dtc_dez
created virtual environment CPython3.8.10.final.0-64 in 302ms
  creator CPython3Posix(dest=/home/jguerrero/venvs/dtc_dez, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/jguerrero/.local/share/virtualenv)
    added seed packages: pip==23.3.1, setuptools==69.0.2, wheel==0.42.0
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator
jguerrero@DESKTOP-FVK443T:~/dtc-dez$ source ~/venvs/dtc_dez/bin/activate
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez$ pip install pgcli
.
.
.
Installing collected packages: wcwidth, zipp, tzdata, typing-extensions, tabulate, sqlparse, six, setproctitle, Pygments, prompt-toolkit, click, backports.zoneinfo, python-dateutil, psycopg, importlib-resources, configobj, time-machine, pgspecial, cli-helpers, pendulum, pgcli
Successfully installed Pygments-2.17.2 backports.zoneinfo-0.2.1 cli-helpers-2.3.0 click-8.1.7 configobj-5.0.8 importlib-resources-6.1.1 pendulum-3.0.0 pgcli-4.0.1 pgspecial-2.1.1 prompt-toolkit-3.0.43 psycopg-3.1.17 python-dateutil-2.8.2 setproctitle-1.3.3 six-1.16.0 sqlparse-0.4.4 tabulate-0.9.0 time-machine-2.13.0 typing-extensions-4.9.0 tzdata-2023.4 wcwidth-0.2.13 zipp-3.17.0

[notice] A new release of pip is available: 23.3.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez$ pgcli -h localhost -p 5432 -u root -d ny_taxi
Password for root: 
Server: PostgreSQL 13.13 (Debian 13.13-1.pgdg120+1)
Version: 4.0.1
Home: http://pgcli.com
root@localhost:ny_taxi> \dt
+--------+------+------+-------+
| Schema | Name | Type | Owner |
|--------+------+------+-------|
+--------+------+------+-------+
SELECT 0
Time: 0.017s
root@localhost:ny_taxi> SELECT 1;
+----------+
| ?column? |
|----------|
| 1        |
+----------+
SELECT 1
Time: 0.007s
root@localhost:ny_taxi>
```

```
jguerrero@DESKTOP-FVK443T:~/dtc-dez$ source ~/venvs/dtc_dez/bin/activate
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez$ pip install pandas
Collecting pandas
  Downloading pandas-2.0.3-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (18 kB)
Requirement already satisfied: python-dateutil>=2.8.2 in /home/jguerrero/venvs/dtc_dez/lib/python3.8/site-packages (from pandas) (2.8.2)
Requirement already satisfied: pytz>=2020.1 in /home/jguerrero/venvs/dtc_dez/lib/python3.8/site-packages (from pandas) (2023.3.post1)
Requirement already satisfied: tzdata>=2022.1 in /home/jguerrero/venvs/dtc_dez/lib/python3.8/site-packages (from pandas) (2023.4)
Collecting numpy>=1.20.3 (from pandas)
  Downloading numpy-1.24.4-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (5.6 kB)
Requirement already satisfied: six>=1.5 in /home/jguerrero/venvs/dtc_dez/lib/python3.8/site-packages (from python-dateutil>=2.8.2->pandas) (1.16.0)
Downloading pandas-2.0.3-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (12.4 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 12.4/12.4 MB 21.3 MB/s eta 0:00:00
Downloading numpy-1.24.4-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (17.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 17.3/17.3 MB 16.8 MB/s eta 0:00:00
Installing collected packages: numpy, pandas
Successfully installed numpy-1.24.4 pandas-2.0.3

[notice] A new release of pip is available: 23.3.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez$ pip install jupyter
.
.
.
Downloading types_python_dateutil-2.8.19.20240106-py3-none-any.whl (9.7 kB)
Installing collected packages: webencodings, pytz, pure-eval, ptyprocess, pickleshare, json5, fastjsonschema, backcall, widgetsnbextension, websocket-client, webcolors, urllib3, uri-template, types-python-dateutil, traitlets, tornado, tomli, tinycss2, soupsieve, sniffio, send2trash, rpds-py, rfc3986-validator, rfc3339-validator, pyzmq, pyyaml, python-json-logger, pycparser, psutil, prometheus-client, platformdirs, pkgutil-resolve-name, pexpect, parso, pandocfilters, packaging, overrides, nest-asyncio, mistune, markupsafe, jupyterlab-widgets, jupyterlab-pygments, jsonpointer, importlib-metadata, idna, fqdn, executing, exceptiongroup, defusedxml, decorator, debugpy, charset-normalizer, certifi, bleach, babel, attrs, async-lru, asttokens, terminado, stack-data, requests, referencing, qtpy, matplotlib-inline, jupyter-core, jinja2, jedi, comm, cffi, beautifulsoup4, arrow, anyio, jupyter-server-terminals, jupyter-client, jsonschema-specifications, isoduration, ipython, argon2-cffi-bindings, jsonschema, ipywidgets, ipykernel, argon2-cffi, qtconsole, nbformat, jupyter-console, nbclient, jupyter-events, nbconvert, jupyter-server, notebook-shim, jupyterlab-server, jupyter-lsp, jupyterlab, notebook, jupyter
Successfully installed anyio-4.2.0 argon2-cffi-23.1.0 argon2-cffi-bindings-21.2.0 arrow-1.3.0 asttokens-2.4.1 async-lru-2.0.4 attrs-23.2.0 babel-2.14.0 backcall-0.2.0 beautifulsoup4-4.12.3 bleach-6.1.0 certifi-2023.11.17 cffi-1.16.0 charset-normalizer-3.3.2 comm-0.2.1 debugpy-1.8.0 decorator-5.1.1 defusedxml-0.7.1 exceptiongroup-1.2.0 executing-2.0.1 fastjsonschema-2.19.1 fqdn-1.5.1 idna-3.6 importlib-metadata-7.0.1 ipykernel-6.29.0 ipython-8.12.3 ipywidgets-8.1.1 isoduration-20.11.0 jedi-0.19.1 jinja2-3.1.3 json5-0.9.14 jsonpointer-2.4 jsonschema-4.21.1 jsonschema-specifications-2023.12.1 jupyter-1.0.0 jupyter-client-8.6.0 jupyter-console-6.6.3 jupyter-core-5.7.1 jupyter-events-0.9.0 jupyter-lsp-2.2.2 jupyter-server-2.12.5 jupyter-server-terminals-0.5.2 jupyterlab-4.0.11 jupyterlab-pygments-0.3.0 jupyterlab-server-2.25.2 jupyterlab-widgets-3.0.9 markupsafe-2.1.4 matplotlib-inline-0.1.6 mistune-3.0.2 nbclient-0.9.0 nbconvert-7.14.2 nbformat-5.9.2 nest-asyncio-1.6.0 notebook-7.0.7 notebook-shim-0.2.3 overrides-7.7.0 packaging-23.2 pandocfilters-1.5.1 parso-0.8.3 pexpect-4.9.0 pickleshare-0.7.5 pkgutil-resolve-name-1.3.10 platformdirs-4.1.0 prometheus-client-0.19.0 psutil-5.9.8 ptyprocess-0.7.0 pure-eval-0.2.2 pycparser-2.21 python-json-logger-2.0.7 pytz-2023.3.post1 pyyaml-6.0.1 pyzmq-25.1.2 qtconsole-5.5.1 qtpy-2.4.1 referencing-0.32.1 requests-2.31.0 rfc3339-validator-0.1.4 rfc3986-validator-0.1.1 rpds-py-0.17.1 send2trash-1.8.2 sniffio-1.3.0 soupsieve-2.5 stack-data-0.6.3 terminado-0.18.0 tinycss2-1.2.1 tomli-2.0.1 tornado-6.4 traitlets-5.14.1 types-python-dateutil-2.8.19.20240106 uri-template-1.3.0 urllib3-2.1.0 webcolors-1.13 webencodings-0.5.1 websocket-client-1.7.0 widgetsnbextension-4.0.9

[notice] A new release of pip is available: 23.3.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez$ cd 01-docker-terraform/
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ jupyter notebook
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ wget https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz 
--2024-01-27 22:21:13--  https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2021-01.csv.gz
Resolving github.com (github.com)... 140.82.113.4
Connecting to github.com (github.com)|140.82.113.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/513814948/f6895842-79e6-4a43-9458-e5b0b454a340?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240128%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240128T042117Z&X-Amz-Expires=300&X-Amz-Signature=bc71ef68de580bc6624d4d1b59c85c6c50c94ee82c6360bd5b387bcd9bf24a78&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=513814948&response-content-disposition=attachment%3B%20filename%3Dyellow_tripdata_2021-01.csv.gz&response-content-type=application%2Foctet-stream [following]
--2024-01-27 22:21:13--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/513814948/f6895842-79e6-4a43-9458-e5b0b454a340?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240128%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240128T042117Z&X-Amz-Expires=300&X-Amz-Signature=bc71ef68de580bc6624d4d1b59c85c6c50c94ee82c6360bd5b387bcd9bf24a78&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=513814948&response-content-disposition=attachment%3B%20filename%3Dyellow_tripdata_2021-01.csv.gz&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.109.133, 185.199.111.133, 185.199.108.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25031880 (24M) [application/octet-stream]
Saving to: ‘yellow_tripdata_2021-01.csv.gz’

yellow_tripdata_2021-01.csv.gz         100%[==========================================================================>]  23.87M  18.8MB/s    in 1.3s    

2024-01-27 22:21:15 (18.8 MB/s) - ‘yellow_tripdata_2021-01.csv.gz’ saved [25031880/25031880]
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ gzip -d yellow_tripdata_2021-01.csv.gz
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ less yellow_tripdata_2021-01.csv
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ wc -l yellow_tripdata_2021-01.csv 
1369766 yellow_tripdata_2021-01.csv
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ cp yellow_tripdata_2021-01.csv docker_sql/
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ pip install sqlalchemy
Collecting sqlalchemy
  Downloading SQLAlchemy-2.0.25-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (9.6 kB)
Requirement already satisfied: typing-extensions>=4.6.0 in /home/jguerrero/venvs/dtc_dez/lib/python3.8/site-packages (from sqlalchemy) (4.9.0)
Collecting greenlet!=0.4.17 (from sqlalchemy)
  Downloading greenlet-3.0.3-cp38-cp38-manylinux_2_24_x86_64.manylinux_2_28_x86_64.whl.metadata (3.8 kB)
Downloading SQLAlchemy-2.0.25-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.1 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.1/3.1 MB 9.9 MB/s eta 0:00:00
Downloading greenlet-3.0.3-cp38-cp38-manylinux_2_24_x86_64.manylinux_2_28_x86_64.whl (622 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 622.3/622.3 kB 13.6 MB/s eta 0:00:00
Installing collected packages: greenlet, sqlalchemy
Successfully installed greenlet-3.0.3 sqlalchemy-2.0.25
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ pip install psycopg2-binary
Collecting psycopg2-binary
  Downloading psycopg2_binary-2.9.9-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (4.4 kB)
Downloading psycopg2_binary-2.9.9-cp38-cp38-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.0 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.0/3.0 MB 8.5 MB/s eta 0:00:00
Installing collected packages: psycopg2-binary
Successfully installed psycopg2-binary-2.9.9
```

Despues de ejecutar el codigo del jupyter notebook
```
root@localhost:ny_taxi> \dt
+--------+------------------+-------+-------+
| Schema | Name             | Type  | Owner |
|--------+------------------+-------+-------|
| public | yellow_taxi_data | table | root  |
+--------+------------------+-------+-------+
SELECT 1
Time: 0.008s

root@localhost:ny_taxi> \d yellow_taxi_data;
+-----------------------+-----------------------------+-----------+
| Column                | Type                        | Modifiers |
|-----------------------+-----------------------------+-----------|
| index                 | bigint                      |           |
| VendorID              | bigint                      |           |
| tpep_pickup_datetime  | timestamp without time zone |           |
| tpep_dropoff_datetime | timestamp without time zone |           |
| passenger_count       | bigint                      |           |
| trip_distance         | double precision            |           |
| RatecodeID            | bigint                      |           |
| store_and_fwd_flag    | text                        |           |
| PULocationID          | bigint                      |           |
| DOLocationID          | bigint                      |           |
| payment_type          | bigint                      |           |
| fare_amount           | double precision            |           |
| extra                 | double precision            |           |
| mta_tax               | double precision            |           |
| tip_amount            | double precision            |           |
| tolls_amount          | double precision            |           |
| improvement_surcharge | double precision            |           |
| total_amount          | double precision            |           |
| congestion_surcharge  | double precision            |           |
:...skipping...
+-----------------------+-----------------------------+-----------+
| Column                | Type                        | Modifiers |
|-----------------------+-----------------------------+-----------|
| index                 | bigint                      |           |
| VendorID              | bigint                      |           |
| tpep_pickup_datetime  | timestamp without time zone |           |
| tpep_dropoff_datetime | timestamp without time zone |           |
| passenger_count       | bigint                      |           |
| trip_distance         | double precision            |           |
| RatecodeID            | bigint                      |           |
| store_and_fwd_flag    | text                        |           |
| PULocationID          | bigint                      |           |
| DOLocationID          | bigint                      |           |
| payment_type          | bigint                      |           |
| fare_amount           | double precision            |           |
| extra                 | double precision            |           |
| mta_tax               | double precision            |           |
| tip_amount            | double precision            |           |
| tolls_amount          | double precision            |           |
| improvement_surcharge | double precision            |           |
| total_amount          | double precision            |           |
| congestion_surcharge  | double precision            |           |
+-----------------------+-----------------------------+-----------+
Indexes:
    "ix_yellow_taxi_data_index" btree (index)
```

```
root@localhost:ny_taxi> select count(1) from yellow_taxi_data;
+---------+
| count   |
|---------|
| 1369765 |
+---------+
SELECT 1
Time: 0.132s
root@localhost:ny_taxi>
```

<h2> Video 1.2.3 </h2>

```
root@localhost:ny_taxi> SELECT MAX(tpep_pickup_datetime), MIN(tpep_pickup_datetime), MAX(total_amount) FROM yellow_taxi_data;
+---------------------+---------------------+---------+
| max                 | min                 | max     |
|---------------------+---------------------+---------|
| 2021-02-22 16:52:16 | 2008-12-31 23:05:14 | 7661.28 |
+---------------------+---------------------+---------+
SELECT 1
Time: 0.569s
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez$ docker run -it \
>   -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
>   -e PGADMIN_DEFAULT_PASSWORD="root" \
>   -p 8080:80 \
> dpage/pgadmin4
Unable to find image 'dpage/pgadmin4:latest' locally
latest: Pulling from dpage/pgadmin4
.
.
.
pgAdmin 4 - Application Initialisation
======================================

postfix/postfix-script: starting the Postfix mail system
[2024-01-28 05:13:41 +0000] [1] [INFO] Starting gunicorn 20.1.0
[2024-01-28 05:13:41 +0000] [1] [INFO] Listening at: http://[::]:80 (1)
[2024-01-28 05:13:41 +0000] [1] [INFO] Using worker: gthread
[2024-01-28 05:13:41 +0000] [118] [INFO] Booting worker with pid: 118
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ docker network create pg-network
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ docker run -it \
>   -e POSTGRES_USER="root" \
>   -e POSTGRES_PASSWORD="root" \
>   -e POSTGRES_DB="ny_taxi" \
>   -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data:rw \
>   -p 5432:5432 \
>   --network=pg-network \
>   --name=pg-database \
> postgres:13

PostgreSQL Database directory appears to contain a database; Skipping initialization

2024-01-28 05:19:25.298 UTC [1] LOG:  starting PostgreSQL 13.13 (Debian 13.13-1.pgdg120+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 12.2.0-14) 12.2.0, 64-bit
2024-01-28 05:19:25.302 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2024-01-28 05:19:25.302 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2024-01-28 05:19:25.310 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2024-01-28 05:19:25.320 UTC [27] LOG:  database system was shut down at 2024-01-28 05:19:03 UTC
2024-01-28 05:19:25.339 UTC [1] LOG:  database system is ready to accept connections
```

```
(dtc_dez) jguerrero@DESKTOP-FVK443T:~/dtc-dez/01-docker-terraform$ docker run -it \
>   -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
>   -e PGADMIN_DEFAULT_PASSWORD="root" \
>   -p 8080:80 \
>   --network=pg-network \
>   --name=pgadmin \
> dpage/pgadmin4
NOTE: Configuring authentication for SERVER mode.

pgAdmin 4 - Application Initialisation
======================================

postfix/postfix-script: starting the Postfix mail system
[2024-01-28 05:23:04 +0000] [1] [INFO] Starting gunicorn 20.1.0
[2024-01-28 05:23:04 +0000] [1] [INFO] Listening at: http://[::]:80 (1)
[2024-01-28 05:23:04 +0000] [1] [INFO] Using worker: gthread
[2024-01-28 05:23:04 +0000] [117] [INFO] Booting worker with pid: 117
```