---
title: "Se est&#225; haciendo referencia indirecta al ensamblado &lt;assemblyname&gt;, versi&#243;n &lt;laterversionnumber&gt;, que contiene &#39;&lt;typename&gt;&#39; | Microsoft Docs"
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
  - "vbc32207"
  - "bc32207"
helpviewer_keywords: 
  - "BC32207"
ms.assetid: a3de74b5-bedd-4e36-b379-485e4b3903f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se est&#225; haciendo referencia indirecta al ensamblado &lt;assemblyname&gt;, versi&#243;n &lt;laterversionnumber&gt;, que contiene &#39;&lt;typename&gt;&#39;
Se está haciendo referencia indirecta al ensamblado \<assemblyname\>, versión \<laterversionnumber\>, que contiene '\<typename\>'. Este proyecto hace referencia a una versión anterior de \<assemblyname\>, versión \<earlierversionnumber\>. Para utilizar '\<typename\>', debe reemplazar la referencia a \<assemblyname\> por la versión \<laterversionnumber\> o una versión posterior.  
  
 Una expresión realiza una referencia indirecta a otro proyecto, que tiene una referencia a una versión anterior del mismo ensamblado.  
  
 Normalmente, debe usar solo la versión más reciente de un ensamblado.  
  
 **Identificador de error:** BC32207  
  
### Para corregir este error  
  
1.  Use el nombre de tipo indicado para determinar qué proyecto también hace referencia al mismo ensamblado.  
  
2.  Determine la versión del ensamblado a la que hace referencia el otro proyecto y modifique su proyecto para que haga referencia a la misma versión.  
  
## Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)