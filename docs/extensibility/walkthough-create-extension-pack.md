---
title: Crear un paquete de extensión con la plantilla de elemento del módulo de extensión | Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: gregvanl
ms.author: gregvanl
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 7899a096bb2a56e93ea55a4ba0a17cde272bd615
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58193710"
---
# <a name="walkthrough-create-an-extension-pack"></a>Tutorial: Crear un paquete de extensión

Un paquete de extensión es un conjunto de extensiones que se pueden instalar juntos. Módulos de extensión permiten compartir sus extensiones favoritas con otros usuarios fácilmente o agrupar un conjunto de extensiones juntos para un escenario determinado.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, Visual Studio SDK se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

La característica de extensión Pack está disponible a partir de Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Crear una extensión con una plantilla de elementos de paquete de extensiones

La plantilla de elemento del módulo de extensión crea un paquete de extensión con el conjunto de extensiones que se pueden instalar juntos.

1. En el **nuevo proyecto** cuadro de diálogo, busque "vsix" y seleccione **proyecto VSIX**. Para **nombre del proyecto**, escriba "Paquete de extensión de prueba". Seleccione **Crear**.

2. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **paquete de extensión**. Deje el nombre de archivo predeterminado (ExtensionPack1.cs).

3. Se agrega ExtensionPack1.vsext archivo que contiene el código siguiente

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. El elemento vsixid de la extensión debe incluir en el paquete de extensiones puede encontrarse en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Busque la extensión que desea incluir y haga clic en **identificador de copia**. Puede actualizar la existente **vsixId** en los pasos anteriores de archivos o agregar otra extensión a la lista.

    ![Copiar elemento VsixId de Marketplace](media/vsixid-marketplace.png)

5. Compile el proyecto y cargar la extensión en Marketplace. Consulte [publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un paquete de extensión solo puede instalar las extensiones que están disponibles en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o [Galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instalar el paquete de extensiones de Visual Studio Marketplace

Ahora que se ha publicado la extensión, instalarlo en Visual Studio y pruébela.

::: moniker range="vs-2017"

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el **extensiones** menú, haga clic en **extensiones administradas**.

::: moniker-end

2. Haga clic en **Online** y, a continuación, busque "Paquete de extensión de prueba".

3. Haga clic en **Descargar**. La extensión y su lista de extensiones incluidas en el paquete de extensiones, a continuación, se programará para su instalación.

4. A continuación es una vista de descarga del paquete de extensiones de ejemplo de la **administrar extensiones** cuadro de diálogo. Si prefiere instalar sólo algunas de las extensiones que se incluye en el módulo de extensión, puede modificar la lista de extensiones en **programado para instalar**.

    ![Descargue el paquete de extensiones de Marketplace](media/vside-extensionpack.png)

5. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Quitar la extensión

Para quitar la extensión de su equipo:

::: moniker range="vs-2017"

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el **extensiones** menú, haga clic en **extensiones administradas**.

::: moniker-end

2. Seleccione **paquete de extensión de pruebas** y, a continuación, haga clic en **desinstalar**. A continuación, se programará para desinstalar la extensión y su lista de extensiones incluidas en el paquete de extensiones.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
