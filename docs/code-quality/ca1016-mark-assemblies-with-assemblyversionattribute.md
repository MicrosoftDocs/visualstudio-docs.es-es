---
title: 'CA1016: Marcar los ensamblados con AssemblyVersionAttribute | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9dc5bea6f18265117c0d284ed048009ff9fdafcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Marcar los ensamblados con AssemblyVersionAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|Identificador de comprobación|CA1016|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 El ensamblado no tiene un número de versión.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La identidad de un ensamblado se compone de la siguiente información:  
  
-   Nombre del ensamblado  
  
-   Número de versión  
  
-   culture  
  
-   Clave pública (para los ensamblados con nombre seguro).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utiliza el número de versión para identificar de forma única un ensamblado y para enlazarse a los tipos de ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue un número de versión al ensamblado utilizando el <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributo. Vea el ejemplo siguiente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla para los ensamblados que se utilizan por terceros, o en un entorno de producción.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un ensamblado que tiene el <xref:System.Reflection.AssemblyVersionAttribute> atributo aplicado.  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Versiones de los ensamblados](/dotnet/framework/app-domains/assembly-versioning)   
 [Cómo: Crear una directiva de publicador](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)