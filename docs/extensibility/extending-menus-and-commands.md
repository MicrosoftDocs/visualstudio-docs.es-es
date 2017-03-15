---
title: "Comandos y men&#250;s de extensi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús, tareas comunes"
  - "VSPackages, tareas de menú"
  - "archivos .vsct, tareas"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 49
---
# Comandos y men&#250;s de extensi&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Comandos son la manera de agregar acciones y procesos en Visual Studio. En la mayoría de los casos se muestran los comandos en menús o barras de herramientas. La plantilla de proyecto de VSPackage muestra cómo implementar un comando muy básico. Para una implementación un poco más larga, aunque todavía básica, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información acerca de los comandos, menús y barras de herramientas de Visual Studio, consulte [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Barras de herramientas, menús y comandos se definen en el archivo .vsct que forma parte de los proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el archivo .vsct en [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Los temas siguientes explican cómo agregar distintos tipos de comandos, menús y barras de herramientas.  
  
## En esta sección  
 [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explica cómo agregar un menú a la parte superior de barra de menús de Visual Studio.  
  
 [Métodos abreviados de teclado de enlace a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explica cómo agregar un método abreviado de teclado \(por ejemplo, CTRL \+ 3\) a un elemento de menú.  
  
 [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explica cómo agregar un submenú del menú superior.  
  
 [Agregar una mayoría recientemente usados para un submenú](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explica cómo agregar una lista usados más recientemente.  
  
 [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md)  
 Describe cómo agrupar elementos de comando de modo que pueden incluirse en varios menús.  
  
 [Agregar iconos a los comandos de menú](../extensibility/adding-icons-to-menu-commands.md)  
 Describe cómo agregar un icono a un comando en una barra de herramientas y un menú.  
  
 [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)  
 Describe el uso de la `TextChanges` marca para habilitar un elemento de menú puede cambiar dinámicamente.  
  
 [Cambiar la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Describe cómo habilitar o deshabilitar un comando de forma dinámica.  
  
 [Actualización de la interfaz de usuario](../extensibility/updating-the-user-interface.md)  
 Describe cómo forzar una actualización de la interfaz de usuario para reflejar los cambios recientes.  
  
 [Localizar los comandos de menú](../extensibility/localizing-menu-commands.md)  
 Explica cómo adaptar los comandos de menú.  
  
## Secciones relacionadas