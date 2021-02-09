---
title: Prioridad del proyecto | Microsoft Docs
description: Obtenga información sobre el esquema de prioridad que el IDE de Visual Studio usa para determinar el mejor proyecto para abrir un elemento si el elemento es miembro de más de un proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75ea6485e2ae613ca03fb3900e3e2ba9d415af95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852601"
---
# <a name="project-priority"></a>Prioridad del proyecto
Un elemento de proyecto normalmente es un miembro de un solo proyecto de la solución. Por lo tanto, el IDE puede determinar fácilmente qué proyecto se usa para abrir el elemento. Sin embargo, si un elemento es miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el mejor proyecto para abrir el elemento.

 La lista siguiente muestra el esquema de prioridad del proyecto:

- El IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> método para cada proyecto de la solución para determinar si el documento es un miembro de ese proyecto.

- Si el documento es un miembro del proyecto, el proyecto responde con una prioridad que el proyecto asigna según su control de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para los archivos de origen de idioma, pero responde con una prioridad más baja para un tipo de archivo no reconocido que no se utiliza como parte de su proceso de compilación.

- Los proyectos que proporcionan editores personalizados, específicos del proyecto o diseñadores de un documento, también reciben una prioridad alta.

- La <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración proporciona los valores de prioridad del documento.

- El proyecto que especifica la prioridad más alta recibe el contexto para abrir el documento. Si dos proyectos devuelven los mismos valores de prioridad, se prefiere el proyecto activo. Si ningún proyecto de la solución responde que puede abrir el documento, el IDE coloca el documento en el proyecto de archivos varios. Para obtener más información, vea [proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Vea también
- [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)
- [Apertura de editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
