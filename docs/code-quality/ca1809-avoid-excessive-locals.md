---
title: 'CA1809: Evitar el exceso de variables locales'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0135241e81fb020d5f5107bcb76e37bad16fb56d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828512"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitar el exceso de variables locales

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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla, o para deshabilitar la regla, si el rendimiento no es un problema.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)