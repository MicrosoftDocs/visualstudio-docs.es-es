---
title: Insertar nuevos registros en una base de datos | Documentos de Microsoft
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 1ebb2621aa8da474c08d12e187feadef85840663
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="insert-new-records-into-a-database"></a>Insertar nuevos registros en una base de datos
Para insertar nuevos registros en una base de datos, puede usar el `TableAdapter.Update` método, o a uno de los métodos DBDirect del TableAdapter (específicamente el `TableAdapter.Insert` método). Para obtener más información, consulte [TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Si su aplicación no utiliza TableAdapters, puede utilizar objetos de comando (por ejemplo, <xref:System.Data.SqlClient.SqlCommand>) para insertar nuevos registros en la base de datos.
  
 Si la aplicación usa conjuntos de datos para almacenar los datos, use la `TableAdapter.Update` método. El `Update` método envía todos los cambios (actualizaciones, inserciones y eliminaciones) a la base de datos.  
  
 Si su aplicación utiliza objetos para almacenar datos, o si desea un mayor control sobre la creación de nuevos registros en la base de datos, use la `TableAdapter.Insert` método.  
  
 Si el TableAdapter no dispone de un `Insert` (método), significa que el TableAdapter está configurado para utilizar procedimientos almacenados o su `GenerateDBDirectMethods` propiedad está establecida en `false`. Intente establecer el TableAdapter `GenerateDBDirectMethods` propiedad `true` desde el **Diseñador de Dataset**y, a continuación, guarde el conjunto de datos. Se volverá a generar el TableAdapter. Si el TableAdapter no tiene todavía un `Insert` método y, a continuación, en la tabla probablemente no proporciona suficiente información de esquema para distinguir entre filas individuales (por ejemplo, no podría haber ningún conjunto de clave principal en la tabla).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Insertar nuevos registros mediante TableAdapters  
 Los TableAdapters proporcionan maneras diferentes de insertar nuevos registros en una base de datos, dependiendo de los requisitos de la aplicación.  
  
 Si la aplicación usa conjuntos de datos para almacenar datos, simplemente puede agregar nuevos registros a lo que se desea <xref:System.Data.DataTable> en el conjunto de datos y, a continuación, llame el `TableAdapter.Update` método. El `TableAdapter.Update` método envía los cambios la <xref:System.Data.DataTable> a la base de datos (incluidos los registros modificados y eliminados).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter.Update  
  
1.  Agregar nuevos registros a lo que se desea <xref:System.Data.DataTable> al crear un nuevo <xref:System.Data.DataRow> y agregarla a la <xref:System.Data.DataTable.Rows%2A> colección. 
  
2.  Después de que las nuevas filas se agregan a la <xref:System.Data.DataTable>, llame a la `TableAdapter.Update` método. Puede controlar la cantidad de datos que se va a actualizar pasando toda una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único <xref:System.Data.DataRow>.  
  
 El código siguiente muestra cómo agregar un nuevo registro para un <xref:System.Data.DataTable> y, a continuación, llame a la `TableAdapter.Update` método para guardar la nueva fila en la base de datos. (Este ejemplo se utiliza la `Region` tabla en la base de datos Northwind.)  
  
 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Para insertar nuevos registros en una base de datos mediante el método TableAdapter.Insert  
Si la aplicación utiliza objetos para almacenar los datos, puede usar el `TableAdapter.Insert` método para crear nuevas filas directamente en la base de datos. El `Insert` método acepta los valores individuales de cada columna como parámetros. Una llamada al método, inserta un nuevo registro en la base de datos con los valores de parámetro pasados.  
  
- Llamar a del TableAdapter `Insert` método, pasando los valores de cada columna como parámetros.  

 El siguiente procedimiento muestra cómo utilizar el `TableAdapter.Insert` método para insertar filas. En este ejemplo se inserta datos en el `Region` tabla en la base de datos Northwind.  
  
 > [!NOTE]
 >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Insertar nuevos registros mediante objetos de comando  
Puede insertar nuevos registros directamente en una base de datos mediante objetos de comando.    
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Para insertar nuevos registros en una base de datos mediante objetos de comando  
  
-   Crear un nuevo objeto de comando y, a continuación, establezca su `Connection`, `CommandType`, y `CommandText` propiedades.  

 El ejemplo siguiente muestra la inserción de registros en una base de datos con objeto de comando. Inserta datos en el `Region` tabla en la base de datos Northwind.
  
 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Debe tener acceso a la base de datos a que está intentando conectarse, así como permiso para realizar inserciones en la tabla deseada.  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)