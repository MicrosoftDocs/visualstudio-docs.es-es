---
title: "C&#243;mo: Actualizar datos utilizando un TableAdapter | Microsoft Docs"
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
  - "datos [Visual Studio], TableAdapters"
  - "datos [Visual Studio], actualizar"
  - "guardar datos"
  - "TableAdapters, actualizar datos"
  - "actualizar datos, TableAdapters"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Actualizar datos utilizando un TableAdapter
Después de modificar y validar los datos en el conjunto de datos, probablemente desee devolver los datos actualizados a una base de datos.  Para enviar los datos modificados a una base de datos, llame al método `Update` de un [TableAdapter](../data-tools/tableadapter-overview.md).  El método `Update` del adaptador actualizará una tabla de datos única y ejecutará el comando correcto \(INSERT, UPDATE o DELETE\) basándose en el <xref:System.Data.DataRow.RowState%2A> de cada fila de datos de la tabla.  Cuando se guardan datos en tablas relacionadas, Visual Studio proporciona un nuevo componente TableAdapterManager que permite guardar en el orden correcto basándose en las restricciones FOREIGN KEY definidas en la base de datos.  Para obtener más información, vea [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Dado que al intentar actualizar un origen de datos con el contenido de un conjunto de datos se pueden producir errores, debe colocar el código que llama al método `Update` del adaptador dentro de un bloque `try`\/`catch`.  
  
 Aunque el procedimiento exacto para actualizar un origen de datos varía dependiendo de las necesidades de la empresa, la aplicación debe incluir los siguientes pasos:  
  
1.  Llame al método `Update` del adaptador dentro de un bloque `try`\/`catch`.  
  
2.  Si se detecta una excepción, buscar la fila de datos que causó el error.  Para obtener más información, vea [Cómo: Localizar filas con errores](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Resuelva el problema de la fila de datos \(si es posible, mediante programación o presentando la fila incorrecta al usuario para que la modifique\) y después vuelva a intentar la actualización \(<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Guardar los datos en una base de datos  
 Llame al método `Update` de un TableAdapter, pasando el nombre de la tabla de datos que contiene los valores que se van a escribir en la base de datos.  
  
#### Para actualizar una base de datos que tiene un conjunto de datos mediante un TableAdapter  
  
-   Incluya el método `Update` del adaptador dentro de un bloque `try`\/`catch`.  El ejemplo siguiente muestra cómo intentar una actualización desde dentro de un bloque `try`\/`catch` con el contenido de la tabla `Customers` en `NorthwindDataSet`.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## Actualización de dos tablas relacionadas de un objeto Dataset con un objeto TableAdapter  
 Al actualizar tablas relacionadas en un conjunto de datos, es importante hacerlo en el orden correcto para reducir la posibilidad de infringir las restricciones de integridad referencial.  El orden de ejecución de los comandos también seguirá los índices de <xref:System.Data.DataRowCollection> en el conjunto de datos.  Para evitar que se produzcan errores de integridad de datos, se recomienda actualizar la base de datos en el siguiente orden:  
  
1.  Tabla secundaria: eliminar registros.  
  
2.  Tabla principal: insertar, actualizar y eliminar registros.  
  
3.  Tabla secundaria: insertar y actualizar registros.  
  
    > [!NOTE]
    >  Si va a actualizar dos o más tablas relacionadas, debe incluir toda la lógica de actualización dentro de una transacción.  Una transacción es un proceso que asegura que todos los cambios relacionados con una base de datos son correctos antes de confirmar cualquier cambio.  Para obtener más información, vea [Transacciones y simultaneidad](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Para actualizar dos tablas relacionadas mediante un objeto TableAdapter  
  
1.  Cree tres tablas de datos temporales para los registros que no son iguales.  
  
2.  Llame al método `Update` para cada subconjunto de filas desde dentro de un bloque `try`\/`catch`.  Si se producen errores en la actualización, se debería preparar una ramificación de salida para resolverlos.  
  
3.  Confirme los cambios en la base de datos.  
  
4.  Elimine las tablas de datos temporales para liberar los recursos.  
  
     En el ejemplo siguiente, se muestra cómo actualizar un origen de datos con un conjunto de datos que contiene tablas relacionadas.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)