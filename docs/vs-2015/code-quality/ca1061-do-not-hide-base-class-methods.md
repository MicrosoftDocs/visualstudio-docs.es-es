---
title: 'CA1061: no ocultar métodos de clase base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c884eb569d5682326d2dc667363f991467171386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533359"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: No ocultar métodos de clase base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|Identificador de comprobación|CA1061|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo derivado declara un método con el mismo nombre y con el mismo número de parámetros que uno de sus métodos base; uno o varios parámetros son un tipo base del parámetro correspondiente en el método base; y cualquier parámetro restante tiene tipos que son idénticos a los parámetros correspondientes en el método base.

## <a name="rule-description"></a>Descripción de la regla
 Un método en un tipo base está oculto por un método con un nombre idéntico en un tipo derivado cuando la firma del parámetro del método derivado solo difiere en los tipos que se derivan de forma más débil que los tipos correspondientes de la firma del parámetro del método base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o cambie el nombre del método o cambie la firma del parámetro para que el método no oculte el método base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que infringe la regla.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]
