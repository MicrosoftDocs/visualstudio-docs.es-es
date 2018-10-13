---
title: Creación de una extensión con una ventana de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13ec73d4b251cc06b6224d2d08f1bb20ad8e98dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204781"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Creación de una extensión con una ventana de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este procedimiento, aprenda a usar la plantilla de proyecto VSIX y la **ventana de herramientas personalizada** plantilla de elemento para crear una extensión con una ventana de herramientas.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Creación de una ventana de herramientas  
  
1.  Cree un proyecto VSIX denominado **FirstWindow**. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Cuando se abra el proyecto, agregue una plantilla de elemento de ventana de herramienta denominada **FirstWindow**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **ventana de herramientas personalizada**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de la ventana de herramienta a **FirstWindow.cs**.  
  
3.  Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4.  En la instancia experimental, vaya a **vista / Windows otros**.  
  
     Debería ver un elemento de menú para **FirstWindow**. Haga clic en él.  
  
     Debería ver una ventana de herramientas con el título **FirstWindow** y un comentario de botón **Click Me!.**

