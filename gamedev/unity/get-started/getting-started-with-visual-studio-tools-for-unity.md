---
title: Introducción a Visual Studio Tools para Unity | Microsoft Docs
description: Obtenga información sobre cómo instalar y configurar Visual Studio desarrollo de Unity.
ms.custom: ''
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 791f25b61c86f0115c225d505bdb1edb07869961
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782613"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Introducción a Visual Studio y Unity

> [!NOTE]
> En esta guía se da por supuesto que ya ha instalado Unity mediante el programa Unity Hub. Si no está nunca en Unity, se recomienda visitar Unity Learn y completar primero la ruta [de aprendizaje de Unity Essentials.](https://learn.unity.com/pathway/unity-essentials)

## <a name="install-unity-support-for-visual-studio"></a>Instalación de la compatibilidad de Unity con Visual Studio

Visual Studio Tools para Unity es una extensión gratuita que proporciona compatibilidad para escribir y depurar C# y mucho más. Visite la [introducción a Herramientas para Unity](./visual-studio-tools-for-unity.md) para obtener una lista completa de lo que incluyen las extensiones.

:::zone pivot="windows"

> [!NOTE]
> Esta guía de instalación es para Visual Studio. Si usa Visual Studio Code, visite la documentación de [desarrollo de Unity con VS Code .](https://code.visualstudio.com/docs/other/unity)

1. [Descargue el Visual Studio o](/visualstudio/install/install-visual-studio.md)ejecute si ya está instalado.
2. Haga clic en **Modificar** (si ya está instalado) o en **Instalar** (si es una nueva instalación) para la versión de Visual Studio que prefiera.
3. En la **pestaña Cargas de trabajo,** desplácese hasta la **sección Juegos** y seleccione la carga de trabajo Desarrollo de juegos **con Unity.**

    ![Cuadro de carga de trabajo Desarrollo de juegos con Unity en el instalador](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Esta guía de instalación es para Visual Studio para Mac. Si usa Visual Studio Code, visite la documentación de [desarrollo de Unity con VS Code .](https://code.visualstudio.com/docs/other/unity)

Las herramientas para Unity se incluyen con la instalación de Visual Studio para Mac y no se requieren pasos de instalación independientes. Puede comprobarlo en el menú **Visual Studio para Mac > Extensiones > game development (Desarrollo de juegos).** **Visual Studio para Mac Tools for Unity** debe estar habilitado.

![Vista del Administrador de extensiones Visual Studio para Mac Herramientas para Unity habilitada](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Buscar actualizaciones

Se recomienda mantener actualizados Visual Studio y Visual Studio para Mac para que tenga las correcciones de errores, las características y la compatibilidad con Unity más recientes. Esto no requiere una actualización de las versiones de Unity.

:::zone pivot="windows"

1. Haga clic **en el menú > Buscar** actualizaciones.

    ![El menú Buscar actualizaciones de Visual Studio 2019](../media/vs/check-for-updates.png)

2. Si hay una actualización disponible, el Instalador de Visual Studio mostrará una nueva versión. Haga clic en el botón **Actualizar**.

:::zone-end
:::zone pivot="macos"

1. Haga clic **en Visual Studio para Mac > buscar actualizaciones...** para abrir el **cuadro de diálogo Visual Studio actualizar.**
2. Si hay una actualización disponible, haga clic en **el botón** Instalar.

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Configuración de Unity para usar Visual Studio

De forma predeterminada, Unity ya debe estar configurado para usar Visual Studio o Visual Studio para Mac como editor de scripts. Puede confirmarlo o cambiar el editor de scripts externos a una versión específica de Visual Studio desde el Editor de Unity.

:::zone pivot="windows"

1. En el Editor de Unity, seleccione el **menú Editar > preferencias.**
2. Seleccione la **pestaña Herramientas** externas de la izquierda.
3. La **lista desplegable Editor de scripts** externos proporciona una manera de elegir diferentes instalaciones de Visual Studio. También puede hacer clic en **Examinar...** en la lista desplegable para agregar una versión no enumerada.

    ![Menú de preferencias herramientas externas en el Editor de Unity en Windows](../media/vs/preferences-external-tools.png)

4. Si **Examinar...** estaba seleccionado, vaya al directorio **Common7/IDE** dentro del directorio de instalación de Visual Studio y seleccione **devenv.exe**. A continuación, haga clic **en Abrir**.
5. Después de que Visual Studio se ha seleccionado en la lista **External Script Editor** (Editor de scripts externo), confirme que la casilla **Editor Attaching** (Asociación de editor) está activada.
6. Cierre el cuadro de diálogo **Preferencias** para completar el proceso de configuración.

:::zone-end
:::zone pivot="macos"

1. En el Editor de Unity, seleccione el menú **> preferencias de Unity.**
2. Seleccione la **pestaña Herramientas** externas de la izquierda.
3. La **lista desplegable Editor de scripts** externos proporciona una manera de elegir diferentes instalaciones de Visual Studio. También puede hacer clic en **Examinar...** en la lista desplegable para agregar una versión no enumerada.

    ![El menú de preferencias Herramientas externas del Editor de Unity en macOS](../media/vsm/preferences-external-tools.png)

4. Cierre el cuadro de diálogo **Preferencias** para completar el proceso de configuración.

:::zone-end

## <a name="next-steps"></a>Pasos siguientes

 Para obtener información sobre cómo trabajar con y depurar el proyecto de Unity en Visual Studio, visite [Uso de Visual Studio Tools para Unity](using-visual-studio-tools-for-unity.md).
