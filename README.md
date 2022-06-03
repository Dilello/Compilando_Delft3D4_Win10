# Compilando Delft3D-4 no Windows (Visual Studio 2019 e oneAPI 2021)

Traduzido e adaptado de [Mathew Topper](https://gist.github.com/H0R5E/8ea0d262b79cadc2c0973d5fc06334a4) (Data Only Greater)

Este é um guia rápido para compilar Delft3D-4 no Windows.

## Download do Delft3D-4 GUI (Interface gráfica do Delft3D-4)

Acessar a página [Get Started] e se registrar na Deltares ou, caso já tenha registro, entrar com login e senha.

Depois de logado, preencher formulário de solicitação (clicar em GUI request form) para obter a interface gráfica com licensa de 1 ano.

Após alguns dias, chegará por email um arquivo zip, em anexo, com a licença de 1 ano (Delft3D_GUI.zip) e no corpo do email o login e senha para baixar o GUI Delft3d-4 (Delft3D GUI Installers 4.04.02 Windows.zip).

## Download do Código Fonte

### Softwares requeridos

1. [TortoiseSVN](https://tortoisesvn.net/downloads.html)

Siga as instruções para instalação padrão do TortoiseSVN.

### Procedimento de transferência do código fonte

Logado na página [Get Started], clicar em:

Delft3D 4 [tag 65936]: https://svn.oss.deltares.nl/repos/delft3d/tags/delft3d4/65936 

1. Copiar o caminho;
1. Abrir o diretório onde receberá os códigos fontes
1. Clicar com botão direito e abrir o TortoiseSVN.
1. Colar o caminho no TortoiseSVN.
1. Iniciar a transferência (Pode demorar...)

## Instalação do Anaconda Python, Visual Studio Community 2019, Intel oneAPI (2021) e Delft3D-4 GUI

### Softwares requeridos

1. [Anaconda Python](https://www.anaconda.com/products/distribution)
1. [Visual Studio Community 2019](https://visualstudio.microsoft.com/pt-br/vs/older-downloads/)
1. [Intel oneAPI Base Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit.html)
1. [Intel oneAPI HPC Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/hpc-toolkit.htm)
1. Delft3D-4 GUI

Siga as instruções para instalação padrão do Anaconda Python.

Vídeo demonstrando a instalação Visual Studio Community 2019, Intel oneAPI 2021, clicar neste [link](https://www.youtube.com/watch?v=D_IWxD9QPn8)

Para o Visual Studio Community 2019, escolha o "Desktop development with C++" e selecione os seguintes componentes adicionais:

1. C++ MFC for latest v142 build tools (x86 & x64)
1. C++/CLI support for v142 build tools (Latest)
1. C++ Modules for v142 build tools (x64/x86 – experimental)

Para o Intel oneAPI Base Toolkit, durante instalação, selecione a opção customizada e selecione os seguintes componentes adicionais:

1. Intel oneAPI Math Kernel Library
1. Intel Distributtion for GDB

Para o Intel oneAPI HPC Toolkit, durante instalação, selecione a opção customizada e selecione os seguintes componentes adicionais:

1. Intel MPI Library
1. Intel oneAPI DPC++/C++ Compiler & Intel C++ Compiler Classic
1. Intel Fortran Compiler & Intel Fortran Comper Classic

Para interface gráfica do Delft3D-4, instale o DS_Flex license manager com seu arquivo de licença e então instale o Delft3D-4 GUI.

1. Install License Manager: localize o arquivo da licença no diretório
1. Install Matalab Runtime
1. Install OSS Delft3D
1. Install Delft3D Tutorial
1. Quit

## Preparando o Visual Studio Community 2019

Salve este script [python helper script] como `prepare_sln_auto.py` no diretório `\path\to\Delft3D\src`.

Agora, rodar o script no Anaconda3 Powershell prompt:

```
(base) PS > cd \path\to\Delft3D\src
(base) PS > python prepare_sln_auto.py
...
Visual Studio  Version : 2019
.Net Framework Version : v4.6.1
Intel oneAPI Version : 2021
Solution path :

```

Vídeo demonstrando, clique [aqui](https://www.youtube.com/watch?v=D_IWxD9QPn8)

## Compilando com Visual Studio Community 2019

Vídeo demonstrando, clique [aqui](https://www.youtube.com/watch?v=D_IWxD9QPn8)

1. Abrir Visual Studio
1. Abrir arquivo `delft3d_open.sln` no diretório `src`
1. Usando o solution explorer, abrir aruivo `third_party_open/netcdf/netcdff/Header Files/nfconfig.inc`
1. Editar linha 99 para `#define HAVE_TS29113_SUPPORT` e salve o arquivo
1. Mude a configuração de "Debug" para "Release"
1. Mude a plataforma de "Win32" para "x64"
1. Selecione "Build Solution" no menu "Build"
1. Espere a compilação terminar...

[Get Started]: https://oss.deltares.nl/web/delft3d/get-started
[tag 65936]: https://svn.oss.deltares.nl/repos/delft3d/tags/delft3d4/65936
[python helper script]: https://github.com/Dilello/Compilar_Delft3D4_Win/blob/main/prepare_sln_auto.py
