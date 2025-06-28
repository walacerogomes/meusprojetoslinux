# Comandos Essenciais de Linux

Este arquivo documenta os comandos Linux que estou aprendendo e utilizando, organizados por categoria para facilitar a consulta e o entendimento.

---

## 1. Manipulação de Arquivos e Diretórios

* **`ls` - Listar conteúdo de diretórios**
    * **Uso:** Exibe os arquivos e diretórios dentro de um caminho especificado.
    * **Exemplos:**
        * `ls`: Lista o conteúdo do diretório atual.
        * `ls -l`: Lista com detalhes (permissões, proprietário, tamanho, data).
        * `ls -a`: Lista todos os arquivos, incluindo ocultos.
        * `ls -lh`: Lista com detalhes e tamanho "human-readable" (ex: 1.5K, 2M).
    * **Observação:** Essencial para navegar e inspecionar o sistema de arquivos.

* **`cd` - Mudar de diretório**
    * **Uso:** Navega entre os diretórios do sistema de arquivos.
    * **Exemplos:**
        * `cd /home/usuario/documentos`: Vai para um caminho absoluto.
        * `cd ..`: Volta um nível no diretório.
        * `cd ~`: Vai para o diretório home do usuário atual.
        * `cd -`: Volta para o diretório anterior.
    * **Observação:** A base da navegação no terminal.

* **`mv` - Mover ou renomear arquivos/diretórios**
    * **Uso:** Move um arquivo ou diretório de um local para outro, ou renomeia.
    * **Exemplos:**
        * `mv arquivo.txt /home/usuario/backup/`: Move `arquivo.txt` para o diretório `backup`.
        * `mv nome_antigo.txt nome_novo.txt`: Renomeia `nome_antigo.txt` para `nome_novo.txt`.
    * **Observação:** Útil para organizar o sistema de arquivos.

* **`cp` - Copiar arquivos/diretórios**
    * **Uso:** Cria uma cópia de um arquivo ou diretório.
    * **Exemplos:**
        * `cp arquivo.txt copia_arquivo.txt`: Cria uma cópia do arquivo no mesmo diretório.
        * `cp -r diretorio_origem diretorio_destino`: Copia um diretório recursivamente.
    * **Observação:** Cuidado ao usar, pode sobrescrever arquivos existentes.

* **`rm` - Remover arquivos/diretórios**
    * **Uso:** Deleta arquivos ou diretórios.
    * **Exemplos:**
        * `rm arquivo.txt`: Deleta o arquivo.
        * `rm -r diretorio_vazio`: Deleta um diretório vazio.
        * `rm -rf diretorio_com_conteudo`: Força a remoção de um diretório e seu conteúdo (USE COM EXTREMA CAUTELA!).
    * **Observação:** Arquivos removidos com `rm` geralmente não vão para uma "lixeira" e são difíceis de recuperar.

* **`mkdir` - Criar diretórios**
    * **Uso:** Cria um novo diretório.
    * **Exemplos:**
        * `mkdir novo_diretorio`: Cria um diretório no local atual.
        * `mkdir -p caminho/do/diretorio/aninhado`: Cria diretórios aninhados se não existirem.

* **`touch` - Criar arquivo vazio ou atualizar timestamp**
    * **Uso:** Cria um arquivo novo e vazio, ou atualiza a data de modificação de um arquivo existente.
    * **Exemplo:** `touch meu_arquivo.txt`

---

## 2. Gerenciamento de Pacotes

* **`yum` / `dnf` - Gerenciador de pacotes (Red Hat, CentOS, Fedora)**
    * **Uso:** Instala, atualiza e remove pacotes de software. `dnf` é o sucessor moderno de `yum`.
    * **Exemplos:**
        * `sudo yum update`: Atualiza todos os pacotes instalados no sistema.
        * `sudo yum install nome_do_pacote`: Instala um novo pacote.
        * `sudo yum remove nome_do_pacote`: Remove um pacote.
        * `sudo yum search termo`: Busca por pacotes que contenham o termo.
    * **Observação:** Para sistemas baseados em Debian/Ubuntu, o comando equivalente é `apt` ou `apt-get`.

* **`apt` / `apt-get` - Gerenciador de pacotes (Debian, Ubuntu, Mint)**
    * **Uso:** Instala, atualiza e remove pacotes de software.
    * **Exemplos:**
        * `sudo apt update`: Atualiza a lista de pacotes disponíveis.
        * `sudo apt upgrade`: Atualiza todos os pacotes instalados.
        * `sudo apt install nome_do_pacote`: Instala um novo pacote.
        * `sudo apt remove nome_do_pacote`: Remove um pacote.
        * `sudo apt search termo`: Busca por pacotes.
    * **Observação:** O `apt` é uma versão mais amigável do `apt-get` para o uso diário.

---

## 3. Permissões de Arquivos e Diretórios

