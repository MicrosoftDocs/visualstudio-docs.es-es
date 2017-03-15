---
title: "Colocar un control de usuario en una ventana de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, agregar controles de usuario"
  - "controles de usuario [SDK de Visual Studio], agregar a ventanas de herramientas"
  - "controles de usuario [SDK de Visual Studio]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# Colocar un control de usuario en una ventana de herramientas
Este tutorial muestra cómo agregar un control de usuario a una ventana de herramientas.  
  
 Un control de usuario es una colección de controles de Windows reunidos en un control. Para agregar un control de usuario a una ventana de herramientas, solo se necesita que el control de usuario aparezca en el **Cuadro de herramientas**. El control de usuario que se usa en este tutorial es el control de reloj desarrollado en [Tutorial: Crear un control compuesto con Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md).  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Crear el control de usuario  
  
1.  Siga los pasos de [Tutorial: Crear un control compuesto con Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md) para crear el control de reloj. No cree el control de reloj de alarma.  
  
> [!NOTE]
>  En los pasos siguientes se supone que el nombre del control de reloj es `ctlClock`.  
  
## Crear una extensión de la ventana de herramientas  
  
1.  Cree un proyecto VSIX denominado `MyToolWindowPackageUC` que tenga una ventana de herramientas denominada `MyToolWindow`. Si necesita ayuda para hacerlo, consulte [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Agregar el control de usuario  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en la solución **MyToolWindowPackageUC**, elija **Agregar** y, después, haga clic en **Proyecto existente**.  
  
2.  En el cuadro de diálogo **Agregar proyecto existente**, abra el proyecto ctlClockLib y seleccione el archivo de proyecto ctlClock.lib.csproj. Haga clic en **Aceptar**. Se habilita el control de usuario que puede usarse en el diseñador.  
  
3.  En el **Explorador de soluciones**, haga clic con el botón derecho en MyToolWindowControl.cs y seleccione **Diseñador de vistas**. Se abre el diseñador de formularios, que muestra el control generado para la ventana de herramientas.  
  
4.  Abra el **Cuadro de herramientas**, busque la sección con la etiqueta **Componentes de ctlClockLib** y haga doble clic en el control **ctlClock** de esa sección para agregarlo al formulario. Al ocultarse el **Cuadro de herramientas**, debería mostrarse una visualización de tiempo en el formulario de la ventana de herramientas.  
  
5.  En el diseñador, seleccione el control de reloj que se acaba de agregar y cambie la propiedad **Anchor** para que sea **Top**.  
  
6.  En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto ctlClockLib y, después, haga clic en **Propiedades**.  
  
7.  En la pestaña **Firma**, seleccione la opción **Firmar el ensamblado**. En el cuadro **Elija un archivo de clave de nombre seguro**, haga clic en **\<examinar\>** y navegue hasta el archivo key.snk en la carpeta del proyecto **MyToolWindowPackageUC**.  
  
8.  Compile el programa y asegúrese de que no existan errores. Este paso registra el VSPackage y su ventana de herramientas con Visual Studio.  
  
9. Presione F5 para abrir una instancia de Visual Studio en el subárbol experimental.  
  
10. En Visual Studio experimental, en el menú **Ver**, seleccione **Otras ventanas** y, después, haga clic en **MyToolWindow**. Se muestra la ventana de herramientas, con una visualización del tiempo de ejecución.  
  
## Vea también  
 [Tutorial: Crear un control compuesto con Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)