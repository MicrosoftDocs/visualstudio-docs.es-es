---
title: 'Cómo: ejecutar un procedimiento almacenado que devuelve un valor único | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandType.StoredProcedure
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- ExecuteReader method example [Visual Basic]
- stored procedures, examples
- stored procedures, executing
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 00e5f497a01d6600d02f3de42aa487819e4dac45
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581681"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-a-single-value"></a>Cómo: Ejecutar un procedimiento almacenado que devuelve un único valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ejecutar un procedimiento almacenado que devuelve un valor único, puede ejecutar la consulta de TableAdapter que está configurada para ejecutar un procedimiento almacenado (por ejemplo, `CustomersTableAdapter.CustomerCount()`).  
  
 Si la aplicación no usa los TableAdapters, llame a la `ExecuteScalar` método en un objeto de comando, estableciendo su `CommandType` propiedad <xref:System.Data.CommandType>. ("Objeto de comando" hace referencia a un comando específico para el [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) usando la aplicación. Por ejemplo, si la aplicación está utilizando el proveedor de datos de .NET Framework para SQL Server, el objeto de comando sería <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Los ejemplos siguientes muestran cómo ejecutar procedimientos almacenados que devuelven valores únicos de una base de datos mediante TableAdapters u objetos de comando. Para obtener más información sobre cómo realizar consultas con TableAdapters y comandos, consulte [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-tableadapter"></a>Ejecutar procedimientos almacenados que devuelven valores únicos utilizando un TableAdapter  
 En este ejemplo se muestra cómo crear una consulta de TableAdapter con el [editar TableAdapters](../data-tools/editing-tableadapters.md), y, a continuación, se proporciona información acerca de cómo declarar una instancia del TableAdapter y ejecutar la consulta.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-tableadapter"></a>Para ejecutar un procedimiento almacenado que devuelve un valor único mediante un TableAdapter  
  
1.  Abrir un conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Si ya tiene uno, cree un TableAdapter. Para obtener más información sobre la creación de los TableAdapters, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Si ya tiene una consulta en el TableAdapter que utiliza un procedimiento almacenado para devolver un valor único, vaya al procedimiento siguiente, "para"declarar una instancia del TableAdapter y ejecutar la consulta. En caso contrario, continúe con el paso 4 para crear una nueva consulta que devuelve un valor único.  
  
4.  Haga clic en el TableAdapter que desee y use el menú contextual para agregar una consulta.  
  
     El **TableAdapter Query Configuration Wizard** se abre.  
  
5.  Seleccione **utilice el procedimiento almacenado existente**y, a continuación, haga clic en **siguiente**.  
  
6.  Seleccione un procedimiento almacenado en la lista desplegable y, a continuación, haga clic en **siguiente**.  
  
7.  Seleccione la opción para devolver **un único valor**y, a continuación, haga clic en **siguiente**.  
  
8.  Proporcione un nombre para la consulta.  
  
9. Haga clic en **siguiente** o **finalizar** para completar el asistente; la consulta se agrega al objeto TableAdapter.  
  
10. Compilar el proyecto.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Para declarar una instancia del TableAdapter y ejecutar la consulta  
  
1.  Declare una instancia del TableAdapter que contiene la consulta que desea ejecutar.  
  
    -   Para crear una instancia mediante herramientas de tiempo de diseño, arrastre el TableAdapter que desee desde la **cuadro de herramientas**. (Componentes del proyecto aparecen ahora en el **cuadro de herramientas** bajo un encabezado que coincida con el nombre del proyecto.) Si el TableAdapter no aparece en el **cuadro de herramientas**, a continuación, es posible que deba compilar el proyecto.  
  
         O bien  
  
    -   Para crear una instancia en el código, reemplace el código siguiente con los nombres de su <xref:System.Data.DataSet> y un TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Los TableAdapters no se encuentran dentro de sus clases de conjunto de datos asociado. Cada conjunto de datos tiene una colección correspondiente de TableAdapters en su propio espacio de nombres. Por ejemplo, si tiene un conjunto de datos denominado `SalesDataSet`, habrá un `SalesDataSetTableAdapters` espacio de nombres que contiene sus TableAdapters.  
  
2.  Llame a la consulta como llamaría a cualquier otro método en el código. La consulta es un método del TableAdapter. Reemplace el código siguiente con los nombres de su TableAdapter y consulta. También necesitará pasar los parámetros requeridos por la consulta. Si no está seguro de si la consulta requiere parámetros, o qué parámetros requiere, a continuación, compruebe IntelliSense para la firma necesaria de la consulta. Dependiendo de si la consulta toma parámetros o no, el código tendría un aspecto similar a uno de los ejemplos siguientes:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     El código completo para declarar una instancia del TableAdapter y ejecutar la consulta debe ser similar al siguiente:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-command-object"></a>Ejecutar procedimientos almacenados que devuelven valores únicos utilizando un objeto de comando  
 El ejemplo siguiente muestra cómo crear un comando y ejecutar un procedimiento almacenado que devuelve un valor único. Para obtener información sobre cómo establecer y obtener los valores de parámetro para un comando, consulte [How to: Set y obtener los parámetros para objetos de comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Este ejemplo se usa el <xref:System.Data.SqlClient.SqlCommand> de objetos y requiere:  
  
-   Las referencias a la <xref:System>, <xref:System.Data>, y <xref:System.Xml> espacios de nombres.  
  
-   Una conexión de datos denominada `SqlConnection1`.  
  
-   Una tabla denominada `Customers` en los datos de origen que `SqlConnection1` se conecta a. (En caso contrario, se necesita una instrucción SQL válida para el origen de datos).  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-datacommand"></a>Para ejecutar un procedimiento almacenado que devuelve un valor único mediante un DataCommand  
  
-   Agregue el código siguiente a un método que desea ejecutar el código. Devolver valores únicos mediante una llamada a la `ExecuteScalar` método de un comando (por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Los datos se devuelven en un `object`.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#14)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#14)]  
  
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