# Oficina Linux - tmux
Tmux: multiplexador de terminal, atalhos e configurações. Conteúdo produzido para o Dia do Fera PET/Computação @ UFCG


## 1. Como instalar o tmux?

```bash
sudo apt update && sudo apt install tmux   # debian/ubuntu/etc
sudo dnf install tmux                      # fedora/rhel/etc
sudo pacman -S tmux                        # arch
brew install tmux                          # macos
```

## 2. O coração do tmux `.tmux.conf`

O arquivo `.tmux.conf` é onde se encontra toda as configurações referentes ao
tmux

## 3. Como ativar o mouse?

Dentro do arquivo de configuração do tmux adicione a seguinte configuração:

```.tmux.conf
set -g mouse on
```

Essa configuração irá ativar o mouse globalmente, a partir de agora em todas as sessões
será possível usar o mouse.

## 4. Atalhos

Por padrão a tecla de atalho do tmux é `ctrl + b`, esse atalho é um pouco
desconfortável para se realizar com frequência. Para melhorar isso podemos aplicar
a seguinte configuração:

```.tmux.conf
unbind C-b                 # desativa o prefixo padrão

set-option -g prefix C-a   # adiciona o Ctrl + a como prefixo
bind-key C-a send-prefix
```

Agora o comando `ctrl + a`, que é mais confortável, irá subtituir o `ctrl + b`.




## Atividade

Crie uma sessão tmux usando o seguinte comando:

```bash
tmux new -s dia_do_fera
```

Divida a tela em formato de T, ao fim você deverá ter 3 painéis, dois
na parte superior e um na parte inferior.

Copie o seguinte código e cole em um arquivo `relogio.py`:

```python
import time
import os

nome = input("Digite seu nome: ")

while True:
    os.system('clear')
    print(f"Olá, {nome}!")
    print("Hora atual:", time.strftime("%H:%M:%S"))
    print("\n[Pressione Ctrl+C no terminal ao lado para parar]")
    time.sleep(2)

```

Esse código possui um erro! Tente executar esse código no terminal ao lado
e descubra como corrigir.

Salve o arquivo e execute.

No painel da parte inferior execute o comando `top`.

Feche o terminal clicando no X da janela.

Abra novamente o terminal e execute:

```bash
tmux attach -t dia_do_fera
```

Veja o que aconteceu.
