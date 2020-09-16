# Tar Zip Everything

## Keeping permissions and hidden files inside the root folder

Run this from the command line inside the main folder you want to zip:

```
shopt -s dotglob && tar -czvpf websitename.tar.gz . && shopt -u dotglob
```

Here the "." represents selecting all files inside the current folder, this could be replced with the name of the folder you want to zip if not running command from inside the folder, for example "htdocs". 
It makes using the tar gzip much easier because you do not have to extract the files then move them all into another folder afterwards.

## Unzip inside the root folder

Create the folder of your project and copy the zip into it. Then run this from the command line:

```
tar -xzvpf websitename.tar.gz
```

## Terminology

Gzip Compression The Gzip format is the most widely used compression format for tar, it is fast for creating and extracting files.

- tar - name of command
- c - create
- x - extract
- z - using g.zip
- v - verbose - prints everthing on screen
- p - keeps permissions
- f - folder to zip

- shopt -s <option> to set (enable) options
- shopt -u <option>  to unset (disable) an option
- dotglob - includes all hidden files