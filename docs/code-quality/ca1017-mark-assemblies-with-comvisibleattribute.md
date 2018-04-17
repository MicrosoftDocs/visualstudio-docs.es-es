---
title: 'CA1017: Marcar los ensamblados con ComVisibleAttribute | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5aa835d06dc081445673bc3a92dff1184d329d51
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Marcar los ensamblados con ComVisibleAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|Identificador de comprobación|CA1017|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un ensamblado no tiene el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo aplicado a ella.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina cómo acceso los clientes COM al código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. Visibilidad COM se puede establecer para un ensamblado entero y, a continuación, se reemplaza para los tipos individuales y miembros de tipo. Si el atributo no está presente, el contenido del ensamblado es visible para los clientes COM.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado. Si no desea que el ensamblado sea visible para los clientes COM, aplique el atributo y establezca su valor en `false`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Si desea que el ensamblado esté visible, aplique el atributo y establezca su valor en `true`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un ensamblado que tiene el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo que se aplica para evitar que sea visible para los clientes COM.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Interoperar con código no administrado](/dotnet/framework/interop/index)   
 [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)