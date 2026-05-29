# Oficina Linux - tmux
Tmux: multiplexador de terminal, atalhos e configurações. Conteúdo produzido para o Dia do Fera PET/Computação @ UFCG


## 1. Como instalar o tmux?

```bash
sudo apt update && sudo apt install tmux   # debian/ubuntu/etc
sudo dnf install tmux                      # fedora/rhel/etc
sudo pacman -S tmux                        # arch
brew install tmux                          # macos
```

## 2. Principais comandos do tmux

```bash
tmux new -s nome_da_sessao           # cria uma nova sessão

tmux a                               # volta para a última sessão

tmux attach -t nome_da_sessao        # volta para uma sessão específica

tmux kill-session -t nome_da_sessao  # encerra uma sessão
``` 

## 3. O coração do tmux `.tmux.conf`

O arquivo `.tmux.conf` é onde se encontra toda as configurações referentes ao
tmux

## 4. Como ativar o mouse?

Dentro do arquivo de configuração do tmux adicione a seguinte configuração:

```.tmux.conf
set -g mouse on
```

Essa configuração irá ativar o mouse globalmente, a partir de agora em todas as sessões
será possível usar o mouse.

## 5. Atalhos

Por padrão a tecla de atalho do tmux é `ctrl + b`, esse atalho é um pouco
desconfortável para se realizar com frequência. Para melhorar isso podemos aplicar
a seguinte configuração:

```.tmux.conf
unbind C-b                 # desativa o prefixo padrão

set-option -g prefix C-a   # adiciona o ctrl + a como prefixo
bind-key C-a send-prefix
```

Agora o atalho `ctrl + a`, que é mais confortável, irá subtituir o `ctrl + b`.

## 6. Personalização

### 6.1 NerdFonts

Uma ótima forma de personalizar o tmux é usar NerdFonts, elas são fontes com
vários símbolos especiais, esses símbolos especiais representam icones, seja
de linguagens, sistemas operacionais etc.

Para baixar nerdfonts acesse [NerdFonts](https://www.nerdfonts.com/font-downloads).
Depois de baixado extraía os arquivos e mova os arquivos `fonte.ttf` para a
pasta reservada `~/.fonts`, caso ela não exista basta criar com o comando `mkdir ~/.fonts`.
Feito isso, vá no terminal e nas preferencias altere a fonte padrão por uma das
nerdfonts que você baixou.

Para buscar os símbolos acesse [NerdFonts - Symbols](https://www.nerdfonts.com/cheat-sheet),
na barra de pesquisa digite o símbolo desejado. Ex.: Python.
Para usar basta copiar e colar no local que desejar.

### 6.2 Personalizando a Status Bar


## Atividade

Crie uma sessão tmux usando o seguinte comando:

```bash
tmux new -s dia_do_fera
```

Divida a tela em formato de T, ao fim você deverá ter 3 painéis, dois
na parte superior e um na parte inferior.

No terminal superior à esquerda copie o seguinte código e cole em um arquivo `relogio.py`:

```python
import time
import os

ano_atual = 2026
nome = input("Digite seu nome: ")
data_nascimento = input("Digite seu ano de nascimento: ")

idade = ano_atual - data_nascimento

while True:
    os.system('clear')
    print(f"O PID desse programa é {os.getpid()}")
    print(f"Olá, {nome}! Você tem {idade} anos e está participando do dia do fera")
    print("Hora atual:", time.strftime("%H:%M:%S"))
    print("\n[Pressione Ctrl+C no terminal para parar]")
    time.sleep(2)

```

Esse código possui um erro! Tente executar esse código no terminal superior à direita
e corrija-o. Salve o arquivo e execute.

No painel da parte inferior execute o comando `top -p pid_do_programa`. Obs.: Para sair do top
basta clicar na tecla 'q'.

Feche o terminal clicando no X da janela.

Abra novamente o terminal e execute:

```bash
tmux attach -t dia_do_fera
```

Veja o que aconteceu.
