---
title: "el descriptor de acceso &#39;&lt;palabraClave&gt;&#39; de &#39;&lt;nombrePropiedad&gt;&#39; est&#225; obsoleto: &#39;&lt;mensajeError&gt;&#39; (error de Visual Basic) | Microsoft Docs"
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
  - "vbc30911"
  - "bc30911"
helpviewer_keywords: 
  - "BC30911"
ms.assetid: b690be0c-4dca-4f79-88ed-4ee3e3f1f90b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# el descriptor de acceso &#39;&lt;palabraClave&gt;&#39; de &#39;&lt;nombrePropiedad&gt;&#39; est&#225; obsoleto: &#39;&lt;mensajeError&gt;&#39; (error de Visual Basic)
Una instrucción intenta leer o escribir una propiedad para la que se ha marcado el procedimiento correspondiente con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como un error.  
  
 Puede marcar que un elemento de programación ya no está en uso aplicándole <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata un intento de usar el elemento como un error. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 **Identificador de error:** BC30911  
  
### Para corregir este error  
  
1.  Examine el mensaje de error indicado y tome las medidas adecuadas.  
  
2.  Asegúrese de que en la referencia de código fuente está escrito correctamente el nombre de la propiedad.  
  
3.  Evite acceder a la propiedad de la manera \(lectura o escritura\) que generó este mensaje.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)