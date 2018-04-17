---
title: 'CA1061: No oculte métodos de clase base | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3119a088c0dfa7a976a12f0c6abb45e409da8d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: No oculte métodos de clases base
|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|Identificador de comprobación|CA1061|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo derivado declara un método con el mismo nombre y con el mismo número de parámetros que uno de sus métodos base; uno o varios de los parámetros son un tipo base del parámetro correspondiente del método base; y los parámetros restantes tienen tipos que son idénticos a los parámetros correspondientes en el método base.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un método en un tipo base está oculto por un método con el mismo nombre en un tipo derivado cuando la firma del parámetro del método derivado solo se diferencia por tipos de manera más débil derivados que los tipos correspondientes de la firma del parámetro del método base.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quitar o cambiar el nombre del método o cambie la firma del parámetro para que el método no oculte el método base.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que infringe la regla.  
  
 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]