---
title: "C&#243;mo: Actualizar los registros de una base de datos | Microsoft Docs"
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
  - "bases de datos, actualizar"
  - "registros, editar"
  - "registros, actualizar"
  - "TableAdapter.Update (método)"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Actualizar los registros de una base de datos
Puede utilizar el método `TableAdapter.Update` para actualizar \(editar\) los registros de una base de datos.  El método `TableAdapter.Update` proporciona varias sobrecargas que realizan operaciones diferentes que dependen de los parámetros pasados.  Es importante entender los resultados que se obtienen al llamar a estas firmas de método diferentes.  
  
> [!NOTE]
>  Si su aplicación no utiliza TableAdapters, puede utilizar objetos de comando para actualizar los registros de su base de datos \(por ejemplo, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  Para obtener más información sobre cómo actualizar datos con objetos de comando, vea "Actualizar registros mediante objetos de comando" más adelante.  
  
 La tabla siguiente describe el comportamiento de los distintos métodos `TableAdapter.Update`:  
  
|Método|Descripción|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Intenta guardar todos los cambios en <xref:System.Data.DataTable> en la base de datos.  \(Incluye quitar filas eliminadas de la tabla, agregar filas insertadas en la tabla y actualizar filas que han cambiado en la tabla.\)|  
|`TableAdapter.Update(DataSet)`|Aunque el parámetro toma un conjunto de datos, el TableAdapter intenta guardar todos los cambios en el objeto <xref:System.Data.DataTable> asociado del TableAdapter en la base de datos.  \(Incluye quitar filas eliminadas de la tabla, agregar filas insertadas en la tabla y actualizar filas que han cambiado en la tabla.\) **Note:**  El objeto <xref:System.Data.DataTable> asociado de un TableAdapter es el objeto <xref:System.Data.DataTable> creado durante la configuración original del TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Intenta guardar todos los cambios en el objeto <xref:System.Data.DataRow> indicado en la base de datos.|  
|`TableAdapter.Update(DataRows())`|Intenta guardar los cambios en cualquier fila de la matriz de <xref:System.Data.DataRow>s en la base de datos.|  
|`TableAdapter.Update("new column values", "original column values")`|Intenta guardar los cambios en una fila única que se identifica por los valores de columna originales.|  
  
 Normalmente utiliza el método `TableAdapter.Update` que toma <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o <xref:System.Data.DataRow> cuando su aplicación utiliza exclusivamente conjuntos de datos para almacenar los datos.  
  
 Normalmente utiliza el método `TableAdapter.Update` que toma valores de columna cuando su aplicación utiliza objetos para almacenar los datos.  
  
 Si el TableAdapter no dispone de un método `Update` que toma valores de columna, significa que el TableAdapter está configurado para utilizar procedimientos almacenados o que su propiedad `GenerateDBDirectMethods` está establecida en `false`.  Pruebe a establecer la propiedad `GenerateDBDirectMethods` de TableAdapter en `true` desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) y guarde el conjunto de datos para volver a generar el TableAdapter.  Si aun así el TableAdapter no dispone de un método `Update` que toma valores de columna, probablemente la tabla no proporciona información suficiente para distinguir entre filas individuales \(por ejemplo, la tabla no dispone de clave principal\).  
  
## Actualizar registros existentes mediante TableAdapters  
 Los TableAdapters proporcionan maneras diferentes de actualizar los registros de una base de datos en función de los requisitos de su aplicación.  
  
 Si la aplicación usa conjuntos de datos para almacenar los datos, puede actualizar simplemente los recursos en el objeto <xref:System.Data.DataTable> que desee y llamar después al método `TableAdapter.Update` y pasar los objetos <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> o una matriz de <xref:System.Data.DataRow>.  En la tabla anterior se describen los diferentes métodos `Update`.  
  
#### Para actualizar registros de una base de datos con el método TableAdapter.Update que toma DataSet, DataTable, DataRow o DataRows\(\)  
  
1.  Edite los registros en el objeto <xref:System.Data.DataTable> deseado editando directamente el objeto <xref:System.Data.DataRow> en <xref:System.Data.DataTable>.  Para obtener más información, vea [Cómo: Editar filas en un objeto DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).  
  
2.  Después de que las filas se editen en <xref:System.Data.DataTable>, llame al método `TableAdapter.Update`.  Puede controlar la cantidad de datos que se actualizan pasando un objeto <xref:System.Data.DataSet> completo, un objeto <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único objeto <xref:System.Data.DataRow>.  
  
     En el código siguiente se muestra cómo editar un registro en un objeto <xref:System.Data.DataTable> y cómo llamar al método `TableAdapter.Update` para guardar los cambios en la base de datos.  \(En este ejemplo se utiliza la tabla Region de la base de datos Northwind.\)  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 Si la aplicación utiliza objetos para almacenar los datos, puede utilizar los métodos `DBDirect` del TableAdapter para enviar datos de los objetos directamente a la base de datos.  Estos métodos permiten pasar valores individuales de cada columna como parámetros de método.  Al llamar a este método, se actualiza un registro existente en la base de datos con los valores de columna pasados en el método.  
  
 El procedimiento siguiente utiliza la tabla `Region` de Northwind como un ejemplo.  
  
#### Para actualizar los registros de una base de datos utilizando el método TableAdapter.Update que toma valores de columna  
  
-   Llame al método `Update` del TableAdapter, pasando los valores nuevos y originales de cada columna como parámetros.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia de TableAdapter que desee utilizar.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## Actualizar registros mediante objetos de comando  
 El ejemplo siguiente actualiza directamente los registros existentes en una base de datos utilizando objetos de comando.  Para obtener más información sobre el uso de objetos de comando para ejecutar comandos y procedimientos almacenados, vea [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
 El procedimiento siguiente utiliza la tabla `Region` de Northwind como un ejemplo.  
  
#### Para actualizar registros existentes en una base de datos utilizando objetos de comando  
  
-   Cree un nuevo objeto de comando; establezca sus propiedades `Connection`, `CommandType` y `CommandText` y, a continuación, abra una conexión y ejecute el comando.  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## Seguridad de .NET Framework  
 Debe tener acceso a la base de datos con la que intenta conectarse, así como permiso para actualizar registros en la tabla deseada.  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Eliminar registros de una base de datos](../data-tools/how-to-delete-records-in-a-database.md)   
 [Cómo: Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)   
 [Cómo: Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)