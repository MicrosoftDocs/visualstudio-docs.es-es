---
title: Ampliación de menús y comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999579"
---
# <a name="extending-menus-and-commands"></a>Ampliación de menús y comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los comandos son la manera de agregar acciones y los procesos para Visual Studio. En la mayoría de los casos se muestran los comandos en menús o barras de herramientas. La plantilla de proyecto VSPackage muestra cómo implementar un comando muy básico. Para una implementación un poco más larga, pero todavía básica, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Para obtener más información acerca de los comandos, menús y barras de herramientas de Visual Studio, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Los comandos, menús y barras de herramientas se definen en el archivo .vsct que forma parte de los proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el archivo .vsct en [cómo VSPackages agregar elementos de la interfaz](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Los siguientes temas explican cómo agregar diferentes tipos de comandos, menús y barras de herramientas.  
  
## <a name="in-this-section"></a>En esta sección  
 [Adición de un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Explica cómo agregar un menú en la parte superior de la barra de menús de Visual Studio.  
  
 [Enlace de métodos abreviados de teclado a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Explica cómo agregar un método abreviado de teclado (por ejemplo, CTRL + 3) a un elemento de menú.  
  
 [Adición de un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)  
 Explica cómo agregar un submenú del menú superior.  
  
 [Adición de una lista Utilizado(s) recientemente a un submenú](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Explica cómo agregar una lista usados más recientemente.  
  
 [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md)  
 Describe cómo agrupar elementos de comando para que pueden incluirse en varios menús.  
  
 [Adición de iconos a comandos de menú](../extensibility/adding-icons-to-menu-commands.md)  
 Describe cómo agregar un icono a un comando en una barra de herramientas y un menú.  
  
 [Cambio del texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md)  
 Describe el uso de la `TextChanges` marca para habilitar un elemento de menú al que se puede cambiar dinámicamente.  
  
 [Cambio de la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Describe cómo habilitar o deshabilitar un comando de forma dinámica.  
  
 [Actualización de la interfaz de usuario](../extensibility/updating-the-user-interface.md)  
 Describe cómo forzar una actualización de la interfaz de usuario para reflejar los cambios recientes.  
  
 [Adaptación de comandos de menú](../extensibility/localizing-menu-commands.md)  
 Explica cómo localizar los comandos de menú.  
  
## <a name="related-sections"></a>Secciones relacionadas
