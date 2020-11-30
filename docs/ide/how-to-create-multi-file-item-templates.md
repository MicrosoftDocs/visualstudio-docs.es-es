---
title: Creación de plantillas de elementos de varios archivos
description: Aprenda a crear una plantilla de elemento en Visual Studio que se compone de varios archivos.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a947d23bd7094e003bae3cfe880299bb3698d92e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597267"
---
# <a name="how-to-create-multi-file-item-templates"></a>Procedimiento Crear plantillas de elemento de varios archivos

Puede que las plantillas de elementos solo especifiquen un elemento, pero a veces el elemento se compone de varios archivos. Por ejemplo, una plantilla de elemento de Windows Forms requiere los tres archivos siguientes:

- Un archivo que contiene el código del formulario.

- Un archivo que contiene la información del diseñador para el formulario.

- Un archivo que contiene los recursos incrustados del formulario.

Las plantillas de elementos de varios archivos requieren parámetros para garantizar que se usan las extensiones de archivo correctas cuando se crea el elemento. Si crea una plantilla de elemento de varios archivos mediante el **Asistente para exportar plantillas**, estos parámetros se generan automáticamente y no se requiere ninguna otra edición.

## <a name="use-the-export-template-wizard"></a>Uso del Asistente para exportar plantillas

Puede crear una plantilla de elementos de varios archivos igual que una plantilla de elemento de archivo único. Vea [Cómo: Crear plantillas de elemento](../ide/how-to-create-item-templates.md). En la página **Seleccionar elemento para exportar** del asistente, seleccione el archivo que tiene archivos dependientes (por ejemplo, un archivo de formulario de Windows Forms). El asistente incluye automáticamente en la plantilla los archivos dependientes, como el diseñador y los archivos de recursos.

## <a name="manually-create-a-multi-file-item-template"></a>Creación manual de una plantilla de elemento de varios archivos

1. Cree la plantilla de elemento igual que lo haría para crear una plantilla de elemento de archivo único, pero incluya cada archivo que compone el elemento de varios archivos.

1. En el archivo XML *.vstemplate*, agregue un elemento `ProjectItem` para cada archivo y, después, agregue un atributo `TargetFileName` a dicho elemento. Establezca el valor del atributo `TargetFileName` en *$fileinputname$.FileExtension*, donde *FileExtension* es la extensión del archivo que se incluye en la plantilla. Por ejemplo:

    ```xml
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     > [!NOTE]
     > Cuando se agrega un elemento derivado de esta plantilla a un proyecto, los nombres de archivo derivarán del nombre que el usuario escriba en el cuadro de diálogo **Agregar nuevo elemento**.

1. Seleccione los archivos que se incluirán en la plantilla, haga clic con el botón derecho en la selección y elija **Enviar a** > **Carpeta comprimida (en zip)** .

   Los archivos seleccionados se comprimen en un archivo *.zip*.

1. Copie el archivo *.zip* en la ubicación de la plantilla de elemento del usuario. De forma predeterminada, el directorio es *%USERPROFILE%\Documentos\Visual Studio \<Version\>\Templates\ItemTemplates*. Para obtener más información, vea [Cómo: Localizar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Cierre Visual Studio y vuelva a abrirlo.

1. Cree un proyecto o bien abra uno existente y, después, elija **Proyecto** > **Agregar nuevo elemento**, o bien pulse **Ctrl**+**Mayús**+**A**.

   La plantilla de elemento de varios archivos aparece en el cuadro de diálogo **Agregar nuevo elemento**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una plantilla de Windows Forms. Cuando se crea un elemento basado en esta plantilla, los nombres de los tres archivos creados coincidirán con el nombre especificado en el cuadro de diálogo **Agregar nuevo elemento**.

```xml
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Cómo: Crear plantillas de elemento](../ide/how-to-create-item-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md)
