---
title: Prioridad del proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b012136c30f72cfdddadfc1a370ed76f567afffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429917"
---
# <a name="project-priority"></a>Prioridad del proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un elemento de proyecto normalmente es un miembro de un solo proyecto de la solución. Por lo tanto, el IDE puede determinar fácilmente qué proyecto se usa para abrir el elemento. Sin embargo, si un elemento es miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el mejor proyecto para abrir el elemento.  
  
 La lista siguiente muestra el esquema de prioridad del proyecto:  
  
- El IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> método para cada proyecto de la solución para determinar si el documento es un miembro de ese proyecto.  
  
- Si el documento es un miembro del proyecto, el proyecto responde con una prioridad que el proyecto asigna según su control de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para los archivos de origen de idioma, pero responde con una prioridad más baja para un tipo de archivo no reconocido que no se utiliza como parte de su proceso de compilación.  
  
- Los proyectos que proporcionan editores personalizados, específicos del proyecto o diseñadores de un documento, también reciben una prioridad alta.  
  
- La <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración proporciona los valores de prioridad del documento.  
  
- El proyecto que especifica la prioridad más alta recibe el contexto para abrir el documento. Si dos proyectos devuelven los mismos valores de prioridad, se prefiere el proyecto activo. Si ningún proyecto de la solución responde que puede abrir el documento, el IDE coloca el documento en el proyecto de archivos varios. Para obtener más información, vea [proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Consulte también  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)   
 [Cómo: abrir editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
