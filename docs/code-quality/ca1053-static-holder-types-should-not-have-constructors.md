---
title: 'CA1053: Los tipos titulares estáticos no deberían tener constructores | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0a17b60cd88170a1df2ace72b8a4ee5206fe6d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Los tipos titulares estáticos no deben tener constructores
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|Identificador de comprobación|CA1053|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o público anidado declara sólo miembros estáticos y tiene un constructor predeterminado público o protegido.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El constructor no es necesario puesto que al llamar a los miembros estáticos no se requiere una instancia del tipo. Además, dado que el tipo no tiene miembros no estáticos, crear una instancia no proporcionan acceso a cualquiera de los miembros del tipo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el constructor predeterminado o que sea privada.  
  
> [!NOTE]
>  Algunos compiladores crean automáticamente un constructor predeterminado público si el tipo no define ningún constructor. Si este es el caso con su tipo, agregue un constructor predeterminado privado para eliminar la infracción.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. La presencia del constructor sugiere que el tipo no es un tipo estático.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe esta regla. Tenga en cuenta que no hay ningún constructor predeterminado en el código fuente. Cuando este código se compila en un ensamblado, el compilador de C# insertará un constructor predeterminado, que infringe esta regla. Para corregir este error, declare un constructor privado.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]