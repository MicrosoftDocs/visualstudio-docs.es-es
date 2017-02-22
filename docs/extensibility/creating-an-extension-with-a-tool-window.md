---
title: "Crear una extensi&#243;n con una ventana de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Crear una extensi&#243;n con una ventana de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este procedimiento, aprenderá a usar la plantilla de proyecto VSIX y **ventana de herramientas personalizada** plantilla de elemento para crear una extensión con una ventana de herramientas.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Creación de una ventana de herramientas  
  
1.  Cree un proyecto VSIX denominado **FirstWindow**. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Cuando se abre el proyecto, agregue una plantilla de elemento de ventana de herramienta denominada **FirstWindow**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **ventana de herramientas personalizada**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de la ventana de herramienta a **FirstWindow.cs**.  
  
3.  Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4.  En la instancia experimental, vaya a **vista y otras ventanas**.  
  
     Debería ver un elemento de menú **FirstWindow**. Haga clic en él.  
  
     Debería ver una ventana de herramientas con el título **FirstWindow** y un botón **Click Me\!.**