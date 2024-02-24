# Program Interaction

### level 1

* /challenge/embryoio\_level1

### level 2

* /challenge/embryoio\_level2
* STDIN: ohlxdzwk

### level 3

* /challenge/embryoio\_level3 zjknqbgpym

### level 4

* export eoenyp=erxmsdihin
* /challenge/embryoio\_level4

### level 5

* touch /tmp/etgyzz
* echo "fzgfqswr" > /tmp/etgyzz
* /challenge/embryoio\_level5 < /tmp/etgyzz

### level 6

* /challenge/embryoio\_level6 > /tmp/mriavb
* cat /tmp/mriavb

### level 7

* bash -c 'exec -c -a "" /challenge/embryoio\_level7'

### level 8

```bash.sh
#!/bin/bash

/challenge/embryoio_level8
```

* bash bash.sh

### level 9

```bash.sh
#!/bin/bash

/challenge/embryoio_level9
```

* bash bash.sh
* arstshwf

### level 10

```bash.sh
#!/bin/bash

/challenge/embryoio_level10 asbiaaphyn
```

* bash bash.sh

### level 11

```bash.sh
#!/bin/bash

export xwzejc=oniobeaqfb
/challenge/embryoio_level11
```

* bash bash.sh

### level 12

```bash.sh
#!/bin/bash

/tmp/kzgaox
echo bczijbap > /tmp/kzgaox
/challenge/embryoio_level12 < /tmp/kzgaox
```

* bash bash.sh

### level 13

```bash.sh
#!/bin/bash

/challenge/embryoio_level13 > /tmp/umcqpn
```

* bash bash.sh
* cat /tmp/umcqpn

### level 14

```bash.sh
#!/bin/bash

bash -c 'exec -c -a "" /challenge/embryoio_level14'
```

* bash bash.sh

### level 15

* ipython

```python
from pwn import *

p = process('/challenge/embryoio_level15')
p.interactive()
```

### level 16

* ipython

```python
from pwn import *

p = process('/challenge/embryoio_level16')
p.interactive()
```

* dwlvbdjr

### level 17

* ipython

```python
from pwn import *

p = process(['/challenge/embryoio_level17', 'fkfxeulkjy'])
p.interactive()
```

### level 18

* ipython

```python
from pwn import *

p = process('/challenge/embryoio_level18', env={'cnsysl':'idndqtahuc'})
p.interactive()
```

### level 19

* ipython

```python
from pwn import *
import os

with open("/tmp/etksmq", 'w') as file:
    file.write("tbbefvop")

fd = os.open("/tmp/etksmq", os.O_RDONLY)

p = process('/challenge/embryoio_level19', stdin=fd)
p.interactive()
```

### level 20

* ipython

```python.py
from pwn import *
import os

fd = os.open("/tmp/wxngwq", os.O_WRONLY | os.O_CREAT)

p = process('/challenge/embryoio_level20', stdout=fd)

with open("/tmp/wxngwq", 'r') as file:
	print(file.read())
p.interactive()
```

### level 21

* ipython

```python.py
from pwn import *
import os

p = process('/challenge/embryoio_level21', env={})

p.interactive()
```

### level 22

```python
from pwn import *

p = process('/challenge/embryoio_level22')
p.interactive()
```

* python python.py

### level 23

```python
from pwn import *

p = process('/challenge/embryoio_level23')
p.interactive()
```

* python python.py
* ulelosql

### level 24

```python
from pwn import *

p = process(['/challenge/embryoio_level24', 'ebyhyvaqeu'])
p.interactive()
```

* python python.py

### level 25

```python
from pwn import *

p = process('/challenge/embryoio_level25', env={'zxkabi':'nuscpaudrt'})
p.interactive()
```

* python python.py

### level 26

```python
from pwn import *
import os

with open("/tmp/touekf", 'w') as file:
    file.write("fnzkutbe")

fd = os.open("/tmp/touekf", os.O_RDONLY)

p = process('/challenge/embryoio_level26', stdin=fd)
p.interactive()
```

* python python.py

### level 27

```python.py
from pwn import *
import os

fd = os.open("/tmp/btxtnc", os.O_WRONLY | os.O_CREAT)

p = process('/challenge/embryoio_level27', stdout=fd)

with open("/tmp/btxtnc", 'r') as file:
	print(file.read())
p.interactive()
```

* python python.py

### level 28

```python.py
from pwn import *
import os

p = process('/challenge/embryoio_level28', env={})

p.interactive()
```

* python python.py

### level 29

```c
#include <stdio.h>
#include <stdlib.h>

void pwncollege () {

}

int main () {
	const char filename[100] = "/challenge/embryoio_level29";

	pid_t cpid;

	if (fork() == 0) {
		execve(filename, NULL, NULL);
		exit(0);
	}
	else {
		cpid = wait(NULL);
	}

	return 0;
}
```

* gcc test.c -o test
* ./test

### level 30

```c
#include <stdio.h>
#include <stdlib.h>

void pwncollege () {

}

int main () {
	const char filename[100] = "/challenge/embryoio_level30";

	pid_t cpid;

	if (fork() == 0) {
		execve(filename, NULL, NULL);
		exit(0);
	}
	else {
		cpid = wait(NULL);
	}

	return 0;
}
```

* gcc test.c -o test
* ./test
* apyhlmya

### level 31

```c
#include <stdio.h>
#include <stdlib.h>

void pwncollege () {

}

int main (int argc, char **argv) {
    const char filename[100] = "/challenge/embryoio_level31";
    
    pid_t cpid;

    char **buff = "chapeafvrb";
    char *argv[] = {filename, "chapeafvrb", NULL};

    int newfd;
    dup2(0, newfd);

    if (fork() == 0) {
	    execve(filename, argv, NULL);
        exit(0);
    }
    else {
        cpid = wait(NULL);
    }

     return 0;
}
```
