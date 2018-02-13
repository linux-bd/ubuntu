### [How to add a directory to the path](https://askubuntu.com/questions/60218/how-to-add-a-directory-to-the-path)

#### Edit .bashrc in your home directory and add the following line
```sh
export PATH="/path/to/dir:$PATH"
```

#### Microsoft Use this Convention
```sh
export PATH="$PATH:/opt/mssql-tools/bin"
```

#### You will need to source your .bashrc or logout/login (or restart the terminal) for the changes to take effect. To source your .bashrc, simply type
```sh
$ source ~/.bashrc
```
