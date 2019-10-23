---
title: Prioridad del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee4c0f41902e74f58684d6806877d352447351bf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725392"
---
# <a name="project-priority"></a>Prioridad del proyecto
Un elemento de proyecto normalmente es un miembro de un solo proyecto de la solución. Por lo tanto, el IDE puede determinar fácilmente qué proyecto se usa para abrir el elemento. Sin embargo, si un elemento es miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el mejor proyecto para abrir el elemento.

 La lista siguiente muestra el esquema de prioridad del proyecto:

- El IDE llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> para cada proyecto de la solución para determinar si el documento es un miembro de ese proyecto.

- Si el documento es un miembro del proyecto, el proyecto responde con una prioridad que el proyecto asigna según su control de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para los archivos de origen de idioma, pero responde con una prioridad más baja para un tipo de archivo no reconocido que no se utiliza como parte de su proceso de compilación.

- Los proyectos que proporcionan editores personalizados, específicos del proyecto o diseñadores de un documento, también reciben una prioridad alta.

- La enumeración <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> proporciona los valores de prioridad del documento.

- El proyecto que especifica la prioridad más alta recibe el contexto para abrir el documento. Si dos proyectos devuelven los mismos valores de prioridad, se prefiere el proyecto activo. Si ningún proyecto de la solución responde que puede abrir el documento, el IDE coloca el documento en el proyecto de archivos varios. Para obtener más información, vea [proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Vea también
- [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)
- [Apertura de editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)