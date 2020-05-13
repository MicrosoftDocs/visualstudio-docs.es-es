---
title: Ampliación de menús y comandos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711796"
---
# <a name="extend-menus-and-commands"></a>Extender menús y comandos
Los comandos son la forma de agregar acciones y procesos a Visual Studio. En la mayoría de los casos, los comandos se muestran en menús o barras de herramientas. La plantilla de proyecto VSPackage muestra cómo implementar un comando muy básico. Para una implementación ligeramente más larga pero básica, consulte [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

 Para obtener más información acerca de los comandos, menús y barras de herramientas de Visual Studio, vea [Comandos, menús y barras](../extensibility/internals/commands-menus-and-toolbars.md)de herramientas .

 Comandos, menús y barras de herramientas se definen en el archivo *.vsct* que forma parte de proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el archivo *.vsct* en [Cómo VSPackages agregan elementos](../extensibility/internals/how-vspackages-add-user-interface-elements.md)de interfaz de usuario .

 En los temas siguientes se explica cómo agregar diferentes tipos de comandos, menús y barras de herramientas.

## <a name="in-this-section"></a>En esta sección
- [Agregue un menú a la barra](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) de menús de Visual Studio Explica cómo agregar un menú a la barra de menús de Visual Studio superior.

- [Enlazar métodos abreviados de teclado a elementos](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) de menú Explica cómo agregar un método abreviado de teclado (como CTRL + 3) a un elemento de menú.

- [Añadir un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) Explica cómo agregar un submenú al menú superior.

- [Agregue una lista utilizada más recientemente a un submenú](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Explica cómo agregar una lista de uso más reciente.

- [Crear grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md) Describe cómo agrupar elementos de comando para que se puedan incluir en varios menús.

- [Añadir iconos a los comandos](../extensibility/adding-icons-to-menu-commands.md) del menú Describe cómo agregar un icono a un comando tanto en una barra de herramientas como en un menú.

- [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md) Describe el uso `TextChanges` de la marca para permitir que un elemento de menú se cambie dinámicamente.

- [Cambiar la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md) Describe cómo habilitar o deshabilitar dinámicamente un comando.

- [Actualizar la interfaz de usuario](../extensibility/updating-the-user-interface.md) Describe cómo forzar una actualización de la interfaz de usuario para reflejar los cambios recientes.

- [Localizar comandos de menú](../extensibility/localizing-menu-commands.md) Explica cómo localizar comandos de menú.
