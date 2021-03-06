---
title: "CA2233: As operações não deveriam estourar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f5d048476997517a835337b568930367f97c2c92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: as operações não devem estourar
|||  
|-|-|  
|NomeDoTipo|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um método executa uma operação aritmética e não validar os operandos antecipadamente para impedir o estouro.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Operações aritméticas não devem ser executadas sem antes validar os operandos para certificar-se de que o resultado da operação não está fora do intervalo de valores possíveis para os tipos de dados envolvidos. Dependendo do contexto de execução e os tipos de dados envolvidos, estouro aritmético pode resultar em um um <xref:System.OverflowException?displayProperty=fullName> ou os bits mais significativos do resultado é descartada.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, valide os operandos antes de executar a operação.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se os valores possíveis dos operandos nunca fará com que a operação aritmética de estouro.  
  
## <a name="example-of-a-violation"></a>Exemplo de uma violação  
  
### <a name="description"></a>Descrição  
 Um método no exemplo a seguir manipula um inteiro que viola essa regra. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]requer o **remover** opção de estouro de inteiro para ser desabilitado para esta seja acionado.  
  
### <a name="code"></a>Código  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>Comentários  
 Se o método neste exemplo é passado <xref:System.Int32.MinValue?displayProperty=fullName>, a operação seria estouro negativo. Isso faz com que o bit mais significativo do resultado sejam descartadas. O código a seguir mostra como isso ocorre.  
  
 [C#]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 [VB]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### <a name="output"></a>Saída  
  
```  
2147483647  
```  
  
## <a name="fix-with-input-parameter-validation"></a>Corrigir com validação de parâmetro de entrada  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir corrige a violação anterior ao validar o valor de entrada.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>Corrigir com um bloco marcado  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir corrige a violação anterior encapsulando a operação em um bloco marcado. Se a operação faz com que um estouro, um <xref:System.OverflowException?displayProperty=fullName> será lançada.  
  
 Observe que não há suporte para blocos marcados no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Ativar check estouro/estouro negativo aritmético  
 Se você ativar check estouro/estouro negativo aritmético em c#, equivale a quebra automática de cada operação de inteiro em um bloco marcado.  
  
 **Para ativar o check-estouro/estouro negativo aritmético em c#**  
  
1.  Em **Solution Explorer**, clique com o botão direito e escolha **propriedades**.  
  
2.  Selecione a guia **Compilar** e clique em **Avançado**.  
  
3.  Selecione **verificar estouro/estouro negativo aritmético** e clique em **Okey**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.OverflowException?displayProperty=fullName>   
 [Operadores do C#](/dotnet/csharp/language-reference/operators/index)   
 [Checked e Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)