---
title: Insertar nuevos registros en una base de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4413949061a4bc48990e9935fe9dd60252cdde0b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47583123"
---
# <a name="insert-new-records-into-a-database"></a>Insertar nuevos registros en una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [insertar nuevos registros en una base de datos](https://docs.microsoft.com/visualstudio/data-tools/insert-new-records-into-a-database).  
  
  
Para insertar nuevos registros en una base de datos, puede usar el `TableAdapter.Update` método, o uno de los métodos DBDirect del TableAdapter (específicamente el `TableAdapter.Insert` método). Para obtener más información, consulte [información general sobre TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Si la aplicación no usa los TableAdapters, puede utilizar objetos de comando (por ejemplo, <xref:System.Data.SqlClient.SqlCommand>) para insertar nuevos registros en la base de datos.  
  
 Si la aplicación usa conjuntos de datos para almacenar los datos, utilice el `TableAdapter.Update` método. El `Update` método envía todos los cambios (actualizaciones, inserciones y eliminaciones) a la base de datos.  
  
 Si la aplicación utiliza objetos para almacenar datos, o si desea un mayor control sobre la creación de nuevos registros en la base de datos, utilice el `TableAdapter.Insert` método.  
  
 Si el TableAdapter no tiene un `Insert` método, significa que el TableAdapter está configurado para utilizar procedimientos almacenados o sus `GenerateDBDirectMethods` propiedad está establecida en `false`. Probar la configuración de TableAdapter `GenerateDBDirectMethods` propiedad `true` desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md)y, a continuación, guarde el conjunto de datos. Se volverá a generar el TableAdapter. Si el TableAdapter no tiene todavía un `Insert` método y, a continuación, en la tabla probablemente no proporciona suficiente información para distinguir entre filas individuales (por ejemplo, no podría haber ningún conjunto de clave principal en la tabla).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Insertar nuevos registros mediante el uso de TableAdapters  
 Los objetos TableAdapter proporcionan diferentes maneras de insertar nuevos registros en una base de datos, según los requisitos de la aplicación.  
  
 Si la aplicación usa conjuntos de datos para almacenar datos, a continuación, simplemente puede agregar nuevos registros a deseado <xref:System.Data.DataTable> en el conjunto de datos y, a continuación, llame el `TableAdapter.Update` método. El `TableAdapter.Update` método envía los cambios el <xref:System.Data.DataTable> a la base de datos (incluidos registros modificados y eliminados).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter.Update  
  
1.  Agregar nuevos registros a deseado <xref:System.Data.DataTable> creando un nuevo <xref:System.Data.DataRow> y agregarla a la <xref:System.Data.DataTable.Rows%2A> colección. Para obtener más información, consulte [Cómo: agregar filas a un objeto DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2.  Después de que las nuevas filas se agregan a la <xref:System.Data.DataTable>, llame a la `TableAdapter.Update` método. Puede controlar la cantidad de datos que se va a actualizar, pasando toda una <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único <xref:System.Data.DataRow>.  
  
     El código siguiente muestra cómo agregar un nuevo registro a un <xref:System.Data.DataTable> y, a continuación, llame a la `TableAdapter.Update` método para guardar la nueva fila en la base de datos. (Este ejemplo se usa el `Region` tabla en la base de datos Northwind.)  
  
     [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
     [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
 Si la aplicación utiliza objetos para almacenar los datos, puede usar el `TableAdapter.Insert` método para crear nuevas filas directamente en la base de datos. El `Insert` método acepta los valores individuales para cada columna como parámetros. Una llamada al método inserta un nuevo registro en la base de datos con los valores de parámetro pasados.  
  
 El siguiente procedimiento usa la `Region` tabla en la base de datos de Northwind como un ejemplo.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter.Insert  
  
-   Llamar a del TableAdapter `Insert` método, pasando los valores para cada columna como parámetros.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Insertar nuevos registros mediante el uso de objetos de comando  
 El ejemplo siguiente inserta nuevos registros directamente en una base de datos mediante objetos de comando. Para obtener más información sobre el uso de objetos de comando para ejecutar comandos y procedimientos almacenados, vea [capturar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
 El siguiente procedimiento usa la `Region` tabla en la base de datos de Northwind como un ejemplo.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para insertar nuevos registros en una base de datos mediante el uso de objetos de comando  
  
-   Cree un nuevo objeto de comando y, a continuación, establezca su `Connection`, `CommandType`, y `CommandText` propiedades.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Debe tener acceso a la base de datos a que está intentando conectarse, así como permiso para realizar inserciones en la tabla deseada.  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)

