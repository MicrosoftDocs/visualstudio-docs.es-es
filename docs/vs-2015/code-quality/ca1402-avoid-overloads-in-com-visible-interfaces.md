---
title: 'CA1402: evitar sobrecargas en interfaces visibles para COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5c1e3af0e35bf92d72e853948c455893b417998
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534945"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Evitar las sobrecargas en interfaces visibles a través de COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|Identificador de comprobación|CA1402|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Una interfaz visible del modelo de objetos componentes (COM) declara métodos sobrecargados.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se exponen métodos sobrecargados a los clientes COM, sólo la primera sobrecarga de método conserva su nombre. Las sobrecargas posteriores se cambian de nombre de forma única anexando al nombre un carácter de subrayado "_" y un entero que se corresponda con el orden de declaración de la sobrecarga. Por ejemplo, considere los siguientes métodos.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Estos métodos se exponen a los clientes COM como se muestra a continuación.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 los clientes COM no pueden implementar métodos de interfaz mediante el uso de un carácter de subrayado en el nombre.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre de los métodos sobrecargados para que los nombres sean únicos. También puede hacer que la interfaz sea invisible para COM cambiando la accesibilidad a `internal` ( `Friend` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) o aplicando el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo establecido en `false` .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una interfaz que infringe la regla y una interfaz que cumple la regla.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1413: Evitar los campos no públicos en tipos de valor visibles a través de COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evitar los miembros estáticos en tipos visibles a través de COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte también
 Interoperar con el [tipo de datos Long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) [de código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
