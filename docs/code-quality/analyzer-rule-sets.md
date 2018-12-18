---
title: Conjuntos de reglas del analizador
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7df084a81de2afc522fc3b82141cf8c5c59205ca
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204533"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Conjuntos de reglas para los analizadores de Roslyn

Conjuntos de reglas predefinidos se incluyen con algunos paquetes de NuGet analyzer. Por ejemplo, los conjuntos de reglas que se incluyen con el [paquete de Microsoft.CodeAnalysis.FxCopAnalyzers NuGet analizador](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (a partir de la versión 2.6.2), habilitar o deshabilitar reglas según su categoría, como la seguridad, nomenclatura, o rendimiento. Usar conjuntos de reglas facilita ver rápidamente sólo esas infracciones de reglas que pertenecen a una categoría determinada de la regla.

Si está migrando de análisis de código estático de "FxCop" heredado para los analizadores de Roslyn, estos conjuntos de reglas permiten seguir usando la misma configuración de regla que usó anteriormente.

## <a name="use-analyzer-rule-sets"></a>Usar conjuntos de reglas del analizador

Después de [instalar un paquete de NuGet analizador](install-roslyn-analyzers.md), busque la regla predefinida que se establece su *rulesets* directorio, por ejemplo *% USERPROFILE %\\.nuget\packages\ Microsoft.codequality.analyzers\<versión > \rulesets*. Desde allí, se puede arrastrar y colocar, o copiar y pegar, uno o varios de los conjuntos de reglas para el proyecto de Visual Studio en **el Explorador de soluciones**.

Para crear una regla de establecer la regla activa establecida para el análisis, haga doble clic en el proyecto en **el Explorador de soluciones** y elija **propiedades**. En las páginas de propiedades del proyecto, seleccione el **análisis de código** ficha. En **ejecutar este conjunto de reglas**, seleccione **examinar**y, a continuación, seleccione el conjunto de reglas que copió en el directorio del proyecto. Ahora verá solo las infracciones de reglas para aquellas reglas que están habilitadas en el conjunto de reglas seleccionado.

También puede [personalizar un conjunto de reglas predefinidas](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) según sus preferencias. Por ejemplo, puede cambiar la gravedad de una o varias reglas para que aparezcan las infracciones como errores o advertencias en el **lista de errores**.

## <a name="available-rule-sets"></a>Conjuntos de reglas disponibles

Los conjuntos de reglas del analizador predefinido incluyen tres conjuntos de reglas que afectan a todas las reglas en el paquete&mdash;que permite que todos ellos, uno que impida a todos ellos y otro que respeta la configuración de la regla predeterminada gravedad y la habilitación de:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Además, hay dos conjuntos de reglas para cada categoría de reglas en el paquete, como el rendimiento o la seguridad. Un conjunto de reglas habilita todas las reglas para la categoría y un conjunto de reglas respeta la configuración predeterminada de gravedad y la habilitación para cada regla de la categoría.

 El [paquete de analizadores de Microsoft.CodeAnalysis.FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) incluye conjuntos de reglas para las siguientes categorías, para que coincida con los conjuntos de reglas disponibles para el análisis de código estático de "FxCop" heredado:

- diseño
- en línea
- mantenimiento
- asignar nombre
- rendimiento
- confiabilidad
- seguridad
- uso

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalar analizadores de .NET Compiler Platform](install-roslyn-analyzers.md)
- [Configurar y usar las reglas del analizador de Roslyn](use-roslyn-analyzers.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md)