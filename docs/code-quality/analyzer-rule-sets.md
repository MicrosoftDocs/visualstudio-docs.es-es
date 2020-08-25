---
title: Archivos editorconfig y conjuntos de reglas del analizador de FxCop
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b99bb08c82725f19f7985a97656edf65f112d5
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800221"
---
# <a name="enable-a-category-of-rules"></a>Habilitar una categoría de reglas

Los paquetes de analizador pueden incluir archivos de [conjunto de reglas](using-rule-sets-to-group-code-analysis-rules.md) y [EditorConfig](use-roslyn-analyzers.md#rule-severity) predefinidos que facilitan y agilizan la habilitación de una categoría de reglas, como reglas de seguridad o de diseño. El paquete del analizador de NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) incluye ambos conjuntos de reglas (a partir de la versión 2.6.2 Critical () y archivos EditorConfig (a partir de la versión 2.9.5). Al habilitar una categoría específica de reglas, puede identificar problemas de destino y condiciones específicas.

> [!NOTE]
> La habilitación de las reglas del analizador y el establecimiento de su gravedad mediante un archivo EditorConfig se admite a partir de la versión 16,3 de Visual Studio 2019.

El paquete de NuGet del analizador de FxCop incluye conjuntos de reglas predefinidos y archivos EditorConfig para las siguientes categorías de reglas:

- Todas las reglas
- Flujo de datos
- Diseño
- Documentación
- Globalización
- Interoperabilidad
- Capacidad de mantenimiento
- Nomenclatura
- Rendimiento
- Trasladado desde FxCop
- Confiabilidad
- Seguridad
- Uso

Cada una de esas categorías de reglas tiene un EditorConfig o un archivo de conjunto de reglas para:

- habilitar todas las reglas de la categoría (y deshabilitar todas las demás reglas)
- usar la configuración predeterminada de gravedad y habilitación de cada regla (y deshabilitar todas las demás reglas)

> [!TIP]
> La categoría "todas las reglas" tiene un EditorConfig adicional o un archivo de conjunto de reglas para deshabilitar todas las reglas. Use este archivo para deshacerse rápidamente de cualquier error o advertencia del analizador en un proyecto.

> [!TIP]
> Si va a migrar desde el análisis de "FxCop" heredado al análisis de código basado en .NET Compiler Platform, los archivos de conjunto de reglas y EditorConfig permiten seguir usando configuraciones de reglas similares a [las que usó anteriormente](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Archivos EditorConfig predefinidos

Los archivos EditorConfig predefinidos para el paquete Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer se encuentran en el directorio *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig* . Por ejemplo, el archivo EditorConfig para habilitar todas las reglas de seguridad se encuentra en *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Copie el archivo. editorconfig elegido en el directorio raíz del proyecto.

## <a name="predefined-rule-sets"></a>Conjunto de reglas predefinidas

Los archivos de conjunto de reglas predefinidos para el paquete Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer se encuentran en el directorio *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets* . Por ejemplo, el archivo de conjunto de reglas para habilitar todas las reglas de seguridad se encuentra en *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.ruleset*.

Copie uno o más conjuntos de reglas y péguelos en el directorio que contiene el proyecto de Visual Studio o directamente en **Explorador de soluciones**.

También puede [personalizar un conjunto de reglas predefinidas según](how-to-create-a-custom-rule-set.md) sus preferencias. Por ejemplo, puede cambiar la gravedad de una o varias reglas para que las infracciones aparezcan como errores o advertencias en el **lista de errores**.

### <a name="set-the-active-rule-set"></a>Establecer el conjunto de reglas activo

El proceso para establecer el conjunto de reglas activo es un poco diferente en función de si tiene un proyecto .NET Core/. NET Standard o un proyecto .NET Framework.

#### <a name="net-core"></a>.NET Core

Para que un conjunto de reglas establezca el conjunto de reglas activo para el análisis en .NET Core o en proyectos de .NET Standard, agregue manualmente la propiedad **CodeAnalysisRuleSet** al archivo de proyecto. Por ejemplo, el fragmento de código siguiente establece `HelloWorld.ruleset` como el conjunto de reglas activo.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

Para que un conjunto de reglas establezca el conjunto de reglas activo para el análisis en .NET Framework proyectos:

- Haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades**.

- En las páginas de propiedades del proyecto, seleccione la pestaña **análisis de código** .

::: moniker range="vs-2017"

- En **ejecutar este conjunto de reglas**, seleccione **examinar**y elija el conjunto de reglas que desea copiar en el directorio del proyecto.

::: moniker-end

::: moniker range=">=vs-2019"

- En **reglas activas**, seleccione **examinar**y elija el conjunto de reglas que desea copiar en el directorio del proyecto.

::: moniker-end

   Ahora solo verá infracciones de reglas para las reglas que están habilitadas en el conjunto de reglas seleccionado.

## <a name="see-also"></a>Consulte también

- [Preguntas más frecuentes sobre analizadores](analyzers-faq.md)
- [Introducción a los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalar analizadores](install-roslyn-analyzers.md)
- [Configurar analizadores](use-roslyn-analyzers.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](using-rule-sets-to-group-code-analysis-rules.md)
