---
title: Proyecto de archivos varios | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a637b37590a0aaf321a4e04896b2cbe12c29691f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="miscellaneous-files-project"></a>Proyecto de archivos varios
Cuando un usuario abre elementos del proyecto, el IDE asigna al proyecto archivos varios todos los elementos que no son miembros de todos los proyectos en una solución.  
  
 Proyectos desempeñan un papel importante en la determinación de qué editor se utiliza cuando un usuario abre un elemento de proyecto. Un proyecto puede diseñarse para abrir determinados archivos mediante un editor específico del proyecto o un editor estándar.  
  
 Un editor específico del proyecto normalmente requiere que el usuario tiene un conocimiento especial o usar interfaces especiales desde el proyecto. Para obtener más información, consulte [Cómo: abrir editores específica del proyecto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un editor estándar puede abrir cualquier archivo con una extensión específica en cualquier proyecto. El usuario puede personalizar algunos editores estándares, como el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor de texto, para los proyectos pero siguen conservar su carácter público. Editores estándares se crean mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método.  
  
 Si ningún proyecto de la solución responde que puede abrir un elemento de proyecto, el IDE proporciona un proyecto especial denominado el proyecto archivos varios que se abre cualquier archivo.  
  
 Este proyecto especial proporciona para abrir un archivo fuera del contexto de un proyecto. Durante el procesamiento de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método, el proyecto archivos varios siempre responde con una prioridad muy baja. Por lo tanto, el proyecto de archivos varios siempre produce a cualquier proyecto de prioridad más alta que pueda abrir archivos.  
  
 El proyecto archivos varios no requiere que el usuario que crear explícitamente con la **nuevo proyecto** cuadro de diálogo. Además, el proyecto archivos varios no administra permanentemente una lista de los miembros del proyecto. Utiliza una característica opcional para grabar una lista de archivos usados más recientemente para cada usuario.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Cómo: abrir editores específica del proyecto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)