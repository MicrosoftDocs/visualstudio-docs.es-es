---
title: EditorConfig
description: Utilizar un archivo de editorconfig para permitir estilos de codificación de proyectos coherente en Visual Studio para Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: be8f508a0055d4cd7cbacf1c728e6d73c8b281f7
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984721"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Crear y editar un archivo EditorConfig personalizado

En Visual Studio para Mac, puede agregar un archivo [EditorConfig](https://editorconfig.org/) al proyecto o la solución para aplicar estilos de codificación coherentes para todos los que trabajen en el código base. La configuración declarada en el archivo EditorConfig tiene prioridad sobre la configuración global del editor de texto de Visual Studio para Mac. Usar un archivo EditorConfig dentro del proyecto o código base le permite establecer el estilo de codificación, las preferencias y las advertencias para el proyecto. Dado que el archivo forma parte del código base, es más fácil que todos los usuarios respeten las prácticas de codificación de un proyecto, independientemente del editor de código o IDE que usen.

Los archivos [EditorConfig](https://editorconfig.org/) son compatibles con muchos editores de código e IDE, incluido Visual Studio 2017.

## <a name="supported-settings"></a>Configuración admitida

El editor de Visual Studio para Mac admite el conjunto principal de [propiedades de EditorConfig](https://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

El archivo EditorConfig también admite las [convenciones de codificación](/visualstudio/ide/editorconfig-code-style-settings-reference) en C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Agregar un archivo EditorConfig a un proyecto

### <a name="adding-a-new-editorconfig-file"></a>Agregar un nuevo archivo EditorConfig

1. Abra el proyecto en Visual Studio para Mac. Seleccione el nodo de la solución o el proyecto al que quiere agregar el archivo EditorConfig. Al agregar el archivo al directorio de la solución se aplica la configuración de .editorconfig a todos los proyectos de la solución.

2. Haga clic con el botón derecho en el nodo y seleccione **Agregar > Nuevo archivo** para abrir el cuadro de diálogo **Nuevo archivo**:

    ![Elementos de menú Contenido](media/editorconfig-image0.png)

3. Elija **Varios > Archivo de texto vacío** y asígnele el **nombre** `.editorconfig`. Presione **Nuevo** para crear el archivo y abrirlo en el editor:

    ![Cuadro de diálogo Nuevo archivo](media/editorconfig-image1.png)

    Al agregar el elemento en el nivel de solución se crea automáticamente y se anida en una carpeta **Elementos de la solución**:

    ![Elemento de solución mostrado en el Panel de solución](media/editorconfig-image1a.png)

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

4. La configuración del archivo `.editorconfig` se aplicará a cualquier código nuevo que escriba, pero puede que sea necesario cambiar el formato del código existente para que sea coherente con la nueva configuración. Para aplicar la configuración del archivo `.editorconfig` en un archivo de origen existente, abra el archivo y elija **Editar > Formato > Dar formato al documento** desde la barra de menús:

    ![Elemento de menú Dar formato al documento](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Agregar un archivo de EditorConfig existente

Si está trabajando con un proyecto o solución que ya contiene un archivo `.editorconfig`, no debe hacer nada para aplicar la configuración. A las nuevas líneas de código se les aplicará formato según la configuración de EditorConfig.

Puede que quiera reutilizar un archivo `.editorconfig` existente en su proyecto. Para agregar un archivo existente, realice lo siguiente:

1. Haga clic con el botón derecho en la carpeta donde quiere agregarlo y seleccione **Agregar > Agregar archivos**.

2. Vaya al directorio del archivo necesario.

3. Los archivos que empiezan por `.` (como `.editorconfig`) son archivos ocultos en macOS, así que presione **comando + Mayús + .** para que el archivo `.editorconfig` esté visible.

4. Seleccione el archivo `.editorconfig` y haga clic en **Abrir**:

    ![Adición de un nuevo campo](media/editorconfig-image3b.png)

5. Cuando se le presenta el siguiente cuadro de diálogo, seleccione la opción **Copy the file to the directory** (Copiar el archivo en el directorio) y seleccione **Aceptar**:

    ![Opciones del cuadro de diálogo Add file to folder (Agregar archivo a carpeta)](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Reflejo de la configuración de .editorconfig

Una vez que agregue un archivo EditorConfig en la base de código, automáticamente se aplicará formato a cualquier código nuevo que se agregue, en función de la configuración especificada. El código existente no refleja automáticamente la configuración a menos que aplique formato al código base.

Para reflejar la configuración del archivo `.editorconfig`, seleccione el nodo de la solución y elija **Editar > Formato > Dar formato al documento** desde la barra de menús:

![Dar formato al documento en la barra de menús](media/editorconfig-image3a.png)

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

Al establecer `root` en `true`, se marca este archivo como el archivo de nivel superior del código base y los archivos de `.editorconfig` posteriores del proyecto se pasan por alto, como se ha explicado en la sección [Invalidar la configuración de EditorConfig](#override-editorconfig-settings).

Cada sección se indica mediante corchetes ( **[]** ) y especifica información sobre los tipos de archivos a los que deberían pertenecer las siguientes propiedades.

En el ejemplo anterior, algunos valores se aplican a todos los archivos del proyecto y otros se agregan solo a los archivos de C#. Las siguientes capturas de pantalla muestran el antes y el después de que se aplique la configuración de `.editorconfig`:

**Antes**:

![Antes de que se aplique la configuración de editorconfig](media/editorconfig-image4.png)

**Después**:

![después de que se aplique la configuración de editorconfig](media/editorconfig-image5.png)

Para obtener más información sobre la configuración de EditorConfig disponible, vea el artículo [Configuración de la convención de codificación de .NET para EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) y la sección [Supported Properties](https://editorconfig.org/#supported-properties) (Propiedades admitidas) en la documentación oficial.

## <a name="override-editorconfig-settings"></a>Invalidar la configuración de EditorConfig

Es posible que haya más de un archivo `.editorconfig` en cada solución. Visual Studio para Mac lee los archivos `.editorconfig` de arriba a abajo en la solución, y agrega y reemplaza valores de configuración sobre la marcha. Esto significa que la configuración en `.editorconfig` _más cercana_ al archivo que está editando tendrá prioridad. Se toma la configuración del archivo `.editorconfig` de la misma carpeta (si existe), y luego `.editorconfig` en la carpeta primaria (si existe), etcétera, hasta que encuentra `root=true`.

Si quiere asegurarse de que _no_ hay ninguna configuración de ningún archivo `.editorconfig` de nivel superior aplicada a esta parte del código base, agregue la propiedad `root=true` al inicio del archivo `.editorconfig` de nivel inferior:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Vea también

- [Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig (Visual Studio en Windows)](/visualstudio/ide/create-portable-custom-editor-options)