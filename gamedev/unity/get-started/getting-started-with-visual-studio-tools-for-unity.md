---
title: Introducción a Visual Studio Tools para Unity | Microsoft Docs
description: Obtenga información sobre cómo instalar y configurar Visual Studio para el desarrollo de Unity.
ms.custom: ''
ms.date: 07/13/2020
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
ms.openlocfilehash: ba95e15be083e0bb1274e01a986f4139d9443240
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341390"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Introducción a Visual Studio y Unity

> [!NOTE]
> En esta guía se da por supuesto que ya tiene instalado Unity con el programa de Unity Hub. Si no está familiarizado con Unity, se recomienda visitar Unity Learn y completar primero el [tutorial Introducción con Unity](https://learn.unity.com/course/getting-started-with-unity) .

## <a name="install-unity-support-for-visual-studio"></a>Instalación de la compatibilidad de Unity con Visual Studio

Visual Studio Tools para Unity es una extensión gratuita que proporciona compatibilidad para escribir y depurar C# y mucho más. Visite la [Introducción a Tools para Unity](./visual-studio-tools-for-unity.md) para obtener una lista completa de lo que incluye las extensiones.

:::zone pivot="windows"

> [!NOTE]
> Esta guía de instalación es para Visual Studio. Si usa Visual Studio Code, visite la [documentación de desarrollo de Unity con vs Code](https://code.visualstudio.com/docs/other/unity).

1. [Descargue el instalador de Visual Studio](/docs/install/install-visual-studio.md)o ejecútelo si ya está instalado.
2. Haga clic en **Modificar** (si ya está instalado) o en **Instalar** (si es una nueva instalación) para la versión de Visual Studio que prefiera.
3. En la pestaña **cargas de trabajo** , desplácese hasta la sección **juegos** y seleccione la carga de trabajo **desarrollo de juegos con Unity** .

    ![Cuadro de carga de trabajo desarrollo de juegos con Unity en el instalador](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Esta guía de instalación es para Visual Studio para Mac. Si usa Visual Studio Code, visite la [documentación de desarrollo de Unity con vs Code](https://code.visualstudio.com/docs/other/unity).

Tools para Unity se incluye con la instalación de Visual Studio para Mac y no se requiere ningún paso de instalación independiente. Puede comprobarlo en el menú **extensiones de Visual Studio para Mac > > desarrollo de juegos** . **Las herramientas de Visual Studio para Mac para Unity** deben estar habilitadas.

![Vista del administrador de extensiones que muestra Visual Studio para Mac Tools para Unity habilitado](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Buscar actualizaciones

Se recomienda mantener Visual Studio y Visual Studio para Mac actualizados para que tenga las correcciones de errores, las características y la compatibilidad con Unity más recientes. Esto no requiere una actualización de las versiones de Unity.

:::zone pivot="windows"

1. Haga clic en el menú **ayuda > buscar actualizaciones** .

    ![El menú buscar actualizaciones en Visual Studio 2019](../media/vs/check-for-updates.png)

2. Si hay una actualización disponible, el Instalador de Visual Studio mostrará una nueva versión. Haga clic en el botón **Actualizar**.

:::zone-end
:::zone pivot="macos"

1. Haga clic en la **Visual Studio para Mac > menú buscar actualizaciones...** para abrir el cuadro de diálogo **actualización de Visual Studio** .
2. Si hay una actualización disponible, haga clic en el botón **instalar** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Configuración de Unity para usar Visual Studio

De forma predeterminada, Unity ya debe estar configurado para usar Visual Studio o Visual Studio para Mac como editor de scripts. Puede confirmarlo o cambiar el editor de scripts externo a una versión específica de Visual Studio desde el editor de Unity.

:::zone pivot="windows"

1. En el editor de Unity, seleccione el menú **Editar preferencias de >** .
2. Seleccione la pestaña **herramientas externas** a la izquierda.
3. La lista desplegable **Editor de script externo** proporciona una manera de elegir distintas instalaciones de Visual Studio. También puede hacer clic en **examinar...** en la lista desplegable para agregar una versión que no esté en la lista.

    ![Menú de preferencias de herramientas externas en el editor de Unity en Windows](../media/vs/preferences-external-tools.png)

4. Si **Examinar...** estaba seleccionado, vaya al directorio **Common7/IDE** dentro del directorio de instalación de Visual Studio y seleccione **devenv.exe**. A continuación, haga clic en **abrir**.
5. Después de que Visual Studio se ha seleccionado en la lista **External Script Editor** (Editor de scripts externo), confirme que la casilla **Editor Attaching** (Asociación de editor) está activada.
6. Cierre el cuadro de diálogo **Preferencias** para completar el proceso de configuración.

:::zone-end
:::zone pivot="macos"

1. En el editor de Unity, seleccione el menú de **preferencias de > Unity** .
2. Seleccione la pestaña **herramientas externas** a la izquierda.
3. La lista desplegable **Editor de script externo** proporciona una manera de elegir distintas instalaciones de Visual Studio. También puede hacer clic en **examinar...** en la lista desplegable para agregar una versión que no esté en la lista.

    ![Menú de preferencias de herramientas externas en el editor de Unity en macOS](../media/vsm/preferences-external-tools.png)

4. Cierre el cuadro de diálogo **Preferencias** para completar el proceso de configuración.

:::zone-end

## <a name="next-steps"></a>Pasos siguientes

 Para obtener información sobre cómo trabajar con el proyecto de Unity y depurarlo en Visual Studio, visite [uso de Visual Studio Tools para Unity](using-visual-studio-tools-for-unity.md).
