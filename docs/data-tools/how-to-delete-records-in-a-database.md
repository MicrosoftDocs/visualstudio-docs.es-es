---
title: "C&#243;mo: Eliminar registros de una base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], guardar"
  - "bases de datos, eliminar registros"
  - "eliminar datos"
  - "registros, eliminar"
  - "guardar datos"
  - "TableAdapter.Delete (método)"
  - "TableAdapter.Update (método)"
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Eliminar registros de una base de datos
Para eliminar registros de una base de datos, utilice el método `TableAdapter.Update` o el método `TableAdapter.Delete`.  Si su aplicación no utiliza TableAdapters, puede utilizar objetos de comando para eliminar registros de una base de datos \(por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  
  
 Generalmente se utiliza el método `TableAdapter.Update` cuando la aplicación utiliza conjuntos de datos para almacenar datos, en tanto que se utiliza el método `TableAdapter.Delete` cuando la aplicación utiliza objetos para almacenar los datos.  
  
 Si el TableAdapter no dispone de un método `Delete`, significa que el TableAdapter está configurado para utilizar procedimientos almacenados o que su propiedad `GenerateDBDirectMethods` está establecida en `false`.  Pruebe a establecer la propiedad `GenerateDBDirectMethods` de TableAdapter en `true` desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) y guarde el conjunto de datos para volver a generar el TableAdapter.  Si aun así el TableAdapter no dispone de un método `Delete`, probablemente la tabla no proporciona información suficiente para distinguir entre filas individuales \(por ejemplo, la tabla no dispone de clave principal\).  
  
## Eliminar registros mediante TableAdapters  
 Los TableAdapters proporcionan maneras diferentes de eliminar registros de una base de datos en función de los requisitos de su aplicación.  
  
 Si la aplicación utiliza conjuntos de datos para almacenar datos, puede eliminar los registros del conjunto <xref:System.Data.DataTable> deseado en <xref:System.Data.DataSet> y, a continuación, llamar al método `TableAdapter.Update`.  El método `TableAdapter.Update` toma cualquier cambio en la tabla de datos y envía esos cambios a la base de datos \(incluidos registros insertados, actualizados y eliminados\).  
  
#### Para eliminar registros de una base de datos utilizando el método TableAdapter.Update  
  
-   Elimine los registros del <xref:System.Data.DataTable> deseado eliminando los objetos <xref:System.Data.DataRow> de la tabla.  Para obtener más información, vea [Cómo: Eliminar filas en un DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).  Después de que las filas se eliminen de <xref:System.Data.DataTable>, llame al método `TableAdapter.Update`.  Puede controlar la cantidad de datos que se actualizan pasando un objeto <xref:System.Data.DataSet> completo, un objeto <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único objeto <xref:System.Data.DataRow>.  En el código siguiente se muestra cómo eliminar un registro de un objeto <xref:System.Data.DataTable> y cómo llamar al método `TableAdapter.Update` para comunicar el cambio y eliminar la fila de la base de datos.  \(En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind.\)  
  
     [!code-vb[VbRaddataSaving#20](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#20](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_1.cs)]  
  
 Si la aplicación utiliza objetos para almacenar los datos, puede utilizar los métodos DBDirect del TableAdapter para eliminar datos de los objetos directamente en la base de datos.  Al llamar al método `Delete`, se quitan registros de la base de datos basándose en los valores de parámetro pasados.  
  
#### Para eliminar registros de una base de datos utilizando el método TableAdapter.Delete  
  
-   Llame al método `Delete` del TableAdapter, pasando los valores de cada columna como parámetros de `Delete`.  \(En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind.\)  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia de TableAdapter que desee utilizar.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_2.cs)]  
  
## Eliminar registros mediante objetos de comando  
 El ejemplo siguiente elimina directamente registros de una base de datos utilizando objetos de comando.  Para obtener más información sobre el uso de objetos de comando para ejecutar comandos y procedimientos almacenados, vea [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
#### Para eliminar registros de una base de datos mediante objetos de comando  
  
-   Cree un nuevo objeto de comando, establezca sus propiedades `Connection`, `CommandType` y `CommandText`.  \(En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind.\)  
  
     [!code-vb[VbRaddataSaving#22](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#22](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_3.cs)]  
  
## Seguridad de .NET Framework  
 Debe tener acceso a la base de datos con la que intenta conectarse, así como permiso para eliminar registros de la tabla deseada.  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)   
 [Cómo: Actualizar los registros de una base de datos](../data-tools/how-to-update-records-in-a-database.md)   
 [Cómo: Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)