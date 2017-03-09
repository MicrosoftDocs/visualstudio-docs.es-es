---
title: "&#39;&lt;elementname&gt;&#39; est&#225; obsoleto: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40000"
  - "vbc40000"
helpviewer_keywords: 
  - "BC40000"
ms.assetid: dade0f57-eca1-4dd0-b978-020678838be6
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; est&#225; obsoleto: &#39;&lt;errormessage&gt;&#39;
Una instrucción intenta obtener acceso a un elemento de programación que se ha marcado con el atributo <xref:System.ObsoleteAttribute> y la directiva para tratarlo como una advertencia.  
  
 Puede marcar que un elemento de programación ya no está en uso aplicándole <xref:System.ObsoleteAttribute>. Si lo hace, puede establecer la propiedad <xref:System.ObsoleteAttribute.IsError%2A> del atributo en `True` o `False`. Si se establece en `True`, el compilador trata un intento de usar el elemento como un error. Si se establece en `False` o se deja el valor predeterminado `False`, el compilador emite una advertencia si hay un intento de usar el elemento.  
  
 De forma predeterminada, este mensaje es una advertencia, ya que la propiedad <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> es `False`. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40000  
  
### Para corregir este error  
  
1.  Examine el mensaje de error indicado y tome las medidas adecuadas.  
  
2.  Asegúrese de que la referencia del código fuente escriba correctamente el nombre del elemento.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos usados en Visual Basic](http://msdn.microsoft.com/es-es/22231318-8a40-49af-9245-e0aab723563b)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)