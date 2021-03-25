---
title: Determinar el estado de los comandos mediante ensamblados de interoperabilidad | Microsoft Docs
description: Obtenga información sobre cómo determinar el estado de los comandos que se administran en un VSPackage mediante la interfaz Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef6940aef83ad3865385b4e39fd9cfd62b8866d7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090907"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determinar el estado del comando mediante ensamblados de interoperabilidad
Un VSPackage debe realizar un seguimiento del estado de los comandos que puede controlar. El entorno no puede determinar cuándo se habilita o deshabilita un comando controlado en el VSPackage. Es responsabilidad del VSPackage informar al entorno sobre los Estados de comandos, por ejemplo, el estado de comandos generales como **cortar**, **copiar** y **pegar**.

## <a name="status-notification-sources"></a>Orígenes de notificación de estado
 El entorno recibe información sobre los comandos a través del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método de VSPackages, que forma parte de la implementación del VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. El entorno llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método del VSPackage en dos condiciones:

- Cuando un usuario abre un menú principal o un menú contextual (haciendo clic con el botón derecho), el entorno ejecuta el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método en todos los comandos de ese menú para determinar su estado.

- Cuando el VSPackage solicita que el entorno actualice la interfaz de usuario (UI) actual. Esta actualización se produce como comandos que actualmente son visibles para el usuario, como **cortar**, **copiar** y **pegar** agrupación en la barra de herramientas estándar, se habilitan y deshabilitan en respuesta a las acciones del usuario y el contexto.

  Dado que el shell hospeda varios VSPackages, el rendimiento del shell no se puede degradar de forma aceptable si era necesario sondear cada VSPackage para determinar el estado del comando. En su lugar, el VSPackage debe notificar activamente al entorno cuando su interfaz de usuario cambia en el momento del cambio. Para obtener más información sobre la notificación de actualización, consulte [actualización de la interfaz de usuario](../../extensibility/updating-the-user-interface.md).

## <a name="status-notification-failure"></a>Error en la notificación de estado
 Un error en el VSPackage para notificar al entorno de un cambio de estado de comando puede poner la interfaz de usuario en un estado incoherente. Recuerde que el usuario puede colocar en una barra de herramientas cualquiera de los comandos de menú o menú contextual. Por lo tanto, la actualización de la interfaz de usuario solo cuando se abre un menú o menú contextual no es suficiente.

## <a name="see-also"></a>Consulte también
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementación](../../extensibility/internals/command-implementation.md)
