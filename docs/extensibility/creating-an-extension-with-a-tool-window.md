---
title: Creación de una extensión con una ventana de herramientas ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739546"
---
# <a name="create-an-extension-with-a-tool-window"></a>Crear una extensión con una ventana de herramientas

En este procedimiento, aprenderá a usar la plantilla de proyecto VSIX y la plantilla de elemento De la ventana de herramientas **personalizada** para crear una extensión con una ventana de herramientas.

## <a name="prerequisites"></a>Prerrequisitos

 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

### <a name="create-a-tool-window"></a>Crear una ventana de herramientas

1. Cree un proyecto VSIX denominado **FirstWindow**. Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de ventana de herramientas denominada **MyWindow**. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione Ventana de **herramientas personalizadas**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de la ventana de herramientas a *MyWindow.cs*.

3. Compile la solución y comience la depuración.

   Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [La instancia experimental](../extensibility/the-experimental-instance.md).

4. En la instancia experimental, vaya a **Ver** > **otras ventanas**.

   Debería ver un elemento de menú para **MyWindow**. Haga clic en él.

   Debería ver una ventana de herramientas con el título **MyWindow** y un botón que dice **Click Me!.**
