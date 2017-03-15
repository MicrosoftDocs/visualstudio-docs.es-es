---
title: "El proyecto &#39;&lt;nombreProyecto&gt;&#39; necesita una referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n1&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39;, pero hace referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n2&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39; (advertencia de Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42203"
  - "bc42203"
helpviewer_keywords: 
  - "BC42203"
ms.assetid: 26a3fa34-ec5d-4817-a947-3959446a924a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El proyecto &#39;&lt;nombreProyecto&gt;&#39; necesita una referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n1&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39;, pero hace referencia a la versi&#243;n &#39;&lt;n&#250;meroVersi&#243;n2&gt;&#39; del ensamblado &#39;&lt;nombreEnsamblado&gt;&#39; (advertencia de Visual Basic)
El proyecto '\<nombreProyecto\>' necesita una referencia a la versión '\<númeroVersión1\>' del ensamblado '\<nombreEnsamblado\>', pero hace referencia a la versión '\<númeroVersión2\>' del ensamblado '\<nombreEnsamblado\>'. Se emitió una referencia a la versión '\<númeroVersión1\>'.  
  
 Un proyecto hace una referencia indirecta a un ensamblado que se define en otra parte, pero el proyecto también tiene una referencia directa a una versión anterior de ese ensamblado.  
  
 Para adaptar el acceso a los tipos y los elementos de programación definidos en la versión más reciente, pero no en la versión anterior, el compilador usa la referencia indirecta a la versión más reciente cuando resuelve los accesos.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42203  
  
### Para corregir este error  
  
-   Quite la referencia directa a la versión anterior del ensamblado o cámbiela para que haga referencia a la versión más reciente.  
  
## Vea también  
 [Ensamblados en Common Language Runtime](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Administrar referencias](http://msdn.microsoft.com/es-es/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)