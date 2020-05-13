---
title: Algoritmo de enrutamiento de comandos (Command Routing Algorithm) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709534"
---
# <a name="command-routing-algorithm"></a>Algoritmo de enrutamiento de comandos
En Visual Studio los comandos se controlan mediante varios componentes diferentes. Los comandos se enrutan desde el contexto más interno, que se basa en la selección actual, al contexto más externo (también conocido como global). Para obtener más información, consulte [Disponibilidad de comandos](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Orden de resolución de mando
 Los comandos se pasan a través de los siguientes niveles de contexto de comando:

1. Complementos: el entorno ofrece primero el comando a los complementos que están presentes.

2. Comandos de prioridad: estos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>comandos se registran mediante . Se llaman para cada comando en Visual Studio y se llaman en el orden en que se registraron.

3. Comandos de menú contextual: un comando ubicado en un menú contextual se ofrece primero al destino del comando que se proporciona al menú contextual, y después de eso al enrutamiento típico.

4. Destinos de comandos del conjunto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>barras de herramientas: estos destinos de comando se registran cuando se llama a . El `pCmdTarget` parámetro `null`puede ser . Si no `null`es así, este destino de comando se utiliza para actualizar los comandos ubicados en la barra de herramientas que está configurando. Si el shell está configurando la barra de herramientas, pasa el marco de la ventana como para `pCmdTarget` que todas las actualizaciones de los comandos de la barra de herramientas fluyan a través del marco de la ventana, incluso cuando no está enfocada.

5. Ventana de herramientas: las ventanas <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> de herramientas, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> que normalmente implementan la interfaz, también deben implementar la interfaz para que Visual Studio pueda obtener el destino del comando cuando la ventana de herramientas es la ventana activa. Sin embargo, si la ventana de herramientas que tiene el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> foco es la ventana **Proyecto,** el comando se enruta a la interfaz que es el elemento primario común de los elementos seleccionados. Si esta selección abarca varios proyectos, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> comando se enruta a la jerarquía. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> contiene los métodos y que <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> son análogos a los comandos correspondientes en la interfaz.

6. Ventana de documento: si `RouteToDocs` el comando tiene el indicador establecido en su archivo *.vsct,* Visual Studio busca <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> un destino de comando en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> de vista de documento, que es una instancia de una interfaz o una instancia de un objeto de documento (normalmente una interfaz o una interfaz). Si el objeto de vista de documento no admite el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comando, Visual Studio enruta el comando a la interfaz que se devuelve. (Esta es una interfaz opcional para objetos de datos de documento.)

7. Jerarquía actual: la jerarquía actual puede ser el proyecto que posee la ventana de documento activa o la jerarquía seleccionada en el **Explorador**de soluciones . Visual Studio busca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la interfaz que se implementa en la jerarquía actual o activa. La jerarquía debe admitir comandos que sean válidos siempre que la jerarquía esté activa, incluso si una ventana de documento de un elemento de proyecto tiene el foco. Sin embargo, los comandos que se aplican <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> solo cuando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> el **Explorador** de soluciones tiene el foco deben admitirse mediante la interfaz y sus métodos.

     **Los**comandos Cortar , **Copiar**, **Pegar**, **Eliminar**, **Cambiar nombre**, **Intro**y **DoubleClick** requieren un control especial. Para obtener información sobre cómo controlar los comandos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> **Delete** y **Remove** en jerarquías, consulte la interfaz.

8. Global: si los contextos mencionados anteriormente no han controlado un comando, Visual Studio intenta enrutarlo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> al VSPackage que posee un comando que implementa la interfaz. Si el VSPackage no se ha cargado ya, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> no se carga cuando Visual Studio llama al método. El VSPackage se carga <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> solo cuando se llama al método.

## <a name="see-also"></a>Vea también
- [Diseño de comandos](../../extensibility/internals/command-design.md)
