Apostila de Comandos Essenciais do Linux

Olá! Bem-vindo(a) à sua jornada no mundo do Linux. Esta apostila foi desenvolvida para guiá-lo(a) pelos comandos mais fundamentais e conceitos cruciais que todo usuário e profissional de cibersegurança precisa dominar. Prepare-se para explorar a linha de comando e desvendar o poder do seu sistema Linux!

Módulo 1: Gerenciamento de Arquivos e Diretórios
1. pwd - Print Working Directory

O que faz: Exibe o caminho completo do diretório atual onde você se encontra no sistema de arquivos. É como perguntar "Onde estou agora?" no terminal.

Exemplo de uso:

code
Bash
download
content_copy
expand_less
pwd

Saída esperada: /home/seu_usuario (se estiver no diretório home) ou /var/log (se estiver no diretório de logs), etc.

Quando usar: Sempre que precisar confirmar sua localização exata no sistema de arquivos.

2. mkdir - Make Directory

O que faz: Cria novos diretórios (pastas) no local especificado.

Sintaxe básica: mkdir [nome_do_diretorio]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
mkdir meus_documentos
mkdir -p projeto/src/main # Cria diretórios aninhados, se não existirem

Quando usar: Para organizar seus arquivos, criar estruturas de projeto ou qualquer necessidade de criar uma nova pasta.

3. touch - Change File Timestamps / Create Empty Files

O que faz:

Cria um arquivo vazio se o arquivo não existir.

Se o arquivo já existir, ele atualiza a data e hora de modificação do arquivo para a hora atual.

Sintaxe básica: touch [nome_do_arquivo]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
touch novo_arquivo.txt
touch relatorio_final.docx # Se o arquivo já existe, atualiza seu timestamp

Quando usar: Para criar rapidamente um arquivo vazio como um placeholder ou para atualizar a data de modificação de um arquivo.

4. ls -l e ls -a - List Directory Contents

O que faz: O comando ls lista o conteúdo de um diretório. As opções -l e -a modificam seu comportamento:

ls -l (long listing format): Exibe uma lista detalhada dos arquivos e diretórios, incluindo permissões, número de links, proprietário, grupo, tamanho, data de última modificação e nome.

ls -a (all): Exibe todos os arquivos, incluindo os arquivos e diretórios ocultos (que começam com um ponto, ex: .bashrc).

Sintaxe básica: ls [opções] [caminho_do_diretorio]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
ls -l            # Lista detalhada do diretório atual
ls -a /home/seu_usuario # Lista todos os arquivos (incluindo ocultos) no diretório home
ls -la           # Combina as duas opções para uma lista detalhada de todos os arquivos

Quando usar: Para inspecionar o conteúdo de diretórios, verificar permissões de arquivos, datas de modificação e identificar arquivos ocultos.

5. rm - Remove

O que faz: Remove (apaga) arquivos ou diretórios. Cuidado: No Linux, arquivos removidos com rm geralmente não vão para uma "lixeira" e são difíceis de recuperar.

Sintaxe básica: rm [opções] [arquivo/diretorio]

Opções comuns:

-f (force): Força a remoção, ignorando arquivos inexistentes e sem pedir confirmação.

-r (recursive): Remove diretórios e seus conteúdos recursivamente. Essencial para remover pastas não vazias.

-i (interactive): Pede confirmação antes de cada remoção.

Exemplo de uso:

code
Bash
download
content_copy
expand_less
rm arquivo_velho.txt       # Remove um arquivo
rm -r pasta_vazia           # Tenta remover uma pasta vazia
rm -r pasta_com_arquivos   # Remove uma pasta e todo o seu conteúdo (cuidado!)
rm -rf pasta_critica       # Remove uma pasta e seu conteúdo sem pedir confirmação (uso extremo, MUITO CUIDADO!)

Quando usar: Para apagar arquivos ou pastas que não são mais necessários.

6. cat - Concatenate and Display Files

O que faz: Lê o conteúdo de arquivos sequencialmente e os exibe na saída padrão (geralmente o terminal). É frequentemente usado para exibir o conteúdo de arquivos de texto pequenos.

Sintaxe básica: cat [arquivo(s)]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
cat meu_texto.txt           # Exibe o conteúdo de meu_texto.txt
cat arquivo1.txt arquivo2.txt # Concatena e exibe o conteúdo de dois arquivos
cat > novo_arquivo.txt      # Cria um novo arquivo e permite digitar o conteúdo (Ctrl+D para salvar)

