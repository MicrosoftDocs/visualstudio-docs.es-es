---
title: "Configuración de Visual Studio for Mac Tools for Unity"
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.topic: article
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: c2290b1165b8d2688b280684e1251b929d002594
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Configuración de Visual Studio for Mac Tools for Unity

En esta sección se explica cómo empezar a usar Visual Studio for Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Instalación de Visual Studio para Mac

Descargue e instale Visual Studio para Mac. Todas las ediciones de Visual Studio para Mac admiten Visual Studio for Mac Tools for Unity, incluida la edición gratuita Community:

* Descargue Visual Studio para Mac desde [visualstudio.com](https://www.visualstudio.com/).
* Visual Studio for Mac Tools for Unity se instala automáticamente durante el proceso de instalación.
* Siga los pasos de la [guía de instalación](/visualstudio/mac/installation) para obtener más ayuda para la instalación.

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Confirme que la extensión Visual Studio for Mac Tools for Unity está habilitada.

Aunque la extensión Visual Studio for Mac Tools for Unity debería estar habilitada de forma predeterminada, puede confirmarlo y comprobar el número de versión instalada:

1.  En el menú de Visual Studio, seleccione **Extensiones...**

  ![Selección de Extensiones](media/setup-vsmac-tools-unity-image1.png)

2.  Expanda la sección Desarrollo de juegos y confirme la entrada Visual Studio for Mac Tools for Unity.

  ![Visualización de entrada de Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Instalación de Unity

Visual Studio for Mac Tools for Unity necesita la versión 5.6.1 o superior de Unity. Todos los planes de Unity funcionan con Visual Studio Tools para Unity, incluido el plan gratuito Personal. Descargue Unity desde [store.unity.com](https://store.unity.com/).

> [!NOTE]
> Para comprobar que Visual Studio Tools para Unity está habilitado en la versión de Unity, seleccione **Acerca de Unity** en el menú de Unity y busque el texto "Microsoft Visual Studio Tools para Unity habilitado" en la parte inferior izquierda del cuadro de diálogo.
>
>   ![Acerca de Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configuración de Unity para su uso con Visual Studio para Mac

Visual Studio se debe establecer como editor de script externo en Unity:

1.  Seleccione **Preferencias...** en el menú de Unity.

  ![Selección de Preferencias](media/setup-vsmac-tools-unity-image4.png)

2.  En el cuadro de diálogo Preferencias, seleccione la pestaña **Herramientas externas**.

3.  En la lista desplegable Editor de script externo, elija **Visual Studio** si aparece; si no, seleccione **Examinar...**

  ![Selección de Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  Si se ha seleccionado **Examinar...**, vaya al directorio Aplicaciones, seleccione Visual Studio y luego haga clic en **Abrir**.

  ![Selección de Abrir](media/setup-vsmac-tools-unity-image6.png)

5.  Una vez que Visual Studio está seleccionado en la lista **Editor de script externo**, cierre el cuadro de diálogo Preferencias para terminar el proceso de configuración.

