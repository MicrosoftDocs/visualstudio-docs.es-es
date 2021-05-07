---
title: Migración de FxCop al análisis de origen (analizadores de .NET)
ms.custom: SEO-VS-2020
description: Obtenga información sobre cómo analizar código por primera vez o cómo migrar desde el análisis binario (FxCop) a la nueva forma de analizar código administrado mediante el análisis de código fuente (analizadores de .NET).
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798237"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migración del análisis heredado (FxCop) al análisis de origen (analizadores de .NET)

El análisis de código .NET Compiler Platform analizadores ("Roslyn") reemplaza [el análisis heredado](../code-quality/code-analysis-for-managed-code-overview.md) para el código administrado. En el caso de las plantillas de proyecto más recientes, como .NET Core .NET Standard proyectos, el análisis heredado no está disponible.

Muchas de las reglas de análisis heredado (FxCop) ya se han reescrito para los analizadores de .NET, un conjunto de analizadores de código Roslyn. Los analizadores de Roslyn ejecutan análisis basados en código fuente durante la ejecución del compilador. Se notifican los resultados del analizador junto con los del compilador.

Para obtener más información sobre las diferencias entre el análisis heredado y el análisis de origen, vea lo siguiente:

- [Análisis de código fuente frente a análisis heredado](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [Preguntas más frecuentes sobre los analizadores de .NET](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Migración

Para migrar al análisis de origen, [habilite o instale los analizadores de .NET](install-net-analyzers.md). Al igual que las infracciones de las reglas de análisis heredados, las infracciones de análisis de código fuente se muestran en la ventana Lista de errores de Visual Studio. Además, las infracciones de análisis de código fuente también se muestran en el editor de código como *subrayados ondulados* bajo el código infractor. El color del subrayado ondulado depende del [valor de gravedad](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la regla. Para ver el estado de las reglas migradas a los nuevos analizadores de .NET, vea [Reglas porteadas y noportadas.](../code-quality/fxcop-rule-port-status.md)

> [!NOTE]
> Antes de Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se suministran como paquete `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se incluyen con el [SDK de .NET.](/dotnet/fundamentals/code-analysis/overview) También están disponibles como paquete `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Para más información, consulte [Migración de analizadores de FxCop a analizadores de .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="configuration"></a>Configuración

Para más información sobre cómo configurar los analizadores de .NET:

- Para configurar analizadores de .NET, consulte [Configuración de analizadores de .NET.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

- Para obtener información sobre cómo configurar analizadores mediante reglas predefinidas con EditorConfig o un archivo de conjunto de reglas, vea [Habilitar una categoría de reglas.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

## <a name="see-also"></a>Consulte también

- [Migración de los analizadores de FxCop a los de .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
