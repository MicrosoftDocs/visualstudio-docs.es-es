---
title: "An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.reference_load_error"
ms.assetid: 0e922611-197b-4607-bc31-03f80bd3e7e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An error has been encountered that prevents reference &#39;reference&#39; from loading. &lt;reason&gt;
Se ha encontrado un error irrecuperable al quitar una referencia del archivo de proyecto.  Las causas de este error se identifican en \<Causa\> y podrían ser:  
  
-   GUID \(*global unique ID*, identificador único global\) incorrecto para una referencia.  Esto se sólo aplica a referencias COM.  
  
-   Herramienta contenedor incorrecta.  Actualmente, la propiedad de la herramienta contenedor puede ser tlbimp, aximp o primary.  Esto se sólo aplica a referencias COM.  
  
-   Cadena de referencia al proyecto incorrecta.  Esto sólo se aplica a referencias entre proyectos.  
  
 **Para corregir este error**  
  
-   Agregue la referencia al proyecto para resolver este error.  
  
     No se cargará en el proyecto ninguna referencia para la que se muestre este diagnóstico.  
  
## Vea también  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/es-es/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)