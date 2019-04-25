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
ms.openlocfilehash: c8f8d98525f1038b4a50dcaa5ca6237bd4c0f7b5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709270"
---
# <a name="extend-menus-and-commands"></a>Extender los menús y comandos
Los comandos son la manera de agregar acciones y los procesos para Visual Studio. En la mayoría de los casos se muestran los comandos en menús o barras de herramientas. La plantilla de proyecto VSPackage muestra cómo implementar un comando muy básico. Para una implementación un poco más larga, pero todavía básica, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

 Para obtener más información acerca de los comandos, menús y barras de herramientas de Visual Studio, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

 Los comandos, menús y barras de herramientas se definen en el *.vsct* archivo que forma parte de los proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el *.vsct* archivo [VSPackages cómo agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Los siguientes temas explican cómo agregar diferentes tipos de comandos, menús y barras de herramientas.

## <a name="in-this-section"></a>En esta sección
- [Agregar un menú en la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) se explica cómo agregar un menú en la barra de menús superior de Visual Studio.

- [Enlazar métodos abreviados de teclado a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) explica cómo agregar un método abreviado de teclado (por ejemplo, CTRL + 3) a un elemento de menú.

- [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) explica cómo agregar un submenú del menú superior.

- [Agregar una lista usa más recientemente a un submenú](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) explica cómo agregar una lista usados más recientemente.

- [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md) se describe cómo agrupar elementos de comando para que pueden incluirse en varios menús.

- [Agregar iconos a comandos de menú](../extensibility/adding-icons-to-menu-commands.md) describe cómo agregar un icono a un comando en una barra de herramientas y un menú.

- [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md) describe el uso de la `TextChanges` marca para habilitar un elemento de menú al que se puede cambiar dinámicamente.

- [Cambiar la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md) se describe cómo habilitar o deshabilitar un comando de forma dinámica.

- [Actualizar la interfaz de usuario](../extensibility/updating-the-user-interface.md) se describe cómo forzar una actualización de la interfaz de usuario para reflejar los cambios recientes.

- [Localizar los comandos de menú](../extensibility/localizing-menu-commands.md) explica cómo localizar los comandos de menú.