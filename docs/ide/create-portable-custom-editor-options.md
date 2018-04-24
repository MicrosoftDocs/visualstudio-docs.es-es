---
title: Uso de la configuración EditorConfig en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 12/13/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-general
ms.openlocfilehash: fe1653df6fc1d71dc4497c6e7e0a9adae9fa0b44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig

En Visual Studio 2017, puede agregar un archivo [EditorConfig](http://editorconfig.org/) al proyecto o código base para aplicar estilos de codificación coherentes para todos los que trabajen en el código base. La configuración de EditorConfig tiene prioridad sobre la configuración global del editor de texto de Visual Studio. Esto significa que puede adaptar cada código base para que use la configuración del editor de texto específica para ese proyecto. Puede establecer sus propias preferencias personales del editor en el cuadro de diálogo **Opciones** de Visual Studio. Esa configuración se aplica siempre que trabaje en un código base sin un archivo *.editorconfig*, o bien cuando dicho archivo no reemplaza un valor específico *.* Un ejemplo de este tipo de preferencia es el estilo de sangría (tabuladores o espacios).

La configuración de EditorConfig es compatible con varios IDE y editores de código, incluido Visual Studio. Es un componente portátil que acompaña al código y se pueden aplicar estilos de codificación incluso fuera de Visual Studio.

> [!NOTE]
> Cuando se agrega un archivo EditorConfig al proyecto en Visual Studio, el formato del código existente no cambia a menos que se dé formato al documento (**Editar** > **Opciones avanzadas**  >  **Dar formato al documento** o **Ctrl**+**K**, **Ctrl**+**D**). Pero a las nuevas líneas de código se les aplicará formato según la configuración de EditorConfig.

## <a name="coding-consistency"></a>Coherencia del código

Las opciones de configuración de los archivos EditorConfig le permiten mantener opciones y estilos de código coherentes en un código base, como el estilo de sangría, el ancho de tabulación, los caracteres de fin de línea y la codificación, entre otros, independientemente del editor o el IDE que use. Por ejemplo, al codificar en C#, si su código base tiene una convención que prefiere que las sangrías siempre consten de cinco caracteres de espacio, que los documentos usen la codificación UTF-8 y que cada línea siempre termine con un CR/LF, puede configurar un archivo *.editorconfig* para realizar esto.

Las convenciones de codificación que usa en sus proyectos personales pueden diferir de las que usa en los proyectos del equipo. Por ejemplo, puede preferir que, cuando codifique, al aplicar sangría se agregue un carácter de tabulación. En cambio, su equipo puede preferir que la aplicación de sangría agregue cuatro caracteres de espacio en lugar de un carácter de tabulación. Los archivos EditorConfig resuelven este problema permitiéndole que tenga una configuración para cada escenario.

Como las opciones de configuración se incluyen en un archivo del código base, se trasladan con este. Siempre que abra el archivo de código en un editor compatible con EditorConfig, la configuración del editor de texto se implementará. Para obtener más información sobre los archivos EditorConfig, vea el sitio web [EditorConfig.org](http://editorconfig.org/).

## <a name="supported-settings"></a>Configuración admitida

El editor de Visual Studio admite el conjunto principal de [propiedades de EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- raíz

La configuración del editor EditorConfig se admiten en todos los lenguajes compatibles con Visual Studio excepto XML. Además, EditorConfig es compatible con las convenciones de [estilo de código](../ide/editorconfig-code-style-settings-reference.md) y de [nomenclatura](../ide/editorconfig-naming-conventions.md) para C# y Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Incorporación y eliminación de los archivos EditorConfig

Agregar un archivo EditorConfig al proyecto o código base no convierte los estilos existentes en los nuevos. Por ejemplo, si tiene sangrías en el archivo cuyo formato se realizó con tabulaciones y agrega un archivo EditorConfig que aplica sangrías con espacios, los caracteres de sangría no se convierten automáticamente en espacios. Pero a las nuevas líneas de código se les aplicará formato según lo estipulado en el archivo EditorConfig. Además, si se aplica formato al documento (**Editar** > **Opciones avanzadas** > **Dar formato al documento** o **Ctrl** + **K**, **Ctrl**+**D**), se aplica la configuración del archivo EditorConfig a las líneas de código existentes.

Si quita un archivo EditorConfig del proyecto o código base, debe cerrar y volver a abrir todo archivo de código abierto para revertir la configuración global del editor para las nuevas líneas de código.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Para agregar un archivo EditorConfig a un proyecto o una solución

1. Abra un proyecto o una solución en Visual Studio. Seleccione el nodo de proyecto o solución, dependiendo de si la configuración de *.editorconfig* debería aplicarse a todos los proyectos de la solución o solamente a uno. También puede seleccionar una carpeta del proyecto o de la solución donde agregar el archivo *.editorconfig*.

1. En la barra de menús, seleccione **Proyecto** > **Agregar nuevo elemento...** o pulse **Ctrl**+**Mayús**+**A**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. En las categorías de la parte izquierda, seleccione **General** y seleccione la plantilla **Archivo de texto**. En el cuadro de texto **Nombre**, indique `.editorconfig` y seleccione **Agregar**.

   Aparecerá un archivo *.editorconfig* en el Explorador de soluciones y se abrirá en el editor.

   ![Archivo .editorconfig en el Explorador de soluciones](media/editorconfig-in-solution-explorer.png)

1. Edite el archivo como quiera, por ejemplo:

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

Como alternativa, puede instalar la [extensión de servicio de lenguaje de EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig). Después de instalar la extensión, seleccione **Agregar** > **Archivo .editorconfig** en el menú contextual o de botón derecho del nodo de solución, nodo de proyecto o cualquier carpeta del Explorador de soluciones.

![Agregar un archivo .editorconfig con extensión](media/editorconfig-extension-add.png)

## <a name="override-editorconfig-settings"></a>Invalidar la configuración de EditorConfig

Cuando agrega un archivo *.editorconfig* a una carpeta en su jerarquía de archivos, su configuración se aplica en todos los archivos aplicables de ese nivel y los posteriores. También puede anular la configuración de EditorConfig para un proyecto, código base o parte de código base concretos, como una que use convenciones distintas a otras partes del código base. Esto puede ser útil al incorporar código de otro sitio sin cambiar las convenciones.

Para anular algunas configuraciones de EditorConfig o todas ellas, agregue un archivo *.editorconfig* en el nivel de la jerarquía de archivos en la que quiera que se aplique esa configuración anulada. La nueva configuración del archivo EditorConfig se aplica a los archivos que se encuentren en el mismo nivel y en cualquier subdirectorio.

![Jerarquía EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Si solo quiere anular algunos valores de configuración, pero no todos, especifique tan solo esos valores en el archivo *.editorconfig*. Solo se anularán las propiedades que indique explícitamente en el archivo de nivel inferior. Se seguirán aplicando otros valores de configuración de los archivos *.editorconfig* de nivel superior. Si quiere asegurarse de que _no_ hay ninguna configuración de _ningún_ archivo *.editorconfig* de nivel superior aplicada a esta parte del código base, agregue la propiedad ```root=true``` al archivo *.editorconfig* de nivel inferior:

```EditorConfig
# top-most EditorConfig file
root = true
```

Los archivos EditorConfig se leen de arriba abajo. Los archivos EditorConfig más cercanos son los últimos en leerse. Se aplican convenciones de las secciones de EditorConfig coincidentes en el orden en que se leyeron, por lo que las convenciones de los archivos más cercanos tienen prioridad.

## <a name="editing-editorconfig-files"></a>Edición de los archivos EditorConfig

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

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Ahora, cuando presiona la tecla **Tabulador**, obtiene caracteres de tabulación en lugar de espacios.

![La tecla TAB agrega caracteres de tabulación](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Solucionar problemas de las opciones de configuración de EditorConfig

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

[Convenciones de estilo de código de .NET](../ide/editorconfig-code-style-settings-reference.md)  
[Convenciones de nomenclatura .NET](../ide/editorconfig-naming-conventions.md)  
[Compatibilidad de EditorConfig con un servicio de lenguaje](../extensibility/supporting-editorconfig.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Escribir código en el editor](writing-code-in-the-code-and-text-editor.md)
