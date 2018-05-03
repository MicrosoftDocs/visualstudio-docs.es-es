---
title: Mejorar el tiempo de inicio de Visual Studio | Microsoft Docs
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ab8098e52f0045c913495dce81d5005772eac836
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="optimize-visual-studio-startup-time"></a>Optimizar el tiempo de inicio de Visual Studio

Visual Studio está diseñado para iniciarse de la forma más rápida y eficaz posible. Sin embargo, ciertas extensiones y ventanas de herramientas de Visual Studio pueden afectar negativamente al tiempo de inicio cuando se cargan. Puede controlar el comportamiento de las extensiones y las ventanas de herramientas lentas desde el cuadro de diálogo **Administrar el rendimiento de Visual Studio**. Para más sugerencias generales sobre cómo mejorar el rendimiento, consulte [Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Comportamiento de inicio

Para evitar que se alargue demasiado el tiempo de inicio, Visual Studio de 2017 carga las extensiones mediante un enfoque _a petición_. Con este comportamiento, las extensiones no se abren inmediatamente cuando Visual Studio se inicia, sino cuando son necesarias. Además, como las ventanas de herramientas que se han quedado abiertas en una sesión de Visual Studio anterior pueden ralentizar el tiempo de inicio, Visual Studio abre ventanas de herramientas de una manera más inteligente para evitar el impacto en el tiempo de inicio.

Si Visual Studio detecta un inicio lento, aparece un mensaje emergente avisándole de la extensión o la ventana de herramientas que está provocando la ralentización. El mensaje ofrece un vínculo al cuadro de diálogo **Administrar el rendimiento de Visual Studio**. También puede acceder a este cuadro de diálogo si elige **Ayuda** > **Administrar el rendimiento de Visual Studio** en la barra de menús.

![Administrar el rendimiento Visual Studio: mensaje emergente en el que se lee "Se ha detectado que la extensión... está ralentizando Visual Studio"](../ide/media/vside_perfdialog_popup.png)

En el cuadro de diálogo se enumeran las ventanas de herramientas y extensiones que afectan negativamente al rendimiento de inicio. Puede cambiar la configuración de la ventana de herramientas y de las extensiones para mejorar el rendimiento de inicio.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Cambiar la configuración de extensión para mejorar el inicio, la carga de solución y el rendimiento de la escritura

1. Abra el cuadro de diálogo **Administrar el rendimiento de Visual Studio**. Para ello, seleccione **Ayuda** > **Administrar el rendimiento de Visual Studio** en la barra de menús.

    Si una extensión está ralentizando el inicio de Visual Studio, la carga de la solución o la escritura, esta aparece en el cuadro de diálogo **Administrar el rendimiento de Visual Studio** en **Extensiones** > **Inicio** (o **Carga de solución** o **Escritura**).

    ![Administración del rendimiento de Visual Studio: vista de extensiones](../ide/media/vside_perfdialog_extensions.png)

2. Elija la extensión que quiera deshabilitar y después elija el botón **Deshabilitar**.

Siempre puede volver a habilitar la extensión en futuras sesiones con el cuadro de diálogo Administrador de extensiones o Administrar el rendimiento de Visual Studio.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Cambiar la configuración de la ventana de herramientas para mejorar el tiempo de inicio

1. Abra el cuadro de diálogo **Administrar el rendimiento de Visual Studio**. Para ello, seleccione **Ayuda** > **Administrar el rendimiento de Visual Studio** en la barra de menús.

    Si una ventana de herramientas ralentiza el inicio de Visual Studio, la ventana de herramientas aparece en el cuadro de diálogo **Administrar el rendimiento de Visual Studio** en **Ventanas de herramientas** > **Inicio**.

2. Elija la ventana de herramientas cuyo comportamiento quiera cambiar.

3. Elija una de las tres opciones siguientes:

    - **Usar el comportamiento predeterminado:** el comportamiento predeterminado de la ventana de herramientas. Si se mantiene esta opción activada, el rendimiento de inicio no mejorará.

    - **No mostrar la ventana al inicio:** la ventana de herramientas especificada está siempre cerrada al abrir Visual Studio, incluso si se ha quedado abierta en una sesión anterior. Cuando lo requiera, podrá abrir la ventana de herramientas desde el menú correspondiente.

    - **Ocultar ventana automáticamente al inicio:** si una ventana de herramientas se ha quedado abierta en una sesión anterior, esta opción contrae el grupo de ventanas de herramientas en el inicio para evitar la inicialización de la ventana de herramientas. Esta opción es una buena opción si utiliza una ventana de herramientas con frecuencia. La ventana de herramientas todavía está disponible, pero ya no afecta negativamente al tiempo de inicio de Visual Studio.

    ![Administración del rendimiento de Visual Studio: vista de ventanas de herramientas](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Algunas versiones anteriores de Visual Studio 2017 tenían una característica llamada **carga de solución ligera**. Esta característica ya no está disponible en la versión 15.5 de Visual Studio 2017 ni en versiones posteriores. En la versión 15.5 de Visual Studio 2017 y versiones posteriores, las soluciones de gran tamaño que contiene código administrado se cargan mucho más rápido que antes, incluso sin la carga de solución ligera.

## <a name="see-also"></a>Vea también

- [Optimización del rendimiento de Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Load solutions faster with Visual Studio 2017 version 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/) (Blog de Visual Studio: Cargar soluciones más rápido con Visual Studio 2017 versión 15.6)
