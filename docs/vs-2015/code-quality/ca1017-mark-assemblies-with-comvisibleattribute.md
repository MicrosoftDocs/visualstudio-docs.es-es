---
title: 'CA1017: Marque los ensamblados con ComVisibleAttribute | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17f0a540a436316d3a4fb3b71a2a51b1c5a90a6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535075"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Marcar los ensamblados con ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|Identificador de comprobación|CA1017|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un ensamblado no tiene <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> aplicado el atributo.

## <a name="rule-description"></a>Descripción de la regla
 El <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina el modo en que los clientes com acceden al código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. La visibilidad de COM se puede establecer para un ensamblado entero y, a continuación, se puede invalidar para tipos y miembros de tipo individuales. Si el atributo no está presente, el contenido del ensamblado es visible para los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado. Si no desea que el ensamblado esté visible para los clientes COM, aplique el atributo y establezca su valor en `false` .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Si desea que el ensamblado esté visible, aplique el atributo y establezca su valor en `true` .

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un ensamblado que tiene <xref:System.Runtime.InteropServices.ComVisibleAttribute> aplicado el atributo para evitar que sea visible para los clientes com.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Consulte también
 [Interoperar con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) que [cumple los tipos de .net para la interoperación](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
