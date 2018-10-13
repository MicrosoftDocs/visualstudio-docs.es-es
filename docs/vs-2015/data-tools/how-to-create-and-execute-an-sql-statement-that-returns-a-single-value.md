---
title: 'Cómo: crear y ejecutar una instrucción SQL que devuelve un valor único | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7d5d57637a25db62832ad535bbad60214a0aa4ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192158"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Cómo: Crear y ejecutar una instrucción SQL que devuelve un único valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ejecutar una instrucción SQL que devuelve un valor único, puede ejecutar una consulta de TableAdapter que está configurada para ejecutar una instrucción SQL (por ejemplo, `CustomersTableAdapter.CustomerCount()`).  
  
 Si la aplicación no usa los TableAdapters, llame a la `ExecuteScalar` método en un objeto de comando, estableciendo su `CommandType` propiedad <xref:System.Data.CommandType>. ("Objeto de comando" hace referencia a un comando específico para el [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) usando la aplicación. Por ejemplo, si la aplicación está utilizando el proveedor de datos de .NET Framework para SQL Server, el objeto de comando sería <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Los ejemplos siguientes muestran cómo ejecutar instrucciones SQL que devuelven valores únicos de una base de datos mediante TableAdapters u objetos de comando. Para obtener más información sobre cómo realizar consultas con TableAdapters y comandos, consulte [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>Ejecutar instrucciones SQL que devuelven valores únicos utilizando un TableAdapter  
 En este ejemplo se muestra cómo crear una consulta de TableAdapter con el [editar TableAdapters](../data-tools/editing-tableadapters.md), y, a continuación, se proporciona información acerca de cómo declarar una instancia del TableAdapter y ejecutar la consulta.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Para crear una instrucción SQL que devuelve un valor único mediante un TableAdapter  
  
1.  Abrir un conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Si ya tiene uno, cree un TableAdapter. Para obtener más información sobre la creación de los TableAdapters, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si ya tiene una consulta en el TableAdapter que utiliza una instrucción SQL para devolver un valor único, omita el siguiente procedimiento, "para"declarar una instancia del TableAdapter y ejecutar la consulta. En caso contrario, continúe con el paso 4 para crear una nueva consulta que devuelve un valor único.  
  
4.  Haga clic en el TableAdapter que desee y use el menú contextual para agregar una consulta.  
  
     El **TableAdapter Query Configuration Wizard** se abre.  
  
5.  Deje el valor predeterminado de **usar instrucciones SQL**y, a continuación, haga clic en **siguiente**.  
  
6.  Elija la **SELECT que devuelve un valor único** opción y, a continuación, haga clic en **siguiente**.  
  
7.  Escriba la instrucción SQL o utilice el **generador de consultas** para ayudar con la creación de uno y, a continuación, haga clic en **siguiente**.  
  
8.  Proporcione un nombre para la consulta.  
  
9. Complete el Asistente; la consulta se agrega al objeto TableAdapter.  
  
10. Compilar el proyecto.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Para declarar una instancia del TableAdapter y ejecutar la consulta  
  
1.  Declare una instancia del TableAdapter que contiene la consulta que desea ejecutar.  
  
    -   Para crear una instancia mediante herramientas de tiempo de diseño, arrastre el TableAdapter que desee desde la **cuadro de herramientas**. (Componentes del proyecto aparecen ahora en el **cuadro de herramientas** bajo un encabezado que coincida con el nombre del proyecto.) Si el TableAdapter no aparece en el **cuadro de herramientas**, a continuación, es posible que deba compilar el proyecto.  
  
         O bien  
  
    -   Para crear una instancia en el código, reemplace el código siguiente con los nombres de su <xref:System.Data.DataSet> y un TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Los TableAdapters no se encuentran dentro de sus clases de conjunto de datos asociado. Cada conjunto de datos tiene una colección correspondiente de TableAdapters en su propio espacio de nombres. Por ejemplo, si tiene un conjunto de datos denominado `SalesDataSet`, a continuación, podría haber un `SalesDataSetTableAdapters` espacio de nombres que contiene sus TableAdapters.  
  
2.  Llame a la consulta como llamaría a cualquier otro método en el código. La consulta es un método del TableAdapter. Reemplace el código siguiente con los nombres de su TableAdapter y consulta. También deberá pasar los parámetros requeridos por la consulta y hacer algo con el valor devuelto (por ejemplo, asignarla a una variable). Si no está seguro de si la consulta requiere parámetros, o qué parámetros requiere, a continuación, compruebe IntelliSense para la firma necesaria de la consulta. Dependiendo de si la consulta toma parámetros o no, el código tendría un aspecto similar a uno de los ejemplos siguientes:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Es probable que deba asignar el valor devuelto por la consulta a una variable. Las consultas de TableAdapter que devuelven un único valor devuelven un tipo de datos basado en la consulta (en contraposición a la `ExecuteScalar` método, que devuelve un objeto). Por ejemplo, si la consulta de TableAdapter selecciona una única columna cuyo tipo de datos es un entero, el valor devuelto de la consulta es un entero. Si la columna permite valores null, el valor devuelto es uno de los tipos que aceptan valores null (por ejemplo, `Nullable(Of Integer)`). Para obtener más información sobre los tipos que aceptan valores NULL, vea <xref:System.Nullable>. El código completo para declarar una instancia de un TableAdapter y ejecutar una consulta debe ser similar al siguiente (en este ejemplo se da por supuesto el retorno de valor es un entero; ajuste el código de acuerdo con el tipo de datos devuelto por la consulta):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>Ejecutar instrucciones SQL que devuelven valores únicos utilizando un objeto de comando  
 El ejemplo siguiente muestra cómo crear un comando y ejecutar una instrucción SQL que devuelve un valor único. Para obtener información sobre cómo establecer y obtener los valores de parámetro para un comando, consulte [How to: Set y obtener los parámetros para objetos de comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Este ejemplo se usa el <xref:System.Data.SqlClient.SqlCommand> de objetos y requiere:  
  
-   Las referencias a la <xref:System>, <xref:System.Data>, y <xref:System.Xml> espacios de nombres.  
  
-   Una conexión de datos denominada `SqlConnection1`.  
  
-   Una tabla denominada `Customers` en los datos de origen que `SqlConnection1` se conecta a. (En caso contrario, se necesita una instrucción SQL válida para el origen de datos).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>Para ejecutar una instrucción SQL que devuelve un valor único mediante un DataCommand  
  
-   Agregue el código siguiente a un método que desea ejecutar el código. Devolver un único valor mediante una llamada a la `ExecuteScalar` método de un comando (por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Los datos se devuelven en un <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La aplicación requiere permiso para tener acceso a la base de datos y ejecutar la instrucción SQL.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Cómo: editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Cómo: rellenar un conjunto de datos](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Cómo: establecer y obtener parámetros de objetos de comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)