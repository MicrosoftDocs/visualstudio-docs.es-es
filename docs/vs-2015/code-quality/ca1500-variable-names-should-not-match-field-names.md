---
title: 'CA1500: Los nombres de variable no deben coincidir con los nombres de campo | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8dc15c95398ed45954c3830d1c558a6653a4346f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191485"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1500: Los nombres de variable no deben coincidir con los nombres de campo](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|Identificador de comprobación|CA1500|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Cuando se desencadena en un parámetro que tiene el mismo nombre que un campo:<br /><br /> No-problemático: si el campo y el método que declara el parámetro no pueden verse fuera del ensamblado, independientemente del cambio que realice.<br />-Importante: si cambia el nombre del campo y se pueden ver desde fuera del ensamblado.<br />-Problemático: si cambia el nombre del parámetro y el método que lo declara puede verse fuera del ensamblado.<br /><br /> Cuando se desencadena en una variable local que tiene el mismo nombre que un campo:<br /><br /> No-problemático: si el campo no puede verse fuera del ensamblado, independientemente del cambio que realice.<br />No-problemático: si cambia el nombre de la variable local y no cambie el nombre del campo.<br />-Problemático: si cambia el nombre del campo y se puede ver desde fuera del ensamblado.|  
  
## <a name="cause"></a>Causa  
 Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo. Para capturar las variables locales que infringen la regla, se debe generar el ensamblado probado utilizando la información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando el nombre de un campo de instancia coincide con un parámetro o un nombre de variable local, el campo de instancia se accede mediante el `this` (`Me` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) la palabra clave cuando se encuentra dentro del cuerpo del método. Al mantener el código, es fácil olvidarse de esta diferencia y se supone que el parámetro o la variable local hace referencia al campo de instancia, lo que conduce a errores. Esto sucede especialmente para los cuerpos de método más largo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre de la variable de parámetros o el campo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra dos infracciones de la regla.  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
