---
title: "Advertencia del compilador (nivel 2) CS3021 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS3021
'tipo' no necesita ningún atributo CLSCompliant porque el ensamblado no tiene ningún atributo CLSCompliant.  
  
 Esta advertencia se produce si `[CLSCompliant(false)]` aparece en una clase de un ensamblado que no tiene un atributo de nivel de ensamblado CLSCompliant establecido en true \(por ejemplo, la línea `[assembly: CLSCompliant(true)]`\). Dado que el ensamblado no se declara a sí mismo conforme a CLS, no hay ninguna necesidad de que nada dentro del ensamblado que se declare no conforme, ya que se supone que no es conforme. Para obtener más información sobre la conformidad con CLS, vea [Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
 Para hacer desaparecer esta advertencia, quite el atributo o agregue el atributo de nivel de ensamblado.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3021:  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## Vea también  
 [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)