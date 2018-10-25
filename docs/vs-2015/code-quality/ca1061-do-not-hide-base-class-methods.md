---
title: 'CA1061: No oculte métodos de clase base | Microsoft Docs'
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
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8bcee9f4bee5f5e505b4dddfb53d6a4cf30c39c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826731"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: No oculte métodos de clases base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|Identificador de comprobación|CA1061|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo derivado declara un método con el mismo nombre y con el mismo número de parámetros como uno de sus métodos base; uno o varios de los parámetros son un tipo base del parámetro correspondiente del método base; y los parámetros restantes tienen tipos que son idénticos a los parámetros correspondientes en el método base.

## <a name="rule-description"></a>Descripción de la regla
 Un método en un tipo base está oculto por un método con el mismo nombre en un tipo derivado cuando la firma del parámetro del método derivado difiere solo en tipos que son más débil derivados que los tipos correspondientes de la firma del parámetro del método base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quitar o cambiar el nombre del método o cambie la firma del parámetro para que el método no oculta el método base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que infringe la regla.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]



