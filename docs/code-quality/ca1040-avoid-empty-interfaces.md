---
title: "CA1040: Evitar interfaces vacías | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e086ffc1b0166ec17954323b8cf7871fd758ea0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitar interfaces vacías
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|Identificador de comprobación|CA1040|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 La interfaz no declara a ningún miembro ni lo implementa dos o más interfaces.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro. Por lo tanto, no define un contrato que se puede implementar.  
  
 Si el diseño incluye vacía interfaces que los tipos se esperan para implementar, probablemente está utilizando una interfaz como un marcador o una forma de identificar un grupo de tipos. Si esta identificación se produce en tiempo de ejecución, la manera correcta de lograrlo es utilizar un atributo personalizado. Utilice la presencia o ausencia del atributo o las propiedades del atributo, para identificar los tipos de destino. Si la identificación debe producirse en tiempo de compilación, es aceptable utilizar una interfaz vacía.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Quite la interfaz o agregarle a miembros. Si la interfaz vacía es que se utiliza para etiquetar un conjunto de tipos, reemplace la interfaz con un atributo personalizado.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la interfaz se usa para identificar un conjunto de tipos en tiempo de compilación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una interfaz vacía.  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]