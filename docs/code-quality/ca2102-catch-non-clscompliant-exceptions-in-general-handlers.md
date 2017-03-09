---
title: "CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales | Microsoft Docs"
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
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102: Detectar las excepciones que no son CLSCompliant en los controladores generales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|Identificador de comprobación|CA2102|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un miembro de un ensamblado que no está marcado con <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o está marcado con `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un bloque catch que controla <xref:System.Exception?displayProperty=fullName> y no contiene un bloque catch general inmediatamente a continuación.  Esta regla omite los ensamblados de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Descripción de la regla  
 Un bloque catch que controla <xref:System.Exception> detecta todas las excepciones conformes a Common Language Specification \(CLS\).  Sin embargo, no detecta las excepciones no conformes a CLS.  Las excepciones no conformes a CLS pueden iniciarse desde código nativo o código administrado generado por el ensamblador del Lenguaje Intermedio de Microsoft \(MSIL\).  Observe que los compiladores de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y C\# no permiten producir excepciones no conformes a CLS, y que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no detecta excepciones no conformes a CLS.  Si la intención del bloque catch es controlar todas las excepciones, utilice la siguiente sintaxis de bloque catch general.  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` o `catch(Object^) {}`  
  
 Una excepción no conforme a CLS que no se controla se convierte en un problema de seguridad cuando en el bloque catch se quitan los permisos anteriormente concedidos.  Dado que no se detectan excepciones no conformes a CLS, un método malintencionado que produzca una excepción no conforme a CLS se podría ejecutar con permisos elevados.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla cuando la intención es detectar todas las excepciones, sustituya o agregue un bloque catch general o marque el ensamblado con `RuntimeCompatibility(WrapNonExceptionThrows = true)`.  Si se quitan los permisos en el bloque catch, duplique la funcionalidad en el bloque catch general.  Si la intención no es controlar todas las excepciones, reemplace el bloque catch que controle <xref:System.Exception> con bloques catch que controlen tipos de excepción específicos.  
  
## Cuándo suprimir advertencias  
 Se puede suprimir de forma segura una advertencia de esta regla si el bloque try no contiene ninguna instrucción que pueda generar una excepción no conforme a CLS.  Dado que cualquier código nativo o administrado podría iniciar una excepción no conforme a CLS, es necesario conocer todos los códigos que se pueden ejecutar en todas las rutas de código dentro del bloque de try.  Observe que Common Language Runtime no inicia excepciones no conformes a CLS.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una clase MSIL que inicia una excepción no conforme a CLS.  
  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra un método que contiene un bloque catch general que cumple la regla.  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Compile los ejemplos anteriores de la manera siguiente.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## Reglas relacionadas  
 [CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## Vea también  
 [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/es-es/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)