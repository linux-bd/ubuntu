### Get All Environment Variables
```
printenv
```

### Get Path Variable
* ``` echo $PATH | tr ":" "\n" ```
```sh
/home/google/bin
/home/google/.local/bin
/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin
/usr/games
/usr/local/games
/snap/bin
/opt/go/bin
/opt/redis
/opt/jdk/bin
/opt/gradle/bin
/opt/nodejs/bin
```
* ``` echo $PATH | tr ":" "\n" | nl ```
```sh
     1	/home/google/bin
     2	/home/google/.local/bin
     3	/usr/local/sbin
     4	/usr/local/bin
     5	/usr/sbin
     6	/usr/bin
     7	/sbin
     8	/bin
     9	/usr/games
    10	/usr/local/games
    11	/snap/bin
    12	/opt/go/bin
    13	/opt/redis
    14	/opt/jdk/bin
    15	/opt/gradle/bin
    16	/opt/nodejs/bin
```
