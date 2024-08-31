
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
  ls2d599ad2d19dad48f37434e2ee65e377
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
2d599ad2d19dad48f37434e2ee65e377
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
  name: reverse_ctf_tester
  topology:
    nodes:
      test:
        kind: linux
        image: reverse-ctf-server
        ports:
          - "2222:22/tcp"
  :wq
  
  sudo containerlab deploy -t topology.yml
  ip a s
  
  ssh networking000@10.13.37.10
  networking000
  ./reverse-ctf.sh 10.13.37.71
  ./secret 6fa1b41f5a40b34ca707c6d36a231d79
  ae87a47a1b8a6eb58843ce6967ab201f
  ```

- **Connect test-server to a router**

  ```bash
  vim topology.yml
  name: test-router-static
  topology:
    nodes:
      r1:
        kind: linux
        image: frrouting/frr:latest
      test:
        kind: linux
        image: reverse-ctf-server
        ports:
          - "2222:22/tcp"
    links: 
      - endpoints: ['r1:eth1', 'test:eth1']
  :wq
  
  sudo containerlab deploy -t topology.yml
  docker exec -it clab-test-router-static-r1 vtysh
  configure terminal
  interface eth1
  ip address 10.0.0.1/24
  end
  write memory
  show interface brief
  
  docker exec -it clab-test-router-statc-test sh
  apk update
  apk add iproute
  ip addr add 10.0.0.50/24 dev eth1 
  ip link set eth1 up
  ip route add default via 10.0.0.1
  
  ssh networking001@10.13.37.10
  ./reverse-ctf.sh 10.13.37.57
  Flag: f1223c77990ca35199cb998259d7358a
  ```

- **Two networks; one router**

  ```bash
  vim topology.yml
  name: test-router-static
  topology:
    nodes:
      r1:
        kind: linux
        image: frrouting/frr:latest
  
      workstation1:
        kind: linux
        image: alpine:latest
  
      test:
        kind: linux
        image: reverse-ctf-server
        ports:
          - "2222:22/tcp"
    links: 
      - endpoints: ['r1:eth1', 'test:eth1']
      - endpoints: ['r1:eth2', 'workstation1:eth1']
  :wq
  
  sudo containerlab deploy -t topology.yml
  sudo docker exec -it clab-test-router-static-r1 vtysh
  interface eth1
  ip address 10.0.0.1/24
  interface eth2
  ip address 10.0.1.1/24
  end
  write memory
  exit
  
  sudo docker exec -it clab-test-router-static-test sh
  apk update
  apk add iproute2
  ip addr add 10.0.0.50/24 dev eth1 
  ip link set eth1 up
  ip route del default via 172.20.20.1 dev eth0
  ip route add default via 10.0.0.1 dev eth1 metric 100
  ip route add default via 172.20.20.1 dev eth0 metric 200
  
  sudo docker exec -it clab-test-router-static-workstation1 sh
  apk update
  apk add iproute2
  ip addr add 10.0.1.50/24 dev eth1 
  ip link set eth1 up
  ip route del default via  172.20.20.1 dev eth0
  ip route add default via 10.0.1.1 dev eth1 metric 100
  ip route add default via 172.20.20.1 dev eth0 metric 200
  
  ssh networking002@10.13.37.10
  networking002
  /reverse-ctf.sh 10.13.37.57
  937fa2856b905a26fc4e1ed17233f9fb
  ```

## Secret

- **secret.000**

  ```bash
  6fa1b41f5a40b34ca707c6d36a231d79
  ```
- **secret.001**

  ```bash
  8f466d07332b4a1476751977005463ea
  ```

- **secret.002**

  ```bash
  2ce7e1ecd7c927681fe302f1e4bd3371
  ```

- **Secret.003**

  ```bash
  e6426f62f9cefe09140847daebc55205
  ```

- **Secret.004**

  ```bash
  027eac9a94926df213c3bf01c9b71832
  ```
- **Secret.005**

  ```bash
  unknown
  ```
- **secret.006**
  
  ```bash
  fa671cd606f8ddc1c23dd0ca1dd7c59e
  ```
  
- **secret.007**
  
  ```bash
  d10be7c70c757544f76cdc3714bd5fdd
  ```
  
- **secret.008**
  
  ```bash
  curl 10.0.0.223/secret.flag
  7dbcc0a0d005ef14acc3d5017f6c5812
  ```
- **secret.009**
  
  ```bash

  ```
  
- **secret.0010**
  
  ```bash
  58681A5174BDC71CDFC9E79B8F8672C3
  ```
  
- **secret.011**
  
  ```bash
  2ef3c122664c6f64f33b8cab58d1f630
  ```

## Challenges

- **challenge.000.000**

  ```bash
  ssh challenge.000.000@10.13.37.10
  challenge.000.000
  ls
  cd inhere
  ls -la
  cat .secret
  03b0cfc0e6a42c09c567184990aeaa9c
  ```

- **challenge.000.001**

  ```bash
  ssh challenge.000.001@10.13.37.10
  challenge.000.001
  find / -type f -size +50c -size -60c | grep flag
  cat /lusr/local/share/obsolete_libs/W344gweSDl.flag
  THE SECRET FLAG IS 0a5f5a226877af1941a1dcbba1c2af2a
  ```

- **challenge.000.002**

  ```bash
  ssh challenge.000.002@10.13.37.10
  challenge.000.002
  cat secret.flag | grep "hunched"
  hunched 2d599ad2d19dad48f37434e2ee65e377
  ```
- **challenge.000.003**

  ```bash
  vim topology.yml
  name: reverse_ctf_tester
  topology:
    nodes:
      test:
        kind: linux
        image: reverse-ctf-server
        ports:
          - "2222:22/tcp"
  :wq
  
  sudo containerlab deploy -t topology.yml
  ip a s
  
  ssh challenge.000.003@10.13.37.10
  challenge.000.003
  ./reverse-ctf.sh 10.13.37.71
  9dd368744a1f1c09753e435434d51326
  ```

- **challenge.000.004**

  ```bash
  vim topology.yml
  name: test-router-static
  topology:
    nodes:
      r1:
        kind: linux
        image: frrouting/frr:latest
      test:
        kind: linux
        image: reverse-ctf-server
        ports:
          - "2222:22/tcp"
    links: 
      - endpoints: ['r1:eth1', 'test:eth1']
  :wq
  
  sudo containerlab deploy -t topology.yml
  docker exec -it clab-test-router-static-r1 vtysh
  configure terminal
  interface eth1
  ip address 10.13.36.50/24
  end
  write memory
  show interface brief
  
  docker exec -it clab-test-router-statc-test sh
  apk update
  apk add iproute
  ip addr add 10.13.36.1/24 dev eth1 
  ip link set eth1 up
  ip route add default via 10.13.36.50
  
  ssh challenge.000.004@10.13.37.10
  challenge.000.004
  ./reverse-ctf.sh 10.13.37.57
  bdbd9e2b898a31807eefbdbf1137b66f
  ```

- **challenge.000.005**

  ```bash
  vim topology.yml
  name: test-router-static
  topology:
    nodes:
      r1:
        kind: linux
        image: frrouting/frr:latest
  
      workstation1:
        kind: linux
        image: alpine:latest
  
        workstation2:
        kind: linux
        image: alpine:latest
  
      test:
        kind: linux
        image: reverse-ctf-server
        ports:
          - "2222:22/tcp"
    links: 
      - endpoints: ['r1:eth1', 'test:eth1']
      - endpoints: ['r1:eth2', 'workstation1:eth1']
      - endpoints: ['r1:eth3', 'workstation2:eth1']
  :wq
  
  sudo containerlab deploy -t topology.yml
  sudo docker exec -it clab-test-router-static-r1 vtysh
  interface eth1
  ip address 10.0.0.1/24
  interface eth2
  ip address 10.13.36.1/24
  interface eth3
  ip address 10.10.10.1/24
  end
  write memory
  exit
  
  sudo docker exec -it clab-test-router-static-test sh
  apk update
  apk add iproute2
  ip addr add 10.0.0.10/24 dev eth1 
  ip link set eth1 up
  ip route del default via 172.20.20.1 dev eth0
  ip route add default via 10.0.0.10 dev eth1 metric 100
  ip route add default via 172.20.20.1 dev eth0 metric 200
  
  sudo docker exec -it clab-test-router-static-workstation1 sh
  apk update
  apk add iproute2
  ip addr add 10.0.13.36.50/24 dev eth1 
  ip link set eth1 up
  ip route del default via 172.20.20.1 dev eth0
  ip route add default via 10.0.13.36.1 dev eth1 metric 100
  ip route add default via 172.20.20.1 dev eth0 metric 200
  
  sudo docker exec -it clab-test-router-static-workstation2 sh
  apk update
  apk add iproute2
  ip addr add 10.10.10.92/24 dev eth1 
  ip link set eth1 up
  ip route del default via 172.20.20.1 dev eth0
  ip route add default via 10.10.10.1 dev eth1 metric 100
  ip route add default via 172.20.20.1 dev eth0 metric 200
  
  ssh challenge.000.005@10.13.37.10
  challenge.000.005
  /reverse-ctf.sh 10.13.37.57
  027eac9a94926df213c3bf01c9b71832
  ```

## Networking Tools

  - **nmap.000**
  ```bash
    ip a
    10.0.0.10
  ```

  - **nmap.001**
  ```bash
  ssh testuser@10.13.37.10 -p 10000
  nmap 10.0.0.0/24
  ssh testuser@10.0.0.100 -p 22
  cat secret.flag
  79d3e22235788332396c80bf0f0f86b6
  ```
  - **nmap.002**
  ```bash
  ssh testuser@10.13.37.10 -p 10000
  nmap 10.0.0.0/24
  curl 10.0.0.223
  2ee630a3edf7208e8439c0a8c7b0cf2f
  ```
