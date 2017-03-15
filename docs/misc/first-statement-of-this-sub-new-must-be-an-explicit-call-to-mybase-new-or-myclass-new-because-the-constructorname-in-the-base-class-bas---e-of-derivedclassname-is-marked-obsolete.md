---
title: "La primera instrucci&#243;n de este &#39;Sub New&#39; debe ser una llamada expl&#237;cita a &#39;MyBase.New&#39; o &#39;MyClass.New&#39; porque el &#39;&lt;nombreConstructor&gt;&#39; de la clase base &#39;&lt;nombreClaseBase&gt;&#39; de &#39;&lt;nombreClaseDerivada&gt;&#39; est&#225; marcado como obsoleto. | Microsoft Docs"
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
  - "vbc30919"
  - "bc30919"
helpviewer_keywords: 
  - "BC30919"
ms.assetid: 437e3204-8ddc-45d3-b9b4-c66d53a61a6d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La primera instrucci&#243;n de este &#39;Sub New&#39; debe ser una llamada expl&#237;cita a &#39;MyBase.New&#39; o &#39;MyClass.New&#39; porque el &#39;&lt;nombreConstructor&gt;&#39; de la clase base &#39;&lt;nombreClaseBase&gt;&#39; de &#39;&lt;nombreClaseDerivada&gt;&#39; est&#225; marcado como obsoleto.
Un constructor de clase no realiza una llamada de manera explícita a un constructor de clase base y el constructor de clase base se marca con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como un error.  
  
 Cuando un constructor de clase derivada no llama a un constructor de clase base, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] intenta generar una llamada implícita a un constructor de clase base sin parámetros. Si no hay ningún constructor accesible en la clase base que se pueda llamar sin argumentos, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar una llamada implícita. En este caso, el constructor necesario se marca con el atributo <xref:System.ObsoleteAttribute>, por lo que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede llamarlo.  
  
 Puede marcar que un elemento de programación ya no está en uso aplicándole <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata un intento de usar el elemento como un error. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 **Identificador de error:** BC30919  
  
### Para corregir este error  
  
-   Incluya una llamada a `MyBase.New()` o `MyClass.New()` como la primera instrucción de `Sub New` en la clase derivada.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)