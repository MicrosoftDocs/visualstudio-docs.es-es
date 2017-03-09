---
title: "Tipo de delegado &#39;&lt;nombreDelegado&gt;&#39; del evento &#39;&lt;nombreEvento&gt;&#39; no es conforme a CLS. | Microsoft Docs"
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
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de delegado &#39;&lt;nombreDelegado&gt;&#39; del evento &#39;&lt;nombreEvento&gt;&#39; no es conforme a CLS.
Una [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement) usa un delegado para especificar su firma, pero la [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement) está marcada como `<CLSCompliant(False)>` o no está marcada.  
  
 Al aplicar el atributo <xref:System.CLSCompliantAttribute> a un elemento de programación, establezca el parámetro `isCompliant` del atributo como `True` o `False` para indicar compatibilidad o incompatibilidad. No hay ningún valor predeterminado para este parámetro y debe proporcionar un valor.  
  
 Si no aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40050  
  
### Para corregir este error  
  
-   Si necesita la conformidad con CLS y tiene control sobre la definición del delegado, aplique <xref:System.CLSCompliantAttribute> a su declaración para marcarlo como `<CLSCompliant(True)>`.  
  
-   Si no tiene control sobre la definición del delegado o no puede marcarlo como conforme, quite el atributo <xref:System.CLSCompliantAttribute> de la instrucción `Event` o márquelo como `<CLSCompliant(False)>`.  
  
## Vea también  
 [\<PAVE OVER\> Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)