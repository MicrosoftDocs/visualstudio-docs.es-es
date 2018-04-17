---
title: 'CA1809: Evitar el exceso de variables locales | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: 63bdcf0ea8363e6deb16034011d0a4446594171f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitar el exceso de variables locales
|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|Identificador de comprobación|CA1809|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un miembro contiene más de 64 variables locales, algunas de las cuales pueden ser generado por el compilador.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una optimización de rendimiento común es almacenar un valor en un registro del procesador en lugar de en memoria, lo que se conoce como *registrar* el valor. Common language runtime considera hasta 64 variables locales para su registro. Las variables que no se registren se colocan en la pila y deben moverse a un registro antes de su manipulación. Para permitir la posibilidad de que todas las variables locales, obtener registren, limite el número de variables locales a 64.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, refactorice la implementación para que use no más de 64 variables locales.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla, o para deshabilitar la regla, si el rendimiento no es un problema.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)