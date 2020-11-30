---
title: Ubicación de plantillas
description: Aprenda a localizar y organizar plantillas de proyecto y elemento.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 517918bf7e56381a4d4d2a36fc43f976a07c29ea
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597163"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Procedimiento Buscar y organizar plantillas de proyecto y elemento

Los archivos de plantilla se deben colocar en una ubicación conocida para que se muestren en los cuadros de diálogo de nuevo proyecto y de nuevo elemento.

::: moniker range="vs-2017"

También puede crear subcategorías personalizadas en la ubicación de la plantilla de usuario, y las categorías se muestran en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**.

::: moniker-end

## <a name="locate-templates"></a>Ubicación de plantillas

Las plantillas instaladas y las plantillas de usuario se almacenan en dos ubicaciones distintas.

### <a name="installed-templates"></a>Plantillas instaladas

De manera predeterminada, las plantillas que se instalan con Visual Studio se encuentran en:

::: moniker range="vs-2017"

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2017\\\<edition>\\Common7\IDE\ProjectTemplates\\<Idioma\>\\<Id. de configuración regional\>*

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2017\\\<edition>\Common7\IDE\ItemTemplates\\<Idioma\>\\<Id. de configuración regional\>*

Por ejemplo, el directorio siguiente contiene las plantillas de elemento de Visual Basic para inglés (LCID 1033):

*C:\\Archivos de programa (x86)\\Microsoft Visual Studio\\2017\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2019\\\<edition>\\Common7\IDE\ProjectTemplates\\<Idioma\>\\<Id. de configuración regional\>*

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2019\\\<edition>\Common7\IDE\ItemTemplates\\<Idioma\>\\<Id. de configuración regional\>*

Por ejemplo, el directorio siguiente contiene las plantillas de elemento de Visual Basic para inglés (LCID 1033):

*C:\\Archivos de programa (x86)\\Microsoft Visual Studio\\2019\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>Plantillas de usuario

Si agrega un archivo comprimido ( *.zip*) que incluye un archivo *.vstemplate* al directorio de plantillas de usuario, la plantilla aparece en los cuadros de diálogo de nuevo proyecto y de nuevo elemento. De manera predeterminada, las plantillas de usuario se encuentran en:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*

Por ejemplo, el siguiente directorio contiene las plantillas de proyecto de usuario para C#:

- *C:\Usuarios\NombreDeUsuario\Documentos\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

Por ejemplo, el siguiente directorio contiene las plantillas de proyecto de usuario para C#:

- *C:\Users\UserName\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C#*

::: moniker-end

> [!TIP]
> Puede cambiar la ubicación conocida de las plantillas de usuario en **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Ubicaciones**.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Organización de plantillas

Las categorías de los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** reflejan las estructuras de directorios que existen en las ubicaciones de plantillas instaladas y de usuario. Las plantillas de usuario se pueden organizar en sus propias categorías agregando nuevas carpetas en el directorio de las plantillas de usuario. Los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** muestran todos los cambios que se realizan en las categorías de plantillas.

> [!NOTE]
> No puede crear una nueva categoría en el nivel del lenguaje de programación. Solo se pueden crear categorías nuevas dentro de cada lenguaje.

### <a name="create-new-user-project-template-categories"></a>Creación de categorías de plantillas de proyecto de usuario

1. Cree una carpeta en la carpeta del lenguaje de programación del directorio de plantillas de proyecto de usuario. Por ejemplo, para establecer una categoría **HolaMundo** para plantillas de proyecto de C#, cree el siguiente directorio:

    - *\%USERPROFILE%\Documentos\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Coloque todas las plantillas de esta categoría en la nueva carpeta.

1. En el menú **Archivo**, elija **Nuevo** > **Proyecto**.

   La categoría **HelloWorld** aparecerá en el cuadro de diálogo **Nuevo proyecto**, en **Instalado** > **Visual C#** .

### <a name="create-new-user-item-template-categories"></a>Creación de categorías de plantillas de elemento de usuario

1. Cree una carpeta en la carpeta del lenguaje de programación del directorio de plantillas de elemento de usuario. Por ejemplo, para establecer una categoría **HolaMundo** para plantillas de elemento de C#, cree el siguiente directorio:

    - *\%USERPROFILE%\Documentos\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Coloque todas las plantillas de esta categoría en la nueva carpeta.

1. Cree un proyecto o abra uno existente. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

   La categoría **HelloWorld** aparecerá en el cuadro de diálogo **Agregar nuevo elemento**, en **Instalado** > **Elementos de Visual C#** .

### <a name="display-templates-in-parent-categories"></a>Visualización de plantillas en categorías primarias

Puede permitir que las plantillas contenidas en subcategorías se muestren en sus categorías primarias utilizando el elemento `NumberOfParentCategoriesToRollUp` en el archivo *.vstemplate*. Estos pasos son idénticos para plantillas de proyecto y plantillas de elemento.

1. Busque el archivo *.zip* que contiene la plantilla.

1. Extraiga el archivo *.zip*.

1. Abra el archivo *.vstemplate* en Visual Studio.

1. En el elemento `TemplateData`, agregue un elemento `NumberOfParentCategoriesToRollUp`. Por ejemplo, el código siguiente hace que la plantilla esté visible en la categoría primaria, pero no en los niveles superiores.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Guarde y cierre el archivo *.vstemplate*.

1. Seleccione los archivos de la plantilla, haga clic con el botón derecho en la selección y elija **Enviar a** > **Carpeta comprimida (en zip)** .

   Los archivos se comprimen en un archivo *.zip*.

1. Elimine los archivos de plantilla extraídos y el archivo *.zip* de plantilla antiguo.

1. Coloque el nuevo archivo *.zip* en el directorio que contenía el archivo *.zip* eliminado.

::: moniker-end

## <a name="see-also"></a>Vea también

- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Plantillas de Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Cómo: Crear plantillas de elemento](../ide/how-to-create-item-templates.md)
