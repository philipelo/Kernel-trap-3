
# 🔒 Linux Kernel Trap: Armadilha Invisível no Núcleo

Monitoramento passivo e avançado diretamente no kernel do Linux, com foco em detectar técnicas de evasão e execução escondida. Este projeto simula uma estratégia real de elite para defesa digital silenciosa, sendo altamente furtivo e sem alertas visíveis ao atacante.

Usa camadas do `auditd` para capturar sinais anômalos de execução, com base em manipulações típicas de rootkits, acesso a `/dev/mem`, `syscalls` modificadas e chamadas ocultas.

## 🛠️ Funcionalidades

* Monitoramento passivo de execução em `/dev/mem`, `/proc/kallsyms` e `syscalls`.
* Alerta silencioso quando houver tentativa de esconder processos.
* Leitura de eventos diretamente da `syscall table` para detectar `hijack`.
* Modo `stealth` total: nenhum processo visível é criado.
* Sem scripts – tudo via comandos nativos e `audit rules` especiais.

## 🚀 Exemplo de uso real

Detecta em tempo real quando alguém executa um binário renomeado para se parecer com um sistema confiável, como:

auditctl -a always,exit -F arch=b64 -S execve -F exe=/usr/bin/bash -k bash_fake
