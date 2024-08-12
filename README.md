
# Linux Terminal Commands

## OS

- **I love cat. I love every kind of cat**

  ```bash
  ssh os_revision000@10.13.37.10
  os_revision001
  ls
  cat secret.flag
  8d484567839bed610fc06f21f27ea5f4
  ```

- **hidden attributes**

  ```bash
  ssh os_revision001@10.13.37.10
  os_revision001
  ls -la
  cat .secret.flag
  ed2d231f3b6142538877c08d01ef2aca1
  ```

- **navigating around**

  ```bash
  ssh os_revision002@10.13.37.10
  os_revision002
  ls -la
  cd inhere
  ls -la
  cat secret.flag
  5ac6dbc5f21c04325afd5051c1033eb3
  ```

- **Why did the file go ot the police?**

  ```bash
  ssh os_revision003@10.13.37.10
  os_revision003
  ls
  cd inhere0
  ls
  file ./*
  cat ./flag06
  355c077b9cc5cc578b0af34cb7ca6153
  ```

- **Why did the computer file feel lost?**

  ```bash
  ssh os_revision004@10.13.37.10
  os_revision004
  ls
  find -name \*.flag
  cat ./inhere3/file35.flag
  d50ebc863697dc03a34c5b19ce7c2b08
  ```

- **What is in a name?**

  ```bash
  ssh os_revision005@10.13.37.10
  os_revision005
  ls
  find ./ -user adam
  cat ./inhere6/file65.flag
  2171934626d97652b9dd79caf97a1694
  ```

- **Does size count?**

  ```bash
  ssh os_revision006@10.13.37.10
  os_revision006
  ls
  find ./ -user adam -size 33c
  cat ./inhere6/fjEkweorWp
  cda2b8470407afa9f957d02671a58de9 
  ```
- **That's a lot of words!**

  ```bash
  ssh os_revision007@10.13.37.10
  os_revision007
  ls
  cat os.revision.007.flag | grep hornstone
  hornstone 75b7f8e0279151b85d31ca258b4a7f06 

  ```

- **What the wget?**

  ```bash
  ls 
  find / -name \*.7z
  wget http://10.13.37.10/secret.flag.7z
  7za e secret.flag.7z -p99647cd064647295fb2b3ff0d4904115
  cat secret.flag
  a690b51cf7fa8ebaa7f733a334648e20
  ```

- **strings that matter the most?**

  ```bash
  ls 
  cat secret
  ./ secret 6fa1b41f5a40b34ca707c6d36a231d79
  CTF Flag: ae87a47a1b8a6eb58843ce6967ab201f
  ```

## Network Administration

- **Hello Containerlabs** 

  ```bash
  mkdir linuxwork
  vim topology.yml
  sudo containerlab deploy -t topology.yml
  ip a s
  ssh networking000@10.13.37.10
  ./reverse-ctf.sh 10.13.37.71
  ./secret 6fa1b41f5a40b34ca707c6d36a231d79
  ae87a47a1b8a6eb58843ce6967ab201f
  ```

- **Example**

  ```bash
  ls
  ```

- **Example**

  ```bash
  ls
  ```

## Secret

- **secret.000**

  ```bash
  6fa1b41f5a40b34ca707c6d36a231d79
  ```
  
- **secret.001**

  ```bash
  Unkown
  ```

- **secret.002**

  ```bash
  2ce7e1ecd7c927681fe302f1e4bd3371
  ```

- **Secret.003**

  ```bash
  e6426f62f9cefe09140847daebc55205
  ```

- **challenge.000.000**

  ```bash
  03b0cfc0e6a42c09c567184990aeaa9c
  ```

- **challenge.000.000**

  ```bash
  find / -type f -size +50c -size -60c | grep flag
  cat /lusr/local/share/obsolete_libs/W344gweSDl.flag
  THE SECRET FLAG IS 0a5f5a226877af1941a1dcbba1c2af2a
  ```


