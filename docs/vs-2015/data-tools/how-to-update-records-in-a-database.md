---
title: 'Cómo: actualizar registros en una base de datos | Microsoft Docs'
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b62dc86425dcbebb225c66eecd51505f674e20ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949037"
---
# <a name="how-to-update-records-in-a-database"></a>Cómo: Actualizar los registros de una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar el `TableAdapter.Update` método para actualizar (Editar) de los registros en una base de datos. El `TableAdapter.Update` método proporciona varias sobrecargas que realizan operaciones diferentes dependiendo de los parámetros pasados en. Es importante entender los resultados de llamar a estas firmas de método diferentes.  
  
> [!NOTE]
>  Si la aplicación no usa los TableAdapters, a continuación, puede utilizar objetos de comando para actualizar registros en la base de datos (por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Para obtener más información sobre cómo actualizar datos con objetos de comando, vea "Actualizar registros mediante objetos de comando" a continuación.  
  
 En la tabla siguiente se describe el comportamiento de los diversos `TableAdapter.Update` métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Intenta guardar todos los cambios en el <xref:System.Data.DataTable> a la base de datos. (Esto incluye quitar filas eliminadas de la tabla, agregar filas insertadas en la tabla y actualizar filas en la tabla que han cambiado).|  
|`TableAdapter.Update(DataSet)`|Aunque el parámetro toma un conjunto de datos, los intentos de TableAdapter para guardar los cambios en el TableAdapter asociado del <xref:System.Data.DataTable> a la base de datos. (Esto incluye quitar filas eliminadas de la tabla, agregar filas insertadas en la tabla y actualizar filas en la tabla que han cambiado). **Nota:** asociada al TableAdapter <xref:System.Data.DataTable> es el <xref:System.Data.DataTable> creado cuando se configuró originalmente el TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Intenta guardar los cambios en el indicado <xref:System.Data.DataRow> a la base de datos.|  
|`TableAdapter.Update(DataRows())`|Intenta guardar los cambios en cualquier fila de la matriz de <xref:System.Data.DataRow>s a la base de datos.|  
|`TableAdapter.Update("new column values", "original column values")`|Intenta guardar los cambios en una sola fila que se identifica mediante los valores de columna original.|  
  
 Normalmente, se utiliza el `TableAdapter.Update` método que toma un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o <xref:System.Data.DataRow>(s) cuando la aplicación usa conjuntos de datos exclusivamente para almacenar datos.  
  
 Normalmente, se utiliza el `TableAdapter.Update` método que toma los valores de columna cuando la aplicación utiliza objetos para almacenar los datos.  
  
 Si el TableAdapter no tiene un `Update` método que toma los valores de columna, significa que el TableAdapter está configurado para utilizar procedimientos almacenados o sus `GenerateDBDirectMethods` propiedad está establecida en `false`. Probar la configuración de TableAdapter `GenerateDBDirectMethods` propiedad `true` desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) y, a continuación, guarde el conjunto de datos para regenerar el TableAdapter. Si el TableAdapter no tiene todavía un `Update` método que toma los valores de columna y, a continuación, en la tabla probablemente no proporciona suficiente información para distinguir entre filas individuales (por ejemplo, no se establece ninguna clave principal en la tabla).  
  
## <a name="update-existing-records-using-tableadapters"></a>Actualizar registros existentes mediante TableAdapters  
 Los TableAdapters proporcionan maneras diferentes para actualizar registros en una base de datos según los requisitos de la aplicación.  
  
 Si la aplicación usa conjuntos de datos para almacenar datos, a continuación, simplemente puede actualizar los registros de la deseada <xref:System.Data.DataTable> y, a continuación, llame a la `TableAdapter.Update` método y pase la <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matriz de <xref:System.Data.DataRow>s. La tabla anterior describe los diferentes `Update` métodos.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Para actualizar registros en una base de datos con el método TableAdapter.Update que toma DataSet, DataTable, DataRow o DataRows()  
  
1. Editar registros en deseado <xref:System.Data.DataTable> editando directamente el <xref:System.Data.DataRow> en el <xref:System.Data.DataTable>. Para obtener más información, consulte [Cómo: Editar filas en un objeto DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2. Después de las filas que se editan en el <xref:System.Data.DataTable>, llame a la `TableAdapter.Update` método. Puede controlar la cantidad de datos que se va a actualizar, pasando toda una <xref:System.Data.DataSet>, un <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único <xref:System.Data.DataRow>.  
  
    El código siguiente muestra cómo editar un registro en un <xref:System.Data.DataTable> y, a continuación, llame a la `TableAdapter.Update` método para guardar los cambios en la base de datos. (En este ejemplo se utiliza la tabla de región de base de datos Northwind.)  
  
    [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
    [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
   Si la aplicación utiliza objetos para almacenar los datos en la aplicación, puede utilizar el TableAdapter `DBDirect` métodos para enviar datos de los objetos directamente a la base de datos. Estos métodos permiten pasar valores individuales para cada columna como parámetros de método. Llamar a este método actualiza un registro existente en la base de datos con los valores de columna que se pasa al método.  
  
   El siguiente procedimiento usa Northwind `Region` tabla como ejemplo.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Para actualizar registros en una base de datos utilizando el método TableAdapter.Update que toma los valores de columna  
  
-   Llamar a del TableAdapter `Update` método, pasando los valores nuevos y originales de cada columna como parámetros.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Actualizar registros mediante objetos de comando  
 El ejemplo siguiente actualiza los registros existentes directamente en una base de datos mediante objetos de comando. Para obtener más información sobre el uso de objetos de comando para ejecutar comandos y procedimientos almacenados, vea [capturar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
 El siguiente procedimiento usa Northwind `Region` tabla como ejemplo.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Para actualizar registros existentes en una base de datos mediante objetos de comando  
  
-   Cree un nuevo objeto de comando; Establezca su `Connection`, `CommandType`, y `CommandText` propiedades; y, a continuación, abra una conexión y ejecute el comando.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Debe tener acceso a la base de datos a que está intentando conectarse, así como permiso para actualizar registros en la tabla deseada.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: eliminar registros en una base de datos](../data-tools/how-to-delete-records-in-a-database.md)   
 [Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)   
 [Guardar datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Información general de aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)