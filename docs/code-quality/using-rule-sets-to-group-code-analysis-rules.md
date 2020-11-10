---
title: Conjuntos de reglas de análisis de código
ms.date: 04/02/2018
description: Obtenga información sobre los conjuntos de reglas integrados y personalizados en el análisis de código de Visual Studio. Vea cómo especificar conjuntos de reglas en archivos y cómo configurar conjuntos de reglas en proyectos.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49d17e8321aa6567a6ae0936291a73d5cb854b5c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436893"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Usar conjuntos de reglas para agrupar reglas de análisis de código

Al configurar el análisis de código en Visual Studio, puede elegir en una lista de *conjuntos de reglas* integrados. Un conjunto de reglas es una agrupación de reglas de análisis de código que identifican problemas de destino y condiciones específicas para ese proyecto. Por ejemplo, puede aplicar un conjunto de reglas diseñado para examinar el código de las API disponibles públicamente. También puede aplicar un conjunto de reglas que incluya todas las reglas disponibles.

Puede personalizar un conjunto de reglas agregando o eliminando reglas o cambiando el gravedad de la regla para que aparezca como advertencias o errores en el **lista de errores**. Los conjuntos de reglas personalizados pueden satisfacer una necesidad de su entorno de desarrollo determinado. Al personalizar un conjunto de reglas, el editor de conjuntos de reglas proporciona herramientas de búsqueda y filtrado que le ayudarán en el proceso.

Los conjuntos de reglas están disponibles para el [análisis de código administrado](/dotnet/fundamentals/code-analysis/code-quality-rule-options), el [análisis heredado de código administrado](how-to-configure-code-analysis-for-a-managed-code-project.md)y el [análisis de código de C++](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

## <a name="rule-set-format"></a>Formato del conjunto de reglas

Un conjunto de reglas se especifica en formato XML en un archivo *. ruleset* . Las reglas, que constan de un identificador y una *acción* , se agrupan por identificador y espacio de nombres del analizador en el archivo.

El contenido de un archivo *. ruleset* tiene un aspecto similar al de este XML:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Es más fácil [editar un conjunto de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md) en el **Editor de conjuntos de reglas** gráfico que a mano.

## <a name="specify-a-rule-set-for-a-project"></a>Especificar un conjunto de reglas para un proyecto

La propiedad **CodeAnalysisRuleSet** del archivo de proyecto de Visual Studio especifica el conjunto de reglas para un proyecto. Por ejemplo:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Consulte también

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)