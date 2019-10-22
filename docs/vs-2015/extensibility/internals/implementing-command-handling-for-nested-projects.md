---
title: Implementación de control de comandos para anidar proyectos | Documentos de Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445424"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementación del control de comandos para proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El IDE puede pasar comandos que se pasan a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaces para proyectos anidados o los proyectos principales se pueden filtrar o reemplazar los comandos.  
  
> [!NOTE]
> Se pueden filtrar solo los comandos que normalmente se controla mediante el proyecto principal. Los comandos como **compilar** y **implementar** que se controlan mediante el IDE no se pueden filtrar.  
  
 Los pasos siguientes describen el proceso para implementar el control de comandos.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-implement-command-handling"></a>Para implementar el control de comandos  
  
1. Cuando el usuario selecciona un nodo o un proyecto anidado en un proyecto anidado:  
  
   1. Las llamadas IDE el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método.  
  
      o  
  
   2. Si el comando se ha originado en una ventana de jerarquía, por ejemplo, un comando de menú contextual en el Explorador de soluciones, el IDE llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método en el elemento primario del proyecto.  
  
2. El proyecto principal puede examinar los parámetros que se pasarán al `QueryStatus`, tales como `pguidCmdGroup` y `prgCmds`, para determinar si el proyecto principal debe filtrar los comandos. Si el proyecto principal se implementa para filtrar los comandos, debe establecer:  
  
   ```  
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
   // make sure it is disabled  
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
   ```  
  
    A continuación, el proyecto principal se debe devolver `S_OK`.  
  
    Si el proyecto principal no filtra el comando, debe devolver simplemente `S_OK`. En este caso, el IDE enruta automáticamente el comando al proyecto secundario.  
  
    No tiene el proyecto principal enrutar el comando al proyecto secundario. El IDE realiza esta tarea...  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Los comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)
