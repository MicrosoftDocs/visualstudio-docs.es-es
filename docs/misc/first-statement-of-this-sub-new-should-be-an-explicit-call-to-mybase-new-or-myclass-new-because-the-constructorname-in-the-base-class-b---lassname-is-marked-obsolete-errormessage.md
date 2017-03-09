---
title: "La primera instrucci&#243;n de este &#39;Sub New&#39; debe ser una llamada expl&#237;cita a &#39;MyBase.New&#39; o &#39;MyClass.New&#39; porque el &#39;&lt;nombreDeConstructor&gt;&#39; de la clase base &#39;&lt;nombreDeClaseBase&gt;&#39; de &#39;&lt;nombreDeClaseDerivada&gt;&#39; est&#225; marcado como obsoleto: &#39;&lt;mensajeDeError&gt;&#39; | Microsoft Docs"
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
  - "bc41004"
  - "vbc41004"
helpviewer_keywords: 
  - "BC41004"
ms.assetid: 61185283-d43d-46ae-bfa0-6fe3e1d0982a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La primera instrucci&#243;n de este &#39;Sub New&#39; debe ser una llamada expl&#237;cita a &#39;MyBase.New&#39; o &#39;MyClass.New&#39; porque el &#39;&lt;nombreDeConstructor&gt;&#39; de la clase base &#39;&lt;nombreDeClaseBase&gt;&#39; de &#39;&lt;nombreDeClaseDerivada&gt;&#39; est&#225; marcado como obsoleto: &#39;&lt;mensajeDeError&gt;&#39;
Un constructor de clase no llama de manera explícita a un constructor de clase base y el constructor de clase base implícito está marcado con el atributo <xref:System.ObsoleteAttribute> y con la directiva para tratarlo como advertencia.  
  
 Cuando un constructor de clase derivada no llama a un constructor de clase base, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] intenta generar una llamada implícita a un constructor de clase base sin parámetros. Si no hay ningún constructor accesible en la clase base que se pueda llamar sin argumentos, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar una llamada implícita. En este caso, el constructor necesario se marca con el atributo <xref:System.ObsoleteAttribute>, por lo que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede llamarlo.  
  
 Para marcar que cualquier elemento de programación ya no está en uso, aplíquele <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata como un error los intentos de usar el elemento. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 De forma predeterminada, este mensaje es una advertencia, ya que la propiedad <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> es `False`. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC41004  
  
### Para corregir este error  
  
1.  Examine el mensaje de error indicado y tome las medidas adecuadas.  
  
2.  Incluya una llamada a `MyBase.New()` o `MyClass.New()` como la primera instrucción de `Sub New` en la clase derivada.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de los atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)