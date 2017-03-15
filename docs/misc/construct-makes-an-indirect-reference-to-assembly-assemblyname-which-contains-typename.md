---
title: "La construcci&#243;n hace una referencia indirecta al ensamblado &#39;&lt;assemblyname&gt;&#39;, que contiene &#39;&lt;typename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31528"
  - "vbc31528"
helpviewer_keywords: 
  - "BC31528"
ms.assetid: 33459c3f-8615-492e-b6ae-531ed597999e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La construcci&#243;n hace una referencia indirecta al ensamblado &#39;&lt;assemblyname&gt;&#39;, que contiene &#39;&lt;typename&gt;&#39;
La construcción hace una referencia indirecta al ensamblado '\<assemblyname\>', que contiene \<typename\>. Agregue una referencia de archivo a \<filename\> a su proyecto.  
  
 Una expresión utiliza un tipo, como una clase, una estructura, una interfaz, una enumeración o un delegado, pero el ensamblado no tiene una referencia de proyecto al ensamblado que define el tipo.  
  
 **Id. de error:** BC31528  
  
### Para corregir este error  
  
-   En las propiedades del proyecto, agregue una referencia al archivo que contiene el ensamblado que define el tipo que está utilizando.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimiento: modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NO ESTÁ EN LA COMPILACIÓN: Procedimiento: agregar o quitar referencias usando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)