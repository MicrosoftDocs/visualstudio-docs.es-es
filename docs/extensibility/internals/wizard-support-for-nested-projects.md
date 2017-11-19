---
title: Asistente para compatibilidad con proyectos anidados | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7191d31d4ec53fb26f4ab20114201836f1b58fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-support-for-nested-projects"></a>Asistente para compatibilidad con proyectos anidados
El IDE ejecuta dos asistentes que puede implementar el proyecto principal para proyectos anidados: el **nuevo proyecto** asistente y **Agregar elemento** asistente.  
  
 Si un usuario inicia la **nuevo proyecto** asistente seleccionando **Agregar proyecto** y haga clic en **nuevo proyecto** en el menú archivo o seleccionando **agregar** y con el botón secundario **nuevo proyecto** en el Explorador de soluciones, el IDE ejecuta el **AddProject** comando y la implementación del proyecto principal de la **AddProject**comando devuelve un archivo de proyecto de plantilla o un archivo de asistente (.vsz) que tiene un conjunto de parámetros de contexto.  
  
 De forma similar, la implementación de un proyecto elemento primario de **AddItem** asistentes devuelve un archivo .vsz que tiene un conjunto diferente de parámetros de contexto.  
  
 Para obtener más información acerca de los asistentes, vea [asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parámetros de contexto](../../extensibility/internals/context-parameters.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)