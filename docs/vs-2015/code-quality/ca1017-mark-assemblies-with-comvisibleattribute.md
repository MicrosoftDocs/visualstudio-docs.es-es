---
title: 'CA1017: Marque los ensamblados con ComVisibleAttribute | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1a5adc7e9fcb0ee78a7dd93f05209ea331d3c768
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996799"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Marcar los ensamblados con ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|Identificador de comprobación|CA1017|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un ensamblado no tiene el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo aplicado a él.

## <a name="rule-description"></a>Descripción de la regla
 El <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina cómo acceder a los clientes COM a código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. La visibilidad COM se puede establecer para todo un ensamblado y, a continuación, se invalida para tipos y miembros de tipo individuales. Si el atributo no está presente, el contenido del ensamblado es visible para los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado. Si no desea que el ensamblado sea visible para los clientes COM, aplique el atributo y establezca su valor en `false`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Si desea que el ensamblado sea visible, aplique el atributo y establezca su valor en `true`.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un ensamblado que tiene el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo aplicado para evitar que sea visible para los clientes COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Vea también
 [Interoperar con código no administrado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [habilitar tipos de .NET para la interoperación](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
