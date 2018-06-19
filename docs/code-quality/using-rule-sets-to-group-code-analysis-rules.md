---
title: Conjuntos de reglas de análisis de código en Visual Studio
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
ms.openlocfilehash: 20e727fd331ebd98a74acbb63738e6921e5ad1a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923060"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Regla de uso se establece para agrupar reglas de análisis de código

Al configurar el análisis de código en Visual Studio, puede elegir entre una lista integrados de *conjuntos de reglas*. Un conjunto de reglas se aplica a un proyecto y es una agrupación de código reglas de análisis que identifican problemas concretos y condiciones específicas para ese proyecto. Por ejemplo, puede aplicar un conjunto de reglas está diseñado para examinar el código para las API disponibles públicamente o simplemente el mínimo recomendado reglas. También puede aplicar un conjunto de reglas que incluye todas las reglas.

Puede personalizar un conjunto de reglas agregando o eliminando las reglas, o cambiando los niveles de gravedad de regla para que aparezca como advertencias o errores en el **lista de errores**. Los conjuntos de reglas personalizados pueden satisfacer una necesidad de su entorno de desarrollo determinado. Al personalizar un conjunto de reglas, el editor de conjunto de reglas proporciona búsqueda y las herramientas para ayudarle en el proceso de filtrado.

## <a name="rule-set-format"></a>Formato de conjunto de reglas

Se especifica un conjunto de reglas en formato XML en un *.ruleset* archivo. Las reglas, que constan de un identificador y un *acción*, agrupados por identificador de analizador y el espacio de nombres en el archivo.

El contenido XML de un *.ruleset* archivo tiene un aspecto similar al siguiente:

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

La regla establecida para un proyecto se especifica mediante el `CodeAnalysisRuleSet` propiedad en el archivo de proyecto de Visual Studio. Por ejemplo:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Vea también

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)
