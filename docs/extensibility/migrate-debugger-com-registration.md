---
title: Migrar o registro de classe do depurador de 64 bits COM | Microsoft Docs
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.workload: greggm
ms.openlocfilehash: 737c970555fce8f3cdac118421eddb09f52d7c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrar o registro de classe COM de depurador de 64 bits

Para as extensões de depurador que registrar classes COM em HKEY_CLASSES_ROOT (por usando regasm, regsvr32, ou gravar diretamente no registro) e carregados no msvsmon.exe (o depurador remoto), agora é possível fornecer esse registro para msvsmon sem a necessidade para gravar HKEY_CLASSES_ROOT. Isso afeta herdados avaliadores de expressão do depurador .NET ou mecanismos de depuração que estão configurados para carregar no processo msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>o msvsmon-comclass-def

Para usar essa técnica, adicione um arquivo de *.msvsmon-comclass-def.json ao lado do msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Aqui está um exemplo de arquivo de definição de comclass msvsmon que registra um gerenciada e uma classe nativo:

Nome do arquivo: MyCompany.MyExample.msvsmon comclass def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
