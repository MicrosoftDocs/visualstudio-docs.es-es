---
title: 'CA1801: Revisar parámetros sin utilizar | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0372588b325a54e6776cd231fbe04484a81310e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574245"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Revisar parámetros sin utilizar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [CA1801: revisar parámetros sin utilizar](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters) en docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|Identificador de comprobación|CA1801|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No problemático: si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice.<br /><br /> No problemático: si cambia el miembro para usar el parámetro dentro del cuerpo.<br /><br /> Problemático: Si quita el parámetro y está visible fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. Esta regla no examina los métodos siguientes:  
  
-   Métodos que se hace referencia a un delegado.  
  
-   Métodos que se usan como controladores de eventos.  
  
-   Los métodos declarados con el `abstract` (`MustOverride` en Visual Basic) modificador.  
  
-   Los métodos declarados con el `virtual` (`Overridable` en Visual Basic) modificador.  
  
-   Los métodos declarados con el `override` (`Overrides` en Visual Basic) modificador.  
  
-   Los métodos declarados con el `extern` (`Declare` instrucción en Visual Basic) modificador.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Revise los parámetros de métodos no virtuales que no se usan en el cuerpo del método para asegurarse de que no hay exactitud en torno al error para tener acceso a ellos. Parámetros sin usar conllevan un costo de mantenimiento y rendimiento.  
  
 A veces, una infracción de esta regla puede señalar a un error en el método de implementación. Por ejemplo, el parámetro debe haberse utilizado en el cuerpo del método. Suprimir advertencias de esta regla si el parámetro tiene que existir por compatibilidad con versiones anteriores.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el parámetro sin usar (un cambio importante) o utilizar el parámetro en el cuerpo del método (un cambio de no separación).  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla para código lanzado al mercado anteriormente para que la solución sería un cambio importante.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra dos métodos. Un método infringe la regla y el otro método cumple la regla.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)

