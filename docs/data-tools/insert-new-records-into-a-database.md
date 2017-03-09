---
title: "C&#243;mo: Insertar nuevos registros en una base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "bases de datos, insertar nuevos registros"
  - "registros, insertar"
  - "guardar datos"
  - "TableAdapters, insertar nuevos registros"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Insertar nuevos registros en una base de datos
Para insertar nuevos registros en una base de datos, puede utilizar el método `TableAdapter.Update` o uno de los métodos DBDirect del TableAdapter \(concretamente el método `TableAdapter.Insert`\).  Para obtener más información, vea [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Si su aplicación no utiliza TableAdapters, puede utilizar objetos de comando para interactuar e insertar nuevos registros en la base de datos \(por ejemplo, <xref:System.Data.SqlClient.SqlCommand>\).  
  
 Utilice el método `TableAdapter.Update` cuando su aplicación utilice conjuntos de datos para almacenar los datos.  El método `Update` envía todos los cambios \(actualizaciones, inserciones y eliminaciones\) a la base de datos.  
  
 Utilice el método `TableAdapter.Insert` cuando la aplicación utilice objetos para almacenar datos o cuando desee conseguir mayor control sobre la creación de registros en la base de datos.  
  
 Si el TableAdapter no dispone de un método `Insert`, significa que el TableAdapter está configurado para utilizar procedimientos almacenados o que su propiedad `GenerateDBDirectMethods` está establecida en `false`.  Pruebe a establecer la propiedad `GenerateDBDirectMethods` de TableAdapter en `true` desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) y guarde el conjunto de datos para volver a generar el TableAdapter.  Si aun así el TableAdapter no dispone de un método `Insert`, probablemente la tabla no proporciona información suficiente para distinguir entre filas individuales \(por ejemplo, la tabla no dispone de clave principal\).  
  
## Insertar nuevos registros utilizando TableAdapters  
 Los TableAdapters proporcionan maneras diferentes de insertar nuevos registros en una base de datos en función de los requisitos de su aplicación.  
  
 Si la aplicación utiliza conjuntos de datos para almacenar datos, puede agregar nuevos registros al objeto <xref:System.Data.DataTable> del conjunto de datos y, a continuación, llamar al método `TableAdapter.Update`.  El método `TableAdapter.Update` toma cualquier cambio en <xref:System.Data.DataTable> y envía esos cambios a la base de datos \(incluidos registros modificados y eliminados\).  
  
#### Para insertar nuevos registros en una base de datos utilizando el método TableAdapter.Update  
  
1.  Agregue nuevos registros al objeto <xref:System.Data.DataTable> deseado creando un nuevo <xref:System.Data.DataRow> y agregándolo a la colección <xref:System.Data.DataTable.Rows%2A>.  Para obtener más información, vea [Cómo: Agregar filas a un DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).  
  
2.  Después de que las filas se agreguen en <xref:System.Data.DataTable>, llame al método `TableAdapter.Update`.  Puede controlar la cantidad de datos que se actualizan pasando un objeto <xref:System.Data.DataSet> completo, un objeto <xref:System.Data.DataTable>, una matriz de <xref:System.Data.DataRow>s o un único objeto <xref:System.Data.DataRow>.  
  
     En el código siguiente se muestra cómo agregar un nuevo registro en un objeto <xref:System.Data.DataTable> y cómo llamar al método `TableAdapter.Update` para guardar la nueva fila en la base de datos.  \(En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind.\)  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 Si la aplicación utiliza objetos para almacenar los datos, puede utilizar el método `TableAdapter.Insert` para crear nuevas filas directamente en la base de datos.  El método `Insert` acepta los valores individuales de cada columna como parámetros.  Al llamar al método, se inserta un nuevo registro en la base de datos con los valores de parámetro pasados.  
  
 El procedimiento siguiente utiliza la tabla `Region` de la base de datos Northwind como un ejemplo.  
  
#### Para insertar nuevos registros en una base de datos utilizando el método TableAdapter.Insert  
  
-   Llame al método `Insert` del TableAdapter, pasando los valores de cada columna como parámetros.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia de TableAdapter que desee utilizar.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## Insertar nuevos registros mediante objetos de comando  
 El ejemplo siguiente inserta nuevos registros directamente en una base de datos utilizando objetos de comando.  Para obtener más información sobre el uso de objetos de comando para ejecutar comandos y procedimientos almacenados, vea [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
 El procedimiento siguiente utiliza la tabla `Region` de la base de datos Northwind como un ejemplo.  
  
#### Para insertar nuevos registros en una base de datos utilizando objetos de comando  
  
-   Cree un nuevo objeto de comando, establezca sus propiedades `Connection`, `CommandType` y `CommandText`.  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## Seguridad de .NET Framework  
 Debe tener acceso a la base de datos con la que intenta conectarse, así como permiso para realizar inserciones en la tabla deseada.  
  
## Vea también  
 [Cómo: Eliminar registros de una base de datos](../data-tools/how-to-delete-records-in-a-database.md)   
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
 [Recuperar valores de identidad o de autonumeración](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)