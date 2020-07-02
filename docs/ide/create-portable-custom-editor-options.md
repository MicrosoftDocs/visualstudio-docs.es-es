---
title: Configuración de EditorConfig
ms.date: 08/01/2018
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 30c2ce8a10a6a1001f8fb7c21ba7db7db7243fe4
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770750"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig

Puede agregar un archivo [EditorConfig](https://editorconfig.org/) al proyecto o código base para aplicar estilos de codificación coherentes para todos los usuarios que trabajan en el código base. La configuración de EditorConfig tiene prioridad sobre la configuración global del editor de texto de Visual Studio. Esto significa que puede adaptar cada código base para que use la configuración del editor de texto específica para ese proyecto. Puede establecer sus propias preferencias personales del editor en el cuadro de diálogo **Opciones** de Visual Studio. Esa configuración se aplica siempre que trabaje en un código base sin un archivo *.editorconfig*, o bien cuando dicho archivo no reemplaza un valor específico *.* Un ejemplo de este tipo de preferencia es el estilo de sangría (tabuladores o espacios).

La configuración de EditorConfig es compatible con varios IDE y editores de código, incluido Visual Studio. Es un componente portátil que acompaña al código y se pueden aplicar estilos de codificación incluso fuera de Visual Studio.

::: moniker range=">=vs-2019"

Cuando se agrega un archivo EditorConfig al proyecto de Visual Studio, se aplica a las nuevas líneas de código el formato de la configuración de EditorConfig. El formato del código existente no cambia, a menos que ejecute uno de los comandos siguientes:

 - [Limpieza de código](../ide/code-styles-and-code-cleanup.md) (**Ctrl**+**K**, **Ctrl**+**E**), que aplica cualquier configuración de espacio en blanco, como el estilo de sangría, y la configuración de estilo de código seleccionada, como la manera de ordenar las directivas `using`.
 - **Editar** > **Opciones avanzadas** > **Dar formato al documento** (o **Ctrl**+**K**, **Ctrl**+**D** en el perfil predeterminado), que solo aplica la configuración de espacio en blanco, como el estilo de sangría.

 ::: moniker-end

::: moniker range="=vs-2017"

Cuando se agrega un archivo EditorConfig al proyecto de Visual Studio, se aplica a las nuevas líneas de código el formato de la configuración de EditorConfig. El formato del código existente no cambia a menos que se dé formato al documento (**Editar** > **Opciones avanzadas** > **Dar formato al documento** o **Ctrl**+**K**, **Ctrl**+**D** en el perfil predeterminado). La aplicación de formato al documento solo afecta a la configuración de espacio en blanco, como el estilo de sangría, a menos que se haya configurado la opción Dar formato al documento de modo que [realice una limpieza de código adicional](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Puede definir qué configuración de EditorConfig quiere que se aplique con **Dar formato al documento** en la página de opciones [**Formato**](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [EditorConfig en Visual Studio para Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Coherencia del código

Las opciones de configuración de los archivos EditorConfig le permiten mantener opciones y estilos de código coherentes en un código base, como el estilo de sangría, el ancho de tabulación, los caracteres de fin de línea y la codificación, entre otros, independientemente del editor o el IDE que use. Por ejemplo, al codificar en C#, si su código base tiene una convención que prefiere que las sangrías siempre consten de cinco caracteres de espacio, que los documentos usen la codificación UTF-8 y que cada línea siempre termine con un CR/LF, puede configurar un archivo *.editorconfig* para realizar esto.

Las convenciones de codificación que usa en sus proyectos personales pueden diferir de las que usa en los proyectos del equipo. Por ejemplo, puede preferir que, cuando codifique, al aplicar sangría se agregue un carácter de tabulación. En cambio, su equipo puede preferir que la aplicación de sangría agregue cuatro caracteres de espacio en lugar de un carácter de tabulación. Los archivos EditorConfig resuelven este problema permitiéndole que tenga una configuración para cada escenario.

Como las opciones de configuración se incluyen en un archivo del código base, se trasladan con este. Siempre que abra el archivo de código en un editor compatible con EditorConfig, la configuración del editor de texto se implementará. Para obtener más información sobre los archivos EditorConfig, vea el sitio web [EditorConfig.org](https://editorconfig.org/).

> [!NOTE]
> Las convenciones que se establecen en un archivo EditorConfig actualmente no se pueden aplicar en una canalización de CI/CD como advertencias o errores de compilación. Las desviaciones de estilo solo aparecen en el editor de Visual Studio y en la **lista de errores**.

## <a name="supported-settings"></a>Configuración admitida

El editor de Visual Studio admite el conjunto principal de [propiedades de EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- raíz

La configuración del editor EditorConfig se admiten en todos los lenguajes compatibles con Visual Studio excepto XML. Además, EditorConfig admite convenciones de [estilo de código](../ide/editorconfig-code-style-settings-reference.md), como [lenguaje](../ide/editorconfig-language-conventions.md) y [formato](../ide/editorconfig-formatting-conventions.md) y convenciones de [nomenclatura](../ide/editorconfig-naming-conventions.md) para C# y Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Incorporación y eliminación de los archivos EditorConfig

Cuando se agrega un archivo EditorConfig al proyecto o código base, las nuevas líneas de código que escribe se formatean según este archivo. Aun así, el hecho de agregar un archivo EditorConfig no convertirá los estilos existentes en los nuevos mientras no aplique formato al documento o ejecute la [Limpieza de código](../ide/code-styles-and-code-cleanup.md). Por ejemplo, si tiene sangrías en el archivo cuyo formato se realizó con tabulaciones y agrega un archivo EditorConfig que aplica sangrías con espacios, los caracteres de sangría no se convierten automáticamente en espacios. Cuando aplica formato al documento (**Editar** > **Opciones avanzadas** > **Dar formato al documento** o **Ctrl**+**K**, **Ctrl**+**D**), se aplica la configuración de espacio en blanco del archivo EditorConfig a las líneas de código existentes.

Si quita un archivo EditorConfig del proyecto o código base y quiere dar formato a nuevas líneas de código de acuerdo con la configuración global del editor, debe cerrar y volver a abrir los archivos de código abiertos.

### <a name="add-an-editorconfig-file-to-a-project"></a>Agregar un archivo EditorConfig a un proyecto

1. Abra un proyecto o una solución en Visual Studio. Seleccione el nodo de proyecto o solución, dependiendo de si la configuración de *.editorconfig* debería aplicarse a todos los proyectos de la solución o solamente a uno. También puede seleccionar una carpeta del proyecto o de la solución donde agregar el archivo *.editorconfig*.

1. En la barra de menús, seleccione **Proyecto** > **Agregar nuevo elemento** o presione **Ctrl**+**Mayús**+**A**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. En el cuadro de búsqueda, busque **editorconfig**.

   Se muestran dos plantillas de elemento **Archivo editorconfig** en los resultados de búsqueda.

   ![Plantillas de elemento Archivo EditorConfig en Visual Studio](media/editorconfig-item-templates.png)

1. Seleccione la plantilla **Archivo editorconfig (predeterminado)** para agregar un archivo EditorConfig rellenado previamente con dos opciones principales de EditorConfig para el estilo y el tamaño de sangría. O bien, seleccione la plantilla **Archivo editorconfig (.NET)** para agregar un archivo EditorConfig rellenado previamente con los valores predeterminados de [estilo de código. NET, formato y convenciones de nomenclatura](../ide/editorconfig-code-style-settings-reference.md).

   Aparecerá un archivo *.editorconfig* en el Explorador de soluciones y se abrirá en el editor.

   ![Archivo .editorconfig en el Explorador de soluciones y el editor](media/editorconfig-dotnet.png)

1. Edite el archivo según sea necesario.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Otras maneras de agregar un archivo EditorConfig

Hay un par de formas más de agregar un archivo EditorConfig a su proyecto:

- La [característica de inferencia de código](/visualstudio/intellicode/code-style-inference) de IntelliCode para Visual Studio infiere los estilos de código del código existente. A continuación, crea un archivo EditorConfig no vacío con sus preferencias de estilo de código ya definidas.

- A partir de Visual Studio 2019, puede [generar un archivo EditorConfig según la configuración de estilo de código](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) en **Herramientas** > **Opciones**.

## <a name="file-hierarchy-and-precedence"></a>Prioridad y jerarquía de los archivos

Cuando agrega un archivo *.editorconfig* a una carpeta en su jerarquía de archivos, su configuración se aplica en todos los archivos aplicables de ese nivel y los posteriores. También puede anular la configuración de EditorConfig para un proyecto, código base o parte de código base concretos, como una que use convenciones distintas a otras partes del código base. Esto puede ser útil al incorporar código de otro sitio sin cambiar las convenciones.

Para anular algunas configuraciones de EditorConfig o todas ellas, agregue un archivo *.editorconfig* en el nivel de la jerarquía de archivos en la que quiera que se aplique esa configuración anulada. La nueva configuración del archivo EditorConfig se aplica a los archivos que se encuentren en el mismo nivel y en cualquier subdirectorio.

![Jerarquía EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Si solo quiere anular algunos valores de configuración, pero no todos, especifique tan solo esos valores en el archivo *.editorconfig*. Solo se anularán las propiedades que indique explícitamente en el archivo de nivel inferior. Se seguirán aplicando otros valores de configuración de los archivos *.editorconfig* de nivel superior. Si quiere asegurarse de que _no_ hay ninguna configuración de _ningún_ archivo *.editorconfig* de nivel superior aplicada a esta parte del código base, agregue la propiedad ```root=true``` al archivo *.editorconfig* de nivel inferior:

```ini
# top-most EditorConfig file
root = true
```

Los archivos EditorConfig se leen de arriba abajo. Si hay varias propiedades con el mismo nombre, la prioridad la tiene la última propiedad encontrada con ese nombre.

## <a name="edit-editorconfig-files"></a>Edición de los archivos EditorConfig

Visual Studio ayuda a editar archivos *.editorconfig* proporcionando listas de finalización de IntelliSense.

![IntelliSense en un archivo .editorconfig](media/editorconfig-intellisense-no-extension.png)

Después de editar el archivo EditorConfig, deberá recargar los archivos de código para que la configuración nueva tenga efecto.

Si modifica muchos archivos *.editorconfig*, puede resultarle útil la extensión del servicio de lenguaje [EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig). Algunas de las características de esta extensión incluyen resaltado de sintaxis, IntelliSense mejorado, validación y formato de código.

![IntelliSense con la extensión de servicio de lenguaje de EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el estado de la sangría de un fragmento de código de C# antes y después de agregar un archivo *.editorconfig* al proyecto. La configuración **Tabulaciones** del cuadro de diálogo **Opciones** del editor de texto de Visual Studio se establece para producir caracteres de espacio al presionar la tecla **Tabulador**.

![Configuración de tabulaciones en el editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Como se esperaba, al presionar la tecla **Tabulador** en la línea siguiente, se aplica la sangría en la línea agregando cuatro caracteres de espacio en blanco adicionales.

![Código antes de usar EditorConfig](../ide/media/vside_editorconfig_before.png)

Agregue un nuevo archivo denominado *.editorconfig* al proyecto con el siguiente contenido. El valor `[*.cs]` significa que este cambio solo se aplica a archivos de código de C# en el proyecto.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Ahora, cuando presiona la tecla **Tabulador**, obtiene caracteres de tabulación en lugar de espacios.

![La tecla TAB agrega caracteres de tabulación](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Solución de problemas de las opciones de configuración de EditorConfig

Si hay un archivo EditorConfig en cualquier lugar de la estructura de directorios en la ubicación del proyecto o encima de esta, Visual Studio aplica al editor la configuración del editor de ese archivo. En este caso, es posible que vea el siguiente mensaje en la barra de estado:

   **"Las preferencias de usuario para este tipo de archivo se han invalidado por las convenciones de codificación de este proyecto."**

Esto significa que si los valores de configuración del editor de **Herramientas** > **Opciones** > **Editor de texto** (como el tamaño y estilo de la sangría, el tamaño de la tabulación o las convenciones de codificación) se especifican en un archivo EditorConfig en la estructura de directorios, en el proyecto o por encima de este, las convenciones del archivo EditorConfig invalidan la configuración que aparece en **Opciones**. Para controlar este comportamiento, cambie la opción **Seguir las convenciones de codificación del proyecto** en **Herramientas** > **Opciones** > **Editor de texto**. Si se desactiva la opción, se desactiva la compatibilidad con EditorConfig en Visual Studio.

![Opciones de herramientas: Seguir las convenciones de codificación del proyecto](media/coding_conventions_option.png)

Para buscar cualquier archivo *.editorconfig* en los directorios primarios, abra un símbolo del sistema y ejecute el siguiente comando desde la raíz del disco que contiene el proyecto:

```Shell
dir .editorconfig /s
```

Para controlar el ámbito de las convenciones de EditorConfig, establezca la propiedad ```root=true``` en el archivo *.editorconfig* en la raíz del repositorio o en el directorio en el que se encuentra el proyecto. Visual Studio busca un archivo denominado *.editorconfig* en el directorio del archivo abierto y en todos los directorios principales. La búsqueda finaliza cuando se llega a la ruta de acceso del archivo raíz o si se encuentra un archivo *.editorconfig* con ```root=true```.

## <a name="see-also"></a>Vea también

- [Convenciones de estilo de código de .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Compatibilidad de EditorConfig con un servicio de lenguaje](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Características del editor de código](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio para Mac)](/visualstudio/mac/editorconfig)
