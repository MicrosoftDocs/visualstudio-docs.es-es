---
title: Migración de FxCop a análisis de código fuente (analizadores de .NET)
ms.custom: SEO-VS-2020
description: Aprenda a analizar el código por primera vez o a migrar desde el análisis binario (FxCop) a la nueva forma de analizar el código administrado mediante el análisis de código fuente (analizadores de .NET).
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
manager: jillfra
ms.openlocfilehash: 84acec58ed78884f0b037950fa25ce40f6adcbfc
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112187"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migrar de análisis heredado (FxCop) al análisis de código fuente (analizadores de .NET)

El análisis de código fuente por .NET Compiler Platform ("Roslyn") reemplaza el [análisis heredado](../code-quality/code-analysis-for-managed-code-overview.md) de código administrado. En el caso de las plantillas de proyecto más recientes, como .NET Core y proyectos de .NET Standard, el análisis heredado no está disponible.

Muchas de las reglas de análisis heredado (FxCop) ya se han reescrito para los analizadores de .NET, un conjunto de analizadores de código Roslyn. Los analizadores de Roslyn ejecutan el análisis basado en código fuente durante la ejecución del compilador. Se notifican los resultados del analizador junto con los del compilador.

Para obtener más información sobre las diferencias entre el análisis heredado y el análisis de código fuente, vea lo siguiente:

- [Análisis de código fuente frente a análisis heredado](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

- [Preguntas más frecuentes sobre los analizadores de .NET](../code-quality/net-analyzers-faq.md)

## <a name="migration"></a>Migración

Para migrar al análisis de código fuente, [habilite o instale los analizadores de .net](install-net-analyzers.md). Al igual que las infracciones de las reglas de análisis heredados, las infracciones de análisis de código fuente se muestran en la ventana Lista de errores de Visual Studio. Además, las infracciones de análisis de código fuente también se muestran en el editor de código como *subrayados ondulados* bajo el código infractor. El color del subrayado ondulado depende del [valor de gravedad](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la regla. Para ver el estado de las reglas que se han trasladado a los nuevos Analizadores de .NET, consulte [reglas de puerto y no trasladadas](../code-quality/fxcop-rule-port-status.md).

> [!NOTE]
> Antes de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se distribuyen como `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). También están disponibles como `Microsoft.CodeAnalysis.NetAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Para obtener más información, vea [migrar de analizadores de FxCop a analizadores de .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Configuración

Para obtener más información sobre cómo configurar los analizadores de .NET:

- Para configurar los analizadores de .NET, vea [configurar analizadores de .net](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Para obtener información acerca de cómo configurar analizadores mediante reglas predefinidas con EditorConfig o un archivo de conjunto de reglas, consulte [habilitación de una categoría de reglas](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Consulta también

- [Migración de analizadores de FxCop a analizadores de .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
