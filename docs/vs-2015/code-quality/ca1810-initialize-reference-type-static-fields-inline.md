---
title: 'CA1810: Tipo de referencia inicializar campos estáticos insertados | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e4d7ffbe4fc821ffd70b0bb299b2a4738d63873b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862689"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializar campos estáticos de tipo de referencia insertados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|Identificador de comprobación|CA1810|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. La inicialización estática se desencadena cuando se tiene acceso a cualquier miembro estático o cuando se crea una instancia del tipo. Sin embargo, la inicialización estática no se desencadena si se declara una variable del tipo pero no lo utilice, que puede ser importante si la inicialización cambia el estado global.

 Cuando todos los datos estáticos está alineada inicializado y no se declara un constructor estático explícito, agregan los compiladores de lenguaje intermedio (MSIL) de Microsoft la `beforefieldinit` indicador y un constructor estático implícito, que inicializa los datos estáticos para el tipo MSIL definición. Cuando se encuentra el compilador JIT la `beforefieldinit` marca, la mayoría de los casos no se agregan las comprobaciones del constructor estático. Se garantiza que la inicialización estática que se produzca en algún momento antes de que se tiene acceso a los campos estáticos, pero no antes de invoca un constructor de instancia o método estático. Tenga en cuenta que la inicialización estática puede producirse en cualquier momento después de declara una variable del tipo.

 Las comprobaciones del constructor estático pueden reducir el rendimiento. A menudo se usa un constructor estático solo para inicializar campos estáticos, en cuyo caso debe solo asegurarse de que la inicialización estática se produce antes del primer acceso a un campo estático. El `beforefieldinit` comportamiento es adecuado para estos y muchos otros tipos. No es adecuado sólo cuando la inicialización estática afecta al estado global y se cumple una de las siguientes acciones:

-   El efecto sobre el estado global es costoso y no es necesario si no se utiliza el tipo.

-   Los efectos de estado global se pueden acceder sin tener acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es una preocupación; o si los cambios de estado global causados por la inicialización estática son costosos o deben garantizarse que se produzca antes de que se llama a un método estático del tipo o se crea una instancia del tipo.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `StaticConstructor`, que infringe la regla y un tipo, `NoStaticConstructor`, que reemplaza el constructor estático con la inicialización en línea para cumplir la regla.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Tenga en cuenta la adición de la `beforefieldinit` marca en la definición de MSIL para el `NoStaticConstructor` clase.

 **.class public auto ansi StaticConstructor** **extiende [mscorlib**
 **{**
 **} / final de la clase StaticConstructor** 
 **.class automática pública ansi beforefieldinit NoStaticConstructor** **extiende [mscorlib**
 **{** 
 **} / final de la clase NoStaticConstructor**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)



