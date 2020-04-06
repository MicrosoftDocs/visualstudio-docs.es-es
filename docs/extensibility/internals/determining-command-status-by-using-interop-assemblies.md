---
title: Determinación del estado del comando mediante el uso de ensamblados de interoperabilidad ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708712"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determinar el estado del comando mediante ensamblados de interoperabilidad
Un VSPackage debe realizar un seguimiento del estado de los comandos que puede controlar. El entorno no puede determinar cuándo un comando controlado dentro del VSPackage se habilita o deshabilita. Es responsabilidad del VSPackage informar al entorno sobre los estados de comando, por ejemplo, el estado de los comandos generales como **Cortar**, **Copiar**y **Pegar**.

## <a name="status-notification-sources"></a>Fuentes de notificación de estado
 El entorno recibe información acerca de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> los comandos a través del método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de VSPackages, que forma parte de la implementación de la interfaz de VSPackage. El entorno <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llama al método del VSPackage en dos condiciones:

- Cuando un usuario abre un menú principal o un menú contextual (haciendo clic con el botón derecho), el entorno ejecuta el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método en todos los comandos de ese menú para determinar su estado.

- Cuando el VSPackage solicita que el entorno actualizar la interfaz de usuario actual (UI). Esta actualización se produce cuando los comandos que actualmente son visibles para el usuario, como la agrupación **Cortar**, **Copiar**y **Pegar** en la barra de herramientas estándar, se habilitan y deshabilitan en respuesta a las acciones de contexto y usuario.

  Puesto que el shell hospeda varios VSPackages, el rendimiento del shell se degradaría inaceptablemente si fuera necesario sondear cada VSPackage para determinar el estado del comando. En su lugar, el VSPackage debe notificar activamente el entorno cuando su interfaz de usuario cambia en el momento del cambio. Para obtener más información sobre la notificación de actualización, consulte [Actualizar la interfaz](../../extensibility/updating-the-user-interface.md)de usuario .

## <a name="status-notification-failure"></a>Error de notificación de estado
 Error de VSPackage para notificar al entorno de un cambio de estado de comando puede colocar la interfaz de usuario en un estado incoherente. Recuerde que cualquiera de los comandos de menú o menú contextual puede ser colocado en una barra de herramientas por el usuario. Por lo tanto, no es suficiente actualizar la interfaz de usuario solo cuando se abre un menú o un menú contextual.

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementación](../../extensibility/internals/command-implementation.md)
