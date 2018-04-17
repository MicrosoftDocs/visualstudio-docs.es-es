---
title: 'CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cff8d36cd80a31cf05ca461730d51703afc106ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales
|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|Identificador de comprobación|CA2102|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un miembro de un ensamblado que no está marcado con el <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o está marcado como `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un bloque catch que controla <xref:System.Exception?displayProperty=fullName> y no contiene un bloque catch general inmediatamente después. Esta regla omite [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ensamblados.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un bloque catch que controla <xref:System.Exception> detecta todas las excepciones compatibles con Common Language Specification (CLS). Sin embargo, no detecta las excepciones no conformes a CLS. No conforme a CLS excepciones conformes se pueden iniciar desde el código nativo o desde el código administrado que fue generado por Microsoft lenguaje intermedio (MSIL) ensamblador. Tenga en cuenta que C# y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] los compiladores no permite no conforme a CLS que se produzcan excepciones conformes y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no detecta excepciones conformes a CLS. Si es la intención del bloque catch controlar todas las excepciones, use la siguiente sintaxis del bloque catch general.  
  
-   C#: `catch {}`  
  
-   C++: `catch(...) {}` o `catch(Object^) {}`  
  
 Una excepción conforme no controlada no conformes a CLS se convierte en un problema de seguridad cuando se quitan los permisos concedidos previamente en el bloque catch. Dado que no se detectan las excepciones no conformes a CLS, podría ejecutar un método malintencionado que produce no conformes a CLS excepción conforme con permisos elevados.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla cuando la intención es todas las detectar excepciones, sustituya o agregue un bloque catch general o marque el ensamblado `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Si se quitan los permisos en el bloque catch, duplicados la funcionalidad en la ficha general bloque catch. Si no es el objetivo de controlar todas las excepciones, reemplace el bloque catch que controla <xref:System.Exception> con bloques catch que controlen tipos de excepción específica.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el bloque try no contiene las instrucciones que podrían generar una excepción no conforme a CLS. Dado que cualquier código nativo o administrado podría producir no conformes a CLS excepción conforme, esto requiere el conocimiento de todo el código que se pueden ejecutar en todas las rutas de código dentro del bloque try. Observe que common language runtime no producen excepciones no conformes a CLS.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una clase MSIL que produce una excepción no conforme a CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que contiene un bloque catch general que cumple la regla.  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Compilar los ejemplos anteriores como se indica a continuación.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>Vea también  
 [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe (Ensamblador de IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)