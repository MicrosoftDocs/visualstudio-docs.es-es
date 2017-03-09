---
title: "At least one reference is missing the &#39;Name&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one reference is missing the &#39;Name&#39; attribute
Cada referencia debe tener una propiedad **Name** asociada, como se muestra a continuación:  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 Este error indica que no se ha encontrado la propiedad **Name** en al menos una referencia.  
  
 Es muy probable que el error esté causado por la edición manual del archivo de proyecto.  
  
 **Para corregir este error**  
  
-   Agregue otra vez la referencia.  
  
     Las referencias afectadas no se agregarán al proyecto.  
  
## Vea también  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)