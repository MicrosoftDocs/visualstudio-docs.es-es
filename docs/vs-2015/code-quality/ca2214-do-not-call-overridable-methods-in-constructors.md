---
title: 'CA2214: no llamar a métodos reemplazables en constructores | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662913"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: No llamar a métodos reemplazables en constructores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|Identificador de comprobación|CA2214|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 El constructor de un tipo no sellado llama a un método virtual definido en su clase.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se llama a un método virtual, el tipo real que ejecuta el método no se selecciona hasta el tiempo de ejecución. Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor de la instancia que invoca el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, no llame a los métodos virtuales de un tipo desde dentro de los constructores del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Se debe rediseñar el constructor para eliminar la llamada al método virtual.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el efecto de infringir esta regla. La aplicación de prueba crea una instancia de `DerivedType`, que hace que se ejecute su constructor de clase base (`BadlyConstructedType`). el constructor de `BadlyConstructedType` llama incorrectamente al método virtual `DoSomething`. Como muestra el resultado, `DerivedType.DoSomething()` ejecuta y lo hace antes de que se ejecute el constructor de `DerivedType`.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Este ejemplo produce el siguiente resultado:

 **Llamando a un constructor base.** **¿se ha llamado a 
 se ha inicializado doSomething? No hay ningún** 
 que**llame a un constructor derivado.**
