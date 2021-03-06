---
title: "Usar PyLint com código do Python no Visual Studio | Microsoft Docs"
description: "Como usar PyLint no Visual Studio para verificar problemas no código do Python."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ec8737db3db3da99ad372b24b9308fc93811ebc4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="using-pylint-to-check-python-code"></a>Usando o PyLint para verificar o código do Python

O [PyLint](https://www.pylint.org/), uma ferramenta amplamente usada que verifica se há erros no código do Python e incentiva bons padrões de codificação do Python, é integrado ao Visual Studio para projetos do Python.

Basta clicar com o botão direito do mouse em um projeto do Python no Gerenciador de Soluções e selecionar **Python > Executar PyLint...**:

![Comando PyLint no menu de contexto em projetos do Python](media/code-pylint-command.png)

Usando esses prompts de comando você instala o PyLint no ambiente ativo se ele ainda não estiver presente.

Os avisos e erros do PyLint são exibidos na janela Lista de Erros:

![Lista de erros do PyLint](media/code-pylint-error-list.png)

Clicar duas vezes em um erro leva você diretamente para o código-fonte que gerou o problema.

> [!Tip]
> Consulte a [referência de recursos do PyLint](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) para obter uma lista detalhada de todas as mensagens de saída do PyLint.

## <a name="setting-pylint-command-line-options"></a>Configurando opções de linha de comando do PyLint

A seção [opções de linha de comando](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) da documentação do PyLint descreve como controlar o comportamento do PyLint por meio de um arquivo de configuração `.pylintrc`. Um arquivo desse tipo pode ser colocado na raiz de um projeto do Python no Visual Studio ou em outro lugar, dependendo da abrangência desejada da aplicação das configurações (consulte a [opções de linha de comando](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) para ver mais detalhes).

Por exemplo, para suprimir os avisos “docstring ausente” mostrados na imagem anterior com um arquivo `.pylintrc` em um projeto, execute as etapas:

1. Na linha de comando, navegue até a raiz do projeto (que contém o arquivo `.pyproj`) e execute o seguinte comando para gerar um arquivo de configuração comentado:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no projeto, selecione **Adicionar > Saindo do Item...**, navegue até o novo arquivo `.pylintrc` e o selecione e, em seguida, selecione **Adicionar**.

1. Abra o arquivo para edição, que contém uma variedade de configurações com as quais você pode trabalhar. Para desabilitar um aviso, localize a seção `[MESSAGES CONTROL]` e, em seguida, localize a configuração `disable` nessa seção. Há uma longa cadeia de mensagens específicas, à qual é possível acrescentar os avisos desejados. Neste exemplo, acrescente `,missing-docstring` (incluindo a vírgula delimitadora).

1. Salve o arquivo `.pylintrc` e execute o PyLint novamente para ver se agora os avisos estão suprimidos.

> [!Tip]
> Para usar um `.pylintrc` de arquivos de um compartilhamento de rede, crie uma variável de ambiente denominada `PYLINTRC` com o valor do nome de arquivo no compartilhamento de rede usando um caminho UNC ou uma letra da unidade mapeada. Por exemplo, `PYLINTRC=\\myshare\python\.pylintrc`.
