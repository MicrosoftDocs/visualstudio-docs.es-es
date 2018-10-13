---
title: 'CA1809: Evitar variables locales excesivas | Microsoft Docs'
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
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e019c79138ab635e056852df426c5060d46da0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223903"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitar el exceso de variables locales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|Identificador de comprobación|CA1809|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un miembro contiene más de 64 variables locales, algunas de las cuales podrían ser generado por el compilador.

## <a name="rule-description"></a>Descripción de la regla
 Una optimización de rendimiento común es almacenar un valor en un registro del procesador en lugar de en memoria, lo que se conoce como *registrar* el valor. Common language runtime considera que un máximo de 64 variables locales para su registro. Las variables que no se registren se colocan en la pila y se deben mover a un registro antes de la manipulación. Para permitir la posibilidad de que todas las variables locales, obtener registren, limite el número de variables locales a 64.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, refactorice la implementación para utilizar no más de 64 variables locales.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla, o para deshabilitar la regla, si el rendimiento no es un problema.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)



