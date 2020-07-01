---
title: 'CA1040: evitar interfaces vacías | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548257"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitar las interfaces vacías
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|Identificador de comprobación|CA1040|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 La interfaz no declara ningún miembro ni implementa dos o más interfaces.

## <a name="rule-description"></a>Descripción de la regla
 Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro. Por lo tanto, no define un contrato que se pueda implementar.

 Si el diseño incluye interfaces vacías que se espera que implementen, probablemente esté usando una interfaz como un marcador o una manera de identificar un grupo de tipos. Si esta identificación se va a producir en tiempo de ejecución, la manera correcta de lograrlo es usar un atributo personalizado. Utilice la presencia o ausencia del atributo, o las propiedades del atributo, para identificar los tipos de destino. Si la identificación debe realizarse en tiempo de compilación, es aceptable usar una interfaz vacía.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite la interfaz o Agréguele miembros. Si la interfaz vacía se usa para etiquetar un conjunto de tipos, reemplace la interfaz por un atributo personalizado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la interfaz se utiliza para identificar un conjunto de tipos en tiempo de compilación.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una interfaz vacía.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
