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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441591"
---
# <a name="command-availability"></a>Disponibilidad de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El contexto de Visual Studio determina qué comandos están disponibles. El contexto puede cambiar en función del proyecto actual, el editor actual, los VSPackages que se cargan y otros aspectos del entorno de desarrollo integrado (IDE).  
  
## <a name="command-contexts"></a>Contextos de comando  
 Los siguientes contextos de comando son los más comunes.  
  
- **IDE** comandos proporcionados por el IDE están siempre disponibles.  
  
- **VSPackage** VSPackages puede definir cuando son los comandos para mostrar u ocultar.  
  
- **Proyecto** comandos de proyecto solo se muestran para el proyecto seleccionado actualmente.  
  
- **Editor** solo editor puede estar activo simultáneamente. Hay comandos desde el editor activo. Un editor trabaja en estrecha colaboración con un servicio de lenguaje. El servicio de lenguaje debe procesar sus comandos en el contexto del editor asociado.  
  
- **Tipo de archivo** un editor puede cargar más de un tipo de archivo. Pueden cambiar los comandos disponibles según el tipo de archivo.  
  
- **Ventana activa** la última ventana de documento activo, Establece el contexto de interfaz de usuario para los enlaces de teclado. Sin embargo, una ventana de herramientas que tiene una tabla de enlace de teclado que se parece el explorador Web interno también puede establecer el contexto de interfaz de usuario. Para ventanas de documento con múltiples fichas, como el editor HTML, cada pestaña tiene un GUID de contexto de otro comando. Una vez registrada una ventana de herramientas, siempre está disponible en el **vista** menú.  
  
- **Contexto de interfaz de usuario** contextos de interfaz de usuario se identifican mediante los valores de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> clase, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> cuando se compila la solución, o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> cuando el depurador está activo. Varios contextos de interfaz de usuario pueden ser activos al mismo tiempo.  
  
## <a name="defining-custom-context-guids"></a>Definir los GUID de contexto personalizado  
 Si un contexto de comando adecuado que GUID ya no está definido, puede definir uno en el paquete de VS y, a continuación, programa que esté activo o inactivo según sea necesario para controlar la visibilidad de los comandos.  
  
1. Registrar identificadores GUID de contexto mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método.  
  
2. Obtener el estado de un GUID de contexto mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método.  
  
3. Activar y desactivar la GUID de contexto mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método.  
  
    > [!CAUTION]
    > Asegúrese de que el VSPackage no afecta a ningún GUID de contexto existente porque otros VSPackages que dependen de ellos.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)   
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
