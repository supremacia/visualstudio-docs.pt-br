---
title: Guia do administrador do Visual Studio | Microsoft Docs
description: Saiba mais sobre como implantar o Visual Studio em um ambiente corporativo.
ms.custom: 
ms.date: 05/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c143456d71057071aa953605e2ee60c6aa9c77de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-2017-administrator-guide"></a>Guia do administrador do Visual Studio 2017

Em ambientes corporativos, é comum que administradores de sistema implantem instalações para os usuários finais de um compartilhamento de rede ou usando software de gerenciamento de sistemas. Projetamos o mecanismo de instalação do Visual Studio para dar suporte à implantação corporativa, permitindo que os administradores de sistema tenham a capacidade de criar um local de instalação de rede, pré-configurar padrões de instalação, implantar chaves de produto durante o processo de instalação e gerenciar atualizações de produto depois de uma implementação com êxito. Este guia do administrador fornece orientações com base em cenários para implantações corporativas em ambientes de rede.

## <a name="deploying-visual-studio-2017-in-an-enterprise-environment"></a>Implantação do Visual Studio 2017 em um ambiente corporativo

Você pode implantar o Visual Studio 2017 para estações de trabalho cliente, contanto que cada computador de destino atenda a [requisitos mínimos de instalação](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Se você estiver implantando por meio de softwares como o System Center ou por meio de um arquivo em lotes, normalmente é preciso percorrer as etapas a seguir:

1. [Crie um compartilhamento de rede que contenha os arquivos de produto do Visual Studio](create-a-network-installation-of-visual-studio.md) para um local de rede.

2. [Selecione as cargas de trabalho e os componentes](workload-and-component-ids.md) que deseja instalar.

3. [Crie um arquivo de resposta](automated-installation-with-response-file.md) que contenha opções de instalação padrão. Ou, como alternativa, [compile um script de instalação](use-command-line-parameters-to-install-visual-studio.md) que use parâmetros de linha de comando para controlar a instalação.

4. Opcionalmente, [aplique uma chave de produto de licença de volume](automatically-apply-product-keys-when-deploying-visual-studio.md) como parte do script de instalação para que os usuários não precisem ativar o software separadamente.

5. Atualize o layout de rede para [controlar quando as atualizações de produto serão entregues aos usuários finais](controlling-updates-to-visual-studio-deployments.md).

6. Como alternativa, defina as chaves do Registro para [controlar o que é armazenado em cache nas estações de trabalho cliente](set-defaults-for-enterprise-deployments.md).

7. Usa a tecnologia de implantação de sua escolha para executar o script gerado nas etapas anteriores em suas estações de trabalho do desenvolvedor de destino.

8. [Atualize seu local de rede com as atualizações mais recentes](update-a-network-installation-of-visual-studio.md) do Visual Studio ao executar o comando usado na etapa 1 regularmente para adicionar componentes atualizados.

> [!IMPORTANT]
> Observe que as instalações de um compartilhamento de rede se “lembrarão” do seu local de origem. Isso significa que um reparo de um computador cliente pode ter que retornar para o compartilhamento de rede do qual o cliente foi instalado originalmente. Escolha cuidadosamente seu local de rede para que ele se alinhe com o tempo de vida esperado de execução de clientes do Visual Studio 2017 na sua organização.

## <a name="visual-studio-tools"></a>Ferramentas do Visual Studio
Temos várias ferramentas disponíveis para ajudar você a [detectar e gerenciar instâncias do Visual Studio instaladas](tools-for-managing-visual-studio-instances.md) em computadores cliente.

> [!TIP]
> Além da documentação no guia do administrador, uma boa fonte de informações sobre a instalação do Visual Studio 2017 é o [blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
  * [Referência de ID de componente e carga de trabalho](workload-and-component-ids.md)
* [Criar uma instalação em rede do Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Instalar os certificados necessários para instalação offline do Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatizar o Visual Studio com um arquivo de resposta](automated-installation-with-response-file.md)
* [Chaves de produto automaticamente durante a implantação do Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Definir padrões para implantações empresariais do Visual Studio](set-defaults-for-enterprise-deployments.md)
* [Desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md)
* [Atualizar uma instalação em rede do Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Atualizações de controle para implantações do Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
