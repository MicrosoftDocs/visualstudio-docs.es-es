---
title: Actualización de las plantillas de elemento de proyecto existentes
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee0118ce4181a12ca4c199b8174a28fb4b431063
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656540"
---
# <a name="how-to-update-existing-templates"></a>Procedimiento Actualizar plantillas existentes

Después de crear una plantilla y comprimir los archivos en un archivo *.zip*, es posible que desee modificarla. Puede hacerlo cambiando manualmente los archivos de la plantilla o exportando una nueva plantilla de un proyecto basado en la plantilla.

## <a name="use-the-export-template-wizard"></a>Uso del Asistente para exportar plantillas

Visual Studio proporciona un **Asistente para exportar plantillas** que se puede usar para actualizar una plantilla:

1. Elija **Archivo** > **Nuevo** > **Proyecto** de la barra de menús.

1. Seleccione la plantilla que quiere actualizar y siga los pasos para crear el proyecto.

1. Modifique el proyecto en Visual Studio. Por ejemplo, cambie el tipo de salida o agregue un nuevo archivo al proyecto.

1. En el menú **Proyecto**, elija **Exportar plantilla**.

    Se abre el **Asistente para exportar plantillas**.

1. Siga las indicaciones del asistente para exportar la plantilla como un archivo *.zip*.

1. (Opcional) Coloque el archivo *.zip* en este directorio: *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates* para que quede disponible para su selección. Tendrá que completar este paso si no ha seleccionado la opción **Importar la plantilla automáticamente en Visual Studio** del **Asistente para exportar plantillas**.

1. Elimine el archivo *.zip* de la plantilla antigua.

## <a name="manually-update-an-existing-template"></a>Actualizar manualmente una plantilla existente

Para actualizar una plantilla sin usar el **Asistente para exportar plantillas**, modifique los archivos del archivo *.zip* comprimido.

### <a name="to-manually-update-an-existing-template"></a>Para actualizar manualmente una plantilla existente

1. Busque el archivo *.zip* que contiene la plantilla. Las plantillas de proyecto del usuario están en *%USERPROFILE%\Documentos\Visual Studio \<versión\>\Templates\ProjectTemplates*.

1. Extraiga el archivo *.zip*.

1. Modifique o elimine los archivos de plantilla actuales, o agregue nuevos archivos a la plantilla.

1. Abra, modifique y guarde el archivo XML *.vstemplate* para controlar el comportamiento actualizado o los nuevos archivos.

    Para obtener más información sobre el esquema *.vstemplate*, vea [Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md). Para más información sobre lo que se puede parametrizar en los archivos de origen, vea [Parámetros de plantilla](../ide/template-parameters.md).

1. Seleccione los archivos en la plantilla y, desde el menú contextual, elija **Enviar a** > **Carpeta comprimida (en zip)** .

    Los archivos seleccionados se comprimen en un archivo *.zip*.

1. Coloque el nuevo archivo *.zip* en el mismo directorio que el antiguo.

1. Elimine los archivos de plantilla extraídos y el archivo *.zip* de plantilla antiguo.

## <a name="see-also"></a>Vea también

- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parámetros de plantilla](../ide/template-parameters.md)