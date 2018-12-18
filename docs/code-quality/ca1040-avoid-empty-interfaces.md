---
title: 'CA1040: Evitar interfaces vacías'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d5c23a52e65d04b5cc8d147cc0ec3bd7c12bde3c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548348"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitar interfaces vacías

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|Identificador de comprobación|CA1040|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 La interfaz no declara a ningún miembro o implementar dos o más interfaces.

## <a name="rule-description"></a>Descripción de la regla
 Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro. Por lo tanto, no define un contrato que se puede implementar.

 Si el diseño incluye vacía interfaces que los tipos de espera se implemente, puede que esté usando una interfaz como un marcador o una forma de identificar un grupo de tipos. Si esta identificación se produce en tiempo de ejecución, la manera correcta para realizar esta acción es utilizar un atributo personalizado. Utilice la presencia o ausencia del atributo o las propiedades del atributo, para identificar los tipos de destino. Si la identificación debe producirse en tiempo de compilación, es aceptable utilizar una interfaz vacía.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite la interfaz o agregar a miembros a él. Si la interfaz vacía se utiliza para etiquetar un conjunto de tipos, reemplace la interfaz con un atributo personalizado.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la interfaz se usa para identificar un conjunto de tipos en tiempo de compilación.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una interfaz vacía.

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]