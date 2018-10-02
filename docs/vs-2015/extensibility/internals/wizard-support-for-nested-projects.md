---
title: Asistente para compatibilidad con proyectos anidados | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4621627faae761bfe63b7fd056427a3771d21582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581381"
---
# <a name="wizard-support-for-nested-projects"></a>Compatibilidad del asistente con los proyectos anidados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [soporte de Asistente para proyectos anidados](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-support-for-nested-projects).  
  
El IDE ejecuta dos asistentes que puede implementar el proyecto principal para proyectos anidados: el **nuevo proyecto** asistente y el **Agregar elemento** asistente.  
  
 Si el usuario inicia la **nuevo proyecto** asistente seleccionando **Agregar proyecto** y haga clic en **nuevo proyecto** en el menú archivo, o bien seleccionando **agregar** y con el botón secundario **nuevo proyecto** en el Explorador de soluciones, el IDE ejecuta el **AddProject** comando y la implementación del proyecto principal de la **AddProject**comando devuelve un archivo de proyecto de plantilla o un archivo de asistentes (.vsz) que tiene un conjunto de parámetros de contexto.  
  
 De forma similar, la implementación de un proyecto elemento primario de **AddItem** asistentes devuelve un archivo .vsz que tiene un conjunto diferente de parámetros de contexto.  
  
 Para obtener más información acerca de los asistentes, vea [asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parámetros de contexto](../../extensibility/internals/context-parameters.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Anidamiento de proyectos](../../extensibility/internals/nesting-projects.md)

