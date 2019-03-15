---
title: EditorConfig frente a los analizadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57874713"
---
# <a name="analyzers-faq"></a>Preguntas más frecuentes de analizadores

Esta página contiene respuestas a algunas preguntas frecuentes acerca de los analizadores de Roslyn en Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Analizadores de Roslyn frente a .editorconfig

**PREGUNTAS Y**: ¿Debo usar analizadores de Roslyn o .editorconfig para el estilo de código?

**R**: Analizadores de Roslyn y los archivos .editorconfig funcionan en la mano. Al definir estilos de código [en un archivo .editorconfig](../ide/editorconfig-code-style-settings-reference.md) o en el [editor de texto opciones](../ide/code-styles-and-quick-actions.md) página, realmente está configurando los analizadores de Roslyn que están integrados en Visual Studio. También pueden utilizarse para configurar algunos paquetes de analizador de terceros, como los archivos EditorConfig [analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig frente a conjuntos de reglas

**PREGUNTAS Y**: ¿Debo configurar mi analizadores mediante un conjunto de reglas o un archivo .editorconfig?

**R**: Conjuntos de reglas y los archivos .editorconfig son mutuamente excluyentes formas de configurar los analizadores. Pueden coexistir. [Conjuntos de reglas](analyzer-rule-sets.md) le permite habilitar y deshabilitar las reglas y establecer su gravedad. Los archivos EditorConfig ofrecen otras formas de configurar las reglas. Analizadores de FxCop, los archivos .editorconfig permiten [definir qué tipos de código para analizar](fxcop-analyzer-options.md). Para los analizadores que están integrados en Visual Studio, los archivos .editorconfig permiten [definir los estilos de código preferido](../ide/editorconfig-code-style-settings-reference.md) para un código base.

Además de conjuntos de reglas y los archivos .editorconfig, algunos analizadores de terceros se configuran mediante el uso de los archivos de texto marcados como [archivos adicionales](../ide/build-actions.md#build-action-values) para el C# y compiladores VB.

> [!NOTE]
> Los archivos EditorConfig no se puede usar para configurar reglas de análisis de código estático, mientras que los conjuntos de reglas pueden.

## <a name="analyzers-in-ci-builds"></a>Analizadores en las compilaciones de CI

**PREGUNTAS Y**: ¿Los analizadores funcionan en compilaciones de integración continua (CI)?

**R**: Sí. Los analizadores que se instalan desde un paquete de NuGet, esas reglas están [aplica en tiempo de compilación](roslyn-analyzers-overview.md#build-errors), incluidos durante una compilación de CI. Analizadores utilizados en configuración de reglas de respeto CI compilaciones desde ambos [conjuntos de reglas](analyzer-rule-sets.md) y [archivos .editorconfig](configure-fxcop-analyzers.md). Actualmente, los analizadores de código que están integrados en Visual Studio no están disponibles como un paquete de NuGet y, por lo que estas reglas no son aplicables en una compilación de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores IDE en comparación con StyleCop

**PREGUNTAS Y**: ¿Qué es la diferencia entre los analizadores de código del IDE de Visual Studio y analizadores de StyleCop?

**R**: El IDE de Visual Studio incluye analizadores integrados que buscan ambos problemas de estilo y la calidad del código. Estas reglas le ayudarán a usar nuevas características del lenguaje, ya que se introducen y mejoran la facilidad de mantenimiento del código. Los analizadores IDE se actualizarán continuamente con cada versión de Visual Studio.

[Los analizadores de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros instalados como un paquete de NuGet que comprobación la coherencia de estilo en el código. En general, las reglas de StyleCop le permiten establecer preferencias personales para un código base sin recomendar un estilo a través de otro.

## <a name="analyzers-versus-static-code-analysis"></a>Analizadores frente a análisis de código estático

**PREGUNTAS Y**: ¿Qué es la diferencia entre los analizadores y análisis de código estático?

**R**: Analizadores de análisis de código fuente en tiempo real y durante la compilación, mientras que el análisis de código estático analiza los archivos binarios de una vez finalizada la compilación. Para obtener más información, consulte [analizadores de Roslyn frente a análisis de código estático](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) y [preguntas más frecuentes sobre los analizadores de FxCop](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Vea también

- [Información general de analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)