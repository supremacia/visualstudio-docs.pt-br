---
title: Desabilitar ou mover o cache do pacote | Microsoft Docs
description: "Desabilitar, habilitar ou mover o cache do pacote para implantações do Visual Studio."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 639c6e52f522bbdb2868d610f0b002abb9dda082
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="disable-or-move-the-package-cache"></a>Desabilitar ou mover o cache do pacote

O cache do pacote fornece uma origem de pacotes instalados, caso você precise reparar o Visual Studio ou outros produtos relacionados, em casos em não há conexão com a Internet. Com algumas unidades ou configurações de sistema, no entanto, não convém manter todos os pacotes.
O instalador os baixará quando necessário. Portanto, se você deseja salvar ou recuperar espaço em disco, pode desabilitar ou mover o cache do pacote.

## <a name="disable-the-package-cache"></a>Desabilitar o cache do pacote

Antes de instalar, modificar ou reparar o Visual Studio ou outros produtos com o novo instalador, você pode iniciar o instalador com a opção `--nocache` para o instalador.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Qualquer operação que você fizer em qualquer produto removerá quaisquer pacotes existentes para o produto e evitará salvar pacotes após a instalação. Se você modificar ou reparar o Visual Studio e pacotes forem necessários, serão baixados automaticamente e removidos após a instalação.

Se você quiser reabilitar o cache, passe `--cache` em vez disso. Somente os pacotes que são necessários serão armazenados. Portanto, se você precisar restaurar todos os pacotes, deverá reparar o Visual Studio antes de se desconectar da rede.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Você também pode definir a `KeepDownloadedPayloads` [política do Registro](set-defaults-for-enterprise-deployments.md) para desabilitar o cache antes de instalar, modificar ou reparar o Visual Studio.

## <a name="move-the-package-cache"></a>Mover o cache do pacote

Uma configuração comum do sistema é ter o Windows instalado em um SSD com um disco rígido maior (ou mais) para necessidades de desenvolvimento, como código-fonte, binários de programa e muito mais. Se quiser trabalhar offline em vez disso, você poderá mover o cache do pacote.

No momento, você só poderá fazer isso se definir a `CachePath`[política do Registro](set-defaults-for-enterprise-deployments.md) antes de instalar, modificar ou reparar o Visual Studio.

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

 * [Instalar o Visual Studio](install-visual-studio.md)
 * [Definir padrões para implantações corporativas](set-defaults-for-enterprise-deployments.md)
 * [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
