# Como configurar/instalar o `Tor Browser` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar o `Tor Browser` no `Linux Ubuntu`.

## _Abstract_

_In this document are contained the main commands and settings to set up/install the `Tor Browser` on `Linux Ubuntu`._


## Descrição [2]

### `Tor Browser`

O "Tor Browser" é um navegador da web projetado para fornecer aos usuários anonimato e privacidade online. Ele é baseado no Mozilla Firefox e incorpora a rede Tor (The Onion Router) para rotear o tráfego da Internet por uma série de servidores voluntários, tornando difícil a rastreabilidade da atividade online do usuário. O Tor Browser é usado por pessoas que buscam navegar na web de forma anônima, contornar a censura da Internet e proteger sua privacidade contra a vigilância online. Ele inclui recursos como bloqueio de scripts e cookies de terceiros para aumentar a segurança e a privacidade do usuário. No entanto, é importante observar que o Tor Browser não é uma solução à prova de falhas e requer práticas de segurança adequadas para proteger completamente a identidade online do usuário. Seu uso é frequente entre jornalistas, ativistas de direitos humanos e qualquer pessoa preocupada com a privacidade online.

## 1. Como configurar/instalar/usar o `Tor Browser` no `Linux Ubuntu` [1]

Para configurar/instalar/usar o `Tor Browser` no `Linux Ubuntu`, você pode seguir estes passos:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

    2.2 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.3 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: `sudo apt update -y`

    2.4 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  `sudo apt list --upgradable`

    2.5 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update -y`. Digite o seguinte comando e pressione `Enter`: `sudo apt full-upgrade -y`

    2.6 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando: `sudo apt autoremove -y`

    2.7 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando: `sudo apt autoclean`

### 1.1 Configurar/Instalar o `Tor Browser`

1. **Instalação Manual:** Tente instalar o `Tor Browser` manualmente:

    1.1 Acesse o site oficial do `Tor Browser` em um navegador comum: https://www.torproject.org/.

    1.2 Baixe a versão mais recente do `Tor Browser` para `Linux Ubuntu`.

    1.3 Abra um `Terminal Emulator` e use os comandos `cd` para navegar até o diretório onde o arquivo foi baixado: `cd ~/Downloads`

    1.4 Extraia o arquivo com o comando `tar -xvJf tor-browser-linux64-*.tar.xz` (substitua o * pelo número da versão baixada).

    1.5 Navegue até a pasta do navegador Tor extraído com `cd ~/Downloads/tor-browser/`

    1.6 **Torne o arquivo `.desktop` executável:** `chmod +x ~/Downloads/tor-browser/start-tor-browser.desktop`

    1.7 Execute o navegador Tor com `./start-tor-browser.desktop.`

    1.8 Para copiar a pasta do `Tor Browser` para o novo local, você pode usar o comando `cp` no terminal: `sudo cp -r ~/Downloads/tor-browser /usr/local/bin/tor-browser/`

    1.9 **Torne o arquivo `.desktop` executável:** `sudo chmod +x /usr/local/bin/tor-browser/start-tor-browser.desktop`

    1.10 **Ajuste as permissões:** Abra um terminal e use o comando `chown` para mudar a propriedade da pasta e seu conteúdo para o seu usuário. Substitua edenedfsls pelo seu nome de usuário real e `tor-browser` pelo nome correto da pasta se for diferente. Aqui está o comando: `sudo chown -R edendenis:edendenis /usr/local/bin/tor-browser/`

    1.11 **Verifique as permissões:** Depois de mudar a propriedade da pasta, verifique se as permissões permitem a leitura e execução do `Tor Browser`. O seguinte comando irá configurar as permissões de forma adequada: `sudo chmod -R 755 /usr/local/bin/tor-browser/`

    Este comando define as permissões para leitura e execução para o usuário, grupo e outros, o que é normalmente suficiente para a maioria das aplicações.

    E então, você atualizaria o arquivo .desktop para usar o novo caminho.


### 1.2 Criar um atalho para o `Tor Browser` no `Linux Xubuntu`

Para criar um atalho para o `Tor Browser` no `Linux Xubuntu`, você pode seguir os passos abaixo. Esses passos vão criar um atalho que você pode usar a partir do seu ambiente de `desktop`:

1. **Crie um arquivo de atalho:** Vá até o seu `desktop` ou onde você quer criar o atalho e abra um terminal: `cd ~/Desktop`

2. **Use um editor de texto para criar o atalho:** Crie um novo arquivo `.desktop` usando um editor de texto da sua escolha. Por exemplo, você pode usar o `nano` para isso: `sudo nano tor-browser.desktop`

3. **Adicione o conteúdo ao arquivo de atalho:** No editor de texto, insira o seguinte conteúdo, adaptando os caminhos se necessário:

    ```
    [Desktop Entry]
    Version=1.0
    Type=Application
    Name=Tor Browser
    Exec=/usr/local/bin/tor-browser/Browser/start-tor-browser --detach
    Icon=/usr/local/bin/tor-browser/Browser/icons/128x128/tor-browser.png
    Path=/usr/local/bin/tor-browser/Browser/
    Comment=Tor Browser is free software and an open network that helps you defend against traffic analysis, a form of network surveillance that threatens personal freedom and privacy.
    Categories=Network;WebBrowser;
    Keywords=web;browser;privacy;anonymity;tor;
    ```

    Assegure-se de que o caminho no campo `Exec` e `Icon` corresponde ao local onde o `Tor Browser` está instalado no seu sistema. O campo `Path` deve ser o diretório que contém o script `start-tor-browser`.

4. **Salve o arquivo:** No nano, você pode salvar e sair pressionando `Ctrl + X`, depois `Y` para confirmar as alterações, e `Enter` para finalizar.

5. **Torne o atalho executável:** De volta ao terminal, dê permissão de execução para o arquivo `.desktop` que você acabou de criar: `sudo chmod +x tor-browser.desktop`

6. **Copiar o diretório tor-browser para `/usr/local/bin/`:** `sudo cp -r ~/Downloads/tor-browser /usr/local/bin/`

    Depois de copiar o diretório do Tor Browser para `/usr/local/bin/`, você pode criar um link simbólico do script de inicialização para o diretório `/usr/local/bin/`, o que permitirá que você inicie o `Tor Browser` de qualquer lugar no terminal apenas digitando `tor-browser`.

7. **Ajuste as permissões:** Abra um terminal e use o comando `chown` para mudar a propriedade da pasta e seu conteúdo para o seu usuário. Substitua edenedfsls pelo seu nome de usuário real e `tor-browser` pelo nome correto da pasta se for diferente. Aqui está o comando: `sudo chown -R edendenis:edendenis /usr/local/bin/tor-browser/`

8. **Verifique as permissões:** Depois de mudar a propriedade da pasta, verifique se as permissões permitem a leitura e execução do `Tor Browser`. O seguinte comando irá configurar as permissões de forma adequada: `sudo chmod -R 755 /usr/local/bin/tor-browser/`

    Este comando define as permissões para leitura e execução para o usuário, grupo e outros, o que é normalmente suficiente para a maioria das aplicações.

9. **Torne o arquivo `.desktop` executável:** `sudo chmod +x /usr/local/bin/tor-browser/start-tor-browser.desktop`

8. **Para fazer isso, execute:** `sudo ln -s /usr/local/bin/tor-browser/start-tor-browser.desktop /usr/local/bin/tor-browser`

10. Depois de criar o link simbólico, você pode iniciar o Tor Browser a partir do terminal simplesmente digitando: `tor-browser`

    Lembre-se de que, se você copiar o diretório para um local do sistema como `/usr/local/bin/`, você precisará atualizar o caminho no atalho .desktop ou em quaisquer outros atalhos ou scripts que você tenha criado para iniciar o Tor Browser.

Após seguir esses passos, você deverá ter um atalho funcional no seu `desktop` que, quando clicado, iniciará o `Tor Browser`. Se você não conseguir ver o ícone imediatamente, talvez precise dar um clique com o botão direito no atalho e selecionar "Permitir a execução do arquivo como um programa" ou algo similar, dependendo do seu ambiente de `desktop`.

Certifique-se de que os caminhos para o `Exec` e para o `Icon` estão corretos e apontam para o local onde o `Tor Browser` está realmente instalado no seu sistema.

## Observação(ões):

Quando você se conecta ao Gmail ou qualquer outro serviço online usando o Tor Browser, o objetivo principal é proteger sua localização e privacidade na internet, dificultando o rastreamento da sua atividade online até você. O Tor Browser faz isso encaminhando sua conexão através de uma série de servidores distribuídos ao redor do mundo, chamados de nós do Tor, antes de chegar ao site de destino.

No entanto, ao se conectar ao Gmail ou a qualquer serviço que exija login, há algumas considerações importantes a serem lembradas:

- **Autenticação:** Quando você faz login no Gmail, você está se identificando para o Google. Isso significa que, embora sua localização e o caminho que sua conexão fez através da internet estejam protegidos pelo Tor, o Google ainda pode reconhecer sua conta e associar essa sessão de login à sua identidade, com base em seu endereço de email e senha.

- **Cookies e sessões:** Após o login, o Gmail e outros serviços online geralmente utilizam cookies para manter sua sessão ativa. Isso significa que, enquanto você estiver logado, o serviço pode rastrear suas atividades dentro do próprio site. O Tor Browser é projetado para isolar cookies e impedir o rastreamento entre sites, mas isso não impede que o Google rastreie sua atividade dentro de seus próprios serviços.

- **Dados fornecidos ao serviço:** Qualquer informação que você fornecer enquanto estiver conectado (por exemplo, emails enviados, buscas realizadas no Google) pode ser associada à sua conta pelo provedor do serviço.

- **Rastreamento de IP e Tor:** Embora o Google não possa ver seu verdadeiro endereço IP quando você está usando o Tor Browser, ele pode identificar que a conexão está vindo de uma rede Tor. Alguns serviços online podem requerer passos adicionais de verificação ou bloquear acessos através do Tor devido a preocupações com segurança e abuso.

## Conclusão:

Usar o Tor Browser para acessar o Gmail melhora sua privacidade em relação a observadores externos, como seu provedor de internet ou atores mal-intencionados tentando espiar sua localização ou atividade na internet. No entanto, não impede que o Google associe sua atividade online à sua conta do Gmail. Para uma privacidade mais robusta, considere usar serviços de email focados em privacidade e segurança, que não rastreiam seus usuários.

### 2. Código completo para configurar/instalar

Para instalar o `Tor Browser` no `Linux Ubuntu` sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abra o `Terminal Emulator`. Você pode fazer isso pressionando: `Ctrl + Alt + T`

2. Digite o seguinte comando e pressione `Enter`:

    ```
    NÃO há.
    ```


## Referências

[1] OPENAI. ***Instalar tor no kali.*** Disponível em: https://chat.openai.com/c/c555438e-2ff7-4b30-bb8b-c542e6c06cc6 (texto adaptado). Acessado em: 14/02/2024 18:30.

[2] OPENAI. ***Vs code: editor popular.*** Disponível em: https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42 (texto adaptado). Acessado em: 14/02/2024 18:30.

