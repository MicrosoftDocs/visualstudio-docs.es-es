---
title: "C&#243;mo: Guardar cambios de un conjunto de datos en una base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DbDataAdapter.Update"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], guardar"
  - "bases de datos, actualizar"
  - "actualizar conjuntos de datos, escribir cambios en el origen de datos"
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Guardar cambios de un conjunto de datos en una base de datos
Después de modificar y validar los datos en el conjunto de datos, probablemente desee devolver los datos actualizados a una base de datos.  Para enviar los datos modificados a una base de datos, llame al método `Update` de un [TableAdapter](../data-tools/tableadapter-overview.md) o de un adaptador de datos.  El método `Update` del adaptador actualiza una sola tabla de datos y ejecuta el comando correcto \(INSERT, UPDATE o DELETE\) basándose en el <xref:System.Data.DataRow.RowState%2A> de cada fila de datos de la tabla.  
  
 Cuando se guardan datos en tablas relacionadas, Visual Studio proporciona un nuevo componente TableAdapterManager que permite guardar en el orden correcto basándose en las restricciones FOREIGN KEY definidas en la base de datos.  Para obtener más información, vea [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Dado que intentar actualizar un origen de datos con el contenido de un conjunto de datos puede producir errores, debe colocar el código que llama al método `Update` del adaptador dentro de un bloque `try`\/`catch`.  
  
 Aunque el procedimiento exacto para actualizar un origen de datos varía dependiendo de las necesidades de la empresa, la aplicación debe incluir los siguientes pasos:  
  
1.  Ejecute código que intenta enviar actualizaciones a la base de datos dentro de un bloque `try`\/`catch`.  
  
2.  Si se detecta una excepción, buscar la fila de datos que causó el error.  Para obtener más información, vea [Cómo: Localizar filas con errores](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Resuelva el problema de la fila de datos \(si es posible, mediante programación o presentando la fila incorrecta al usuario para que la modifique\) y después vuelva a intentar la actualización \(propiedad <xref:System.Data.DataRow.HasErrors%2A>, método <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Guardar los datos en una base de datos  
 Llame al método `Update` de un objeto TableAdapter o adaptador de datos, pasando el nombre de la tabla de datos que contiene los valores que se van a escribir en la base de datos.  Para obtener más información sobre cómo guardar los datos de una única tabla de datos en una base de datos, vea [Tutorial: Guardar datos en una base de datos \(Tabla única\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
#### Para actualizar una base de datos con un conjunto de datos utilizando un objeto TableAdapter  
  
-   Incluya el método `TableAdapter.Update` dentro de un bloque `try`\/`catch`.  El ejemplo siguiente muestra cómo intentar una actualización con el contenido de la tabla `Customers` del conjunto de datos `NorthwindDataSet`.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_1.vb)]  
  
#### Para actualizar una base de datos con un conjunto de datos utilizando un adaptador de datos  
  
-   Incluya el método `DataAdapter.Update` dentro de un bloque `try`\/`catch`.  El ejemplo siguiente muestra cómo intentar una actualización en un origen de datos con el contenido de `Table1` en `DataSet1`.  
  
     [!code-vb[VbRaddataSaving#26](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#26](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_2.cs)]  
  
## Actualizar dos tablas relacionadas de un conjunto de datos  
 Al actualizar tablas relacionadas en un conjunto de datos, es importante hacerlo en el orden correcto para reducir la posibilidad de infringir las restricciones de integridad referencial.  El orden de ejecución de los comandos también seguirá los índices de <xref:System.Data.DataRowCollection> en el conjunto de datos.  Para evitar que se produzcan errores de integridad de datos, se recomienda actualizar la base de datos en el siguiente orden:  
  
1.  Tabla secundaria: eliminar registros.  
  
2.  Tabla principal: insertar, actualizar y eliminar registros.  
  
3.  Tabla secundaria: insertar y actualizar registros.  
  
 Para obtener información detallada sobre cómo guardar los datos de varias tablas, vea [Tutorial: Guardar datos en una base de datos \(Varias tablas\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
 Si va a actualizar dos o más tablas relacionadas, debe incluir toda la lógica de actualización dentro de una transacción.  Una transacción es un proceso que asegura que todos los cambios relacionados con una base de datos son correctos antes de confirmar cualquier cambio.  Para obtener más información, vea [Transacciones y simultaneidad](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Para actualizar dos tablas relacionadas mediante un objeto TableAdapter  
  
1.  Cree tres <xref:System.Data.DataTable>s temporales para contener los registros que no son iguales.  
  
2.  Llame al método `Update` para cada subconjunto de filas desde dentro de un bloque `try`\/`catch`.  Si se producen errores de actualización, la acción sugerida es separarlos y resolverlos.  
  
3.  Confirmar los cambios desde el conjunto de datos en la base de datos.  
  
4.  Elimine las tablas de datos temporales para liberar los recursos.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_3.cs)]  
  
#### Para actualizar dos tablas relacionadas mediante un adaptador de datos  
  
-   Llame al método `Update` de cada adaptador de datos.  
  
     En el ejemplo siguiente, se muestra cómo actualizar un origen de datos con un conjunto de datos que contiene tablas relacionadas.  Para seguir el orden anterior, se crean tres tablas <xref:System.Data.DataTable>s temporales donde se incluirán los registros que no son iguales.  Después, se llama al método `Update` para cada subconjunto de filas desde dentro de un bloque `try`\/`catch`.  Si se producen errores de actualización, la acción sugerida es separarlos y resolverlos.  Después, el conjunto de datos confirma los cambios.  Por último, las tablas de datos provisionales se eliminan para liberar los recursos.  
  
     [!code-vb[VbRaddataSaving#28](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_4.vb)]
     [!code-cs[VbRaddataSaving#28](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_4.cs)]  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)