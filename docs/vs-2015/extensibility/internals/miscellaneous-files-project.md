---
title: Proyecto de archivos varios | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c128475ad9f5cb71b98325bbece4e524507a08b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179783"
---
# <a name="miscellaneous-files-project"></a>Proyecto de archivos varios
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando un usuario abre elementos del proyecto, el IDE asigna al proyecto archivos varios los elementos que no son miembros de los proyectos de una solución.  
  
 Los proyectos de desempeñan un papel importante en determinar qué editor se utiliza cuando un usuario abre un elemento de proyecto. Un proyecto puede diseñarse para abrir determinados archivos con un editor específico del proyecto o un editor estándar.  
  
 Normalmente, un editor específico del proyecto requiere que el usuario tiene un conocimiento especial o usar interfaces especiales del proyecto. Para obtener más información, consulte [Cómo Apertura de editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Un editor estándar puede abrir cualquier archivo de una extensión específica en cualquier proyecto. El usuario puede personalizar algunos editores estándares, como el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor de texto, para los proyectos, pero siguen conservar su carácter público. Editores estándar se crean mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método.  
  
 Si ningún proyecto de la solución responde que puede abrir un elemento de proyecto, el IDE proporciona un proyecto especial denominado proyecto archivos varios que se abre cualquier archivo.  
  
 Este proyecto especial que se proporciona para abrir un archivo fuera del contexto de un proyecto. Durante el procesamiento de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método, el proyecto archivos varios siempre responde con una prioridad muy baja. Por lo tanto, el proyecto de archivos varios siempre produce a cualquier proyecto de mayor prioridad que pueda abrir archivos.  
  
 El proyecto archivos varios no requiere que el usuario crear explícitamente con la **nuevo proyecto** cuadro de diálogo. Además, el proyecto archivos varios no administra permanentemente una lista de los miembros del proyecto. Usa una característica opcional para grabar una lista de archivos usados más recientemente para cada usuario.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Cómo: Abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)   
 [Adición de proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
