---
title: "System.CLSCompliantAttribute no se puede aplicar a la propiedad &#39;Get&#39; o &#39;Set&#39; | Microsoft Docs"
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
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.CLSCompliantAttribute no se puede aplicar a la propiedad &#39;Get&#39; o &#39;Set&#39;
Una definición de propiedad aplica el atributo <xref:System.CLSCompliantAttribute> a su instrucción `Get` o `Set`.  
  
 Para una propiedad que sea conforme a [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), toda la propiedad debe estar marcada como `<CLSCompliant(True)>`. Se debe aplicar <xref:System.CLSCompliantAttribute> a la [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement), no a la instrucción `Get` o `Set`.  
  
 Al aplicar <xref:System.CLSCompliantAttribute> a un elemento de programación, se establece el parámetro `isCompliant` del atributo en `True` o `False` para indicar su conformidad o no conformidad. No hay ningún valor predeterminado para este parámetro, por lo que debe proporcionar uno.  
  
 Si no aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC40043  
  
### Para corregir este error  
  
-   Quite <xref:System.CLSCompliantAttribute> de la instrucción `Get` o `Set`.  
  
-   Si la propiedad debe ser conforme a CLS, marque la instrucción `Property` como `<CLSCompliant(True)>`.  
  
## Vea también  
 [\<PAVE OVER\> Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement)