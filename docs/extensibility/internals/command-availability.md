---
title: Disponibilidad de comandos ? Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709695"
---
# <a name="command-availability"></a>Disponibilidad de comandos

El contexto de Visual Studio determina qué comandos están disponibles. El contexto puede cambiar en función del proyecto actual, el editor actual, los VSPackages que se cargan y otros aspectos del entorno de desarrollo integrado (IDE).

## <a name="command-contexts"></a>Contextos de comando

Los siguientes contextos de comando son los más comunes:

- IDE: los comandos proporcionados por el IDE siempre están disponibles.

- VSPackage: VSPackages puede definir cuándo se van a mostrar u ocultar comandos.

- Proyecto: los comandos de proyecto solo aparecen para el proyecto seleccionado actualmente.

- Editor: Solo un editor puede estar activo a la vez. Los comandos del editor activo están disponibles. Un editor trabaja en estrecha colaboración con un servicio de lenguaje. El servicio de lenguaje debe procesar sus comandos en el contexto del editor asociado.

- Tipo de archivo: un editor puede cargar más de un tipo de archivo. Los comandos disponibles pueden cambiar en función del tipo de archivo.

- Ventana activa: la última ventana de documento activo establece el contexto de la interfaz de usuario (UI) para los enlaces de clave. Sin embargo, una ventana de herramientas que tiene una tabla de enlace de claves similar al explorador web interno también podría establecer el contexto de la interfaz de usuario. Para las ventanas de documentos con varias pestañas, como el editor HTML, cada pestaña tiene un GUID de contexto de comando diferente. Después de registrar una ventana de herramientas, siempre está disponible en el menú **Ver.**

- Contexto de interfaz de usuario: los <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> contextos de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> interfaz de usuario <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> se identifican mediante los valores de la clase, por ejemplo, cuando se compila la solución o cuando el depurador está activo. Varios contextos de interfaz de usuario pueden estar activos al mismo tiempo.

## <a name="define-custom-context-guids"></a>Definir GUID de contexto personalizados

Si aún no se ha definido un GUID de contexto de comando adecuado, puede definir uno en el VSPackage y, a continuación, programarlo para que esté activo o inactivo según sea necesario para controlar la visibilidad de los comandos:

1. Registrar GUID de contexto <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> mediante una llamada al método.

2. Obtener el estado de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> GUID de contexto mediante una llamada al método.

3. Active y desactive los GUID de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> contexto llamando al método.

> [!CAUTION]
> Asegúrese de que el VSPackage no afecta a los GUID de contexto existentes porque otros VSPackages pueden depender de ellos.

## <a name="see-also"></a>Vea también

- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)
- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
