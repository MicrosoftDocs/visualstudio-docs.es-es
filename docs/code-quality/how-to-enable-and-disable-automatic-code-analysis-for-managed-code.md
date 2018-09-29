---
title: 'Cómo: Habilitar y deshabilitar el análisis de código automático para código administrado'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443550"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de código automático para código administrado

Puede configurar análisis de código para ejecutar después de cada compilación de un proyecto de código administrado. Puede establecer propiedades de análisis para cada configuración de compilación de código diferente, por ejemplo, debug y release.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar o deshabilitar el análisis de código automático

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, elija **propiedades**.

1. En el cuadro de diálogo Propiedades del proyecto, elija el **análisis de código** ficha.

1. Especifique el tipo de compilación en **configuración** y la plataforma de destino en **plataforma**.

1. Para habilitar o deshabilitar el análisis de código automático, active o desactive el **Habilitar análisis de código al compilar** casilla de verificación.

> [!NOTE]
> El **Habilitar análisis de código al compilar** casilla de verificación sólo afecta a los análisis de código estático. No se ve afectada [analizadores de código Roslyn](roslyn-analyzers-overview.md), que siempre se ejecutan en la compilación si se instaló como un paquete de NuGet. Si desea borrar errores del analizador desde la **lista de errores**, puede suprimir todas las infracciones actuales eligiendo **analizar** > **ejecutar análisis de código y suprimir activo Problemas** en la barra de menús. Para obtener más información, consulte [suprimir infracciones](use-roslyn-analyzers.md#suppress-violations).
