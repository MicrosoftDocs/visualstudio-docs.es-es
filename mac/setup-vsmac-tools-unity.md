---
title: Configuración de Visual Studio for Mac Tools for Unity
description: Configurar e instalar herramientas de Unity para su uso en Visual Studio para Mac
author: therealjohn
ms.author: johmil
ms.date: 04/02/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: b9e033b765df4ae4396c011fe37939b4fc63e372
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809271"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Configurar Visual Studio para Mac Tools para Unity

En esta sección se explica cómo empezar a usar Visual Studio for Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Instalación de Visual Studio para Mac

### <a name="unity-bundled-installation"></a>Instalación agrupada de Unity

A partir de Unity 2018.1, Visual Studio para Mac es el entorno de desarrollo integrado (IDE) de C# predeterminado para Unity y se incluye en el Asistente para la descarga de Unity y en la herramienta de instalación de Unity Hub. Descargue Unity desde [store.unity.com](https://store.unity.com/).

Durante la instalación, asegúrese de que Visual Studio para Mac está activado en la lista de componentes que quiere instalar con Unity:

#### <a name="unity-hub"></a>Unity Hub

![Instalación de Unity Hub](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Asistente para la descarga de Unity

![Instalación del Asistente para la descarga de Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Buscar actualizaciones de Visual Studio para Mac

Es posible que la versión de Visual Studio para Mac incluida con la instalación de Unity no sea la más reciente. Se recomienda buscar actualizaciones para asegurarse de tener acceso a las herramientas y características más recientes.

* [Actualización de Visual Studio para Mac](update.md)

### <a name="manual-installation"></a>Instalación manual

Si ya tiene Unity 5.6.1 o una versión posterior, pero no tiene Visual Studio para Mac, puede instalar Visual Studio para Mac manualmente. Todas las ediciones de Visual Studio para Mac incluyen Visual Studio for Mac Tools for Unity, incluida la edición gratuita Community:

* Descargue Visual Studio para Mac desde [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio for Mac Tools for Unity se instala automáticamente durante el proceso de instalación.
* Siga los pasos de la [guía de instalación](/visualstudio/mac/installation) para obtener más ayuda para la instalación.

> [!NOTE]
> Visual Studio for Mac Tools for Unity necesita la versión 5.6.1 o superior de Unity. Para comprobar que Visual Studio Tools para Unity está habilitado en la versión de Unity, seleccione **Acerca de Unity** en el menú de Unity y busque el texto "Microsoft Visual Studio Tools para Unity habilitado" en la parte inferior izquierda del cuadro de diálogo.
>
> ![Acerca de Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Confirme que la extensión Visual Studio for Mac Tools for Unity está habilitada.

Aunque la extensión Visual Studio for Mac Tools for Unity debería estar habilitada de forma predeterminada, puede confirmarlo y comprobar el número de versión instalada:

1. En el menú de Visual Studio, seleccione **Extensiones...**

   ![Selección de Extensiones](media/setup-vsmac-tools-unity-image1.png)

2. Expanda la sección Desarrollo de juegos y confirme la entrada Visual Studio for Mac Tools for Unity.

   ![Visualización de entrada de Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configuración de Unity para su uso con Visual Studio para Mac

A partir de Unity 2018.1, Visual Studio debe ser el editor de scripts externos predeterminado en Unity. Puede confirmarlo o cambiar el editor de scripts externos a Visual Studio:

1. Seleccione **Preferencias...** en el menú de Unity.

   ![Selección de Preferencias](media/setup-vsmac-tools-unity-image4.png)

2. En el cuadro de diálogo Preferencias, seleccione la pestaña **Herramientas externas**.

3. En la lista desplegable Editor de script externo, elija **Visual Studio** si aparece; si no, seleccione **Examinar...**

   ![Selección de Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Si se ha seleccionado **Examinar...**, vaya al directorio Aplicaciones, seleccione Visual Studio y luego haga clic en **Abrir**.

   ![Selección de Abrir](media/setup-vsmac-tools-unity-image6.png)

5. Una vez que Visual Studio está seleccionado en la lista **Editor de script externo**, cierre el cuadro de diálogo Preferencias para terminar el proceso de configuración.