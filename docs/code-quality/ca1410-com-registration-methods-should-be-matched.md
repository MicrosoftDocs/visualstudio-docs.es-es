---
title: "CA1410: Los m&#233;todos de registro COM se deben adjuntar | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410: Los m&#233;todos de registro COM se deben adjuntar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|Identificador de comprobación|CA1410|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo declara un método marcado con el atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> pero no declara un método marcado con el atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, o viceversa.  
  
## Descripción de la regla  
 Para que los clientes del Modelo de objetos componentes \(COM\) creen un tipo de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], primero se debe registrar el tipo.  Si está disponible, se llama a un método marcado con el atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> durante el proceso del registro para ejecutar código especificado por el usuario.  Se llama a un método correspondiente marcado con el atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> durante el proceso del anulación del registro, para invertir las operaciones del método de registro.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el método de registro o anulación de registro correspondiente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  El código marcado como comentario muestra la corrección para la infracción.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## Reglas relacionadas  
 [CA1411: Los métodos de registro COM no deben ser visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## Vea también  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)