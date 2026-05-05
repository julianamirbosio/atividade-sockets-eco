# Relatório — Atividade Prática: Sockets TCP

**Disciplina:** Sistemas Distribuídos
**Trio:** Juliana Miranda Bosio / Sofia Bianchi Schmitz / Vinícios Rosa Buzzi
**Data:** 05/05/26

---

## Nível 1 — Inspecionar o código

### 1.1 Servidor (`servidor.py`)

Descreva com suas palavras o que cada chamada abaixo faz e por que ela
é necessária:

| Chamada | O que ela faz? |
|---------|---------------|
| `socket.socket(AF_INET, SOCK_STREAM)` | Instancia o objeto socket passando a família de enderecos (AF_INET) e define o protocolo de comunicacão TCP (SOCKET_STREAM)|
| `servidor_socket.bind((HOST, PORTA))` | Associa ao objeto socket uma porta e um endereco |
| `servidor_socket.listen(5)` | O socket entra em modo escuta, e pode armazenar até 5 clientes fila |
| `servidor_socket.accept()` | Espera a conexão do cliente, retornando um novo socket e a informacão do endereco quando aceito |
| `conn.recv(TAMANHO_BUFFER)` | Recebe uma mensagem codificada do cliente |
| `conn.sendall(resposta.encode("utf-8"))` | Envia para todos os clientes a resposta codificada |
| `conn.close()` | Fecha a conexão com o cliente |

### 1.2 Cliente (`cliente.py`)

| Chamada | O que ela faz? |
|---------|---------------|
| `socket.socket(AF_INET, SOCK_STREAM)` | Instancia o objeto socket passando a família de enderecos (AF_INET) e define o protocolo de comunicacão TCP (SOCKET_STREAM)|
| `cliente_socket.connect((HOST_SERVIDOR, PORTA_SERVIDOR))` | Conecta com o servidor |
| `cliente_socket.sendall(mensagem.encode("utf-8"))` | Envia todos os bytes da mensagem, repetidamente até que todos os dados cheguem ao servidor ou ocorra um erro |
| `cliente_socket.recv(TAMANHO_BUFFER)` | Aguarda a resposta enviada pelo servidor |

### 1.3 Rede e contêineres

Por que o cliente usa o hostname `"servidor"` em vez de `"localhost"`
para se conectar? O que aconteceria se usasse `"localhost"`?

> _Resposta:_ O hostname da rede garante que a aplicacão encontre o servidor correto, independentemente de onde esteja. Logo, se usássemos localhost ele não encontraria aplicacões que estivessem hospedados em máquinas diferentes.

---

## Nível 2 — Modificar o servidor

Descreva as mudanças que você fez no `servidor.py` para:

1. Devolver a mensagem **em maiúsculas**:

   > _O que foi alterado e por quê:_ Utilizamos a funcão .upper() sobre a string enviada (mensagem).

2. Exibir no log o **contador de mensagens recebidas** acumulado:

   > _O que foi alterado e por quê:_ Ao receber a mensagem, incrementamos o contador e printamos no log do servidor.

Após a modificação, você precisou rodar `docker compose up --build`.
Por que o `--build` é necessário aqui?

> _Resposta:_ Sim, pois é necessário recriar as imagens do docker para refletir as mudancas feitas no código do servidor.

---

## Observações livres

Anote aqui qualquer comportamento inesperado que observaram, erros que
apareceram e como resolveram, ou dúvidas que ainda têm:

>

---

## Dúvida para a próxima aula

Escreva **uma pergunta** que surgiu durante a atividade e que vocês
gostariam de ver respondida na aula seguinte:

> Vinícios: Como grandes aplicacões lidam com as mudancas no código fonte dos servidores em tempo real sem afetar a usabilidade dos clientes?


