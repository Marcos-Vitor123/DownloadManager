# Download Manager

Um gerenciador de downloads para Windows, moderno, rápido e com tema escuro. Baixa arquivos grandes dividindo-os em **muitas partes paralelas** (como o torrent), **retoma downloads no ponto exato** onde pararam (como o IDM/JDownloader) e ainda mostra **velocidade real e tempo restante estimado** para cada arquivo.

![Janela principal do Download Manager](Image/01.png)

---

## Propósito do projeto

O objetivo é dar ao usuário o máximo de controle e velocidade no download de arquivos da internet, mesmo em servidores lentos ou instáveis. O aplicativo:

- Divide o download em **até 256 partes paralelas**, acelerando arquivos grandes;
- **Retoma sem perder o progresso** se você fechar o programa, pausar ou cair a internet;
- Mostra **tempo restante (ETA)**, velocidade média e progresso de cada parte;
- Permite **pausar, continuar, cancelar e remover** downloads;
- **Abre a pasta** do arquivo ao finalizar;
- Indica imediatamente quando o download termina.

![Download em andamento com o painel de partes](Image/02.png)

---

## A que se assemelha e como funciona

O **Download Manager** combina o melhor dos gerenciadores de download mais conhecidos:

| Semelhança | Explicação |
|---|---|
| **Internet Download Manager (IDM)** | Interface por lista com itens, velocidade, barra de progresso e fila de downloads. |
| **JDownloader** | Facilidade de uso: colar o link e baixar, com estrutura de pastas e gerenciamento da lista. |
| **Torrent (µTorrent/qBittorrent)** | O arquivo é dividido em **partes** baixadas em paralelo e montado no final — e você pode **continuar de onde parou** mesmo após fechar o programa ou reiniciar o PC. |

Na prática: o programa divide o arquivo em segmentos (ex.: 64 partes), baixa cada parte em uma conexão simultânea e, ao final, **monta o arquivo** na pasta escolhida. Se um servidor limita uma única conexão, ele se adapta e funciona igualmente bem. Tudo isso validado: ao interromper no meio, fechar e abrir no outro dia, o download **continua exatamente de onde parou** e o arquivo final é idêntico (integridade verificada).

> **Importante:** nem todos os sites/servidores aceitam baixar em várias partes ao mesmo tempo. Quando o servidor permite apenas **uma** conexão (caso comum em sites de hospedagem direta, como os que o JDownloader também baixa com 1 parte), o aplicativo percebe sozinho e baixa normalmente com **1 parte**. Se aparecer apenas "1 parte" baixando, **não é bug** — é o comportamento correto para funcionar naquele site; em sites que aceitam múltiplas conexões, as partes paralelas aparecem normalmente.

![Janela de configurações do Download Manager](Image/03.png)

---

## Como usar

1. **Baixe o executável** (arquivo `.exe`) e coloque em qualquer pasta (ex.: `C:\Arquivos de Programas` ou `Documentos`).
2. **Crie um atalho** para o `DownloadManager.exe` onde quiser (Área de Trabalho, Menu Iniciar) e abra.
3. **Cole o link** do arquivo no campo superior e clique em **Baixar**.
4. Acompanhe o progresso: velocidade, tempo restante e o painel de partes.
5. Use os botões do item:
   - **Pausar / Continuar** — pausa sem perder o progresso;
   - **X (Cancelar)** — para o download e o remove da lista;
   - **Abrir pasta** — mostra o arquivo baixado;
6. Clique no **engrenagem** para configurar:

   - Pasta de destino final;
   - Pasta temporária (onde as partes ficam durante o download);
   - **Número de partes por download** (1 a 256);
   - **Downloads simultâneos**;
   - **Tentativas** ao ocorrer erro de conexão;
   - **Iniciar com o Windows** — abre o programa junto com o sistema (marque/desmarque quando quiser).

> A pasta pode ser escolhida a qualquer momento, antes de baixar.

---

## Atualizações automáticas

O aplicativo **já vem preparado para receber atualizações sozinho**: ao iniciar, ele consulta o repositório (arquivo `version.json`). Se houver versões mais recentes, uma janela aparece listando **cada versão disponível** com as notas do que mudou — e **você escolhe** se quer atualizar, **para qual versão** quer ir, ou simplesmente continuar na versão atual. Basta fechar e reabrir o programa para ver as opções novamente.

A versão atual fica visível no rodapé da janela (ex.: `v1.1.0`). Todas as versões lançadas ficam disponíveis para sempre na seção **Releases** do repositório no GitHub.

---

## Tecnologias

- **C#** (linguagem moderna, com `async/await` e tipagem segura);
- **.NET 10** (framework atual da Microsoft);
- **WPF** com **XAML** para a interface (tema escuro, janela customizada);
- **HTTP Range Requests** para download em partes e retomada;
- **SHA-256** para verificação de integridade das atualizações;
- **Publicação em arquivo único autocontido** — o `.exe` possui tudo embutido e **não exige instalar o .NET** no computador.

---

## Sobre o desenvolvimento

Este projeto foi desenvolvido por **Marcos Vitor**, com o auxílio de **inteligência artificial** nos testes, depuração e implementação de código, sempre **supervisionado por um humano** que decide os comandos e as funcionalidades.

---

## ⚠️ Aviso sobre antivírus e SmartScreen

O executável **não possui certificado digital** assinado pela Microsoft. Por causa disso, é **normal** que o Windows SmartScreen ou algum antivírus mostre um alerta acusando "vírus" ou "arquivo desconhecido". **Isso é um falso positivo** e acontece com praticamente todo programa sem certificado pago. O aplicativo é seguro.

Ao **baixar pelo navegador** (Edge, Chrome ou Firefox), também pode aparecer um aviso dizendo que o arquivo "não é seguro" ou "não é segurável". Nesse caso, clique em **Manter** (opção *Keep*) — é o nosso executável oficial.

Para executar mesmo assim:

1. Abra o alerta do SmartScreen;
2. Clique em **Mais informações**;
3. Clique em **Executar assim mesmo**.

---

## Requisitos

- **Windows 10 ou 11** (64 bits);
- Nenhum outro componente precisa ser instalado.

---

## Versões

- **v1.1.0** — correções e novas opções:
  - **Correção:** o 2º/3º download simultâneo também baixa em paralelo — se o servidor esconder o tamanho ou impedir a consulta inicial, o aplicativo **descobre o tamanho durante o próprio download** e sobe sozinho de 1 parte para paralelo (antes ficava preso em "1 parte" e "tamanho desconhecido");
  - Até **256 partes** por download;
  - **Fila por ordem de chegada** quando o limite de downloads simultâneos é atingido — quando libera, continua na ordem;
  - Opção **Iniciar com o Windows** nas configurações;
  - **Escolha de versão** na atualização: você decide se quer atualizar e para qual versão, ou ficar na atual.

- **v1.0.0** — primeira versão oficial:
  - Download em até 128 partes paralelas;
  - Retomada de downloads (fechou/parou, continua de onde estava);
  - Pausa, continuar, cancelar e remover;
  - Painel de partes, velocidade média e **tempo restante (ETA)**;
  - Configurações de pasta, partes, downloads simultâneos e tentativas;
  - **Atualização automática** via GitHub;
  - Arquivo único, sem necessidade de instalação.