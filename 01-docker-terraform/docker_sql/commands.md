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
