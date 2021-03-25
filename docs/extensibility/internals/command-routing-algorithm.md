---
title: Algoritmo de enrutamiento de comandos | Microsoft Docs
description: Obtenga información sobre el orden de resolución de comandos en Visual Studio, ya que los comandos se controlan mediante distintos componentes y se enrutan desde el interior al contexto más externo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e02493cbb2f872806ade33d77609d45d1938ccd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057317"
---
# <a name="command-routing-algorithm"></a>Algoritmo de enrutamiento de comandos
En Visual Studio, los comandos se controlan mediante una serie de componentes diferentes. Los comandos se enrutan desde el contexto más interno, que se basa en la selección actual, al contexto externo (también conocido como global). Para obtener más información, vea [disponibilidad de comandos](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Orden de resolución de comandos
 Los comandos se pasan a través de los siguientes niveles de contexto de comando:

1. Complementos: el entorno ofrece primero el comando a cualquier complemento que esté presente.

2. Comandos de prioridad: estos comandos se registran mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Se llama para cada comando en Visual Studio y se llama en el orden en el que se registraron.

3. Comandos del menú contextual: un comando ubicado en un menú contextual se ofrece primero al destino del comando que se proporciona al menú contextual y, después, al enrutamiento típico.

4. Conjunto de barras de herramientas destinos de comando: estos destinos de comando se registran cuando se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . El `pCmdTarget` parámetro puede ser `null` . Si no es así `null` , este destino de comando se usa para actualizar los comandos ubicados en la barra de herramientas que está configurando. Si el shell está configurando la barra de herramientas, pasa el marco de la ventana como `pCmdTarget` para que todas las actualizaciones de los comandos de la barra de herramientas fluyan a través del marco de la ventana, aunque no tenga el foco.

5. Ventana de herramientas: las ventanas de herramientas, que normalmente implementan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz, también deben implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz para que Visual Studio pueda obtener el destino del comando cuando la ventana de herramientas sea la ventana activa. Sin embargo, si la ventana de herramientas que tiene el foco es la ventana del **proyecto** , el comando se enruta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz que es el elemento primario común de los elementos seleccionados. Si esta selección abarca varios proyectos, el comando se enruta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> jerarquía. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz contiene los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos y que son análogos a los comandos correspondientes en la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.

6. Ventana de documento: Si el comando tiene la `RouteToDocs` marca establecida en su archivo *. Vsct* , Visual Studio busca un destino de comando en el objeto de vista de documento, que es una instancia de una <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz o una instancia de un objeto de documento (normalmente una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaz o una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz). Si el objeto de vista de documento no admite el comando, Visual Studio enruta el comando a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz que se devuelve. (Esta es una interfaz opcional para los objetos de datos de documento).

7. Jerarquía actual: la jerarquía actual puede ser el proyecto propietario de la ventana de documento activa o la jerarquía seleccionada en **Explorador de soluciones**. Visual Studio busca la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz implementada en la jerarquía actual, o activa. La jerarquía debe admitir comandos que son válidos cada vez que la jerarquía está activa, incluso si una ventana de documento de un elemento de proyecto tiene el foco. Sin embargo, los comandos que se aplican solo cuando **Explorador de soluciones** tiene el foco deben admitirse mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz y sus <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos y.

     Los comandos **cortar**, **copiar**, **pegar**, **eliminar**, **cambiar nombre**, **entrar** y **DoubleClick** requieren un tratamiento especial. Para obtener información sobre cómo controlar los comandos **Delete** y **Remove** en las jerarquías, vea la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaz.

8. Global: si los contextos mencionados anteriormente no han controlado un comando, Visual Studio intenta enrutarlo al VSPackage que posee un comando que implementa la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Si el VSPackage no se ha cargado ya, no se carga cuando Visual Studio llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. El VSPackage solo se carga cuando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> se llama al método.

## <a name="see-also"></a>Consulte también
- [Diseño de comandos](../../extensibility/internals/command-design.md)
