---
title: Crear una extensión con una ventana de herramientas | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 597b84854dd398abee9dc21090e085273bc94c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903898"
---
# <a name="create-an-extension-with-a-tool-window"></a>Crear una extensión con una ventana de herramientas

En este procedimiento, aprenderá a usar la plantilla de proyecto de VSIX y la plantilla de elementos de la **ventana de herramientas personalizada** para crear una extensión con una ventana de herramientas.

## <a name="prerequisites"></a>Requisitos previos

 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Crear una ventana de herramientas

1. Cree un proyecto VSIX denominado **FirstWindow**. Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de ventana de herramientas denominada My **Window**. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >  **Extensibility** y seleccione **ventana de herramientas personalizada**. En el campo **nombre** de la parte inferior de la ventana, cambie el nombre del archivo de la ventana de herramientas a *MyWindow.CS*.

3. Compile la solución y comience la depuración.

   Aparece la instancia experimental de Visual Studio. Para obtener más información sobre la instancia experimental, vea [la instancia experimental](../extensibility/the-experimental-instance.md).

4. En la instancia experimental, vaya a **Ver**  >  **otras ventanas**.

   Debería ver un elemento de menú para la **ventana**. Haga clic en él.

   Debería ver una ventana de herramientas con el título mi **ventana** y un botón diciendo **click me.**
