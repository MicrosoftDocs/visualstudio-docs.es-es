---
title: Implementación de la gestión de comandos para proyectos anidados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707609"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementación del control de comandos para proyectos anidados
El IDE puede pasar comandos <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> que <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> se pasan a través de las interfaces y a los proyectos anidados, o los proyectos primarios pueden filtrar o invalidar los comandos.

> [!NOTE]
> Solo se pueden filtrar los comandos que normalmente controla el proyecto primario. Los comandos como **Build** e **Deploy** controlados por el IDE no se pueden filtrar.

 En los pasos siguientes se describe el proceso para implementar el control de comandos.

## <a name="procedures"></a>Procedimientos

#### <a name="to-implement-command-handling"></a>Para implementar el control de comandos

1. Cuando el usuario selecciona un proyecto anidado o un nodo en un proyecto anidado:

   1. El IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llama al método.

      — o —

   2. Si el comando se originó en una ventana de jerarquía, como un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> comando de menú contextual en el Explorador de soluciones, el IDE llama al método en el elemento primario del proyecto.

2. El proyecto primario puede examinar `QueryStatus`los parámetros que se van a pasar a , como `pguidCmdGroup` y `prgCmds`, para determinar si el proyecto primario debe filtrar los comandos. Si el proyecto primario se implementa para filtrar comandos, debe establecer:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    A continuación, el `S_OK`proyecto primario debe devolver .

    Si el proyecto primario no filtra el `S_OK`comando, solo debe devolver . En este caso, el IDE enruta automáticamente el comando al proyecto secundario.

    El proyecto primario no tiene que enrutar el comando al proyecto secundario. El IDE realiza esta tarea.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
