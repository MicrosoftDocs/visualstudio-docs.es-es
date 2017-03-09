---
title: "Soluci&#243;n de problemas de excepciones: System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NoNullAllowedException (clase)"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.NoNullAllowedException
Cuando se intenta insertar un valor nulo en una columna donde el valor de la propiedad <xref:System.Data.NoNullAllowedException> está establecido en <xref:System.Data.DataColumn.AllowDBNull%2A>, se produce una excepción `false`.  
  
## Sugerencias asociadas  
 **Compruebe que el valor sea de tipo DBNull antes de agregárselo a la columna.**  
 Si la propiedad <xref:System.Data.DataColumn.AllowDBNull%2A> está establecida en `false`, no podrá insertar un valor nulo. Para obtener más información, consulta <xref:System.DBNull>.  
  
 **Establezca AllowDBNull en true.**  
 Si establece esta propiedad en `true`, podrá insertar valores nulos. Para obtener más información, consulta <xref:System.Data.DataColumn.AllowDBNull%2A>.  
  
## Comentarios  
 Si utiliza los botones de navegación para desplazarse por los registros de una tabla de base de datos en un formulario de datos, esta excepción puede producirse con la información adicional "La columna 'columna' no permite tener valores nulos". Este comportamiento se produce cuando la clave principal o la columna "not NULL" de la tabla de base de datos no se seleccionan en el Asistente para formularios de datos. Si la clave principal o la columna "not NULL" de la base de datos no se han seleccionado en el Asistente para formularios de datos al crear el formulario de datos, la opción **Agregar \- Crea un nuevo registro** no estará deshabilitada. Para evitar este problema, seleccione las columnas siguientes de la tabla seleccionada al agregar un formulario de datos usando el Asistente para formularios de datos: la columna principal y una columna que no permita valores nulos \(NULL\).  
  
## Vea también  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)