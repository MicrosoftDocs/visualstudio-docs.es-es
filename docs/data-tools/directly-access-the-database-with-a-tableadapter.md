---
title: "C&#243;mo: Obtener acceso directamente a la base de datos con un TableAdapter | Microsoft Docs"
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
  - "bases de datos [Visual Basic], obtener acceso con TableAdapter"
  - "conjuntos de datos [Visual Basic], agregar a proyectos"
  - "DBDirect (métodos)"
  - "GenerateDbDirectMethods (propiedad)"
  - "guardar datos"
  - "TableAdapter.Delete (método)"
  - "TableAdapter.GenerateDBDirectMethods (propiedad)"
  - "TableAdapter.Insert (método)"
  - "TableAdapter.Update (método)"
  - "TableAdapters"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Obtener acceso directamente a la base de datos con un TableAdapter
Además de con los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos.  Se puede llamar a estos métodos \(`TableAdapter.Insert`, `TableAdapter.Update` y `TableAdapter.Delete`\) para manipular los datos directamente en la base de datos.  
  
 Si no desea crear estos métodos directos, establezca la propiedad `GenerateDbDirectMethods` de TableAdapter en `false` en la ventana **Propiedades**.  Cualquier consulta agregada a TableAdapter además de la consulta principal es una consulta independiente, no genera estos métodos DbDirect.  
  
## Envío de un comando directamente a la base de datos  
 Llame al método DbDirect de TableAdapter que realiza la tarea que está intentando llevar a cabo.  
  
#### Para insertar nuevos registros directamente en una base de datos  
  
-   Llame al método `Insert` del TableAdapter, pasando los valores de cada columna como parámetros.  El procedimiento siguiente utiliza la tabla `Region` de la base de datos Northwind como un ejemplo.  
  
    > [!NOTE]
    >  Si no dispone de ninguna instancia, cree la instancia de TableAdapter que desee usar.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### Para actualizar registros directamente en una base de datos  
  
-   Llame al método `Update` del TableAdapter, pasando los valores nuevos y originales de cada columna como parámetros.  
  
    > [!NOTE]
    >  Si no dispone de ninguna instancia, cree la instancia de TableAdapter que desee usar.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### Para eliminar registros directamente de una base de datos  
  
-   Llame al método `Delete` del TableAdapter, pasando los valores de cada columna como parámetros de `Delete`.  \(En este ejemplo se utiliza la tabla `Region` de la base de datos Northwind.\)  
  
    > [!NOTE]
    >  Si no dispone de ninguna instancia, cree la instancia de TableAdapter que desee usar.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## Vea también  
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comandos y parámetros](../Topic/Commands%20and%20Parameters.md)