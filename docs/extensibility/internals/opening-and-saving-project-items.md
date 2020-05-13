---
title: Apertura y ahorro de elementos de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706964"
---
# <a name="opening-and-saving-project-items"></a>Apertura y guardado de elementos de proyecto
Al agregar un nuevo tipo de proyecto, debe administrar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] apertura y el guardado de los archivos de proyectos en el entorno de desarrollo integrado (IDE). En los temas siguientes se describen los diferentes enfoques para abrir y guardar archivos.

## <a name="in-this-section"></a>En esta sección
- [Visualización de archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Proporciona una explicación paso a paso de cómo el IDE controla el comando **Abrir archivo** y el rol de los proyectos para responder a este comando.

- [Visualización de archivos mediante el comando Abrir con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Proporciona una explicación detallada paso a paso de cómo el IDE controla el comando **Abrir con,** lo que solicita la apertura de un archivo que tiene alguna opción de editores estándar.

- [Apertura de editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md)

 Proporciona instrucciones paso a paso para especificar que los archivos de un tipo determinado en el proyecto se deben abrir mediante un editor específico del proyecto.

- [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)

 Proporciona instrucciones paso a paso para especificar cómo habilitar el IDE para abrir un editor estándar para los archivos en el tipo de proyecto.

- [Apertura de editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)

 Proporciona instrucciones paso a paso para abrir un editor específico del proyecto para un archivo abierto.

- [Guardado de un documento estándar](../../extensibility/internals/saving-a-standard-document.md)

 Proporciona una explicación detallada de cómo el IDE controla los comandos **Guardar**, **Guardar como**y Guardar **todo** para un documento abierto en un editor estándar.

- [Guardado de un documento personalizado](../../extensibility/internals/saving-a-custom-document.md)

 Proporciona un diagrama y una explicación detallada de cómo el IDE controla los comandos **Guardar**, **Guardar como**y Guardar **todo** para los documentos abiertos en un editor personalizado.

- [Determinación del editor que abre un archivo en un proyecto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Describe el proceso que sigue el IDE para seleccionar el editor o diseñador adecuado para un archivo.

## <a name="related-sections"></a>Secciones relacionadas
- [Creación de diseñadores y editores personalizados](../../extensibility/creating-custom-editors-and-designers.md)

 Enumera los cuatro tipos de editores que el IDE puede hospedar y proporciona descripciones de cada editor.

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Describe cómo los proyectos controlan la forma en que se compila y compila el código, cómo se abren los editores y cómo se da formato a los elementos de proyecto.