Quando usar: Para visualizar rapidamente o conteúdo de arquivos de texto, especialmente arquivos de configuração ou logs pequenos.

Módulo 2: Manipulação de Texto e Privilégios
7. grep - Global Regular Expression Print

O que faz: Procura por padrões de texto (strings ou expressões regulares) dentro de arquivos ou da saída de outros comandos. É uma ferramenta poderosa para filtrar informações.

Sintaxe básica: grep [opções] 'padrao' [arquivo(s)]

Opções comuns:

-i (ignore-case): Ignora diferenças entre maiúsculas e minúsculas.

-r (recursive): Pesquisa recursivamente em diretórios.

-v (invert-match): Exibe as linhas que não contêm o padrão.

-n (line-number): Exibe o número da linha junto com o resultado.

-E (extended-regexp) ou egrep: Permite o uso de expressões regulares estendidas.

Exemplo de uso:

code
Bash
download
content_copy
expand_less
grep 'erro' /var/log/syslog     # Procura por "erro" no log do sistema
grep -i 'warning' meus_logs.txt # Procura por "warning" (ignorando maiúsculas/minúsculas)
ps aux | grep 'firefox'         # Filtra processos para encontrar o Firefox

Quando usar: Para encontrar informações específicas em logs, arquivos de configuração ou qualquer saída de texto, sendo fundamental para troubleshooting e análise.

8. sudo - SuperUser DO

O que faz: Permite que usuários autorizados executem comandos com os privilégios de superusuário (root) ou de outro usuário especificado, sem precisar saber a senha do root. É a forma padrão de executar tarefas administrativas no Linux.

Sintaxe básica: sudo [comando]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
sudo apt update              # Atualiza a lista de pacotes (requer privilégios de root)
sudo systemctl restart apache2 # Reinicia o serviço Apache (requer privilégios de root)
sudo apt install neofetch    # Instala o pacote 'neofetch'

Quando usar: Sempre que um comando exigir privilégios administrativos. É uma boa prática usar sudo para tarefas específicas em vez de logar como root diretamente.

9. Logando como Root vs. Usuário Comum (~)

Conceito:

Usuário root: É o superusuário do sistema, com controle total sobre tudo. Seu diretório home padrão é /root.

Usuário Comum (ezequieltop, por exemplo): É um usuário com privilégios limitados, ideal para o uso diário. Seu diretório home padrão é /home/seu_usuario. O caractere ~ (til) é um atalho que representa o diretório home do usuário logado no momento.

Implicações:

Quando você loga como root, seu prompt mostrará algo como root@servidor:~# (o # indica root).

Quando você loga como um usuário comum, seu prompt será parecido com ezequieltop@servidor:~$ (o $ indica usuário comum, e ~ indica que você está no seu diretório home).

Melhores Práticas: É altamente desencorajado usar a conta root para o uso diário ou para tarefas que não exigem privilégios elevados, especialmente em servidores. Em vez disso, use um usuário comum e utilize sudo quando necessário. Isso minimiza o risco de danos acidentais ao sistema ou de exploração de vulnerabilidades.

Módulo 3: Monitoramento de Sistema
10. top - Display Linux Processes

O que faz: Fornece uma visualização dinâmica e em tempo real dos processos em execução no sistema. Mostra o uso da CPU, memória, lista de processos, seus IDs (PID), quem os executou, etc.

Exemplo de uso:

code
Bash
download
content_copy
expand_less
top

Dentro do top:

Pressione 1: Alterna a exibição para mostrar o uso individual de cada núcleo de CPU, em vez de um total agregado. Útil para identificar gargalos em núcleos específicos.

Pressione q: Sai do programa top.

Quando usar: Para monitorar o desempenho do sistema, identificar processos que estão consumindo muitos recursos (CPU ou memória) e solucionar problemas de lentidão.

11. df -h - Disk Free

O que faz: Exibe a quantidade de espaço em disco livre e usado em todos os sistemas de arquivos montados.

Opção -h (human-readable): Formata os tamanhos em unidades mais fáceis de ler (GB, MB, etc.).

Exemplo de uso:

code
Bash
download
content_copy
expand_less
df -h

Saída esperada (exemplo):

code
Code
download
content_copy
expand_less
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   20G   75G  21% /
tmpfs           3.9G    0  3.9G   0% /dev/shm
/dev/sdb1       500G  100G  400G  20% /data

Quando usar: Para verificar o espaço em disco disponível, identificar volumes que estão ficando cheios e gerenciar o armazenamento.

