---
title: "Proyecto ya tiene una referencia al ensamblado &lt;assemblyidentity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32208"
  - "vbc32208"
helpviewer_keywords: 
  - "BC32208"
ms.assetid: a9f73a2c-5135-4315-bf2c-710ef216095d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proyecto ya tiene una referencia al ensamblado &lt;assemblyidentity&gt;
Proyecto ya tiene una referencia al ensamblado \<assemblyidentity\>. No se puede agregar una segunda referencia a '\<filepath\>'.  
  
 Un proyecto realiza más de una referencia al mismo ensamblado.  
  
 La identidad del ensamblado incluye el nombre del ensamblado, la versión, la clave pública, si existe, y la referencia cultural.  
  
 Una posible causa de este error es que se haya hecho referencia a otra copia del ensamblado a través de una ruta de acceso de archivo distinta de la de la referencia original.  
  
 **Identificador de error:** BC32208  
  
### Para corregir este error  
  
-   Quite la segunda referencia. No es necesario porque hace referencia al mismo ensamblado.  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)