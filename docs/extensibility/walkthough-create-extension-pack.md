---
title: Crear un paquete de extensión con la plantilla de elemento de paquete de extensión . Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697752"
---
# <a name="walkthrough-create-an-extension-pack"></a>Tutorial: Creación de un paquete de extensión

Un paquete de extensión es un conjunto de extensiones que se pueden instalar juntas. Los paquetes de extensión le permiten compartir fácilmente sus extensiones favoritas con otros usuarios o agrupar un conjunto de extensiones para un escenario determinado.

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, el SDK de Visual Studio se incluye como una característica opcional en la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

La característica Paquete de extensión está disponible a partir de Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Cree una extensión con una plantilla de elemento de paquete de extensión

La plantilla de elemento Paquete de extensión crea un paquete de extensión con un conjunto de extensiones que se pueden instalar juntas.

1. En el cuadro de diálogo **Nuevo proyecto,** busque "vsix" y seleccione **Proyecto VSIX**. En **Project name**, escriba "Test Extension Pack". Seleccione **Crear**.

2. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. Vaya al nodo **Extensibilidad** de Visual C- y seleccione **Paquete de extensión**. Deje el nombre de archivo predeterminado (ExtensionPack1.cs).

3. ExtensionPack1.vsext se agrega el archivo que contiene el siguiente código

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

4. El vsixid de la extensión que se va a incluir en el paquete de extensión se puede encontrar en [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Busque la extensión que desea incluir y haga clic en **Copiar ID**. Puede actualizar el **vsixId** existente en el archivo anterior o agregar otra extensión a la lista.

    ![Copiar VsixId de Marketplace](media/vsixid-marketplace.png)

5. Compile el proyecto y cargue la extensión en Marketplace. Consulte [Publicación de una extensión](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)de Visual Studio .

> [!NOTE]
> Un paquete de extensión solo puede instalar extensiones que estén disponibles en la galería [de Visual Studio Marketplace](https://marketplace.visualstudio.com/) o [Private](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instale el paquete de extensión desde Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébela allí.

::: moniker range="vs-2017"

1. En Visual Studio, en el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el menú **Extensiones** , haga clic en **Extensiones administradas**.

::: moniker-end

2. Haga clic en **En línea** y, a continuación, busque "Test Extension Pack".

3. Haga clic en **Descargar**. La extensión y su lista de extensiones incluidas en el paquete de extensión se programarán para su instalación.

4. A continuación se muestra una vista de descarga del paquete de extensión de ejemplo del cuadro de diálogo **Administrar extensiones.** Si prefiere instalar solo algunas de las extensiones incluidas en el paquete de extensiones, puede modificar la lista de extensiones en **Programado para la instalación.**

    ![Descargar Paquete de Extensión de Marketplace](media/vside-extensionpack.png)

5. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Para eliminar la extensión del equipo:

::: moniker range="vs-2017"

1. En Visual Studio, en el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, en el menú **Extensiones** , haga clic en **Extensiones administradas**.

::: moniker-end

2. Seleccione **Probar paquete de extensión** y, a continuación, haga clic en **Desinstalar**. La extensión y su lista de extensiones incluidas en el paquete de extensión se programarán para su desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
