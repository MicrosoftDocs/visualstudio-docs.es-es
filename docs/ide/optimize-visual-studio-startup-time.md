---
title: Optimizar el tiempo de inicio de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 8/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Optimizar el tiempo de inicio de Visual Studio
Lo ideal es que Visual Studio se inicie siempre lo antes posible. En cambio, las ventanas de herramientas abiertas y las extensiones de Visual Studio pueden afectar negativamente al tiempo de inicio porque se cargan automáticamente al arrancar. En la ventana **Administrar el rendimiento de Visual Studio** puede ver qué extensiones y características afectan al tiempo de inicio de Visual Studio y controlar el comportamiento de carga de dichas extensiones y características.

Para obtener más sugerencias generales sobre cómo mejorar el rendimiento, vea [Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="control-startup-behavior"></a>Controlar el comportamiento de inicio

Para evitar extender demasiado el tiempo de inicio, Visual Studio 2017 impide la carga de extensiones durante el inicio mediante un enfoque de carga a petición. Con este comportamiento, las extensiones no se abren inmediatamente después de que Visual Studio se inicia, sino solo cuando resulta necesario después del inicio. Además, como las ventanas de herramientas que se han quedado abiertas en una sesión de Visual Studio anterior pueden ralentizar el tiempo de inicio, Visual Studio abre ventanas de herramientas de una manera más inteligente para evitar el impacto en el tiempo de inicio.

Si Visual Studio detecta un inicio lento, aparece un mensaje emergente avisándole de la extensión o la ventana de herramientas que está provocando la ralentización. El mensaje también proporciona un vínculo al cuadro de diálogo **Administrar el rendimiento de Visual Studio**. También puede abrir esta ventana utilizando el comando de menú **Ayuda > Administrar el rendimiento de Visual Studio**.

![Administrar el rendimiento Visual Studio: mensaje emergente en el que se lee "Se ha detectado que la extensión... está ralentizando Visual Studio"](../ide/media/vside_perfdialog_popup.png)

En el cuadro de diálogo se enumeran las ventanas de herramientas y extensiones que afectan negativamente al rendimiento de inicio. Este cuadro de diálogo le permite cambiar la configuración de la ventana de herramientas y de las extensiones para mejorar el rendimiento de inicio.

### <a name="change-extension-settings"></a>Cambio de la configuración de las extensiones

Si una extensión está ralentizando el inicio de Visual Studio, esta aparece en el cuadro de diálogo **Administrar el rendimiento de Visual Studio** cuando selecciona uno de los tipos de extensión. En el cuadro de diálogo se muestra qué extensión afecta al rendimiento de inicio, cuándo se carga una solución y cuándo se escribe en el editor.

![Administrar el rendimiento Visual Studio: vista de extensiones](../ide/media/vside_perfdialog_extensions.png)

Si el impacto en el tiempo de inicio, de carga de soluciones o de escritura en el editor resulta excesivamente alto, deshabilite la extensión para dicho escenario; para ello, seleccione **Deshabilitar**. Siempre puede volver a habilitar la extensión en futuras sesiones con el cuadro de diálogo Administrador de extensiones o Administrar el rendimiento de Visual Studio.

### <a name="change-tool-window-settings"></a>Cambio de la configuración de la ventana de herramientas

Si una ventana de herramientas está ralentizando el inicio de Visual Studio y desea modificar el impacto, puede invalidar su comportamiento; para ello, seleccione una de estas dos opciones en lugar de **Usar comportamiento predeterminado**:

- **No mostrar ventana al inicio:** la ventana de herramientas especificada siempre estará cerrada la próxima vez que abra Visual Studio, incluso si se ha quedado abierta en una sesión anterior. Puede abrir la ventana de herramientas desde el menú correspondiente.
- **Ocultar ventana automáticamente al inicio:** si una ventana de herramientas se ha quedado abierta en una sesión anterior, esta opción contrae el grupo de ventanas de herramientas en el inicio para evitar la inicialización de la ventana de herramientas. Se trata de una buena opción si usa una ventana de herramientas frecuentemente, porque esta todavía está disponible, pero ya no afecta negativamente al tiempo de inicio de Visual Studio.

![Administrar el rendimiento Visual Studio: vista de ventanas de herramientas](../ide/media/vside_perfdialog_toolwindows.png)

Siempre puede volver a este cuadro de diálogo en cualquier momento para cambiar la configuración de una ventana de herramientas concreta.

## <a name="speed_up_solution_load"></a>Carga de soluciones grandes más rápido en Visual Studio de 2017

Visual Studio 2017 presenta una nueva característica denominada Carga de solución ligera que reduce la cantidad de tiempo y memoria necesarias para cargar soluciones grandes en el IDE. Si tiene una solución grande que contiene muchos proyectos de C#, VB o C++, probablemente verá una ventaja de rendimiento sustancial si habilita la carga de solución ligera. Para información detallada sobre cómo se podría beneficiar utilizando esta característica, consulte [Optimize solution loading](../ide/optimize-solution-loading-in-visual-studio) (Optimización de la carga de la solución).

> [!NOTE]
> Este contenido se aplica a Visual Studio 2017 Update 3.

### <a name="enable-or-disable-lightweight-solution-load"></a>Habilitación o deshabilitación de la característica Carga de solución ligera

Puede hacer clic con el botón derecho en el nombre de la solución en el Explorador de soluciones y seleccionar **Habilitar la carga de solución ligera**. Después de seleccionar la opción, debe cerrar y volver a abrir la solución para activar la carga de la solución ligera.

![Explorador de soluciones](../ide/media/VSIDE_LSL_Solution_Setting.png)

Para definir la configuración global para la carga de solución ligera, consulte [Optimize solution loading](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings) (Optimización de la carga de la solución).

## <a name="see-also"></a>Vea también
[Sugerencias y trucos de rendimiento de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)