12. free -m - Display Free and Used Memory

O que faz: Exibe a quantidade total, usada e livre de memória RAM e swap no sistema.

Opção -m: Mostra os valores em megabytes (MB). Outras opções incluem -g (gigabytes) ou -h (human-readable, que escolhe a melhor unidade).

Exemplo de uso:

code
Bash
download
content_copy
expand_less
free -m

Saída esperada (exemplo):

code
Code
download
content_copy
expand_less
total        used        free      shared  buff/cache   available
Mem:           7858        1234        5678         123         945        6000
Swap:          2047           0        2047

Quando usar: Para monitorar o uso da memória RAM, verificar se o sistema está com pouca memória e diagnosticar problemas de desempenho relacionados à memória.

Módulo 4: Rede e Conectividade
13. ifconfig - Configure Network Interfaces

O que faz: Exibe informações detalhadas sobre as interfaces de rede do sistema (placas de rede). Ele mostra endereços IP, máscaras de rede, endereços MAC, estado da interface (up/down), pacotes enviados/recebidos, etc.

Nota: Em sistemas Linux mais recentes, o comando ip a (ou ip address) é a ferramenta moderna e preferida, mas ifconfig ainda é amplamente encontrado.

Exemplo de uso:

code
Bash
download
content_copy
expand_less
ifconfig
# Ou, em sistemas modernos:
ip a

Quando usar: Para verificar a configuração de rede do seu sistema, encontrar seu endereço IP, solucionar problemas de conectividade e garantir que as interfaces de rede estão ativas.

14. ping - Packet Internet Groper

O que faz: Envia pacotes de dados (ICMP echo requests) para um host de destino e mede o tempo que leva para receber uma resposta. É usado para testar a conectividade de rede entre dois hosts e medir a latência.

Sintaxe básica: ping [destino]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
ping google.com       # Pinga o servidor do Google pelo nome
ping 8.8.8.8          # Pinga o servidor DNS do Google pelo IP
ping -c 4 192.168.1.1 # Envia 4 pacotes para um roteador local e para

Quando usar: Para verificar se um servidor ou site está online e acessível, diagnosticar problemas de rede (como perda de pacotes ou alta latência).

15. wget - Non-interactive Network Downloader

O que faz: Uma ferramenta de linha de comando para baixar arquivos da web. É "não interativo" porque pode funcionar em segundo plano, mesmo se você fechar a sessão do terminal.

Sintaxe básica: wget [url]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
wget https://example.com/arquivo.zip    # Baixa um arquivo ZIP
wget -r -l1 https://www.example.com     # Baixa recursivamente uma página (nível 1)

Quando usar: Para baixar arquivos de um servidor web ou FTP de forma programática ou em scripts.

16. curl - Client URL

O que faz: Uma ferramenta versátil para transferir dados de ou para um servidor, usando uma vasta gama de protocolos (HTTP, HTTPS, FTP, etc.). Ao contrário do wget que foca em baixar para um arquivo, o curl por padrão exibe o conteúdo na saída padrão (terminal).

Sintaxe básica: curl [opções] [url]

Opções comuns:

-O (remote-name): Salva o arquivo com o nome original.

-o (output): Salva o arquivo com um nome específico.

-L (location): Segue redirecionamentos.

-I (head): Exibe apenas os cabeçalhos HTTP.

Exemplo de uso:

code
Bash
download
content_copy
expand_less
curl https://example.com/               # Exibe o HTML da página no terminal
curl -O https://example.com/data.json   # Baixa o arquivo data.json
curl -I https://example.com             # Exibe apenas os cabeçalhos HTTP

Quando usar: Para interagir com APIs RESTful, testar serviços web, baixar arquivos de forma programática e verificar cabeçalhos HTTP.

17. netstat -tulnp | grep 8080 - Checar Portas em Uso

O que faz: Este é um comando combinado.

netstat (Network Statistics): Exibe conexões de rede, tabelas de roteamento, estatísticas de interface, etc.

-t: Conexões TCP

-u: Conexões UDP

-l: Somente portas em "listen" (escutando)

-n: Numérico (não resolve nomes de host/porta)

-p: Exibe o PID (ID do processo) e o nome do programa

| (pipe): Redireciona a saída do netstat como entrada para o grep.

grep 8080: Filtra as linhas que contêm "8080".

Exemplo de uso:

code
Bash
download
content_copy
expand_less
netstat -tulnp | grep 8080 # Mostra processos escutando na porta 8080
netstat -tulnp | grep ssh  # Mostra processos SSH (normalmente na porta 22)

