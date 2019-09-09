---
title: Habilitar o deshabilitar el análisis de código
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551036"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Procedimiento Habilitar y deshabilitar el análisis de código automático para código administrado

Puede configurar el análisis de código (estático) para que se ejecute después de cada compilación de un proyecto de código administrado. Puede establecer distintas propiedades de análisis de código para cada configuración de compilación, por ejemplo, Debug y Release.

Este artículo se aplica solo al análisis heredado y no al análisis de código activo mediante [analizadores de código](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar o deshabilitar el análisis de código automático

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y elija **propiedades**.

1. En el cuadro de diálogo Propiedades del proyecto, elija la pestaña **análisis de código** .

   > [!TIP]
   > Los tipos de proyecto más recientes como las aplicaciones .NET Core y .NET Standard no tienen una pestaña **análisis de código** . El análisis heredado no está disponible para estos tipos de proyecto, pero puede obtener análisis de código en directo mediante [analizadores de código basados en .net Compiler Platform](roslyn-analyzers-overview.md). Para suprimir las advertencias de los analizadores de código, consulte la nota al final de este artículo.

1. Especifique el tipo de compilación en la **configuración** y la plataforma de destino en **plataforma**.

1. Para habilitar o deshabilitar el análisis de código automático, Active o desactive la casilla **Habilitar análisis de código al compilar** .

> [!NOTE]
> La casilla **Habilitar análisis de código al compilar** solo afecta al análisis heredado. No afecta a los [analizadores de código basados en .net Compiler Platform](roslyn-analyzers-overview.md), que siempre se ejecutan en la compilación si se instalan como un paquete NuGet. Si desea borrar los errores del analizador del **lista de errores**, puede suprimir todas las infracciones actuales eligiendo **analizar** > **Ejecutar Análisis de código y suprimir problemas activos** en la barra de menús. Para obtener más información, vea [suprimir infracciones](use-roslyn-analyzers.md#suppress-violations).
