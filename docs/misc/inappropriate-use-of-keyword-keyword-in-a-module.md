---
title: "Uso no apropiado de la palabra clave &lt;keyword&gt; en un m&#243;dulo | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Uso no apropiado de la palabra clave &lt;keyword&gt; en un m&#243;dulo
Los módulos no tienen instancias, no admiten la herencia ni implementan interfaces. Por lo tanto, las palabras clave siguientes no se aplican a una declaración de módulo:  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 Las únicas palabras clave que se admiten en una [Module \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/module-statement) son [Public](/dotnet/visual-basic/language-reference/modifiers/public) y [Friend](/dotnet/visual-basic/language-reference/modifiers/friend).  
  
 Además, no puede usar la instrucción [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) o la [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) en el bloque de instrucciones del módulo.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42028  
  
### Para corregir este error  
  
-   Si desea que este elemento de programación sea un módulo, use solo la palabra clave `Public` o `Friend` en su declaración. De forma predeterminada, un módulo se usa para `Friend` si no se especifica su nivel de acceso.  
  
-   Si piensa crear instancias de este elemento de programación, declárelo como una clase. A continuación, podrá usar las palabras clave que se aplican a una declaración de clase.  
  
## Vea también  
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)