Quando usar: Para identificar quais processos estão escutando em quais portas, diagnosticar conflitos de portas, verificar se um serviço está realmente ativo e escutando na porta esperada.

Módulo 5: Gerenciamento de Pacotes e Shell Scripting
18. apt update e apt upgrade - Advanced Package Tool

Contexto: apt é a ferramenta de linha de comando para gerenciar pacotes de software em distribuições baseadas em Debian (como Ubuntu, Mint, Kali).

apt update:

O que faz: Sincroniza a lista de pacotes disponíveis com os repositórios (servidores) configurados no seu sistema. Ele não instala ou atualiza software, apenas atualiza o "catálogo" de pacotes que podem ser instalados.

Exemplo de uso: sudo apt update (sempre requer sudo)

apt upgrade:

O que faz: Depois de executar apt update, este comando instala as novas versões dos pacotes que já estão instalados no seu sistema. Ele fará o download e aplicará as atualizações de segurança e melhorias.

Exemplo de uso: sudo apt upgrade (sempre requer sudo)

Quando usar:

apt update: Regularmente (diariamente/semanalmente) para manter seu catálogo de pacotes atualizado.

apt upgrade: Para aplicar atualizações de segurança e manter seu sistema com as últimas versões de software.

19. apt install - Advanced Package Tool

O que faz: Instala novos pacotes de software a partir dos repositórios configurados.

Sintaxe básica: sudo apt install [nome_do_pacote]

Exemplo de uso:

code
Bash
download
content_copy
expand_less
sudo apt install firefox       # Instala o navegador Firefox
sudo apt install build-essential # Instala pacotes necessários para compilação de software
sudo apt install python3-pip   # Instala o gerenciador de pacotes pip para Python 3

Quando usar: Para adicionar novos programas ou ferramentas ao seu sistema.

20. O que é e como criar um Shell Script simples

O que é um Shell Script?

Um shell script é um arquivo de texto que contém uma sequência de comandos Linux (os mesmos que você digitaria no terminal). O shell (Bash, Zsh, etc.) interpreta e executa esses comandos um após o outro.

Para que serve: Automação de tarefas repetitivas, execução de sequências complexas de comandos, criação de utilitários personalizados, gerenciamento de sistemas e muito mais. É a espinha dorsal de muitas operações em ambientes Linux.

Como criar um Shell Script simples:

Crie um arquivo: Use touch ou seu editor de texto favorito (ex: nano, vim) para criar um novo arquivo com a extensão .sh (convenção, não obrigatório, mas ajuda a identificar). Ex: meu_script.sh

Adicione o Shebang: A primeira linha do script deve ser o "shebang" (#!), que informa ao sistema qual interpretador de shell deve ser usado para executar o script. Para Bash, é #!/bin/bash.

Escreva os comandos: Adicione os comandos Linux, um por linha.

Dê permissão de execução: Por padrão, scripts não são executáveis. Você precisa dar permissão com chmod.

Execute o script:

Exemplo de Criação e Execução:

Crie o arquivo saudacao.sh:

code
Bash
download
content_copy
expand_less
nano saudacao.sh

Adicione este conteúdo ao saudacao.sh:

code
Bash
download
content_copy
expand_less
#!/bin/bash
# Este é um script simples de saudação
NOME="Ezequiel"
echo "Olá, $NOME! Bem-vindo ao mundo dos shell scripts."
echo "Hoje é $(date +%F)."
echo "Seu diretório atual é: $(pwd)"

Salve e feche o editor.

Dê permissão de execução:

code
Bash
download
content_copy
expand_less
chmod +x saudacao.sh

Execute o script:

code
Bash
download
content_copy
expand_less
./saudacao.sh

Saída esperada:

code
Code
download
content_copy
expand_less
Olá, Ezequiel! Bem-vindo ao mundo dos shell scripts.
Hoje é 2023-10-27.
Seu diretório atual é: /home/seu_usuario

Quando usar: Para automatizar tarefas diárias, criar ferramentas personalizadas, compilar programas, instalar configurações e muito mais. É um passo crucial para se tornar um usuário Linux avançado ou um profissional de cibersegurança eficiente.

Espero que esta formatação e as explicações detalhadas ajudem você a aprofundar seu conhecimento em cada um desses comandos e conceitos! O próximo passo é praticar com os exercícios que você solicitou.

code
Code
download
content_copy
expand_less
