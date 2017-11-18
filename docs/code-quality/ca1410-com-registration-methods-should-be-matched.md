---
title: "CA1410: Los métodos de registro COM deben coincidir | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c6191aff1433d050c1f7b50097c88d1d3cf2a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Los métodos de registro COM se deben adjuntar
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|Identificador de comprobación|CA1410|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo declara un método que se marca con la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo pero no declara un método que se marca con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo, o viceversa.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Para los clientes del modelo de objetos componentes (COM) crear un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipo, el tipo debe registrarse primero. Si está disponible, un método que se marca con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributo se denomina durante el proceso de registro para ejecutar código especificado por el usuario. Un método correspondiente que se marca con el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributo se denomina durante el proceso de anulación del registro para invertir las operaciones del método de registro.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el método de la anulación del registro o el registro correspondiente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla. El código marcado como comentario muestra la solución para la infracción.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1411: Los métodos de registro COM no deben ser visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrar ensamblados con COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (Herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)