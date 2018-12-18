---
title: 'Cómo: eliminar registros en una base de datos | Microsoft Docs'
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
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 87ab5ccde2c1100fbd0efc5f4272efe27803b717
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938622"
---
# <a name="how-to-delete-records-in-a-database"></a>Cómo: Eliminar registros de una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para eliminar registros de una base de datos, use el `TableAdapter.Update` método o la `TableAdapter.Delete` método. O bien, si la aplicación no usa los TableAdapters, puede usar los objetos de comando para eliminar registros de una base de datos (por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 El `TableAdapter.Update` método suele usarse cuando la aplicación usa conjuntos de datos para almacenar los datos, mientras que el `TableAdapter.Delete` método suele usarse cuando la aplicación utiliza objetos para almacenar los datos.  
  
 Si el TableAdapter no tiene un `Delete` método, significa que el TableAdapter está configurado para usar los procedimientos almacenados, o su `GenerateDBDirectMethods` propiedad está establecida en `false`. Probar la configuración de TableAdapter `GenerateDBDirectMethods` propiedad `true` desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) y, a continuación, guarde el conjunto de datos para regenerar el TableAdapter. Si el TableAdapter no tiene todavía un `Delete` método y, a continuación, en la tabla probablemente no proporciona suficiente información para distinguir entre filas individuales (por ejemplo, no se establece ninguna clave principal en la tabla).  
  
## <a name="delete-records-using-tableadapters"></a>Eliminar registros mediante TableAdapters  
 Los TableAdapters proporcionan maneras diferentes para eliminar registros de una base de datos según los requisitos de la aplicación.  
  
 Si la aplicación usa conjuntos de datos para almacenar los datos simplemente se pueden eliminar registros de deseado <xref:System.Data.DataTable> en el <xref:System.Data.DataSet>y, a continuación, llame a la `TableAdapter.Update` método. El `TableAdapter.Update` método toma cualquier cambio en la tabla de datos y envía esos cambios a la base de datos (incluidos registros insertados, actualizados y eliminados).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Para eliminar registros de una base de datos utilizando el método TableAdapter.Update  
  
- Eliminar registros de la deseada <xref:System.Data.DataTable> eliminando <xref:System.Data.DataRow> objetos de la tabla. Para obtener más información, consulte [Cómo: eliminar filas en un objeto DataTable](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Después de que las filas se eliminan de la <xref:System.Data.DataTable>, llame a la `TableAdapter.Update` método. Puede controlar la cantidad de datos para actualizar al pasar de toda una matriz <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único <xref:System.Data.DataRow>. El código siguiente muestra cómo eliminar un registro de un <xref:System.Data.DataTable> y, a continuación, llame a la `TableAdapter.Update` método para comunicar el cambio y eliminar la fila de la base de datos. (Este ejemplo utiliza la base de datos Northwind `Region` tabla.)  
  
   [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
   [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
  Si la aplicación utiliza objetos para almacenar los datos en la aplicación, puede usar los métodos DBDirect del TableAdapter para eliminar datos directamente desde la base de datos. Una llamada a la `Delete` método elimina los registros de la base de datos según los valores de parámetro pasados.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Para eliminar registros de una base de datos utilizando el método TableAdapter.Delete  
  
-   Llamar a del TableAdapter `Delete` método, pasando los valores de cada columna como parámetros de la `Delete` método. (Este ejemplo utiliza la base de datos Northwind `Region` tabla.)  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Eliminar registros mediante objetos de comando  
 El ejemplo siguiente elimina registros directamente desde una base de datos mediante objetos de comando. Para obtener más información sobre el uso de objetos de comando para ejecutar comandos y procedimientos almacenados, vea [capturar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Para eliminar registros de una base de datos mediante objetos de comando  
  
-   Cree un nuevo objeto de comando, establezca su `Connection`, `CommandType`, y `CommandText` propiedades. (Este ejemplo utiliza la base de datos Northwind `Region` tabla.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Debe tener acceso a la base de datos a que está intentando conectarse, así como permiso para eliminar registros de la tabla deseada.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)   
 [Cómo: actualizar registros en una base de datos](../data-tools/how-to-update-records-in-a-database.md)   
 [Guardar datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Información general de aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)