---
title: Algoritmo de enrutamiento de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fc431f008c59a7d4ceff2d9b9ec14d85091daf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728000"
---
# <a name="command-routing-algorithm"></a>Algoritmo de enrutamiento de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En Visual Studio, los comandos se controlan mediante una serie de diferentes componentes. Los comandos se enrutan desde el contexto más interno, que se basa en la selección actual, en el contexto más externo (también conocido como global). Para obtener más información, consulte [disponibilidad](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Orden de resolución de comando  
 Los comandos se pasan a través de los niveles de contexto de los comandos siguientes:  
  
1.  Complementos: El entorno ofrece primero el comando para los complementos que están presentes.  
  
2.  Comandos de prioridad: se registran con estos comandos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Que se invocan para todos los comandos de Visual Studio y se llaman en el orden en que se registran.  
  
3.  Comandos de menú contextual: primero se ofrece un comando que se encuentra en un menú contextual para el destino del comando que se proporciona en el menú contextual y, después en el enrutamiento típicos.  
  
4.  Barra de herramientas del conjunto de destinos de comando: se registran estos destinos de comando cuando se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. El `pCmdTarget` parámetro puede ser `null`. Si no es `null`, a continuación, este destino de comando se usa para actualizar todos los comandos se encuentra en la barra de herramientas que se va a configurar. Si el shell es la configuración de la barra de herramientas, a continuación, pasa el marco de ventana como la `pCmdTarget` para que todas las actualizaciones a los comandos en el flujo de la barra de herramientas mediante el marco de ventana, incluso cuando no está en el foco.  
  
5.  Ventana de herramientas: Ventanas, que normalmente se implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> de la interfaz, también debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para que Visual Studio puede obtener el destino del comando cuando la ventana de herramientas es la ventana activa. Sin embargo, si la ventana de herramientas que tiene el foco es el **proyecto** ventana y, a continuación, el comando se enruta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz que es el elemento primario común de los elementos seleccionados. Si esta selección abarca varios proyectos, el comando se enruta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> jerarquía. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz contiene la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos que son análogos a los correspondientes comandos en el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.  
  
6.  Ventana de documento: Si el comando tiene el indicador de RouteToDocs establecido en su archivo .vsct, Visual Studio busca un destino de comando en el objeto de vista de documento, que puede ser una instancia de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz o una instancia de un objeto de documento (normalmente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interfaz o un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz). Si el objeto de vista de documento no es compatible con el comando, Visual Studio enruta el comando para el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz que se devuelve. (Esto es una interfaz opcional para los objetos de datos de documento).  
  
7.  Jerarquía actual: la jerarquía actual puede ser el proyecto que posee la ventana de documento activo o en la jerarquía que está seleccionada en **el Explorador de soluciones**. Visual Studio busca la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz que se implementa en la jerarquía activa o actual. La jerarquía debe admitir los comandos que son válidos siempre que la jerarquía está activa, incluso si una ventana de documento de un elemento de proyecto tiene el foco. Sin embargo, los comandos que aplican solo cuando **el Explorador de soluciones** tiene foco debe ser compatibles con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz y su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>métodos.  
  
     **Cortar**, **copia**, **pegar**, **eliminar**, **cambiar el nombre de**, **escriba**y **DoubleClick** comandos requieren un tratamiento especial. Para obtener información sobre cómo controlar **eliminar** y **quitar** comandos en las jerarquías, consulte el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaz.  
  
8.  Global: Si un comando no se ha controlado por los contextos mencionados anteriormente, Visual Studio intenta dirigirlo al VSPackage que posee un comando que implementa el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Si ya no se ha cargado el VSPackage, no se carga cuando Visual Studio llama a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. El VSPackage se carga solo cuando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [Diseño de comandos](../../extensibility/internals/command-design.md)

