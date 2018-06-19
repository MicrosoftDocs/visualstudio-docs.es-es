---
title: 'CA1810: Inicializar campos estáticos de tipo de referencia insertados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b31a0bbea244d5d196364517b5c5a2ca8d7a53a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914645"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializar campos estáticos de tipo de referencia insertados
|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|Identificador de comprobación|CA1810|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. Se desencadena la inicialización estática cuando se tiene acceso a cualquier miembro estático o cuando se crea una instancia del tipo. Sin embargo, no se desencadena la inicialización estática si declara una variable del tipo, pero no lo utilice, que puede ser importante si la inicialización modifica el estado global.

 Cuando todos los datos estáticos se inicializado en línea y no se declara un constructor estático explícito, los compiladores de lenguaje intermedio (MSIL) de Microsoft agregan el `beforefieldinit` indicador y un constructor estático implícito, que inicializa los datos estáticos para el tipo MSIL definición. Cuando el compilador JIT encuentra el `beforefieldinit` marca, la mayoría de las veces no se agregan las comprobaciones del constructor estático. Inicialización estática se garantiza que se producen en algún momento antes de que se tiene acceso a los campos estáticos, pero no antes de invoca un constructor de instancia o método estático. Tenga en cuenta que la inicialización estática puede producirse en cualquier momento después de que se declara una variable del tipo.

 Las comprobaciones del constructor estático pueden reducir el rendimiento. A menudo un constructor estático se usa solo para inicializar campos estáticos, en cuyo caso debe sólo asegurarse de que la inicialización estática se produce antes del primer acceso a un campo estático. La `beforefieldinit` comportamiento es adecuado para estos y muchos otros tipos. Solo es inadecuado cuando inicialización estática afecta al estado global y se cumple una de las siguientes acciones:

-   El efecto sobre el estado global es costoso y no es necesario si no se utiliza el tipo.

-   Pueden tener acceso a los efectos de estado global sin tener acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es importante; o bien cuando los cambios de estado global provocados por inicialización estática son caros o deben garantizarse a producir antes de que se llama a un método estático del tipo o se crea una instancia del tipo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `StaticConstructor`, que infringe la regla y un tipo, `NoStaticConstructor`, que reemplaza al constructor estático con la inicialización en línea para cumplir la regla.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

 Tenga en cuenta la adición de la `beforefieldinit` marca en la definición de MSIL para el `NoStaticConstructor` clase.

 **.class public auto ansi StaticConstructor** **extiende [mscorlib**
 **{**
 **} / / end de clase StaticConstructor** 
 **.class pública auto ansi beforefieldinit NoStaticConstructor** **extiende [mscorlib**
 **{** 
 **} / / end de clase NoStaticConstructor**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)