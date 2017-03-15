---
title: "El descriptor de acceso &#39;&lt;palabraClave&gt;&#39; de &#39;&lt;nombreDePropiedad&gt;&#39; est&#225; obsoleto (error de Visual Basic) | Microsoft Docs"
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
  - "vbc30912"
  - "bc30912"
helpviewer_keywords: 
  - "BC30912"
ms.assetid: f1fa965e-090c-49f3-ab1e-cbb2f9b2a5f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El descriptor de acceso &#39;&lt;palabraClave&gt;&#39; de &#39;&lt;nombreDePropiedad&gt;&#39; est&#225; obsoleto (error de Visual Basic)
Una instrucción intenta leer o escribir una propiedad para la que se marcó el procedimiento correspondiente con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como un error.  
  
 Para marcar que cualquier elemento de programación ya no está en uso, aplíquele <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata un intento de usar el elemento como un error. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si se produce un intento de usar el elemento.  
  
 **Identificador de error:** BC30912  
  
### Para corregir este error  
  
1.  Asegúrese de que en la referencia de código fuente está escrito correctamente el nombre de la propiedad.  
  
2.  Evite acceder a la propiedad de la manera \(lectura o escritura\) que generó este mensaje.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de los atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)