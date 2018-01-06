---
title: "Extender los menús y comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 815aac693686dc59d6934b00fb456c3a1afce72c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="extending-menus-and-commands"></a>Extender menús y comandos
Comandos son la forma agregar acciones y procesos en Visual Studio. En la mayoría de los casos los comandos se muestran en los menús o barras de herramientas. La plantilla de proyecto de VSPackage muestra cómo implementar un comando muy básico. Para una implementación de un poco más, aunque todavía básica, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información sobre comandos, menús y barras de herramientas de Visual Studio, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Comandos, menús y barras de herramientas se definen en el archivo .vsct que forma parte de proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el archivo .vsct en [cómo VSPackages agregar elementos de la interfaz](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Los temas siguientes explican cómo agregar diferentes tipos de comandos, menús y barras de herramientas.  
  
## <a name="in-this-section"></a>En esta sección  
 [Adición de un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explica cómo agregar un menú a la parte superior de barra de menús de Visual Studio.  
  
 [Enlace de métodos abreviados de teclado a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explica cómo agregar un método abreviado de teclado (por ejemplo, CTRL + 3) a un elemento de menú.  
  
 [Adición de un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explica cómo agregar un submenú al menú superior.  
  
 [Adición de una lista Utilizado(s) recientemente a un submenú](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explica cómo agregar una lista usados más recientemente.  
  
 [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md)  
 Describe cómo agrupar los elementos de comando para que pueden incluirse en varios menús.  
  
 [Adición de iconos a comandos de menú](../extensibility/adding-icons-to-menu-commands.md)  
 Describe cómo agregar un icono a un comando en una barra de herramientas y un menú.  
  
 [Cambio del texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)  
 Describe el uso de la `TextChanges` marca para habilitar un elemento de menú que pueden cambiar dinámicamente.  
  
 [Cambio de la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Describe cómo habilitar o deshabilitar un comando de forma dinámica.  
  
 [Actualización de la interfaz de usuario](../extensibility/updating-the-user-interface.md)  
 Describe cómo forzar una actualización de la interfaz de usuario para reflejar los cambios recientes.  
  
 [Adaptación de comandos de menú](../extensibility/localizing-menu-commands.md)  
 Explica cómo localizar los comandos de menú.  
  
## <a name="related-sections"></a>Secciones relacionadas