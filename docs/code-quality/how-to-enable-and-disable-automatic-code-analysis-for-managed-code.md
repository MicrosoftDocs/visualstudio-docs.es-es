---
title: Deshabilitar análisis de código heredado
ms.date: 10/04/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 656b36e6d0a90bb44eaa5745312f1a57e1ea3474
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448939"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de código binario para código administrado

Puede configurar el análisis de código heredado (análisis binario) para que se ejecute después de cada compilación de un proyecto de código administrado. También puede tener valores diferentes para cada configuración de compilación, por ejemplo, Debug y Release.

> [!NOTE]
> El análisis heredado no está disponible para los tipos de proyecto más recientes, como .NET Core y aplicaciones .NET Standard. Estos proyectos usan [analizadores de código basados en .net Compiler Platform](roslyn-analyzers-overview.md) para analizar el código, tanto en directo como en tiempo de compilación. Para obtener información sobre cómo deshabilitar el análisis de código fuente en estos proyectos, vea [cómo deshabilitar el análisis de código fuente](disable-code-analysis.md).

Para habilitar o deshabilitar el análisis de código heredado:

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y elija **propiedades**.

2. En el cuadro de diálogo Propiedades del proyecto, elija la pestaña **análisis de código** .

3. Especifique el tipo de compilación en la **configuración** y la plataforma de destino en **plataforma**. (Solo para proyectos de Non-.NET Core/.net Standard).

::: moniker range="vs-2017"

4. Para habilitar o deshabilitar el análisis de código automático, Active o desactive la casilla **Habilitar análisis de código al compilar** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Para habilitar o deshabilitar el análisis de código automático, Active o desactive la casilla **ejecutar al compilar** en la sección **analizadores binarios** .

   ![Ejecutar análisis de código binario al compilar en Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Deshabilitar el análisis de código binario al compilar no afecta a los [analizadores de código basados en .net Compiler Platform](roslyn-analyzers-overview.md), que siempre se ejecutan en la compilación si se instalan como un paquete NuGet. Para obtener información sobre cómo deshabilitar el análisis de estos analizadores, vea [cómo deshabilitar el análisis de código fuente](disable-code-analysis.md).
