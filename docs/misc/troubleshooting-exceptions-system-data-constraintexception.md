---
title: "Soluci&#243;n de problemas de excepciones: System.Data.ConstraintException | Microsoft Docs"
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
  - "ConstraintException (clase)"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.ConstraintException
Se produce una excepción <xref:System.Data.ConstraintException> cuando se intenta realizar una acción que infringe una restricción.  
  
## Sugerencias asociadas  
 **Amplíe o desactive las restricciones en el conjunto de datos**.  
 Puede utilizar la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> para desactivar temporalmente las restricciones mientras se rellenan las tablas en un objeto <xref:System.Data.DataSet>.  
  
 **Asegúrese de que no intenta asignar un valor a un campo de clave principal donde la clave principal ya existe en la tabla de datos.**  
 Si la clave principal ya existe, se produce esta excepción.  
  
 **Borrar conjuntos de datos antes de cargarlos del estado de vista.**  
 Si hay datos en el conjunto de datos cuando lo carga, se puede producir esta excepción.  
  
## Vea también  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)