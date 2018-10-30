---
title: 'CA2214: No llamar a métodos reemplazables en constructores | Microsoft Docs'
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
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b43400dbd516328e133ed6e103d4a4f2a7ccf8a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921475"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: No llamar a métodos reemplazables en constructores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|Identificador de comprobación|CA2214|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 El constructor de un tipo no sellado llama a un método virtual definido en su clase.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se llama a un método virtual, el tipo real que se ejecuta el método no está activado hasta que el tiempo de ejecución. Cuando un constructor llama a un método virtual, es posible que no haya ejecutado el constructor para la instancia que invoca el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, no llame a métodos virtuales del tipo desde dentro de los constructores del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. El constructor debe rediseñarse para eliminar la llamada al método virtual.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra el efecto de infringir esta regla. La aplicación de prueba crea una instancia de `DerivedType`, lo que hace que su clase base (`BadlyConstructedType`) ejecute el constructor. `BadlyConstructedType`de forma incorrecta, constructor llama al método virtual `DoSomething`. Como se muestra en la salida, `DerivedType.DoSomething()` ejecuta y lleva a cabo antes `DerivedType`del constructor se ejecuta.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Este ejemplo produce el siguiente resultado:

 **Llamar al constructor base. ¿ ** 
 **DoSomething derivado se denomina - inicializado? No**
**derivados de llamar al constructor.**



