---
title: 'CA1402: Evite sobrecargas en interfaces visibles para COM | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9294e1aab07aa05bc10de507e0a5885a47ebcc40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Evite sobrecargas en interfaces visibles para COM
|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|Identificador de comprobación|CA1402|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un modelo de objetos componentes (COM) visible interfaz declara los métodos sobrecargados.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre. Las sobrecargas subsiguientes son un nombre único resultante de anexar al nombre un carácter de subrayado "_" y un entero que corresponde al orden de declaración de la sobrecarga. Por ejemplo, considere los siguientes métodos.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Estos métodos se exponen a los clientes COM de la forma siguiente.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Los clientes COM de Visual Basic 6 no pueden implementar métodos de interfaz mediante el uso de un carácter de subrayado en el nombre.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre de los métodos sobrecargados para que los nombres sean únicos. O bien, hacer que la interfaz sea invisible para COM cambiando la accesibilidad a `internal` (`Friend` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o aplicando la <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo establecido en `false`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una interfaz que infringe la regla y una interfaz que cumple la regla.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Vea también  
 [Interoperar con código no administrado](/dotnet/framework/interop/index)   
 [Long (tipo de datos)](/dotnet/visual-basic/language-reference/data-types/long-data-type)