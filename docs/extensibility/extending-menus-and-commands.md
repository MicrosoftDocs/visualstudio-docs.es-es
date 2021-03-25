---
title: Extensión de menús y comandos | Microsoft Docs
description: Obtenga información sobre los comandos, que agregan acciones y procesos a Visual Studio. La plantilla de proyecto VSPackage muestra cómo implementar un comando muy básico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a96978cdad45c669b607c18e12b2e492dcf95bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075216"
---
# <a name="extend-menus-and-commands"></a>Extender menús y comandos
Los comandos son la manera de agregar acciones y procesos a Visual Studio. En la mayoría de los casos, los comandos se muestran en menús o barras de herramientas. La plantilla de proyecto VSPackage muestra cómo implementar un comando muy básico. Para una implementación ligeramente más larga pero todavía básica, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

 Para obtener más información sobre los comandos, menús y barras de herramientas de Visual Studio, vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

 Los comandos, menús y barras de herramientas se definen en el archivo *. Vsct* que forma parte de los proyectos de VSPackage. Puede encontrar información sobre el IDE de Visual Studio y el archivo *. Vsct* en [cómo los VSPackages agregan elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 En los temas siguientes se explica cómo agregar diferentes tipos de comandos, menús y barras de herramientas.

## <a name="in-this-section"></a>En esta sección
- [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Explica cómo agregar un menú a la barra de menús superior de Visual Studio.

- [Enlazar métodos abreviados de teclado a elementos de menú](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Explica cómo agregar un método abreviado de teclado (por ejemplo, CTRL + 3) a un elemento de menú.

- [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) Explica cómo agregar un submenú al menú superior.

- [Agregar una lista de usados más recientemente a un submenú](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Explica cómo agregar una lista de usados más recientemente.

- [Crear grupos de botones reutilizables](../extensibility/creating-reusable-groups-of-buttons.md) Describe cómo agrupar los elementos de comando para que se puedan incluir en varios menús.

- [Agregar iconos a comandos de menú](../extensibility/adding-icons-to-menu-commands.md) Describe cómo agregar un icono a un comando en una barra de herramientas y un menú.

- [Cambiar el texto de un comando de menú](../extensibility/changing-the-text-of-a-menu-command.md) Describe el uso de la `TextChanges` marca para habilitar el cambio dinámico de un elemento de menú.

- [Cambiar la apariencia de un comando](../extensibility/changing-the-appearance-of-a-command.md) Describe cómo habilitar o deshabilitar un comando dinámicamente.

- [Actualizar la interfaz de usuario](../extensibility/updating-the-user-interface.md) Describe cómo forzar una actualización de la interfaz de usuario para que refleje los cambios recientes.

- [Localizar comandos de menú](../extensibility/localizing-menu-commands.md) Explica cómo localizar comandos de menú.
