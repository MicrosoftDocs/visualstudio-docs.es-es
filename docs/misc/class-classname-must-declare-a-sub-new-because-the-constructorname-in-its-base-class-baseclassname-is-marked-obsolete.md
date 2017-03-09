---
title: "La clase &#39;&lt;nombreClase&gt;&#39; debe declarar un &#39;Sub New&#39; porque el &#39;&lt;nombreConstructor&gt;&#39; de su clase base &#39;&lt;nombreClaseBase&gt;&#39; est&#225; marcado como obsoleto. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30917"
  - "bc30917"
helpviewer_keywords: 
  - "BC30917"
ms.assetid: 764d222d-e058-40ad-a354-29b956a8027b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase &#39;&lt;nombreClase&gt;&#39; debe declarar un &#39;Sub New&#39; porque el &#39;&lt;nombreConstructor&gt;&#39; de su clase base &#39;&lt;nombreClaseBase&gt;&#39; est&#225; marcado como obsoleto.
Una declaración de clase no incluye un constructor y el constructor de clase base se marca con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como un error.  
  
 Cuando una clase derivada no declara un constructor, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] intenta generar un constructor sin parámetros implícito que llama a `MyBase.New()`. Si no hay ningún constructor accesible en la clase base que se pueda llamar sin argumentos, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar un constructor implícito. En este caso, el constructor necesario se marca con el atributo <xref:System.ObsoleteAttribute>, por lo que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede llamarlo.  
  
 Puede marcar que un elemento de programación ya no está en uso aplicándole <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata un intento de usar el elemento como un error. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 **Identificador de error:** BC30917  
  
### Para corregir este error  
  
-   Use `Sub New` para declarar un constructor en la clase derivada.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)