---
title: Deshabilitar análisis de código heredado
ms.date: 10/04/2019
description: Obtenga información sobre cómo activar y desactivar el análisis de código binario en Visual Studio. Vea cómo configurar esta característica en proyectos de código administrado.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c10aa602c2c9af3c51812073d62d5bd9bff06664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860079"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de código binario para código administrado

Puede configurar el análisis de código heredado (análisis binario) para que se ejecute después de cada compilación de un proyecto de código administrado. También puede tener valores diferentes para cada configuración de compilación, por ejemplo, Debug y Release.

> [!NOTE]
> El análisis heredado no está disponible para los tipos de proyecto más recientes, como .NET Core y aplicaciones .NET Standard. Estos proyectos usan [analizadores de código basados en .net Compiler Platform](roslyn-analyzers-overview.md) para analizar el código, tanto en directo como en tiempo de compilación. Para obtener información sobre cómo deshabilitar el análisis de código fuente en estos proyectos, vea [cómo deshabilitar el análisis de código fuente](disable-code-analysis.md).

Para habilitar o deshabilitar el análisis de código heredado:

1. En **Explorador de soluciones**, seleccione y mantenga presionado (o haga clic con el botón derecho) en el proyecto y, a continuación, seleccione **propiedades**.

2. En el cuadro de diálogo Propiedades del proyecto, vaya a la pestaña **análisis de código** .

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
