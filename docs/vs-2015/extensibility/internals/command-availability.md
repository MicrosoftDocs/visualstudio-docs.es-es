---
title: Disponibilidad de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842383"
---
# <a name="command-availability"></a>Disponibilidad de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El contexto de Visual Studio determina qué comandos están disponibles. El contexto puede cambiar según el proyecto actual, el editor actual, los VSPackages cargados y otros aspectos del entorno de desarrollo integrado (IDE).  
  
## <a name="command-contexts"></a>Contextos de comandos  
 Los siguientes contextos de comando son los más comunes.  
  
- **IDE** de Los comandos proporcionados por el IDE siempre están disponibles.  
  
- **VSPackage** Los VSPackages pueden definir cuándo se van a mostrar u ocultar los comandos.  
  
- **Proyecto** de Los comandos del proyecto solo aparecen para el proyecto seleccionado actualmente.  
  
- **Editor** de Solo un editor puede estar activo a la vez. Los comandos del editor activo están disponibles. Un editor trabaja en estrecha colaboración con un servicio de lenguaje. El servicio de lenguaje debe procesar sus comandos en el contexto del editor asociado.  
  
- **Tipo de archivo** Un editor puede cargar más de un tipo de archivo. Los comandos disponibles pueden cambiar en función del tipo de archivo.  
  
- **Ventana activa** La última ventana de documento activo establece el contexto de la interfaz de usuario para los enlaces de teclado. Sin embargo, una ventana de herramientas que tiene una tabla de enlaces de claves similar al explorador Web interno también podría establecer el contexto de la interfaz de usuario. En el caso de las ventanas de documentos con varias pestañas, como el editor HTML, cada pestaña tiene un GUID de contexto de comando diferente. Una vez registrada una ventana de herramientas, siempre está disponible en el menú **Ver** .  
  
- **Contexto** de la interfaz de usuario Los contextos de la interfaz de usuario se identifican mediante los valores de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> clase, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> cuando se compila la solución o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> cuando el depurador está activo. Varios contextos de la interfaz de usuario pueden estar activos al mismo tiempo.  
  
## <a name="defining-custom-context-guids"></a>Definir GUID de contexto personalizados  
 Si aún no se ha definido un GUID de contexto de comando adecuado, puede definir uno en el VSPackage y, a continuación, programarlo para que esté activo o inactivo según sea necesario para controlar la visibilidad de los comandos.  
  
1. Registre los GUID de contexto mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método.  
  
2. Obtiene el estado de un GUID de contexto mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método.  
  
3. Activar y desactivar los GUID de contexto llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método.  
  
    > [!CAUTION]
    > Asegúrese de que el VSPackage no afecte a ningún GUID de contexto existente, ya que otros VSPackages pueden depender de ellos.  
  
## <a name="see-also"></a>Consulte también  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
