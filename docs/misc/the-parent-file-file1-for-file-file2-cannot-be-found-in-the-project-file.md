---
title: "The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_dependency"
ms.assetid: 1902c0b5-d09d-49b9-8f71-e325f7b9cfd7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file
El sistema del proyecto no encuentra ningún nodo que corresponda a un archivo.  
  
 Los archivos dependientes se almacenan en el archivo de proyecto agregando un atributo `DependentUpon` al nodo `<File>`.  Por ejemplo:  
  
```  
<File  
    RelPath = "Form1.resx"  
    SubType = "Code"  
    BuildAction = "EmbeddedResource"  
    DependentUpon="Form1.vb"  
/>  
```  
  
 Esto hará que Form1.resx aparezca debajo de Form1.vb en la jerarquía de proyecto.  
  
 Es muy probable que el error esté causado por la edición manual del archivo de proyecto.  
  
### Para corregir este error  
  
-   Edite y actualice el archivo de proyecto.  
  
     Los archivos afectados se agregarán al proyecto, aunque no se conservará la dependencia.  
  
## Vea también  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)