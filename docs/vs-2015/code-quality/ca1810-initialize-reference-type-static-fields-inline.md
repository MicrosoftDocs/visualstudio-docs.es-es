---
title: 'CA1810: inicializar campos estáticos de tipo de referencia insertados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9032ac105477370477b13554afe4ee65bd7cd733
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609015"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializar campos estáticos de tipo de referencia insertados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|Identificador de comprobación|CA1810|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. La inicialización estática se desencadena cuando se tiene acceso a cualquier miembro estático o cuando se crea una instancia del tipo. Sin embargo, la inicialización estática no se desencadena si se declara una variable del tipo pero no se usa, lo que puede ser importante si la inicialización cambia el estado global.

 Cuando todos los datos estáticos se inicializan en línea y no se declara un constructor estático explícito, los compiladores del lenguaje intermedio de Microsoft (MSIL) agregan la marca `beforefieldinit` y un constructor estático implícito, que inicializa los datos estáticos, en el tipo de MSIL. definir. Cuando el compilador JIT encuentra la marca `beforefieldinit`, no se agrega la mayor parte del tiempo que las comprobaciones del constructor estático. Se garantiza que la inicialización estática se produce en algún momento antes de que se tenga acceso a los campos estáticos, pero no antes de que se invoque un método estático o un constructor de instancia. Tenga en cuenta que la inicialización estática puede producirse en cualquier momento después de declarar una variable del tipo.

 Las comprobaciones del constructor estático pueden reducir el rendimiento. A menudo, solo se usa un constructor estático para inicializar campos estáticos, en cuyo caso solo debe asegurarse de que la inicialización estática se produce antes del primer acceso de un campo estático. El comportamiento `beforefieldinit` es adecuado para estos y otros tipos. Solo es apropiado cuando la inicialización estática afecta al estado global y se cumple una de las siguientes condiciones:

- El efecto en el estado global es costoso y no es necesario si no se utiliza el tipo.

- Se puede tener acceso a los efectos globales de estado sin tener acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es un problema. o bien, si los cambios de estado global causados por la inicialización estática son caros o se debe garantizar que se produzcan antes de que se llame a un método estático del tipo o se cree una instancia del tipo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `StaticConstructor`, que infringe la regla y un tipo, `NoStaticConstructor`, que reemplaza el constructor estático por inicialización alineada para satisfacer la regla.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Observe la adición del indicador `beforefieldinit` en la definición de MSIL para la clase `NoStaticConstructor`.

 **. class public ANSI StaticConstructor** **extends [mscorlib] System. Object** 
 **{** 
 **}//End de la clase StaticConstructor** 
 **. class public auto ansi beforefieldinit NoStaticConstructor** ** extiende [mscorlib] System. Object** 
 **{** 1 **}//End de la clase NoStaticConstructor**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
