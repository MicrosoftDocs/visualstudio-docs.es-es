---
title: Ubicación predeterminada del comando, el grupo y la barra de herramientas | Microsoft Docs
description: Obtenga información sobre los comandos del IDE, los comandos de producto y los comandos de editor que se muestran de forma predeterminada en la interfaz de usuario de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cacf8db933c7d56d44351da11b7b310bc0bdb8aa
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329892"
---
# <a name="default-command-group-and-toolbar-placement"></a>Ubicación predeterminada del comando, el grupo y la barra de herramientas
En cuanto a la uniformidad y la estabilidad del producto, la interfaz de usuario muestra determinados grupos de comandos de forma predeterminada y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona definiciones para los comandos y los grupos de comandos. Los VSPackages también pueden usar los comandos y grupos de comandos estándar.

 Los grupos de comandos predeterminados se dividen en tres categorías: comandos del IDE, comandos del producto y comandos del editor.

## <a name="default-ide-commands"></a>Comandos IDE predeterminados
 La barra de herramientas predeterminada del IDE incluye comandos compartidos por todos los productos contenidos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Estos incluyen comandos relacionados con las operaciones de proyecto genéricas, como el comando **Save** y el comando **Add item** . Los VSPackages no deben agregar ni quitar de esta barra de herramientas, con una excepción: Si el producto o el VSPackage agregan una nueva ventana de herramientas, la ventana se debe agregar a la lista de ventanas de herramientas disponibles en el menú **Ver** . Los nuevos productos o VSPackages pueden agregar su propia barra de herramientas.

## <a name="default-product-commands"></a>Comandos predeterminados del producto
 Cada producto puede proporcionar el IDE con su propia barra de herramientas predeterminada que contiene comandos importantes y usados con frecuencia. Sin embargo, es mejor usar los menús y las barras de herramientas existentes siempre que sea posible y complementarlos con otras barras de herramientas específicas de tareas según sea necesario.

 El campo prioridad de una barra de herramientas determina la ubicación de la fila. La prioridad cero coloca la barra de herramientas en la tercera fila (fila 3), debajo de la barra de menús (fila 1) y la barra de herramientas **estándar** (fila 2). Por lo tanto, otras barras de herramientas aparecen en la fila (Priority + 3). Las barras de herramientas subsiguientes se colocan en la misma fila, si hay espacio; de lo contrario, se mueven automáticamente a la siguiente fila.

## <a name="default-editor-commands"></a>Comandos de editor predeterminados
 Un VSPackage que proporciona un editor personalizado debe proporcionar una barra de herramientas predeterminada que contenga los comandos más importantes y usados con frecuencia en ese editor. La barra de herramientas del editor debe aparecer cuando el editor está activo y debe ocultarse cuando el editor no está activo. Esta visibilidad se controla en el `VisibilityConstraints` elemento del archivo *. Vsct* .

 Las barras de herramientas del editor deben colocarse debajo del IDE y de las barras de herramientas del producto.

## <a name="see-also"></a>Consulte también
- [Comandos, menús y grupos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
