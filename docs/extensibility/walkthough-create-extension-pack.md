---
title: Crear un paquete de extensión
description: Aprenda a crear un paquete de extensiones con la plantilla de elemento Paquete de extensiones.
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 213e3e71503ebea8074594bbc88a06980e3e64b4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905142"
---
# <a name="walkthrough-create-an-extension-pack"></a>Tutorial: Creación de un paquete de extensión

Un paquete de extensiones es un conjunto de extensiones que se pueden instalar de forma conjunta. Los paquetes de extensiones le permiten compartir fácilmente las extensiones favoritas con otros usuarios o agrupar un conjunto de extensiones para un escenario determinado.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, el SDK de Visual Studio se incluye como una característica opcional en la instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [Instalación del SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

La característica Paquete de extensiones está disponible a partir de Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Creación de una extensión con una plantilla de elemento Paquete de extensiones

La plantilla de elemento Paquete de extensiones crea un paquete de extensiones con un conjunto de extensiones que se pueden instalar de forma conjunta.

1. En el cuadro de diálogo **Nuevo proyecto**, busque "vsix" y seleccione **Proyecto VSIX**. En **Nombre del proyecto**, escriba "Paquete de extensiones de prueba". Seleccione **Crear**.

2. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y seleccione **Agregar** > **Nuevo elemento**. Vaya al nodo **Extensibilidad** de Visual C# y seleccione **Paquete de extensión**. Deje el nombre de archivo predeterminado (ExtensionPack1.cs).

3. Se agrega el archivo ExtensionPack1.vsext que contiene el código siguiente

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

4. El elemento vsixid de la extensión que se va a incluir en el paquete de extensiones se puede encontrar en [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Busque la extensión que quiera incluir y haga clic en **Copiar id.** . Puede actualizar el valor **vsixId** existente en el archivo anterior o agregar otra extensión a la lista.

    ![Copia de VsixId desde Marketplace](media/vsixid-marketplace.png)

5. Compile el proyecto y cargue la extensión en Marketplace. Vea [Publicación de una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un paquete de extensiones solo puede instalar las extensiones que están disponibles en [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o la [galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instalación del paquete de extensión desde Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébela.

::: moniker range="vs-2017"

1. En Visual Studio, en el menú **Herramientas**, haga clic en **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el menú **Extensiones**, haga clic en **Extensiones administradas**.

::: moniker-end

2. Haga clic en **En línea** y busque "Paquete de extensiones de prueba".

3. Haga clic en **Descargar**. La extensión y su lista de extensiones incluidas en el paquete de extensión se programarán para su instalación.

4. A continuación se muestra una vista de descarga del paquete de extensiones de ejemplo del cuadro de diálogo **Administrar extensiones**. Si prefiere instalar solo algunas de las extensiones incluidas en el paquete de extensión, puede modificar la lista de extensiones en **Programado para instalación**.

    ![Descarga del paquete de extensión desde Marketplace](media/vside-extensionpack.png)

5. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Para quitar la extensión del equipo:

::: moniker range="vs-2017"

1. En Visual Studio, en el menú **Herramientas**, haga clic en **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el menú **Extensiones**, haga clic en **Extensiones administradas**.

::: moniker-end

2. Seleccione **Probar paquete de extensión** y, después, haga clic en **Desinstalar**. La extensión y su lista de extensiones incluidas en el paquete de extensión se programarán para su desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
