---
title: Ubicación predeterminada de comandos, grupos y barras de herramientas ? Microsoft Docs
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
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708888"
---
# <a name="default-command-group-and-toolbar-placement"></a>Colocación predeterminada de comandos, grupos y barras de herramientas
Para la uniformidad y estabilidad del producto, la interfaz de usuario muestra determinados grupos de comandos de forma predeterminada y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona definiciones para comandos y grupos de comandos. VSPackages también puede usar los comandos estándar y grupos de comandos.

 Los grupos de comandos predeterminados se dividen en tres categorías: comandos IDE, comandos de producto y comandos de editor.

## <a name="default-ide-commands"></a>Comandos IDE predeterminados
 La barra de herramientas IDE predeterminada incluye [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comandos compartidos por todos los productos contenidos en . Estos incluyen comandos relacionados con operaciones de proyecto genéricas, como el comando **Guardar** y el comando **Agregar elemento.** VSPackages no debe agregar o restar de esta barra de herramientas, con una excepción: si el producto o VSPackage agrega una nueva ventana de herramientas, a continuación, la ventana debe agregarse a la lista de ventanas de herramientas disponibles en el **vista** menú. Los nuevos productos o VSPackages pueden agregar su propia barra de herramientas.

## <a name="default-product-commands"></a>Comandos de producto predeterminados
 Cada producto puede proporcionar al IDE su propia barra de herramientas predeterminada que contiene comandos importantes y utilizados con frecuencia. Sin embargo, es mejor utilizar menús y barras de herramientas existentes siempre que sea posible y complementarlos con otras barras de herramientas específicas de la tarea según sea necesario.

 El campo de prioridad de una barra de herramientas determina su ubicación de fila. Prioridad cero coloca la barra de herramientas en la tercera fila (fila 3), debajo de la barra de menús (fila 1) y la barra de herramientas **Estándar** (fila 2). Por lo tanto, otras barras de herramientas aparecen en la fila (prioridad + 3). Las barras de herramientas posteriores se colocan en la misma fila, si hay espacio; de lo contrario, se mueven automáticamente a la siguiente fila.

## <a name="default-editor-commands"></a>Comandos de editor predeterminados
 Un VSPackage que proporciona un editor personalizado debe proporcionar una barra de herramientas predeterminada que contiene los comandos más importantes y utilizados con frecuencia en ese editor. La barra de herramientas del editor debe aparecer cuando el editor está activo y debe estar oculto cuando el editor no está activo. Esta visibilidad se controla en el `VisibilityConstraints` elemento del archivo *.vsct.*

 Las barras de herramientas del editor deben colocarse debajo del IDE y las barras de herramientas del producto.

## <a name="see-also"></a>Vea también
- [Comandos, menús y grupos definidos por IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
