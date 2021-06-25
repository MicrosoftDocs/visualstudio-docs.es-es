---
title: Implementar el control de comandos para proyectos anidados | Microsoft Docs
description: Obtenga información sobre cómo implementar el control de comandos para proyectos anidados en el Visual Studio de desarrollo integrado (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4324e207d7b424295137f9523ed0bed538b3d806
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899991"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementación del control de comandos para proyectos anidados
El IDE puede pasar comandos que se pasan a través de y las interfaces a proyectos anidados, o bien los proyectos primarios pueden filtrar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> invalidar los comandos.

> [!NOTE]
> Solo se pueden filtrar los comandos que controla normalmente el proyecto primario. Los comandos como **Build** e **Deploy** que administra el IDE no se pueden filtrar.

 En los pasos siguientes se describe el proceso para implementar el control de comandos.

## <a name="procedures"></a>Procedimientos

#### <a name="to-implement-command-handling"></a>Para implementar el control de comandos

1. Cuando el usuario selecciona un proyecto anidado o un nodo en un proyecto anidado:

   1. El IDE llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método .

      o

   2. Si el comando se originó en una ventana de jerarquía, como un comando de menú contextual en Explorador de soluciones, el IDE llama al método en el elemento primario <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> del proyecto.

2. El proyecto primario puede examinar los parámetros que se pasan a , como y , para determinar si el `QueryStatus` proyecto primario debe filtrar los `pguidCmdGroup` `prgCmds` comandos. Si el proyecto primario se implementa para filtrar comandos, debe establecer:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    A continuación, el proyecto primario debe devolver `S_OK` .

    Si el proyecto primario no filtra el comando, solo debe devolver `S_OK` . En este caso, el IDE enruta automáticamente el comando al proyecto secundario.

    El proyecto primario no tiene que enrutar el comando al proyecto secundario. El IDE realiza esta tarea.

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
