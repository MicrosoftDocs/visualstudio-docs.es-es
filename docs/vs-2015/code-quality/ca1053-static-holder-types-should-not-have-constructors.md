---
title: 'CA1053: Los tipos titulares estáticos no deben tener constructores | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83000143674e7cc3bc412c0ca8a579660160514c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444557"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Los tipos titulares estáticos no deben tener constructores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|Identificador de comprobación|CA1053|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o público anidado declara sólo miembros estáticos y tiene un constructor predeterminado público o protegido.

## <a name="rule-description"></a>Descripción de la regla
 El constructor no es necesario puesto que al llamar a los miembros estáticos no se requiere una instancia del tipo. Además, dado que el tipo no tiene miembros no estáticos, crear una instancia no proporciona acceso a cualquiera de los miembros del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el constructor predeterminado o hacerla privada.

> [!NOTE]
> Algunos compiladores crean automáticamente un constructor predeterminado público si el tipo no define ningún constructor. Si esto sucede con su tipo, agregue un constructor privado predeterminado para eliminar la infracción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. La presencia del constructor sugiere que el tipo no es un tipo estático.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla. Tenga en cuenta que no hay ningún constructor predeterminado en el código fuente. Cuando este código se compila en un ensamblado, el compilador de C# insertará un constructor predeterminado, que infringe esta regla. Para corregir este problema, declare un constructor privado.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
