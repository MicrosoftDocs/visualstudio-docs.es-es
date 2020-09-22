---
title: Implementar el control de comandos para proyectos anidados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2fbce80b2e8c337eddf0d34954a7fd70b895d891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842758"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementación del control de comandos para proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El IDE puede pasar comandos que se pasan a través de las <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaces y a proyectos anidados, o los proyectos primarios pueden filtrar o invalidar los comandos.  
  
> [!NOTE]
> Solo se pueden filtrar los comandos que normalmente controla el proyecto primario. No se pueden filtrar los comandos como **compilación** e **implementación** administrados por el IDE.  
  
 En los pasos siguientes se describe el proceso para implementar el control de comandos.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-implement-command-handling"></a>Para implementar el control de comandos  
  
1. Cuando el usuario selecciona un proyecto anidado o un nodo en un proyecto anidado:  
  
   1. El IDE llama al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método.  
  
      o  
  
   2. Si el comando se originó en una ventana de jerarquía, como un comando de menú contextual en Explorador de soluciones, el IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método en el elemento primario del proyecto.  
  
2. El proyecto primario puede examinar los parámetros que se van a pasar a `QueryStatus` , como `pguidCmdGroup` y `prgCmds` , para determinar si el proyecto primario debe filtrar los comandos. Si el proyecto primario se implementa para filtrar comandos, debe establecer:  
  
   ```  
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
   // make sure it is disabled  
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
   ```  
  
    Después, el proyecto primario debe devolver `S_OK` .  
  
    Si el proyecto primario no filtra el comando, debe devolver simplemente `S_OK` . En este caso, el IDE enruta automáticamente el comando al proyecto secundario.  
  
    El proyecto primario no tiene que enrutar el comando al proyecto secundario. El IDE realiza esta tarea.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
