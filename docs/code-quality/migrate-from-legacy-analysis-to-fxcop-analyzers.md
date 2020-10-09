---
title: Migrar de FxCop a análisis de código fuente (analizadores de FxCop)
ms.custom: SEO-VS-2020
description: Aprenda a analizar el código por primera vez o a migrar desde el análisis binario (FxCop) a la nueva forma de analizar el código administrado mediante el análisis de origen (analizadores de FxCop).
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
ms.openlocfilehash: cb75b7374e7f88f4643a5ecc4a9c193d8144efc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860476"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migración de análisis heredado (FxCop) al análisis de código fuente (analizadores de FxCop)

El análisis de código fuente por .NET Compiler Platform ("Roslyn") reemplaza el [análisis heredado](../code-quality/code-analysis-for-managed-code-overview.md) de código administrado. En el caso de las plantillas de proyecto más recientes, como .NET Core y proyectos de .NET Standard, el análisis heredado no está disponible.

Muchas de las reglas de análisis heredado (FxCop) ya se han reescrito para los analizadores de FxCop, un conjunto de analizadores de código Roslyn. Los [analizadores de FxCop se instalan como un paquete NuGet](install-fxcop-analyzers.md#nuget-package) al que hace referencia el proyecto o la solución. Los analizadores de FxCop ejecutan análisis basados en código fuente durante la ejecución del compilador. Se notifican los resultados del analizador junto con los del compilador.

Para obtener más información sobre las diferencias entre el análisis heredado y el análisis de código fuente, vea lo siguiente:

- [Análisis de código fuente frente a análisis heredado](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [Preguntas más frecuentes sobre los analizadores de FxCop](../code-quality/fxcop-analyzers-faq.md)

Para migrar al análisis de código fuente, [Instale los analizadores de FxCop](../code-quality/install-fxcop-analyzers.md). Al igual que las infracciones de las reglas de análisis heredados, las infracciones de análisis de código fuente se muestran en la ventana Lista de errores de Visual Studio. Además, las infracciones de análisis de código fuente también se muestran en el editor de código como *subrayados ondulados* bajo el código infractor. El color del subrayado ondulado depende del [valor de gravedad](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la regla. Para ver el estado de las reglas que se han trasladado a los nuevos Analizadores de FxCop, consulte [reglas de puerto y no trasladadas](../code-quality/fxcop-rule-port-status.md).

Para obtener más información sobre cómo configurar los analizadores de FxCop:

- Para configurar los analizadores de FxCop, vea [configurar analizadores de FxCop](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Para obtener información acerca de cómo configurar analizadores mediante reglas predefinidas con EditorConfig o un archivo de conjunto de reglas, consulte [habilitación de una categoría de reglas](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
