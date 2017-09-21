---
title: "Editar datos en conjuntos de datos | Microsoft Docs"
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
  - "datos [Visual Studio], editar en conjuntos de datos"
  - "conjuntos de datos [Visual Basic], editar datos"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Editar datos en conjuntos de datos
La edición de los datos en <xref:System.Data.DataSet> es el proceso de manipular los datos reales en los objetos <xref:System.Data.DataTable> individuales que constituyen un conjunto de datos.  Los datos de las tablas de datos se editan de forma muy similar a como edita los datos de una tabla de una base de datos; el proceso puede incluir insertar, actualizar y eliminar registros de la tabla.  
  
 Además de cambiar los datos reales, puede consultar un objeto <xref:System.Data.DataTable> para devolver filas específicas de datos, por ejemplo, filas individuales, versiones específicas de filas \(original y propuesta\), sólo filas que han cambiado o filas con errores.  
  
## Tareas comunes de tablas de datos  
 La tabla siguiente proporciona vínculos a las tareas comunes asociadas con la edición y la consulta de datos de un conjunto de datos:  
  
|Tarea|Descripción|  
|-----------|-----------------|  
|Insertar nuevos registros en una tabla de datos.|Crea un nuevo <xref:System.Data.DataRow> y lo agrega a la colección de filas de la tabla.  Para obtener más información, vea [Cómo: Agregar filas a un DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|Actualizar registros existentes en una tabla de datos.|Asigna un valor directamente a la columna específica de una fila de datos.  Para obtener más información, vea [Cómo: Editar filas en un objeto DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).|  
|Eliminar registros existentes de una tabla de datos.|Llama al método <xref:System.Data.DataRow.Delete%2A> de la fila de datos que se desea quitar de la tabla.  Para obtener más información, vea [Cómo: Eliminar filas en un DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).|  
|Localizar registros cambiados en una tabla de datos.|Llama al método <xref:System.Data.DataTable.GetChanges%2A> de una tabla de datos.  Para obtener más información, vea [Cómo: Recuperar filas modificadas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).|  
|Obtener acceso a versiones diferentes de una fila en una tabla de datos.|Obtiene acceso a las columnas individuales de una fila de datos pasando el elemento <xref:System.Data.DataRowVersion> que se desea ver.  Para obtener más información, vea [Cómo: Obtener versiones específicas de una fila de datos](../data-tools/how-to-get-specific-versions-of-a-datarow.md).|  
|Localizar filas con errores en una tabla de datos.|Inspecciona la propiedad <xref:System.Data.DataTable.HasErrors%2A> de una tabla de datos.  Para obtener más información, vea [Cómo: Localizar filas con errores](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).|  
  
## Vea también  
 [DataTables](../Topic/DataTables.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [DataTables](../Topic/DataTables.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)