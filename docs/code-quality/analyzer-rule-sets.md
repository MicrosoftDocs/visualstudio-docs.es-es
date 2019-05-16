---
title: Conjuntos de reglas del analizador
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 696e6bd46c17054494be2ea0e0f2a1af4fd703d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675485"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Conjuntos de reglas para los analizadores de Roslyn

Conjuntos de reglas predefinidos se incluyen con algunos paquetes de NuGet analyzer. Por ejemplo, los conjuntos de reglas que se incluyen con el [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) paquete de analizadores de NuGet (a partir de la versión 2.6.2) habilitar o deshabilitar reglas según su categoría, como la seguridad, nomenclatura, o rendimiento. Usar conjuntos de reglas facilita ver rápidamente sólo esas infracciones de reglas que pertenecen a una categoría determinada de la regla.

Si está migrando de análisis de código estático de "FxCop" heredado para los analizadores de Roslyn, estos conjuntos de reglas permiten seguir usando la misma configuración de regla que usó anteriormente.

## <a name="use-analyzer-rule-sets"></a>Usar conjuntos de reglas del analizador

Después de [instalar un paquete de NuGet analizador](install-roslyn-analyzers.md), busque la regla predefinida que se establece su *rulesets* directory. Por ejemplo, si hace referencia a la `Microsoft.CodeAnalysis.FxCopAnalyzers` paquete de analizadores, a continuación, se puede encontrar su *rulesets* directorio en *% USERPROFILE %\\.nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\ \<versión\>\rulesets*. Desde allí, copiar uno o varios de los conjuntos de reglas y péguelos en el directorio que contiene el proyecto de Visual Studio o directamente en **el Explorador de soluciones**.

También puede [personalizar un conjunto de reglas predefinidas](how-to-create-a-custom-rule-set.md) según sus preferencias. Por ejemplo, puede cambiar la gravedad de una o varias reglas para que aparezcan las infracciones como errores o advertencias en el **lista de errores**.

## <a name="set-the-active-rule-set"></a>Establecer el conjunto de reglas activo

El proceso para establecer el conjunto de reglas activo es ligeramente diferente dependiendo de si tiene un proyecto de .NET Core/.NET Standard o .NET Framework.

### <a name="net-core"></a>Núcleo de .NET

Para crear una regla de establecer la regla activa establecida para el análisis en los proyectos de .NET Core o .NET Standard, agregar manualmente el **CodeAnalysisRuleSet** propiedad al archivo de proyecto. Por ejemplo, el código siguiente fragmento de código establece `HelloWorld.ruleset` como la regla active establecido.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Para crear una regla de establecer la regla activa establecida para el análisis en los proyectos de .NET Framework, haga doble clic en el proyecto en **el Explorador de soluciones** y elija **propiedades**. En las páginas de propiedades del proyecto, seleccione el **análisis de código** ficha. En **ejecutar este conjunto de reglas**, seleccione **examinar**y, a continuación, seleccione el conjunto de reglas que copió en el directorio del proyecto. Ahora verá solo las infracciones de reglas para aquellas reglas que están habilitadas en el conjunto de reglas seleccionado.

## <a name="available-rule-sets"></a>Conjuntos de reglas disponibles

Los conjuntos de reglas del analizador predefinido incluyen tres conjuntos de reglas que afectan a todas las reglas en el paquete&mdash;que permite que todos ellos, uno que impida a todos ellos y otro que respeta la configuración de la regla predeterminada gravedad y la habilitación de:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Además, hay dos conjuntos de reglas para cada categoría de reglas en el paquete, como el rendimiento o la seguridad. Un conjunto de reglas habilita todas las reglas para la categoría y un conjunto de reglas respeta la configuración predeterminada de gravedad y la habilitación para cada regla de la categoría.

El [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) paquete de NuGet analyzer incluye conjuntos de reglas para las siguientes categorías, que coinciden con los conjuntos de reglas disponibles para el análisis de código estático heredado "FxCop":

- diseño
- en línea
- mantenimiento
- asignar nombre
- rendimiento
- confiabilidad
- seguridad
- uso

## <a name="see-also"></a>Vea también

- [Preguntas más frecuentes sobre analizadores](analyzers-faq.md)
- [Introducción a los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalar analizadores](install-roslyn-analyzers.md)
- [Usar los analizadores](use-roslyn-analyzers.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md)
