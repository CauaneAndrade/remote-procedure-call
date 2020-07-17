No `arquivo cal.x`, especifica-se os procedimentos do Remote Procedure Call
e é o arquivo de entrada do RPCGEN. <br>
O rpcgen cria um programa de servidor executável. É para converter procedimentos locais em procedimentos remotos.

Padrão de criação de programa para o rpcgen compilar:
```c
program MEU_RPC_SERVER {  /* Nome do Programa remoto */
    version PROGRAMA {  /* Declaracao do numero da versao do programa*/
        int faca_alguma_coisa(in) = 1;  /* Procedimento numero 1 */
    } = 1;  /* Definicao da versao do programa */
} = 0x3012225;  /* numero do programa remoto (deve ser unico)*/
```

Em `rpcClient.c`, define-se o programa para o cliente.
Client side remote procedure call interface.
no método **clnt_create** está sendo criado uma rotina de criação de cliente genérica. São suportados os protocolos ***udp*** e ***tcp***.  
O método **clnt_destroy** destroi o identificador do cliente RPC

Em `rpcServer.c`, tem-se os métodos de soma e multiplicação. São chamados pelo cliente e o servidor retorna a resposta

ao chamar o rpcgen passando o arquivo de definição do procedimento RPC é gerado os seguintes arquivos:
- calc.h
- calc_clnt.c
- calc_svc.c
- calc_xdr.c

em `calc.h` tem-se a a definição dos nomes dos métodos *soma_1*, *soma_1_svc* chamados e criados em rpcClient.c e rpcServer.c

