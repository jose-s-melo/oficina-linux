# Oficina Linux - tmux
Tmux: multiplexador de terminal, atalhos e configurações. Conteúdo produzido para o Dia do Fera PET/Computação @ UFCG


## 1. Como instalar o tmux?

```bash
sudo apt update && sudo apt install tmux   # debian/ubuntu/etc
sudo dnf install tmux                      # fedora/rhel/etc
sudo pacman -S tmux                        # arch
brew install tmux                          # macos
```

---

## 2. Principais comandos do tmux

```bash
tmux new -s nome_da_sessao           # cria uma nova sessão

tmux a                               # volta para a última sessão

tmux attach -t nome_da_sessao        # volta para uma sessão específica

tmux kill-session -t nome_da_sessao  # encerra uma sessão
``` 

---

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

---

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

## 5.1 Mapa de atalhos do tmux

---

### 5.1.1 Janelas

| Ação | Atalho |
|------|---------|
| Nova janela | `Ctrl+a c` |
| Próxima janela | `Ctrl+a n` |
| Janela anterior | `Ctrl+a p` |
| Última janela usada | `Ctrl+a l` |
| Ir para janela 0–9 | `Ctrl+a 0` até `Ctrl+a 9` |
| Renomear janela | `Ctrl+a ,` |
| Listar janelas | `Ctrl+a w` |
| Fechar janela | `exit` |

---

### 5.1.2 Painéis

| Ação | Atalho |
|------|---------|
| Dividir verticalmente | `Ctrl+a =` |
| Dividir horizontalmente | `Ctrl+a -` |
| Ir para painel esquerdo | `Ctrl+a ←` |
| Ir para painel direito | `Ctrl+a →` |
| Ir para painel acima | `Ctrl+a ↑` |
| Ir para painel abaixo | `Ctrl+a ↓` |
| Alternar entre painéis | `Ctrl+a o` |
| Mostrar números dos painéis | `Ctrl+a q` |
| Fechar painel | `exit` |
| Trocar painel de lugar | `Ctrl+a }` ou `Ctrl+a {` |
| Tornar painel uma janela | `Ctrl+a !` |
| Alternar layouts | `Ctrl+a Space` |
| Zoom no painel | `Ctrl+a z` |

---

### 5.1.3 Redimensionamento

| Ação | Atalho |
|------|---------|
| Entrar no prompt de comando | `Ctrl+a :` |
| Redimensionar painel | `resize-pane -L/R/U/D N` |

Exemplo:

```tmux
resize-pane -L 5
resize-pane -R 5
resize-pane -U 5
resize-pane -D 5
```

---

### 5.1.4 Copy Mode

| Ação | Atalho |
|------|---------|
| Entrar em copy mode | `Ctrl+a [` |
| Colar buffer | `Ctrl+a ]` |
| Sair do copy mode | `q` ou `Esc` |
| Iniciar busca | `/` |
| Próxima ocorrência | `n` |
| Ocorrência anterior | `N` |

---

### 5.1.5 Informações e Ajuda

| Ação | Atalho |
|------|---------|
| Listar atalhos | `Ctrl+a ?` |
| Mostrar relógio | `Ctrl+a t` |
| Mostrar informações da sessão | `Ctrl+a s` |
| Escolher janela visualmente | `Ctrl+a w` |

---

## 5.2 Atalhos Mais Usados no Dia a Dia

| Ação | Atalho |
|------|---------|
| Detach | `Ctrl+a d` |
| Nova janela | `Ctrl+a c` |
| Split vertical | `Ctrl+a =` |
| Split horizontal | `Ctrl+a -` |
| Navegar entre painéis | `Ctrl+a` + setas |
| Zoom painel | `Ctrl+a z` |
| Copy mode | `Ctrl+a [` |
| Colar | `Ctrl+a ]` |
| Listar janelas | `Ctrl+a w` |
| Ajuda | `Ctrl+a ?` |

---

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

---

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

Feche o aplicativo do terminal clicando no X da janela.

Abra novamente o terminal e execute:

```bash
tmux attach -t dia_do_fera
```

Veja o que aconteceu.
