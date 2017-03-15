---
title: "Crear opciones de configuración del editor personalizadas y portátiles | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 31f433b28b67dc6f3179be87cb5894b5b3f0aa4f
ms.openlocfilehash: 8c986958f141d3efc2ffe29b4176b43e9960e0e1

---
# <a name="create-portable-custom-editor-settings"></a>Crear opciones de configuración del editor personalizadas y portátiles
Las opciones de configuración del editor de texto en Visual Studio se aplican a todos los proyectos de un tipo determinado. Por ejemplo, si cambia una opción de configuración del editor de texto de C#, esa opción se aplica a *todos* los proyectos de C# en Visual Studio. En cambio, en algunos casos, puede que necesite usar convenciones que difieran de sus propias preferencias personales del editor. Los archivos [EditorConfig](http://editorconfig.org/) le permiten realizar esto proporcionando opciones comunes de editor de texto por proyecto. Las opciones de configuración EditorConfig, que se incluyen en un archivo .editorconfig que se ha agregado a su código base, sustituyen las opciones globales del editor de texto de Visual Studio. Esto significa que puede adaptar cada código base para que use las opciones del editor de texto que prefiera. No se necesita ningún complemento para usar esta función en Visual Studio.

## <a name="coding-consistency"></a>Coherencia del código
Las opciones de configuración de los archivos EditorConfig le permiten mantener opciones y estilos de código coherentes para un lenguaje, como el estilo de sangría, el ancho de pestaña, los caracteres de fin de línea y la codificación, entre otros, en un código base independientemente del editor o el IDE que use. Por ejemplo, al codificar en C#, si su código base tiene una convención que prefiere que las sangrías siempre consten de cinco caracteres de espacio, que los documentos usen la codificación UTF-8 y que cada línea siempre termine con un CR/LF, puede configurar un archivo .editorconfig para realizar esto.

Las convenciones de codificación que usa en sus proyectos personales pueden diferir de las que usa en los proyectos del equipo. Por ejemplo, puede preferir que cuando esté codificando, al presionar la tecla TAB se agregue un carácter de tabulación. En cambio, su equipo puede preferir que la aplicación de sangría agregue cuatro caracteres de espacio en lugar de un carácter de tabulación. Los archivos EditorConfig resuelven este problema permitiéndole que tenga una configuración para cada escenario.

Como las opciones de configuración se incluyen en un archivo del código base, se trasladan con este. Siempre que abra el archivo de código en un editor compatible con EditorConfig, la configuración del editor de texto se implementará. Para obtener más información sobre los archivos EditorConfig, vea el sitio web [EditorConfig.org](http://editorconfig.org/). Si edita muchos archivos .editorconfig, puede resultarle útil la extensión del [servicio de lenguaje EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

## <a name="override-editorconfig-settings"></a>Invalidar la configuración de EditorConfig
Cuando agrega un archivo .editorconfig a una carpeta en su jerarquía de archivos, su configuración se aplica en todos los archivos aplicables de ese nivel y los posteriores. Para invalidar las opciones de configuración de EditorConfig para un código base o un proyecto determinado y usar valores de invalidación o diferentes a los del archivo .editorconfig de nivel superior, simplemente agregue un archivo .editorconfig al nivel que quiera cambiar.

![Jerarquía de EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

La nueva configuración del archivo .editorconfig se aplicará al nivel en el que se encuentra y en todos sus archivos secundarios.

## <a name="supported-settings"></a>Configuración admitida
El editor de Visual Studio admite los siguientes valores del conjunto principal de opciones de EditorConfig.
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- raíz
- [convenciones de estilo de código](../ide/editorconfig-code-style-settings-reference.md)

Las opciones de configuración de EditorConfig se admiten en todos los lenguajes compatibles con Visual Studio excepto XML.

## <a name="example"></a>Ejemplo
Este es un ejemplo que muestra el estado de la sangría de un fragmento de código de C# antes y después de agregar un archivo .editorconfig al proyecto. La configuración **Tabulaciones** del cuadro de diálogo **Opciones** del editor de texto de Visual Studio se establece para producir caracteres de espacio al presionar la tecla TAB en su código.

![Configuración de tabulaciones en el editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Como se esperaba, al presionar la tecla TAB en la línea siguiente, se aplica la sangría en la línea agregando cuatro caracteres de espacio en blanco adicionales.

![Código antes de usar EditorConfig](../ide/media/vside_editorconfig_before.png)

Agregaremos lo siguiente en un nuevo archivo denominado .editorconfig al proyecto. (El valor `[*.cs]` significa que este cambio se aplicará solo en archivos .cs en este proyecto).

![Archivo .editorconfig agregado al proyecto](../ide/media/vside_editorconfig_addconfig.png)

Ahora, cuando presiona la tecla TAB, obtiene caracteres de tabulación en lugar de espacios.

![TAB agrega caracteres de tabulación](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Agregar un archivo .editorconfig en su proyecto o código base no convertirá los estilos existentes en los nuevos, solo se aplicará a las líneas que se agreguen a partir de ese momento. Si quita un archivo .editorconfig de su proyecto o código base, debe volver a cargar los archivos de código para que la configuración del editor vuelva a la configuración global. Cualquier error en los archivos .editorconfig se notifica en la ventana de error de Visual Studio.



<!--HONumber=Feb17_HO4-->


