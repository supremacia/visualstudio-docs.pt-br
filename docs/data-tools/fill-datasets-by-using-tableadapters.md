---
title: Preencher conjuntos de dados usando TableAdapters | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e338335263a9c0757bbf6305a42fd092d4f90c04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="fill-datasets-by-using-tableadapters"></a>Preencher conjuntos de dados usando TableAdapters
Um componente do TableAdapter preenche um dataset com dados do banco de dados, com base em uma ou mais consultas ou procedimentos armazenados que você especificar. Também pode executar TableAdapters adiciona, atualizações e exclusões no banco de dados para manter as alterações feitas ao conjunto de dados. Você também pode emitir comandos globais que estão relacionados a qualquer tabela específica.  
  
> [!NOTE]
>  TableAdapters são gerados pelos designers do Visual Studio. Se você estiver criando conjuntos de dados programaticamente, use DataAdapter, que é uma classe do .NET Framework.  
  
 Para obter informações detalhadas sobre as operações do TableAdapter, você poderá pular diretamente para um destes tópicos:  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Como usar os designers para criar e configurar TableAdapters|  
|[Criar consultas TableAdapter parametrizadas](../data-tools/create-parameterized-tableadapter-queries.md)|Como habilitar usuários fornecer argumentos para procedimentos do TableAdapter ou consultas|  
|[Acessar diretamente o banco de dados com um TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Como usar os métodos Dbdirect de TableAdapters|  
|[Desligar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Como trabalhar com restrições de chave estrangeira quando a atualização de dados|  
|[Como estender a funcionalidade de um TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Como adicionar código personalizado a TableAdapters|  
|[Ler dados XML em um conjunto de dados](../data-tools/read-xml-data-into-a-dataset.md)|Como trabalhar com XML|  
  
<a name="tableadapter-overview"></a>  
  
## <a name="tableadapter-overview"></a>Visão geral do TableAdapter  
 TableAdapters são componentes gerados pelo designer que se conectam a um banco de dados, executadas consultas ou procedimentos armazenados e preencher sua DataTable com os dados retornados. TableAdapters também enviar dados atualizados do seu aplicativo no banco de dados. Você pode executar consultas quantos desejar em um TableAdapter desde que elas retornam dados de acordo com o esquema da tabela à qual o TableAdapter está associado. O diagrama a seguir mostra como os TableAdapters interagir com bancos de dados e outros objetos na memória:  
  
 ![Fluxo de dados em um aplicativo cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Enquanto TableAdapters são criados com o **Dataset Designer**, as classes de TableAdapter não são geradas como classes aninhadas do <xref:System.Data.DataSet>. Eles estão localizados nos namespaces separados que são específicas para cada conjunto de dados. Por exemplo, se você tiver um dataset chamado `NorthwindDataSet`, os TableAdapters associados <xref:System.Data.DataTable>s no `NorthwindDataSet` estaria no `NorthwindDataSetTableAdapters` namespace. Para acessar um determinado TableAdapter programaticamente, você deve declarar uma nova instância do TableAdapter. Por exemplo:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
 [!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]  
  
## <a name="associated-datatable-schema"></a>Esquema de DataTable associado  
 Quando você criar um TableAdapter, você usar a consulta inicial ou procedimento armazenado para definir o esquema do TableAdapter associada <xref:System.Data.DataTable>. Execute esta consulta inicial ou procedimento armazenado chamando o TableAdapter `Fill` método (que preenche o TableAdapter associada do <xref:System.Data.DataTable>). As alterações feitas na consulta principal do TableAdapter são refletidas no esquema da tabela de dados associada. Por exemplo, remover uma coluna da consulta principal também remove a coluna da tabela de dados associada. Se quaisquer consultas adicionais no TableAdapter usam instruções SQL que retornam colunas que não estão na consulta principal, o designer tentará sincronizar as alterações de coluna entre a consulta principal e as consultas adicionais. 
  
## <a name="tableadapter-update-commands"></a>Comandos de atualização do TableAdapter  
 A funcionalidade de atualização de um TableAdapter é dependente de quanta informação está disponível na consulta principal no Assistente do TableAdapter. Por exemplo, TableAdapters configurados para buscar valores de várias tabelas (JOINs), valores escalares, exibições ou os resultados de funções de agregação não são criados inicialmente com a capacidade de enviar atualizações de volta para o banco de dados subjacente. No entanto, você pode configurar os comandos INSERT, UPDATE e DELETE manualmente no **propriedades** janela.  
  
## <a name="tableadapter-queries"></a>consultas TableAdapter  
 ![TableAdapter com várias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters pode conter várias consultas para preencher suas tabelas de dados associados. Você pode definir tantas consultas para um TableAdapter quanto seu aplicativo requer, desde que cada consulta retorna dados de acordo com o mesmo esquema que sua tabela de dados associada. Esse recurso permite um TableAdapter carregar resultados diferentes com base em critérios diferentes.  
  
 Por exemplo, se seu aplicativo contiver uma tabela com nomes de clientes, você pode criar uma consulta que preenche a tabela com cada nome de cliente que começa com uma letra específica e outra que preenche a tabela com todos os clientes que estão localizados no mesmo estado. Para preencher um `Customers` tabela com os clientes em um determinado estado, você pode criar um `FillByState` consulta que usa um parâmetro para o valor do estado da seguinte maneira: `SELECT * FROM Customers WHERE State = @State`. Execute a consulta chamando o `FillByState` método e passar o valor do parâmetro assim: `CustomerTableAdapter.FillByState("WA")`.  
  
 Além de adicionar consultas que retornam dados do mesmo esquema que a tabela de dados do TableAdapter, você pode adicionar consultas que retornam valores escalares de (único). Por exemplo, uma consulta que retorna uma contagem de clientes (`SELECT Count(*) From Customers`) é válido para um `CustomersTableAdapter,` , embora os dados retornados não está de acordo com o esquema da tabela.  
  
## <a name="clearbeforefill-property"></a>Propriedade ClearBeforeFill  
 Por padrão, toda vez que você executa uma consulta para preencher a tabela de dados do TableAdapter, os dados existentes serão limpos e somente os resultados da consulta são carregados na tabela. Definir o TableAdapter `ClearBeforeFill` propriedade `false` se você deseja adicionar ou mesclar os dados retornados de uma consulta para os dados existentes em uma tabela de dados. Independentemente de se você limpar os dados, você precisa explicitamente enviar atualizações de volta para o banco de dados, se você deseja mantê-las. Portanto, lembre-se de salvar as alterações dos dados na tabela antes de executar outra consulta que preenche a tabela. Para obter mais informações, consulte [atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Herança do TableAdapter  
 TableAdapters estendem a funcionalidade dos adaptadores de dados padrão, encapsulando configurado <xref:System.Data.Common.DataAdapter> classe. Por padrão, o TableAdapter herda o <xref:System.ComponentModel.Component> de classe e não pode ser convertido para o <xref:System.Data.Common.DataAdapter> classe. Converter um TableAdapter para o <xref:System.Data.Common.DataAdapter> classe resulta em um <xref:System.InvalidCastException> erro. Para alterar a classe base de um TableAdapter, você pode especificar uma classe que deriva de <xref:System.ComponentModel.Component> no **classe Base** propriedade do TableAdapter no **Dataset Designer**.  
  
## <a name="tableadapter-methods-and-properties"></a>Propriedades e métodos do TableAdapter  
 A classe TableAdapter não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Isso significa que você não pode procurar por ele na documentação ou **Pesquisador de objetos**. Ela é criada em tempo de design, quando você usa um dos assistentes mencionados anteriormente. O nome atribuído a um TableAdapter quando você criá-lo baseia-se no nome da tabela que você está trabalhando. Por exemplo, quando você cria um TableAdapter com base em uma tabela em um banco de dados denominado `Orders`, o TableAdapter é nomeado `OrdersTableAdapter`. O nome da classe do TableAdapter pode ser alterado usando o **nome** propriedade o **Dataset Designer**.  
  
 A seguir estão os métodos mais usados e as propriedades de TableAdapters:  
  
|Membro|Descrição|  
|------------|-----------------|  
|`TableAdapter.Fill`|Preenche a tabela de dados associados do TableAdapter com os resultados do comando SELECT do TableAdapter.|  
|`TableAdapter.Update`|Envia as alterações no banco de dados e retorna um inteiro que representa o número de linhas afetadas pela atualização. Para obter mais informações, consulte [atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Retorna um novo <xref:System.Data.DataTable> que é preenchida com dados.|  
|`TableAdapter.Insert`|Cria uma nova linha na tabela de dados. Para obter mais informações, consulte [inserir novos registros em um banco de dados](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Determina se uma tabela de dados é esvaziada antes de chamar um do `Fill` métodos.|  
  
## <a name="tableadapter-update-method"></a>Método de atualização do TableAdapter  
 TableAdapters usam comandos de dados para leitura e gravação do banco de dados. Inicial do TableAdapter `Fill` consulta (principal) é usada como base para criar o esquema da tabela de dados associada, bem como o `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandos que estão associados a `TableAdapter.Update` método. Chamando um TableAdapter `Update` método executa as instruções que foram criadas quando o TableAdapter foi originalmente configurado, não uma das consultas adicionais que foi adicionado com o **Assistente de configuração de consulta do TableAdapter**.  
  
 Quando você usa um TableAdapter, ele efetivamente executa as mesmas operações com os comandos que você geralmente deseja executar. Por exemplo, quando você chama o adaptador `Fill` método, o adaptador executa o comando de dados no seu `SelectCommand` propriedade e usa um leitor de dados (por exemplo, <xref:System.Data.SqlClient.SqlDataReader>) para carregar o resultado na tabela de dados. Da mesma forma, quando você chama o adaptador `Update` método, ele executa o comando apropriado (no `UpdateCommand`, `InsertCommand`, e `DeleteCommand` propriedades) para cada registro na tabela de dados alterado.  
  
> [!NOTE]
>  Se não houver informações suficientes na consulta principal, o `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandos são criados por padrão quando o TableAdapter é gerado. Se a consulta do TableAdapter principal é a mais de uma instrução SELECT única tabela, é possível que o designer não será capaz de gerar `InsertCommand`, `UpdateCommand`, e `DeleteCommand`. Se esses comandos não são gerados, você poderá receber um erro ao executar o `TableAdapter.Update` método.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods do TableAdapter  
 Além `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, TableAdapters são criados com métodos que podem ser executados diretamente no banco de dados. Esses métodos (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) podem ser chamados diretamente para manipular dados no banco de dados. Isso significa que você pode chamar esses métodos individuais do seu código em vez de chamar `TableAdapter.Update` para tratar as inserções, atualizações e exclusões pendentes para a tabela de dados associada.  
  
 Se você não quiser criar esses métodos diretos, defina o TableAdapter **GenerateDbDirectMethods** propriedade `false` (no **propriedades** janela). Consultas adicionais que são adicionadas ao TableAdapter são consultas autônomas — elas não geram esses métodos.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Suporte do TableAdapter para tipos anuláveis  
 TableAdapters oferecem suporte a tipos anuláveis `Nullable(Of T)` e `T?`. Para obter mais informações sobre tipos que permitem valor nulo no Visual Basic, consulte [Tipos de valores que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Para obter mais informações sobre tipos anuláveis em c#, consulte [usando tipos anuláveis](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).  
  
<a name="tableadaptermanager-reference"></a>  
  
## <a name="tableadaptermanager-reference"></a>Referência de TableAdapterManager  
 Por padrão, um `TableAdapterManager` classe é gerada quando você cria um conjunto de dados que contém as tabelas relacionadas. Para impedir que a classe que está sendo gerado, altere o valor da `Hierarchical Update` propriedade do conjunto de dados como false. Quando você arrastar uma tabela que tenha uma relação na superfície de design de um formulário do Windows ou a página do WPF, o Visual Studio declara uma variável de membro da classe. Se você não usa associação de dados, você deve manualmente declarar a variável.  
  
 O `TableAdapterManager` a classe não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Portanto, você não pode procurar por ele na documentação. Ele é criado em tempo de design como parte do processo de criação de conjunto de dados.  
  
 A seguir estão os métodos usados frequentemente e propriedades do `TableAdapterManager` classe:  
  
|Membro|Descrição|  
|------------|-----------------|  
|Método `UpdateAll`|Salva todos os dados de todas as tabelas de dados.|  
|Propriedade `BackUpDataSetBeforeUpdate`|Determina se é necessário criar uma cópia de backup do conjunto de dados antes de executar o `TableAdapterManager.UpdateAll` método. Valor booliano.|  
|*tableName* `TableAdapter` propriedade|Representa um `TableAdapter`. Gerado `TableAdapterManager` contém uma propriedade para cada `TableAdapter` ele gerencia. Por exemplo, um conjunto de dados com uma tabela clientes e pedidos é gerado com um `TableAdapterManager` que contém `CustomersTableAdapter` e `OrdersTableAdapter` propriedades.|  
|Propriedade `UpdateOrder`|Controla a ordem dos comandos delete, insert individual e atualização. Defina isso para um dos valores a `TableAdapterManager.UpdateOrderOption` enumeração.<br /><br /> Por padrão, o `UpdateOrder` é definido como **InsertUpdateDelete**. Isso significa que insere, em seguida, atualiza e exclui, em seguida, são executadas para todas as tabelas no conjunto de dados.|

## <a name="security"></a>Segurança  
Quando você usa comandos de dados com uma propriedade CommandType definida como <xref:System.Data.CommandType.Text>, cuidadosamente verifique informações que são enviadas de um cliente antes de passá-la para seu banco de dados. Usuários mal-intencionados podem tentar enviar (inserir) instruções SQL modificadas ou adicionais em um esforço para obter acesso não autorizado ou danificar o banco de dados. Antes de transferir a entrada do usuário para um banco de dados, sempre verifique se que as informações são válidas. Uma prática recomendada é sempre usar consultas parametrizadas ou procedimentos armazenados quando possível.  
  
## <a name="see-also"></a>Consulte também
[Ferramentas do conjunto de dados](../data-tools/dataset-tools-in-visual-studio.md)