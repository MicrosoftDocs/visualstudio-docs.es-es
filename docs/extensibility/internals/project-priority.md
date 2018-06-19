---
title: Prioridad del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27341f78fb17fa5346a9dfbc7cdd3f86439d3d23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130885"
---
# <a name="project-priority"></a>Prioridad del proyecto
Normalmente, un elemento de proyecto es un miembro de un único proyecto de la solución. Por lo tanto, el IDE puede determinar con facilidad qué proyecto se utiliza para abrir el elemento. Sin embargo, si un elemento es un miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el proyecto recomendado para abrir el elemento.  
  
 En la lista siguiente se muestra el esquema de prioridades del proyecto:  
  
-   Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> método para cada proyecto de la solución para determinar si el documento es un miembro de ese proyecto.  
  
-   Si el documento es un miembro del proyecto, el proyecto responde con una prioridad que el proyecto se asigna según su propio control de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para sus archivos de origen de idioma, pero responde con una prioridad más baja para un tipo de archivo no reconocido que no se utiliza como parte de su proceso de compilación.  
  
-   Proyectos que proporcionan personalizados y específica del proyecto editores o diseñadores de un documento también reciben una prioridad alta.  
  
-   El <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración proporciona valores de prioridad de documento.  
  
-   El proyecto que especifica la prioridad más alta se proporciona el contexto para abrir el documento. Si dos proyectos devuelven valores de igual prioridad, es preferible el proyecto activo. Si ningún proyecto de la solución responde que puede abrir el documento, el IDE pone el documento en el proyecto archivos varios. Para obtener más información, consulte [proyecto archivos varios](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Vea también  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)   
 [Cómo: abrir editores para los documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)