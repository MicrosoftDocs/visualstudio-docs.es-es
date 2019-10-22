---
title: 'CA1809: evitar variables locales excesivas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d23d9cc6006997c82451ac061e3ee0353e59b1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671495"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitar el exceso de variables locales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|Identificador de comprobación|CA1809|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un miembro contiene más de 64 variables locales, algunas de las cuales podrían ser generadas por el compilador.

## <a name="rule-description"></a>Descripción de la regla
 Una optimización de rendimiento común consiste en almacenar un valor en un registro del procesador en lugar de en la memoria, lo que se conoce como *registrar* el valor. El Common Language Runtime considera hasta 64 variables locales para el registro. Las variables que no están registradas se colocan en la pila y deben moverse a un registro antes de la manipulación. Para permitir la posibilidad de que se registren todas las variables locales, limite el número de variables locales a 64.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, refactorice la implementación para que no use más de 64 variables locales.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla o deshabilitar la regla si el rendimiento no es un problema.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)
