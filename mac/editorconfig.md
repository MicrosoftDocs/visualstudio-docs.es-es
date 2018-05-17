---
title: EditorConfig
description: Utilizar un archivo de editorconfig para permitir estilos de codificación de proyectos coherente en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 553a8ceeae16b660115ea3c8e32e544e903a72af
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Crear y editar un archivo EditorConfig personalizado

En Visual Studio para Mac, puede agregar un archivo [EditorConfig](http://editorconfig.org/) al proyecto o código base para aplicar estilos de codificación coherentes para todos los que trabajen en el código base. La configuración declarada en el archivo de EditorConfig tiene prioridad sobre la configuración global del editor de texto de Visual Studio. Usar EditorConfig dentro del proyecto o código base le permite establecer el estilo de codificación, las preferencias y las advertencias para el proyecto. Esto facilita que todos los usuarios de Visual Studio para Mac cumplan con las prácticas de codificación de un proyecto.

Los archivos [EditorConfig](http://editorconfig.org/) son compatibles con muchos editores de código e IDE, incluido Visual Studio 2017. 

## <a name="supported-settings"></a>Configuración admitida

El editor de Visual Studio admite el conjunto principal de [propiedades de EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig también admite el [formato de estilo de código](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) en C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Agregar un archivo EditorConfig a un proyecto

### <a name="adding-a-new-editorconfig-file"></a>Agregar un nuevo archivo EditorConfig

1. Abra el proyecto en Visual Studio para Mac. Seleccione el nodo de proyecto al que quiere agregar archivos.

2. Con el nodo de proyecto seleccionado, vaya a **Archivo > Nuevo archivo...** en la barra de menús para abrir el cuadro de dialogo **Nuevo archivo**.

3. Elija **Varios > Archivo de texto vacío** y asígnele el **nombre** `.editorconfig`. Presione **Nuevo** para crear el archivo y abrirlo en el editor:

    ![Cuadro de diálogo Nuevo archivo](media/editorconfig-image1.png)

4. Edite el archivo. Por ejemplo:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Agregar el archivo no actualiza automáticamente la configuración. Para reflejar la configuración del archivo `.editorconfig`, seleccione el nodo del proyecto y elija **Editar > Formato > Dar formato al documento** desde la barra de menús:

    ![Elemento de menú Dar formato al documento](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Agregar un archivo de EditorConfig existente

Si está trabajando con un proyecto o solución que ya contiene un archivo `.editorconfig`, no debe hacer nada para aplicar la configuración. A las nuevas líneas de código se les aplicará formato según la configuración de EditorConfig. Tenga en cuenta que mientras Visual Studio para Mac respetará los archivos `.editorconfig` en el nivel de solución, podrían no aparecer en el panel de solución porque los archivos que comienzan por `.` son archivos ocultos en macOS.

Puede que quiera reutilizar un archivo `.editorconfig` existente en su proyecto. Para agregar un archivo existente, primero debe mostrar los archivos ocultos en Finder escribiendo el comando siguiente en **Terminal**:

```
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

Una vez que el archivo `.editorconfig` es visible, arrástrelo hasta el nodo del proyecto. Cuando se le presenta el siguiente cuadro de diálogo, seleccione la opción **Copy the file to the directory** (Copiar el archivo en el directorio) y seleccione **Aceptar**:

![Elemento de menú Dar formato al documento](media/editorconfig-image3.png)

Para reflejar la configuración del archivo `.editorconfig`, seleccione el nodo del proyecto y elija **Editar > Formato > Dar formato al documento** desde la barra de menús.

## <a name="editing-an-editorconfig-file"></a>Edición de un archivo EditorConfig

Los archivos de EditorConfig usan un diseño de archivo sencillo para especificar la configuración, lo cual se explica a continuación usando un ejemplo anterior:


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Al establecer `root` en `true` se marcará este archivo como el archivo de nivel superior del código base y los archivos de `.editorconfig` posteriores del proyecto se pasarán por alto, como se explica en la sección [Invalidar la configuración de EditorConfig](#override-editorconfig-settings).

Cada sección se indica mediante corchetes (**[]**) y especifica información sobre los tipos de archivos a los que deberían pertenecer las siguientes propiedades.

En el ejemplo anterior, algunos valores se aplican a todos los archivos del proyecto y otros se agregan solo a los archivos de C#. Las siguientes capturas de pantalla muestran el antes y el después de que se aplique la configuración de `.editorconfig`:

**Antes**:

![Antes de que se aplique la configuración de editorconfig](media/editorconfig-image4.png)

**Después**:

![después de que se aplique la configuración de editorconfig](media/editorconfig-image5.png)

Para obtener más información sobre la configuración de EditorConfig disponible, vea el artículo [Configuración de la convención de codificación de .NET para EditorConfig](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) y la sección [Supported Properties](http://editorconfig.org/#supported-properties) (Propiedades admitidas) en la documentación oficial.

## <a name="override-editorconfig-settings"></a>Invalidar la configuración de EditorConfig

Es posible que haya más de un archivo `.editorconfig` en cada solución. Visual Studio para Mac lee archivos `.editorconfig` de arriba hacia abajo en la solución, y agrega y reemplaza la configuración a medida que avanza. Esto significa que la configuración del `.editorconfig` _más cercano_ al archivo que está editando tendrá prioridad. 

Si quiere asegurarse de que _no_ hay ninguna configuración de ningún archivo `.editorconfig` de nivel superior aplicada a esta parte del código base, agregue la propiedad `root=true` al inicio del archivo `.editorconfig` de nivel inferior:

```EditorConfig
# top-most EditorConfig file
root = true
```