* **`chmod` - Modificar permissões de arquivos/diretórios**
    * **Uso:** Controla quem pode ler, escrever e executar arquivos e diretórios.
    * **Conceito:** Permissões para (u)usuário, (g)grupo, (o)outros. Permissões: (r)leitura=4, (w)escrita=2, (x)execução=1.
    * **Exemplos (Notação Octal):**
        * `chmod 755 script.sh`: `rwx` para o proprietário, `rx` para grupo e outros. (executável para todos)
        * `chmod 644 arquivo.txt`: `rw` para o proprietário, `r` para grupo e outros. (leitura para todos, escrita só para o proprietário)
    * **Exemplos (Notação Simbólica):**
        * `chmod u+x script.sh`: Adiciona permissão de execução para o proprietário.
        * `chmod go-w arquivo.txt`: Remove permissão de escrita para grupo e outros.
    * **Observação:** Essencial para segurança e funcionamento correto de scripts e aplicações.

* **`chown` - Mudar proprietário de arquivo/diretório**
    * **Uso:** Altera o usuário proprietário e/ou grupo de um arquivo ou diretório.
    * **Exemplos:**
        * `sudo chown usuario arquivo.txt`: Muda o proprietário para `usuario`.
        * `sudo chown usuario:grupo arquivo.txt`: Muda o proprietário e o grupo.
        * `sudo chown -R usuario:grupo /caminho/do/diretorio`: Muda recursivamente.
    * **Observação:** Requer permissões de root (sudo).

* **`chgrp` - Mudar grupo de arquivo/diretório**
    * **Uso:** Altera apenas o grupo proprietário de um arquivo ou diretório.
    * **Exemplo:** `sudo chgrp novo_grupo arquivo.txt`

---

## 4. Rede e Conectividade (Sua área de interesse!)

* **`ssh` - Secure Shell (Acesso Remoto Seguro)**
    * **Uso:** Conecta-se a um servidor remoto de forma segura.
    * **Exemplos:**
        * `ssh usuario@ip_do_servidor`: Conecta-se usando nome de usuário e IP.
        * `ssh -p 2222 usuario@ip_do_servidor`: Conecta-se em uma porta diferente da padrão (22).
        * `ssh -i ~/.ssh/minha_chave.pem usuario@ip_do_servidor`: Conecta-se usando uma chave SSH.
    * **Observação:** Fundamental para administrar servidores remotos. Pratique com máquinas virtuais ou em serviços de nuvem gratuitos.

* **`scp` - Secure Copy (Cópia Segura de Arquivos)**
    * **Uso:** Copia arquivos entre máquinas locais e remotas de forma segura usando SSH.
    * **Exemplos:**
        * `scp arquivo_local.txt usuario@ip_do_servidor:/caminho/destino/`: Copia arquivo local para remoto.
        * `scp usuario@ip_do_servidor:/caminho/origem/arquivo_remoto.txt .`: Copia arquivo remoto para o diretório atual local.
        * `scp -r diretorio_local/ usuario@ip_do_servidor:/caminho/destino/`: Copia diretório recursivamente.
    * **Observação:** Extremamente útil para transferir arquivos para servidores.

* **`ping` - Testar Conectividade de Rede**
    * **Uso:** Envia pacotes ICMP para um host e mede o tempo de resposta, verificando se está acessível.
    * **Exemplo:** `ping google.com`
    * **Observação:** Ferramenta básica para diagnóstico de rede.

* **`ifconfig` ou `ip a` - Configuração de Interfaces de Rede**
    * **Uso:** Exibe e configura informações sobre as interfaces de rede do sistema. `ip a` é o comando mais moderno e preferido em muitos sistemas.
    * **Exemplos:**
        * `ifconfig`: Exibe todas as interfaces de rede e seus IPs.
        * `ip a`: Idem ao `ifconfig`, mas com mais detalhes e formato moderno.
    * **Observação:** Essencial para verificar o endereço IP da sua máquina.

* **`netstat` - Estatísticas de Rede**
    * **Uso:** Exibe conexões de rede, tabelas de roteamento, estatísticas de interface, etc.
    * **Exemplo:** `netstat -tunlp` (mostra portas abertas e programas que as usam - UDP, TCP, numeric, listening, programs)
    * **Observação:** Útil para depurar problemas de conectividade e segurança.

---

## 5. Processos e Monitoramento

* **`ps` - Listar Processos**
    * **Uso:** Exibe os processos em execução no sistema.
    * **Exemplos:**
        * `ps aux`: Mostra todos os processos de todos os usuários com detalhes (user, pid, cpu, mem, etc.).
        * `ps -ef`: Outro formato comum para listar todos os processos.
    * **Observação:** Usado para identificar processos.

* **`top` / `htop` - Monitoramento Interativo de Processos**
    * **Uso:** Exibe uma lista em tempo real dos processos em execução, uso de CPU, memória, etc. `htop` é uma versão mais amigável e com mais recursos.
    * **Exemplo:** `top` ou `htop` (se instalado)
    * **Observação:** Ótimo para identificar o que está consumindo recursos.

* **`kill` - Encerrar Processos**
    * **Uso:** Envia um sinal para um processo, geralmente para encerrá-lo.
    * **Exemplos:**
        * `kill PID`: Envia o sinal SIGTERM (solicita encerramento).
        * `kill -9 PID`: Envia o sinal SIGKILL (encerra forçadamente, use com cautela).
    * **Observação:** É preciso saber o PID (ID do Processo) para usar.

---

## Próximos Passos e Áreas de Estudo:

* **Curingas e comandos diversos.
