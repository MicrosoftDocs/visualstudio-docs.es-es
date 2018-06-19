---
title: Implementar el control de comandos para anidar proyectos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3f02752fad6932bac90597d56f27257e78b84cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129005"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementar el control de comandos para proyectos anidados
El IDE puede pasar comandos que se pasan a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaces proyectos anidados o primario proyectos puedan filtrar o reemplazar los comandos.  
  
> [!NOTE]
>  Se pueden filtrar solo los comandos normalmente controlados el proyecto principal. Comandos como **generar** y **implementar** que se administran mediante el IDE no se pueden filtrar.  
  
 Los siguientes pasos describen el proceso para implementar la gestión de comandos.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-implement-command-handling"></a>Para implementar el control de comando  
  
1.  Cuando el usuario selecciona un nodo o un proyecto anidado en un proyecto anidado:  
  
    1.  Las llamadas IDE el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método.  
  
     o  
  
    1.  Si el comando se ha originado en una ventana de jerarquía, por ejemplo, un comando de menú contextual en el Explorador de soluciones, el IDE llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método en el elemento primario del proyecto.  
  
2.  El proyecto principal puede examinar los parámetros que se pasan a `QueryStatus`, como `pguidCmdGroup` y `prgCmds`, para determinar si el proyecto principal debe filtrar los comandos. Si se implementa el proyecto principal para filtrar los comandos, debe establecer:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     A continuación, el proyecto principal debe devolver `S_OK`.  
  
     Si el proyecto principal no filtra el comando, debe devolver simplemente `S_OK`. En este caso, el IDE distribuye automáticamente el comando al proyecto secundario.  
  
     El proyecto principal no tiene que enrutar el comando al proyecto secundario. El IDE realiza esta tarea...  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)