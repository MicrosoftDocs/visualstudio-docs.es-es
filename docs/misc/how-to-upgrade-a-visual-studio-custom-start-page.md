---
title: "C&#243;mo: Actualizar una p&#225;gina de inicio personalizada de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# C&#243;mo: Actualizar una p&#225;gina de inicio personalizada de Visual Studio
Puede actualizar una página de inicio personalizada de Visual Studio 2010 o de Visual Studio 2012 a Visual Studio 2015 siguiendo los pasos indicados a continuación.  
  
> [!WARNING]
>  La página de inicio personalizada que se actualiza en este procedimiento es la creada con la plantilla de la [página de inicio personalizada](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) en la Galería de Visual Studio. La página de inicio puede tener otras características que necesiten actualizarse.  
  
### Para actualizar una página de inicio personalizada a Visual Studio 2015  
  
1.  Asegúrese de que están instalados Visual Studio 2015 y el SDK de Visual Studio 2015. Puede descargar el VSSDK de [Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/?linkid=9863867).  
  
2.  Abra el proyecto de plantilla personalizada. Verá un mensaje que le notifica que el proyecto se debe actualizar. Haga clic en **Aceptar** y espere a que se complete la actualización.  
  
3.  En las propiedades del proyecto para el proyecto de página de inicio y el proyecto de control, asegúrese de que el marco de trabajo de destino es al menos .NET Framework 4.5.  
  
4.  En la categoría de depuración de las propiedades del proyecto para el proyecto de página de inicio, establezca la ruta de acceso a la versión de devenv.exe de Visual Studio 2015.  
  
5.  En las referencias de proyecto para ambos proyectos, quite las referencias a Microsoft.VisualStudio.Shell.11.0 y agregue referencias a Microsoft.VisualStudio.Shell.14.0.  
  
6.  Abra StartPage.xaml con el editor XML y realice los cambios siguientes:  
  
    1.  Actualice los espacios de nombres. Cambie las siguientes líneas:  
  
        ```  
  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0" xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"  
        ```  
  
         por las siguientes:  
  
        ```  
  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0" xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0" xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        ```  
  
7.  Abra MyControl.xaml y cambie la referencia de espacio de nombres `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` a `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .