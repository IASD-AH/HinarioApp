<div align="center">

<img src="assets/hinario.svg" alt="Hinário IASD — Aplicação para macOS" width="100%">

<br>

[![Licença: ISC](https://img.shields.io/badge/licen%C3%A7a-ISC-d4a94f?style=for-the-badge)](#licença)
[![macOS 11+](https://img.shields.io/badge/macOS-11%2B-1e2327?style=for-the-badge&logo=apple&logoColor=white)](#requisitos)
[![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-M1%20%C2%B7%20M2-1e2327?style=for-the-badge&logo=apple&logoColor=white)](#compatibilidade)
[![Electron](https://img.shields.io/badge/Electron-41-1e2327?style=for-the-badge&logo=electron&logoColor=9feaf9)](https://www.electronjs.org/)
[![Gratuito](https://img.shields.io/badge/uso-gratuito-2ea44f?style=for-the-badge)](#licença)

**Aplicação desktop para macOS que reproduz vídeos de hinos da Igreja Adventista do Sétimo Dia em ecrã completo, de forma simples, rápida e sem distrações.**

[Descarregar](https://github.com/filmfer/HinarioApp/releases) ·
[Funcionalidades](#funcionalidades) ·
[Instalação](#instalação) ·
[Desenvolvimento](#desenvolvimento) ·
[English](#english)

</div>

---

## Sobre

O **Hinário IASD** foi pensado para o momento do culto: escreve-se o número ou o nome do hino, prime-se `Enter` e o vídeo abre em ecrã completo no monitor ou projetor pretendido. Quando o vídeo termina, o player fecha-se sozinho e a aplicação fica pronta para o próximo hino.

A aplicação é **gratuita**, de código aberto e funciona de forma totalmente local, sem contas, sem internet e sem publicidade.

## Funcionalidades

| | Funcionalidade | Descrição |
|---|---|---|
| 🔎 | **Pesquisa de hinos** | Encontre hinos por número ou por nome, com resultados instantâneos. |
| 🖥️ | **Ecrã completo em qualquer monitor** | Reproduza o vídeo em qualquer ecrã ou projetor ligado ao Mac. |
| 🌑 | **Interface minimalista** | Design escuro e limpo, ideal para ambientes com pouca luz como cultos e auditórios. |
| ⌨️ | **Navegação por teclado** | Use `↑` `↓` para percorrer a lista e `Enter` para reproduzir. |
| ⏹️ | **Fecho automático** | O player fecha-se quando o vídeo termina, sem necessidade de intervenção. |
| 📁 | **Seleção de pasta** | Escolha a pasta onde estão os vídeos MP4. A configuração fica guardada. |

## Requisitos

- macOS 11 (Big Sur) ou superior
- Mac com processador **Apple Silicon**
- Vídeos dos hinos em formato **MP4**

> [!NOTE]
> Os vídeos dos hinos **não estão incluídos** nesta aplicação. Deve indicar uma pasta com os seus próprios ficheiros MP4.

## Compatibilidade

| Chip | Estado |
|---|---|
| Apple M1 (M1 / Pro / Max / Ultra) | ✅ Testado |
| Apple M2 (M2 / Pro / Max / Ultra) | ✅ Testado |
| Apple M3 | ⚠️ Não testado |
| Apple M4 | ⚠️ Não testado |
| Apple M5 | ⚠️ Não testado |
| Intel | ❌ Não suportado (a compilação é apenas ARM64) |

A aplicação foi desenvolvida e testada em Macs com **M1** e **M2**. Os chips **M3, M4 e M5** não foram testados por falta de hardware disponível. Como a arquitetura é a mesma (ARM64), é provável que funcione, mas não existe confirmação.

Se testar num destes chips, ajude-nos a atualizar a tabela: abra uma [issue](https://github.com/filmfer/HinarioApp/issues) a indicar o modelo, a versão do macOS e se tudo funcionou corretamente.

## Instalação

1. Descarregue o ficheiro `.dmg` ou `.zip` na [página de releases](https://github.com/filmfer/HinarioApp/releases).
2. Abra o `.dmg` e arraste a aplicação para a pasta **Applications**.
3. Na primeira execução, clique com o botão direito na aplicação e escolha **Abrir**. Este passo é necessário porque a aplicação não está assinada com um Developer ID da Apple.
4. Na janela inicial, escolha a pasta com os seus vídeos MP4.

### Permissões do macOS

Dependendo de onde estão os vídeos, o macOS pode pedir autorização em **Definições do Sistema → Privacidade e Segurança**:

- **Volumes Amovíveis** (*Removable Volumes*): se os vídeos estiverem num disco externo ou pen USB.
- **Acesso Total ao Disco** (*Full Disk Access*): se os vídeos estiverem em pastas protegidas.

### Como utilizar

1. Abra a aplicação e escolha a pasta dos vídeos (apenas na primeira vez).
2. Escreva o número ou o nome do hino na caixa de pesquisa.
3. Use `↑` e `↓` para selecionar e prima `Enter` para reproduzir.
4. O vídeo abre em ecrã completo e fecha-se automaticamente no final.

## Desenvolvimento

### Pré-requisitos

- [Node.js](https://nodejs.org/) 18 ou superior
- npm

### Executar em modo de desenvolvimento

```bash
# Clonar o repositório
git clone https://github.com/filmfer/HinarioApp.git
cd HinarioApp

# Instalar dependências
npm install

# Executar a aplicação
npm start
```

### Compilar

```bash
# Compilar para macOS ARM64 (Apple Silicon)
npm run make -- --arch=arm64
```

Os ficheiros compilados ficam em `out/make/`.

### Compilação automática

O repositório inclui um workflow de **GitHub Actions** que compila a aplicação para macOS ARM64 em cada *push* para a branch `main` e sempre que é criada uma tag `v*`.

### Estrutura do projeto

```text
HinarioApp/
├── assets/                 # Banner e imagens do repositório
├── index.js                # Processo principal do Electron
├── index.html              # Interface principal
├── renderer.js             # Lógica do renderer
├── player.html             # Player de vídeo em ecrã completo
├── preload.js              # Script de preload (contextBridge)
├── style.css               # Estilos da interface
├── forge.config.js         # Configuração do Electron Forge
├── entitlements.mac.plist  # Entitlements do macOS
├── extend.plist            # Info.plist estendido
└── LICENSE                 # Licença ISC
```

### Tecnologias

- **[Electron](https://www.electronjs.org/) 41**: framework para aplicações desktop
- **[Electron Forge](https://www.electronforge.io/)**: empacotamento e distribuição
- **Node.js**: ambiente de execução JavaScript
- **HTML, CSS e JavaScript**: interface do utilizador, sem frameworks adicionais

## Contribuir

Contribuições são bem-vindas. Pode ajudar de várias formas:

- Testando em Macs com **M3, M4 ou M5** e reportando o resultado
- Reportando erros através de uma [issue](https://github.com/filmfer/HinarioApp/issues)
- Sugerindo melhorias ou enviando um *pull request*

## Aviso

Este é um projeto independente e **não está afiliado, patrocinado ou endossado oficialmente** pela Igreja Adventista do Sétimo Dia. A aplicação é apenas um reprodutor: os hinos, vídeos e outros conteúdos que utilizar com ela são da responsabilidade do utilizador, que deve respeitar os direitos de autor e as licenças aplicáveis a esses materiais.

## Licença

Este projeto é distribuído sob a **Licença ISC**, uma licença permissiva e de utilização livre. Pode usar, copiar, modificar e distribuir este software gratuitamente, para qualquer fim, incluindo o comercial, desde que mantenha o aviso de copyright e esta nota de permissão.

```text
ISC License

Copyright (c) 2026, filmfer

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

### Software de terceiros

A aplicação distribuída inclui o **Electron**, licenciado sob a Licença MIT:

```text
MIT License

Copyright (c) Electron contributors
Copyright (c) 2013-2020 GitHub Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

O Electron inclui ainda o Chromium e outros componentes, cada um com as suas próprias licenças, disponíveis na aplicação compilada (`LICENSES.chromium.html`).

---

<a id="english"></a>

<details>
<summary><b>🇬🇧 English version</b></summary>

<br>

### Hinário IASD — macOS App

A desktop app for macOS that plays Seventh-day Adventist hymn videos in full screen, built for quick and distraction-free use during services.

### Features

- 🔎 **Hymn search**: find hymns by number or name
- 🖥️ **Full-screen playback on any display**: play on any monitor or projector connected to your Mac
- 🌑 **Minimalist dark interface**: clean design suited to low-light venues
- ⌨️ **Keyboard navigation**: `↑` `↓` to browse, `Enter` to play
- ⏹️ **Auto-close**: the player closes itself when the video ends
- 📁 **Folder selection**: choose the folder with your MP4 videos; the setting is remembered

### Requirements

- macOS 11 (Big Sur) or later
- Mac with **Apple Silicon**
- Hymn videos in **MP4** format (not included; bring your own)

### Compatibility

| Chip | Status |
|---|---|
| Apple M1 family | ✅ Tested |
| Apple M2 family | ✅ Tested |
| Apple M3 / M4 / M5 | ⚠️ Not tested (no hardware available) |
| Intel | ❌ Not supported (ARM64 builds only) |

The app has been tested on **M1** and **M2** Macs. It has **not** been tested on **M3, M4 or M5** due to a lack of hardware. It should work, since the architecture is the same (ARM64), but this is unconfirmed. If you try it on one of these chips, please [open an issue](https://github.com/filmfer/HinarioApp/issues) with your Mac model, macOS version and the result.

### Installation

1. Download the `.dmg` or `.zip` from the [releases page](https://github.com/filmfer/HinarioApp/releases).
2. Open the `.dmg` and drag the app into **Applications**.
3. On first launch, right-click the app and choose **Open** (the app is not signed with an Apple Developer ID).
4. Select the folder containing your MP4 videos.

Depending on where your videos are stored, macOS may ask for **Removable Volumes** or **Full Disk Access** permission in *System Settings → Privacy & Security*.

### Development

```bash
git clone https://github.com/filmfer/HinarioApp.git
cd HinarioApp
npm install
npm start                              # run in development
npm run make -- --arch=arm64           # build for Apple Silicon
```

Requires Node.js 18+. Build output goes to `out/make/`.

### License

Released under the **ISC License**. It is free to use, copy, modify and distribute for any purpose, including commercial use, as long as the copyright and permission notice are kept. The full text is in [`LICENSE`](LICENSE) and in the *Licença* section above. The app bundles Electron, which is MIT-licensed.

### Disclaimer

This is an independent project and is **not affiliated with or officially endorsed** by the Seventh-day Adventist Church. The app is only a player; you are responsible for the hymns and videos you use with it and for respecting any applicable copyrights and licenses.

</details>

---

<div align="center">

Feito com ♪ para louvar · Made with ♪ for worship

</div>
<div align="center">

<img src="assets/hinario.svg" alt="Hinário IASD — Aplicação para macOS" width="100%">

<br>

[![Licença: ISC](https://img.shields.io/badge/licen%C3%A7a-ISC-d4a94f?style=for-the-badge)](#licença)
[![macOS 11+](https://img.shields.io/badge/macOS-11%2B-1e2327?style=for-the-badge&logo=apple&logoColor=white)](#requisitos)
[![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-M1%20%C2%B7%20M2-1e2327?style=for-the-badge&logo=apple&logoColor=white)](#compatibilidade)
[![Electron](https://img.shields.io/badge/Electron-41-1e2327?style=for-the-badge&logo=electron&logoColor=9feaf9)](https://www.electronjs.org/)
[![Gratuito](https://img.shields.io/badge/uso-gratuito-2ea44f?style=for-the-badge)](#licença)

**Aplicação desktop para macOS que reproduz vídeos de hinos da Igreja Adventista do Sétimo Dia em ecrã completo, de forma simples, rápida e sem distrações.**

[Descarregar](https://github.com/filmfer/HinarioApp/releases) ·
[Funcionalidades](#funcionalidades) ·
[Instalação](#instalação) ·
[Desenvolvimento](#desenvolvimento) ·
[English](#english)

</div>

---

## Sobre

O **Hinário IASD** foi pensado para o momento do culto: escreve-se o número ou o nome do hino, prime-se `Enter` e o vídeo abre em ecrã completo no monitor ou projetor pretendido. Quando o vídeo termina, o player fecha-se sozinho e a aplicação fica pronta para o próximo hino.

A aplicação é **gratuita**, de código aberto e funciona de forma totalmente local, sem contas, sem internet e sem publicidade.

## Funcionalidades

| | Funcionalidade | Descrição |
|---|---|---|
| 🔎 | **Pesquisa de hinos** | Encontre hinos por número ou por nome, com resultados instantâneos. |
| 🖥️ | **Ecrã completo em qualquer monitor** | Reproduza o vídeo em qualquer ecrã ou projetor ligado ao Mac. |
| 🌑 | **Interface minimalista** | Design escuro e limpo, ideal para ambientes com pouca luz como cultos e auditórios. |
| ⌨️ | **Navegação por teclado** | Use `↑` `↓` para percorrer a lista e `Enter` para reproduzir. |
| ⏹️ | **Fecho automático** | O player fecha-se quando o vídeo termina, sem necessidade de intervenção. |
| 📁 | **Seleção de pasta** | Escolha a pasta onde estão os vídeos MP4. A configuração fica guardada. |

## Requisitos

- macOS 11 (Big Sur) ou superior
- Mac com processador **Apple Silicon**
- Vídeos dos hinos em formato **MP4**

> [!NOTE]
> Os vídeos dos hinos **não estão incluídos** nesta aplicação. Deve indicar uma pasta com os seus próprios ficheiros MP4.

## Compatibilidade

| Chip | Estado |
|---|---|
| Apple M1 (M1 / Pro / Max / Ultra) | ✅ Testado |
| Apple M2 (M2 / Pro / Max / Ultra) | ✅ Testado |
| Apple M3 | ⚠️ Não testado |
| Apple M4 | ⚠️ Não testado |
| Apple M5 | ⚠️ Não testado |
| Intel | ❌ Não suportado (a compilação é apenas ARM64) |

A aplicação foi desenvolvida e testada em Macs com **M1** e **M2**. Os chips **M3, M4 e M5** não foram testados por falta de hardware disponível. Como a arquitetura é a mesma (ARM64), é provável que funcione, mas não existe confirmação.

Se testar num destes chips, ajude-nos a atualizar a tabela: abra uma [issue](https://github.com/filmfer/HinarioApp/issues) a indicar o modelo, a versão do macOS e se tudo funcionou corretamente.

## Instalação

1. Descarregue o ficheiro `.dmg` ou `.zip` na [página de releases](https://github.com/filmfer/HinarioApp/releases).
2. Abra o `.dmg` e arraste a aplicação para a pasta **Applications**.
3. Na primeira execução, clique com o botão direito na aplicação e escolha **Abrir**. Este passo é necessário porque a aplicação não está assinada com um Developer ID da Apple.
4. Na janela inicial, escolha a pasta com os seus vídeos MP4.

### Permissões do macOS

Dependendo de onde estão os vídeos, o macOS pode pedir autorização em **Definições do Sistema → Privacidade e Segurança**:

- **Volumes Amovíveis** (*Removable Volumes*): se os vídeos estiverem num disco externo ou pen USB.
- **Acesso Total ao Disco** (*Full Disk Access*): se os vídeos estiverem em pastas protegidas.

### Como utilizar

1. Abra a aplicação e escolha a pasta dos vídeos (apenas na primeira vez).
2. Escreva o número ou o nome do hino na caixa de pesquisa.
3. Use `↑` e `↓` para selecionar e prima `Enter` para reproduzir.
4. O vídeo abre em ecrã completo e fecha-se automaticamente no final.

## Desenvolvimento

### Pré-requisitos

- [Node.js](https://nodejs.org/) 18 ou superior
- npm

### Executar em modo de desenvolvimento

```bash
# Clonar o repositório
git clone https://github.com/filmfer/HinarioApp.git
cd HinarioApp

# Instalar dependências
npm install

# Executar a aplicação
npm start
```

### Compilar

```bash
# Compilar para macOS ARM64 (Apple Silicon)
npm run make -- --arch=arm64
```

Os ficheiros compilados ficam em `out/make/`.

### Compilação automática

O repositório inclui um workflow de **GitHub Actions** que compila a aplicação para macOS ARM64 em cada *push* para a branch `main` e sempre que é criada uma tag `v*`.

### Estrutura do projeto

```text
HinarioApp/
├── assets/                 # Banner e imagens do repositório
├── index.js                # Processo principal do Electron
├── index.html              # Interface principal
├── renderer.js             # Lógica do renderer
├── player.html             # Player de vídeo em ecrã completo
├── preload.js              # Script de preload (contextBridge)
├── style.css               # Estilos da interface
├── forge.config.js         # Configuração do Electron Forge
├── entitlements.mac.plist  # Entitlements do macOS
├── extend.plist            # Info.plist estendido
└── LICENSE                 # Licença ISC
```

### Tecnologias

- **[Electron](https://www.electronjs.org/) 41**: framework para aplicações desktop
- **[Electron Forge](https://www.electronforge.io/)**: empacotamento e distribuição
- **Node.js**: ambiente de execução JavaScript
- **HTML, CSS e JavaScript**: interface do utilizador, sem frameworks adicionais

## Contribuir

Contribuições são bem-vindas. Pode ajudar de várias formas:

- Testando em Macs com **M3, M4 ou M5** e reportando o resultado
- Reportando erros através de uma [issue](https://github.com/filmfer/HinarioApp/issues)
- Sugerindo melhorias ou enviando um *pull request*

## Aviso

Este é um projeto independente e **não está afiliado, patrocinado ou endossado oficialmente** pela Igreja Adventista do Sétimo Dia. A aplicação é apenas um reprodutor: os hinos, vídeos e outros conteúdos que utilizar com ela são da responsabilidade do utilizador, que deve respeitar os direitos de autor e as licenças aplicáveis a esses materiais.

## Licença

Este projeto é distribuído sob a **Licença ISC**, uma licença permissiva e de utilização livre. Pode usar, copiar, modificar e distribuir este software gratuitamente, para qualquer fim, incluindo o comercial, desde que mantenha o aviso de copyright e esta nota de permissão.

```text
ISC License

Copyright (c) 2026, filmfer

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

### Software de terceiros

A aplicação distribuída inclui o **Electron**, licenciado sob a Licença MIT:

```text
MIT License

Copyright (c) Electron contributors
Copyright (c) 2013-2020 GitHub Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

O Electron inclui ainda o Chromium e outros componentes, cada um com as suas próprias licenças, disponíveis na aplicação compilada (`LICENSES.chromium.html`).

---

<a id="english"></a>

<details>
<summary><b>🇬🇧 English version</b></summary>

<br>

### Hinário IASD — macOS App

A desktop app for macOS that plays Seventh-day Adventist hymn videos in full screen, built for quick and distraction-free use during services.

### Features

- 🔎 **Hymn search**: find hymns by number or name
- 🖥️ **Full-screen playback on any display**: play on any monitor or projector connected to your Mac
- 🌑 **Minimalist dark interface**: clean design suited to low-light venues
- ⌨️ **Keyboard navigation**: `↑` `↓` to browse, `Enter` to play
- ⏹️ **Auto-close**: the player closes itself when the video ends
- 📁 **Folder selection**: choose the folder with your MP4 videos; the setting is remembered

### Requirements

- macOS 11 (Big Sur) or later
- Mac with **Apple Silicon**
- Hymn videos in **MP4** format (not included; bring your own)

### Compatibility

| Chip | Status |
|---|---|
| Apple M1 family | ✅ Tested |
| Apple M2 family | ✅ Tested |
| Apple M3 / M4 / M5 | ⚠️ Not tested (no hardware available) |
| Intel | ❌ Not supported (ARM64 builds only) |

The app has been tested on **M1** and **M2** Macs. It has **not** been tested on **M3, M4 or M5** due to a lack of hardware. It should work, since the architecture is the same (ARM64), but this is unconfirmed. If you try it on one of these chips, please [open an issue](https://github.com/filmfer/HinarioApp/issues) with your Mac model, macOS version and the result.

### Installation

1. Download the `.dmg` or `.zip` from the [releases page](https://github.com/filmfer/HinarioApp/releases).
2. Open the `.dmg` and drag the app into **Applications**.
3. On first launch, right-click the app and choose **Open** (the app is not signed with an Apple Developer ID).
4. Select the folder containing your MP4 videos.

Depending on where your videos are stored, macOS may ask for **Removable Volumes** or **Full Disk Access** permission in *System Settings → Privacy & Security*.

### Development

```bash
git clone https://github.com/filmfer/HinarioApp.git
cd HinarioApp
npm install
npm start                              # run in development
npm run make -- --arch=arm64           # build for Apple Silicon
```

Requires Node.js 18+. Build output goes to `out/make/`.

### License

Released under the **ISC License**. It is free to use, copy, modify and distribute for any purpose, including commercial use, as long as the copyright and permission notice are kept. The full text is in [`LICENSE`](LICENSE) and in the *Licença* section above. The app bundles Electron, which is MIT-licensed.

### Disclaimer

This is an independent project and is **not affiliated with or officially endorsed** by the Seventh-day Adventist Church. The app is only a player; you are responsible for the hymns and videos you use with it and for respecting any applicable copyrights and licenses.

</details>

---

<div align="center">

Feito com ♪ para louvar · Made with ♪ for worship

</div>

---

<div align="center">

Filipe Fernandes - jfilipefernandes.com - filmfer - filmfer@gmail.com

</div>
