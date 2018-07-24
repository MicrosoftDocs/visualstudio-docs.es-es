---
title: Conjuntos de reglas de análisis de código
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa287570213e6238d0a8dffc9f6e70367b133591
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204432"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Usar conjuntos de reglas para agrupar reglas de análisis de código

Al configurar el análisis de código en Visual Studio, puede elegir entre una lista de integrados *conjuntos de reglas*. Un conjunto de reglas se aplica a un proyecto y es una agrupación de código reglas de análisis que identifican problemas concretos y condiciones específicas para ese proyecto. Por ejemplo, puede aplicar un conjunto de reglas está diseñado para examinar el código para las API disponibles públicamente o simplemente el mínimo recomendado reglas. También puede aplicar un conjunto de reglas que incluye todas las reglas.

Puede personalizar un conjunto de reglas mediante la adición o eliminación de reglas, o cambiando los niveles de gravedad de regla aparezca como advertencias o errores en el **lista de errores**. Los conjuntos de reglas personalizados pueden satisfacer una necesidad de su entorno de desarrollo determinado. Al personalizar un conjunto de reglas, el editor de conjunto de reglas proporciona búsqueda y las herramientas para ayudarle en el proceso de filtrado.

Conjuntos de reglas que están disponibles para [análisis estático de código administrado](how-to-configure-code-analysis-for-a-managed-code-project.md), [análisis de código C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md), y [analizadores de Roslyn](analyzer-rule-sets.md).

## <a name="rule-set-format"></a>Formato de conjunto de reglas

Se especifica un conjunto de reglas en formato XML en un *.ruleset* archivo. Las reglas, que constan de un identificador y un *acción*, se agrupan por identificador de analizador y el espacio de nombres en el archivo.

El contenido de un *.ruleset* archivo es similar a este código XML:

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
> Es más fácil [editar un conjunto de reglas](../code-quality/working-in-the-code-analysis-rule-set-editor.md) en el gráfico **Editor de conjunto de reglas** de forma manual.

La regla establecida para un proyecto especificado por el **CodeAnalysisRuleSet** propiedad en el archivo de proyecto de Visual Studio. Por ejemplo:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Vea también

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)