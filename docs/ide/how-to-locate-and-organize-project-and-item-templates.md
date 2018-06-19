---
title: Organización de plantillas en Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65d4940e7a7969fe28fe115ec7ef42cfdc645c9a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948735"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Cómo: Localizar y organizar plantillas de proyecto y de elemento

Los archivos de plantilla se deben colocar en una ubicación que Visual Studio reconozca de forma que estas aparezcan en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**. También puede crear subcategorías personalizadas en la ubicación de la plantilla de usuario, y las categorías se muestran en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**.

## <a name="locate-templates"></a>Ubicación de plantillas

Las plantillas instaladas y las plantillas de usuario se almacenan en dos ubicaciones distintas.

### <a name="user-templates"></a>Plantillas de usuario

Si agrega un archivo comprimido (*.zip*) que incluye un archivo *.vstemplate* al directorio de plantillas de usuario, la plantilla aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**. De manera predeterminada, las plantillas de usuario se encuentran en:

- *%USERPROFILE%\Documentos\Visual Studio \<Versión\>\Templates\ProjectTemplates*

- *%USERPROFILE%\Documenots\Visual Studio \<Versión\>\Templates\ItemTemplates*

Por ejemplo, el siguiente directorio contiene las plantillas de proyecto de usuario para C#:

- *C:\Usuarios\NombreDeUsuario\Documentos\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

> [!TIP]
> Puede establecer la ubicación de las plantillas de usuario en **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Ubicaciones**.

### <a name="installed-templates"></a>Plantillas instaladas

De manera predeterminada, las plantillas que se instalan con Visual Studio se encuentran en:

- *\\< directorioDeInstalaciónDeVisualStudio\>\Common7\IDE\ItemTemplates\\<Lenguade de programación\>\\<Locale ID>*

- *\\< directorioDeInstalaciónDeVisualStudio\>\Common7\IDE\ProjectTemplates\\<Lenguade de programación\>\\<Locale ID>*

Por ejemplo, el directorio siguiente contiene las plantillas de elemento de Visual Basic para inglés (LCID 1033):

- *C:\\< directorioDeInstalaciónDeVisualStudio\>\Common7\IDE\ItemTemplates\VisualBasic\1033*

## <a name="organize-templates"></a>Organización de plantillas

Las categorías de los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** reflejan las estructuras de directorios que existen en las ubicaciones de plantillas instaladas y de usuario. Las plantillas de usuario se pueden organizar en sus propias categorías agregando nuevas carpetas en el directorio de las plantillas de usuario. Los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** muestran todos los cambios que se realizan en las categorías de plantillas.

> [!NOTE]
> No puede crear una nueva categoría en el nivel del lenguaje de programación. Solo se pueden crear categorías nuevas dentro de cada lenguaje.

### <a name="to-create-new-user-project-template-categories"></a>Para crear nuevas categorías de plantillas de proyecto de usuario

1. Cree una carpeta en la carpeta del lenguaje de programación del directorio de plantillas de proyecto de usuario. Por ejemplo, para establecer una categoría **HolaMundo** para plantillas de proyecto de C#, cree el siguiente directorio:

    - *\%USERPROFILE%\Documentos\Visual Studio \<Versión\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Coloque todas las plantillas de esta categoría en la nueva carpeta.

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

   La categoría **HolaMundo** aparecerá en el cuadro de diálogo **Nuevo proyecto**, en **Instalado** > **Visual C#**.

### <a name="to-create-new-user-item-template-categories"></a>Para crear nuevas categorías de plantillas de elemento de usuario

1. Cree una carpeta en la carpeta del lenguaje de programación del directorio de plantillas de elemento de usuario. Por ejemplo, para establecer una categoría **HolaMundo** para plantillas de elemento de C#, cree el siguiente directorio:

    - *\%USERPROFILE%\Documentos\Visual Studio \<Versión\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Coloque todas las plantillas de esta categoría en la nueva carpeta.

1. Cree un proyecto o abra uno existente. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

   La categoría **HolaMundo** aparecerá en el cuadro de diálogo **Agregar nuevo elemento**, en **Instalado** > **Elementos de Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Visualización de plantillas en categorías primarias

Puede permitir que las plantillas contenidas en subcategorías se muestren en sus categorías primarias utilizando el elemento `NumberOfParentCategoriesToRollUp` en el archivo *.vstemplate*. Estos pasos son idénticos para plantillas de proyecto y plantillas de elemento.

#### <a name="to-display-templates-in-parent-categories"></a>Para mostrar las plantillas en categorías primarias

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

1. Seleccione los archivos de la plantilla, haga clic con el botón derecho en la selección y elija **Enviar a** > **Carpeta comprimida (en zip)**.

   Los archivos se comprimen en un archivo *.zip*.

1. Elimine los archivos de plantilla extraídos y el archivo *.zip* de plantilla antiguo.

1. Coloque el nuevo archivo *.zip* en el directorio que contenía el archivo *.zip* eliminado.

## <a name="see-also"></a>Vea también

- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Plantillas de Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)