---
title: "El atributo &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; no se admite en esta versi&#243;n. | Microsoft Docs"
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
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; no se admite en esta versi&#243;n.
El atributo <xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName> permite especificar el juego de caracteres que se usa en cadenas con referencias calculadas. Su valor toma un miembro de la enumeración <xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName>.  
  
 La versión actual de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no es compatible con este atributo. La compatibilidad es posible en versiones futuras.  
  
 **Identificador de error:** BC32510  
  
### Para corregir este error  
  
-   Use [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement) para especificar el juego de caracteres para el procedimiento externo que está declarando. Esto se ilustra en el siguiente ejemplo:  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     Si no se especifica el conjunto de caracteres en la instrucción `Declare`, el valor predeterminado es ANSI.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement)