---
title: "CA1411: Los métodos de registro COM no deben ser visibles | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67a4d4124ac1aae99327fdcd757db546cb50adfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Los métodos de registro COM no deben ser visibles
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|Identificador de comprobación|CA1411|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método que se marca con la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo es visible externamente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando un ensamblado se registra con el modelo de objetos componentes (COM), se agregan las entradas en el registro para cada tipo visible para COM del ensamblado. Los métodos que se marcan con la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> y <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributos se denominan durante los procesos de registro y anulación del registro, respectivamente, para ejecutar el código de usuario que es específico para el registro o la anulación del registro de estos tipos. No se debe llamar a este código fuera de estos procesos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie la accesibilidad del método que se `private` o `internal` (`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo muestra dos métodos que infringen la regla.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1410: Los métodos de registro COM se deben asociar](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrar ensamblados con COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (Herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)