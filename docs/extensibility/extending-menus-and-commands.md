---
title: Ampliación de menús y comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 052dff899c1f6c6141e605c41e8269a584800ed7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966821"
---
# <a name="extend-menus-and-commands"></a>Extender los menús y comandos
Los comandos son la manera de agregar acciones y los procesos para Visual Studio. En la mayoría de los casos se muestran los comandos en menús o barras de herramientas. La plantilla de proyecto VSPackage muestra cómo implementar un comando muy básico. Para una implementación un poco más larga, pero todavía básica, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información acerca de los comandos, menús y barras de herramientas de Visual Studio, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Los comandos, menús y barras de herramientas se definen en el *.vsct* archivo que forma parte de los proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el *.vsct* archivo [VSPackages cómo agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Los siguientes temas explican cómo agregar diferentes tipos de comandos, menús y barras de herramientas.  
  
## <a name="in-this-section"></a>En esta sección  
 [Agregar un menú en la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explica cómo agregar un menú en la parte superior de la barra de menús de Visual Studio.  
  
 [Enlazar métodos abreviados de teclado a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explica cómo agregar un método abreviado de teclado (por ejemplo, CTRL + 3) a un elemento de menú.  
  
 [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explica cómo agregar un submenú del menú superior.  
  
 [Agregar que una lista a un submenú usados recientemente](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explica cómo agregar una lista usados más recientemente.  
  
 [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md)  
 Describe cómo agrupar elementos de comando para que pueden incluirse en varios menús.  
  
 [Agregar iconos a comandos de menú](../extensibility/adding-icons-to-menu-commands.md)  
 Describe cómo agregar un icono a un comando en una barra de herramientas y un menú.  
  
 [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)  
 Describe el uso de la `TextChanges` marca para habilitar un elemento de menú al que se puede cambiar dinámicamente.  
  
 [Cambiar la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Describe cómo habilitar o deshabilitar un comando de forma dinámica.  
  
 [Actualización de la interfaz de usuario](../extensibility/updating-the-user-interface.md)  
 Describe cómo forzar una actualización de la interfaz de usuario para reflejar los cambios recientes.  
  
 [Localizar los comandos de menú](../extensibility/localizing-menu-commands.md)  
 Explica cómo localizar los comandos de menú.  