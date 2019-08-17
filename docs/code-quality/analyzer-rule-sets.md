---
title: Conjuntos de reglas del analizador
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c0be66559802188503c3b8f8c1c2cf2955dbd8a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547943"
---
# <a name="rule-sets-for-analyzer-packages"></a>Conjuntos de reglas para paquetes de analizador

Los conjuntos de reglas predefinidos se incluyen en algunos paquetes del analizador de NuGet. Por ejemplo, los conjuntos de reglas que se incluyen con el paquete del analizador de NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (a partir de la versión 2.6.2 Critical () habilitan o deshabilitan reglas en función de su categoría, como la seguridad, la nomenclatura o el rendimiento. El uso de conjuntos de reglas facilita la rápida consulta únicamente de las infracciones de reglas que pertenecen a una determinada categoría de regla.

Si va a migrar desde el análisis de "FxCop" heredado al análisis de código basado en .NET Compiler Platform, estos conjuntos de reglas permiten seguir usando las mismas configuraciones de reglas que usó anteriormente.

## <a name="use-analyzer-package-rule-sets"></a>Usar conjuntos de reglas de paquetes de analizador

Después de [instalar un paquete del analizador de NuGet](install-roslyn-analyzers.md), busque el conjunto de reglas predefinidas en su directorio de *conjuntos* de reglas. Por ejemplo, si hace referencia al paquete `Microsoft.CodeAnalysis.FxCopAnalyzers` de analizador, puede encontrar su directorio de *conjuntos* de las *versiones% userprofile\\%.\\\<nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers versión \rulesets\>* . Desde ahí, copie uno o más de los conjuntos de elementos y péguelos en el directorio que contiene el proyecto de Visual Studio o directamente en **Explorador de soluciones**.

También puede [personalizar un conjunto de reglas predefinidas según](how-to-create-a-custom-rule-set.md) sus preferencias. Por ejemplo, puede cambiar la gravedad de una o varias reglas para que las infracciones aparezcan como errores o advertencias en el **lista de errores**.

## <a name="set-the-active-rule-set"></a>Establecer el conjunto de reglas activo

El proceso para establecer el conjunto de reglas activo es un poco diferente en función de si tiene un proyecto .NET Core/. NET Standard o un proyecto .NET Framework.

### <a name="net-core"></a>Núcleo de .NET

Para que un conjunto de reglas establezca el conjunto de reglas activo para el análisis en .NET Core o en proyectos de .NET Standard, agregue manualmente la propiedad **CodeAnalysisRuleSet** al archivo de proyecto. Por ejemplo, el fragmento de código siguiente `HelloWorld.ruleset` establece como el conjunto de reglas activo.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Para que un conjunto de reglas establezca el conjunto de reglas activo para el análisis en .NET Framework proyectos, haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y elija **propiedades**. En las páginas de propiedades del proyecto, seleccione la pestaña **análisis de código** . En **ejecutar este conjunto de reglas**, seleccione **examinar**y, a continuación, seleccione el conjunto de reglas que desea copiar en el directorio del proyecto. Ahora solo verá infracciones de reglas para las reglas que están habilitadas en el conjunto de reglas seleccionado.

## <a name="available-rule-sets"></a>Conjuntos de reglas disponibles

Los conjuntos de reglas del analizador predefinido incluyen tres conjuntos de reglas que afectan a todas&mdash;las reglas del paquete que los habilita, uno que los deshabilita todos, y otro que respeta la configuración de la gravedad y habilitación predeterminada de cada regla:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Además, hay dos conjuntos de reglas para cada categoría de reglas en el paquete, como el rendimiento o la seguridad. Un conjunto de reglas habilita todas las reglas de la categoría y un conjunto de reglas respeta la gravedad y la configuración de habilitación predeterminadas para cada regla de la categoría.

El paquete del analizador de NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) incluye conjuntos de reglas para las siguientes categorías, que coinciden con los conjuntos de reglas disponibles para el análisis heredado:

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
- [Usar analizadores](use-roslyn-analyzers.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md)
