# Instalar o serviço
```bash
$ sudo apt-get update
$ sudo apt-get install rpcbind
```

# Ordem de compilaçao dos programas
```bash
rpcgen calc.x
gcc -c calc_clnt.c
gcc -c calc_svc.c
gcc -c calc_xdr.c
```

```bash
gcc -c rpcClient.c
gcc -c rpcServer.c
```

```bash
gcc -o client calc_clnt.o calc_xdr.o rpcClient.o
gcc -o server calc_svc.o calc_xdr.o rpcServer.o
```

Em um terminal executar o servidor + ip
```bash
./server 127.0.0.1
```

Em outro terminal ou computador, executar o client + ip
```bash
./client 127.0.0.1
```