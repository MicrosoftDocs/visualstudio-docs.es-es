---
title: Crear un paquete de extensión con la plantilla de elemento del módulo de extensión | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 2e0215b22c66d6b555650e05985a674f2ad9aed4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943107"
---
# <a name="walkthrough-create-an-extension-pack"></a>Tutorial: Creación de un paquete de extensión

Un paquete de extensión es un conjunto de extensiones que se pueden instalar juntos. Módulos de extensión permiten compartir sus extensiones favoritas con otros usuarios fácilmente o agrupar un conjunto de extensiones juntos para un escenario determinado.
  
## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  

La característica de extensión Pack está disponible a partir de Visual Studio 15,8 Preview 2.
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Crear una extensión con una plantilla de elementos de paquete de extensiones

La plantilla de elemento del módulo de extensión crea un paquete de extensión con el conjunto de extensiones que se pueden instalar juntos.
  
1. En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre** , escriba `Test Extension Pack`. Haga clic en **Aceptar**.  
  
2. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **paquete de extensión**. Deje el nombre de archivo predeterminado (ExtensionPack1.cs).  
  
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

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones...** .

2. Haga clic en **Online** y, a continuación, busque `Test Extension Pack`.

3. Haga clic en **Descargar**. La extensión y su lista de extensiones incluidas en el paquete de extensiones, a continuación, se programará para su instalación.

4. A continuación es una vista de descarga del paquete de extensiones de ejemplo de la **extensiones y actualizaciones** cuadro de diálogo. Si prefiere instalar sólo algunas de las extensiones que se incluye en el módulo de extensión, puede modificar la lista de extensiones en **programado para instalar**.

    ![Descargue el paquete de extensiones de Marketplace](media/vside-extensionpack.png)

5. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Quitar la extensión

Para quitar la extensión de su equipo:

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones...** .

2. Seleccione `Test Extension Pack` y, a continuación, haga clic en **desinstalar**. A continuación, se programará para desinstalar la extensión y su lista de extensiones incluidas en el paquete de extensiones.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
