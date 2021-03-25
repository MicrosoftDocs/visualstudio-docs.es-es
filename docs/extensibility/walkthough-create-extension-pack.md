---
title: Crear un paquete de extensión
description: Obtenga información sobre cómo crear un paquete de extensión con la plantilla de elementos del paquete de extensión
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 57b447be3ee411b737c1aea5b0a4be5ef966c8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062153"
---
# <a name="walkthrough-create-an-extension-pack"></a>Tutorial: Creación de un paquete de extensión

Un paquete de extensión es un conjunto de extensiones que se pueden instalar juntas. Los paquetes de extensión permiten compartir fácilmente sus extensiones favoritas con otros usuarios o agrupar un conjunto de extensiones para un escenario determinado.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, el SDK de Visual Studio se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

La característica de paquete de extensiones está disponible a partir de Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Crear una extensión con una plantilla de elemento de paquete de extensión

La plantilla de elementos del paquete de extensión crea un paquete de extensión con un conjunto de extensiones que se pueden instalar juntos.

1. En el cuadro de diálogo **nuevo proyecto** , busque "VSIX" y seleccione **Proyecto VSIX**. En **nombre de proyecto**, escriba "test Extension Pack". Seleccione **Crear**.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. Vaya al nodo **extensibilidad** de Visual C# y seleccione **paquete de extensión**. Deje el nombre de archivo predeterminado (ExtensionPack1. CS).

3. Se agrega el archivo ExtensionPack1. VSExt que contiene el código siguiente:

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

4. El vsixid de la extensión que se va a incluir en el paquete de extensión se puede encontrar en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Busque la extensión que desea incluir y haga clic en el **identificador de copia**. Puede actualizar el **vsixId** existente en el archivo anterior o agregar otra extensión a la lista.

    ![Copia de VsixId de Marketplace](media/vsixid-marketplace.png)

5. Compile el proyecto y cargue la extensión en Marketplace. Vea [publicar una extensión de Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un paquete de extensiones solo puede instalar las extensiones que están disponibles en la [Galería](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o privada.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instale el paquete de extensión desde el Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébelo en ella.

::: moniker range="vs-2017"

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el menú **extensiones** , haga clic en **extensiones administradas**.

::: moniker-end

2. Haga clic en **en línea** y busque "test Extension Pack".

3. Haga clic en **Descargar**. La extensión y su lista de extensiones incluidas en el paquete de extensiones se programarán para su instalación.

4. A continuación se muestra una vista de descarga del paquete de extensión del cuadro de diálogo **administrar extensiones** . Si prefiere instalar solo algunas de las extensiones incluidas en el paquete de extensión, puede modificar la lista de extensiones en **programado para su instalación**.

    ![Descargar el paquete de extensiones de Marketplace](media/vside-extensionpack.png)

5. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Para quitar la extensión del equipo:

::: moniker range="vs-2017"

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el menú **extensiones** , haga clic en **extensiones administradas**.

::: moniker-end

2. Seleccione **Test Extension Pack** y, a continuación, haga clic en **desinstalar**. La extensión y su lista de extensiones incluidas en el paquete de extensiones se programarán para la desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
