---
title: 'CA1500: Los nombres de Variable no deberían coincidir con los nombres de campo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2dc3e217d0645d4acc5afaf416c40f2f16f81bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|Identificador de comprobación|CA1500|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Cuando se desencadena en un parámetro que tiene el mismo nombre que un campo:<br /><br /> No-problemático: si el campo y el método que declara el parámetro no pueden ver desde fuera del ensamblado, sin tener en cuenta el cambio realizado.<br />-Problemático: si cambia el nombre del campo y se pueden ver desde fuera del ensamblado.<br />-Problemático: si cambia el nombre del parámetro y el método que lo declara puede verse fuera del ensamblado.<br /><br /> Cuando se desencadena en una variable local que tiene el mismo nombre que un campo:<br /><br /> No-problemático: si el campo no pueden ver desde fuera del ensamblado, sin tener en cuenta el cambio realizado.<br />No-problemático: si cambia el nombre de la variable local y no cambie el nombre del campo.<br />-Problemático: si cambia el nombre del campo y se puede ver desde fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo. Para detectar las variables locales que infringen la regla, el ensamblado probado se debe generar mediante el uso de información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando el nombre de un campo de instancia coincide con un parámetro o un nombre de variable local, el campo de instancia se accede mediante la `this` (`Me` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (palabra clave) cuando esté en el cuerpo del método. Cuando el mantenimiento del código, es fácil olvidarse de esta diferencia y se supone que el parámetro o la variable local hace referencia al campo de instancia, lo que conduce a errores. Esto es cierto especialmente para los cuerpos de método largos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre de la variable de parámetros o el campo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra dos infracciones de esta regla.  
  
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]