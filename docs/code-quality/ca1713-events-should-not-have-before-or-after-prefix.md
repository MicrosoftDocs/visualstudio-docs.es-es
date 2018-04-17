---
title: 'CA1713: Los eventos no deberían tener prefijos antes ni después | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3daa93429a59e0b6c3f03db0fc62dd7850df3be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Los eventos no deberían tener prefijos antes ni después
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|Identificador de comprobación|CA1713|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 El nombre de un evento empieza por 'Before' o 'After'.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Nombres de evento deben describir la acción que provoca el evento. Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones. Por ejemplo, cuando asigne nombres a un par de eventos que se provocan al cerrar un recurso, podría denomínelo 'Closing' y 'Cerrado', en lugar de 'BeforeClose' y 'AfterClose'.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Quite el prefijo del nombre de evento y considere la posibilidad de cambiar el nombre que se usará el tiempo presente o pasado de un verbo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.