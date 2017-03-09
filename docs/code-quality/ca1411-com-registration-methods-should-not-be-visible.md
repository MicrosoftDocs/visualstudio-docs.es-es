---
title: "CA1411: Los m&#233;todos de registro COM no deben ser visibles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411: Los m&#233;todos de registro COM no deben ser visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|Identificador de comprobación|CA1411|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método marcado con el atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> es visible externamente.  
  
## Descripción de la regla  
 Cuando un ensamblado se registra con el Modelo de objetos componentes \(COM\), se agregan entradas al Registro para cada tipo visible a través de COM en el ensamblado.  Durante los procesos de registro y anulación de registro se llama a métodos marcados, respectivamente, con los atributos <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> y <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>, para ejecutar el código de usuario específico del registro y la anulación de registro de estos tipos.  No se debe llamar a este código fuera de estos procesos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie la accesibilidad del método a `private` o `internal` \(`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra dos métodos que infringen la regla.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## Reglas relacionadas  
 [CA1410: Los métodos de registro COM se deben adjuntar](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## Vea también  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)