---
title: "Uso de la configuración EditorConfig en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload: multiple
ms.openlocfilehash: 0219ff704e22ab1c27d47e312825a66cb3a15166
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig

En Visual Studio 2017, puede agregar un archivo [EditorConfig](http://editorconfig.org/) al proyecto o código base para aplicar estilos de codificación coherentes para todos los que trabajen en el código base. La configuración de EditorConfig tiene prioridad sobre la configuración global del editor de texto de Visual Studio. Esto significa que puede adaptar cada código base para que use la configuración del editor de texto específica para ese proyecto. Puede establecer sus propias preferencias personales del editor en el cuadro de diálogo **Opciones** de Visual Studio. Esa configuración se aplica siempre que trabaje en un código base sin un archivo .editorconfig, o bien cuando este no reemplaza un valor específico. Un ejemplo de este tipo de preferencia es el estilo de sangría (tabuladores o espacios).

La configuración de EditorConfig es compatible con varios IDE y editores de código, incluido Visual Studio. Es un componente portátil que acompaña al código y se pueden aplicar estilos de codificación incluso fuera de Visual Studio.

## <a name="coding-consistency"></a>Coherencia del código

Las opciones de configuración de los archivos EditorConfig le permiten mantener opciones y estilos de código coherentes en un código base, como el estilo de sangría, el ancho de tabulación, los caracteres de fin de línea y la codificación, entre otros, independientemente del editor o el IDE que use. Por ejemplo, al codificar en C#, si su código base tiene una convención que prefiere que las sangrías siempre consten de cinco caracteres de espacio, que los documentos usen la codificación UTF-8 y que cada línea siempre termine con un CR/LF, puede configurar un archivo .editorconfig para realizar esto.

Las convenciones de codificación que usa en sus proyectos personales pueden diferir de las que usa en los proyectos del equipo. Por ejemplo, puede preferir que, cuando codifique, al aplicar sangría se agregue un carácter de tabulación. En cambio, su equipo puede preferir que la aplicación de sangría agregue cuatro caracteres de espacio en lugar de un carácter de tabulación. Los archivos EditorConfig resuelven este problema permitiéndole que tenga una configuración para cada escenario.

Como las opciones de configuración se incluyen en un archivo del código base, se trasladan con este. Siempre que abra el archivo de código en un editor compatible con EditorConfig, la configuración del editor de texto se implementará. Para obtener más información sobre los archivos EditorConfig, vea el sitio web [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Invalidar la configuración de EditorConfig

Cuando agrega un archivo .editorconfig a una carpeta en su jerarquía de archivos, su configuración se aplica en todos los archivos aplicables de ese nivel y los posteriores. Para invalidar las opciones de configuración de EditorConfig para un código base o un proyecto concreto de modo que use convenciones diferentes a las del archivo EditorConfig de nivel superior, agregue un archivo .editorconfig a la raíz del repositorio o el directorio de proyecto del código base. Asegúrese de colocar la propiedad ```root=true``` en el archivo de manera que Visual Studio no busque los archivos .editorconfig hacia los niveles superiores de la estructura de directorios. La nueva configuración del archivo EditorConfig se aplica a los archivos que se encuentren en el mismo nivel y en cualquier subdirectorio.

```
# top-most EditorConfig file
root = true
```

![Jerarquía EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Los archivos EditorConfig se leen de arriba abajo. Los archivos EditorConfig más cercanos son los últimos en leerse. Se aplican convenciones de las secciones de EditorConfig coincidentes en el orden en que se leyeron, por lo que las convenciones de los archivos más cercanos tienen prioridad.

## <a name="supported-settings"></a>Configuración admitida

El editor de Visual Studio admite las siguientes propiedades del conjunto principal de [propiedades de EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- raíz

La configuración del editor EditorConfig se admiten en todos los lenguajes compatibles con Visual Studio excepto XML. Además, EditorConfig es compatible con las convenciones de [estilo de código](../ide/editorconfig-code-style-settings-reference.md) y de [nomenclatura](../ide/editorconfig-naming-conventions.md) para C# y Visual Basic.

## <a name="editing-editorconfig-files"></a>Edición de los archivos EditorConfig

Visual Studio proporciona IntelliSense limitado para editar archivos .editorconfig. Si modifica muchos archivos .editorconfig, puede resultarle útil la extensión del [servicio de lenguaje EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

Después de editar el archivo EditorConfig, deberá recargar los archivos de código para que la configuración nueva tenga efecto.

## <a name="adding-and-removing-editorconfig-files"></a>Incorporación y eliminación de los archivos EditorConfig

Agregar un archivo EditorConfig al proyecto o código base no convierte los estilos existentes en los nuevos. Por ejemplo, si tiene sangrías en el archivo cuyo formato se realizó con tabulaciones y agrega un archivo EditorConfig que aplica sangrías con espacios, los caracteres de sangría no se convierten en espacios. Sin embargo, a las líneas de código nuevas se les aplicará formato según lo estipulado en el archivo EditorConfig.

Si quita un archivo EditorConfig del proyecto o código base, debe cerrar y volver a abrir todo archivo de código abierto para revertir la configuración global del editor para las nuevas líneas de código.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el estado de la sangría de un fragmento de código de C# antes y después de agregar un archivo .editorconfig al proyecto. La configuración **Tabulaciones** del cuadro de diálogo **Opciones** del editor de texto de Visual Studio se establece para producir caracteres de espacio al presionar la tecla **Tabulador**.

![Configuración de tabulaciones en el editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Como se esperaba, al presionar la tecla **Tabulador** en la línea siguiente, se aplica la sangría en la línea agregando cuatro caracteres de espacio en blanco adicionales.

![Código antes de usar EditorConfig](../ide/media/vside_editorconfig_before.png)

Agregaremos un nuevo archivo denominado .editorconfig al proyecto con el siguiente contenido. El valor `[*.cs]` significa que este cambio solo se aplica a archivos de código de C# en el proyecto.

```
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

Esto significa que, si se especifica cualquier configuración del editor en **Herramientas**, **Opciones**, **Editor de texto** (como el tamaño y estilo de la sangría, el tamaño de la tabulación o las convenciones de codificación) en un archivo EditorConfig en la estructura de directorios del proyecto o por encima de esta, las convenciones del archivo EditorConfig invalidan la configuración que aparece en Opciones. Para controlar este comportamiento, cambie la opción **Seguir las convenciones de codificación del proyecto** en **Herramientas**, **Opciones**, **Editor de texto**. Si se desactiva la opción, se desactiva la compatibilidad con EditorConfig en Visual Studio.

![Opciones de herramientas: Seguir las convenciones de codificación del proyecto](media/coding_conventions_option.png)

Para buscar cualquier archivo .editorconfig en los directorios primarios, abra un símbolo del sistema y ejecute el siguiente comando desde la raíz del disco que contiene el proyecto:

```
dir .editorconfig /s
```

Para controlar el ámbito de las convenciones de EditorConfig, establezca la propiedad ```root=true``` en el archivo .editorconfig en la raíz del repositorio o en el directorio en el que se encuentra el proyecto. Visual Studio busca un archivo denominado .editorconfig en el directorio del archivo abierto y en todos los directorios principales. La búsqueda finaliza cuando se llega a la ruta de acceso del archivo raíz o si se encuentra un archivo .editorconfig con ```root=true```.

## <a name="see-also"></a>Vea también

[Convenciones de estilo de código de .NET](../ide/editorconfig-code-style-settings-reference.md)  
[Compatibilidad de EditorConfig con un servicio de lenguaje](../extensibility/supporting-editorconfig.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Escribir código en el editor](writing-code-in-the-code-and-text-editor.md)