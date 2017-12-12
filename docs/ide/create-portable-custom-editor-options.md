---
title: "Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig
Las opciones de configuración del editor de texto en Visual Studio se aplican a todos los proyectos de un tipo determinado. Por ejemplo, si cambia una opción de configuración del editor de texto de C#, esa opción se aplica a *todos* los proyectos de C# en Visual Studio. En cambio, en algunos casos, puede que necesite usar convenciones que difieran de sus propias preferencias personales del editor. Los archivos [EditorConfig](http://editorconfig.org/) le permiten realizar esto proporcionando opciones comunes de editor de texto por proyecto. Las opciones de configuración EditorConfig, que se incluyen en un archivo .editorconfig que se ha agregado a su código base, sustituyen las opciones globales del editor de texto de Visual Studio. Esto significa que puede adaptar cada código base para que use las opciones del editor de texto que prefiera. No se necesita ningún complemento para usar esta función en Visual Studio.

## <a name="coding-consistency"></a>Coherencia del código
Las opciones de configuración de los archivos EditorConfig le permiten mantener opciones y estilos de código coherentes para un lenguaje, como el estilo de sangría, el ancho de pestaña, los caracteres de fin de línea y la codificación, entre otros, en un código base independientemente del editor o el IDE que use. Por ejemplo, al codificar en C#, si su código base tiene una convención que prefiere que las sangrías siempre consten de cinco caracteres de espacio, que los documentos usen la codificación UTF-8 y que cada línea siempre termine con un CR/LF, puede configurar un archivo .editorconfig para realizar esto.

Las convenciones de codificación que usa en sus proyectos personales pueden diferir de las que usa en los proyectos del equipo. Por ejemplo, puede preferir que cuando esté codificando, al presionar la tecla TAB se agregue un carácter de tabulación. En cambio, su equipo puede preferir que la aplicación de sangría agregue cuatro caracteres de espacio en lugar de un carácter de tabulación. Los archivos EditorConfig resuelven este problema permitiéndole que tenga una configuración para cada escenario.

Como las opciones de configuración se incluyen en un archivo del código base, se trasladan con este. Siempre que abra el archivo de código en un editor compatible con EditorConfig, la configuración del editor de texto se implementará. Para obtener más información sobre los archivos EditorConfig, vea el sitio web [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Invalidar la configuración de EditorConfig
Cuando agrega un archivo .editorconfig a una carpeta en su jerarquía de archivos, su configuración se aplica en todos los archivos aplicables de ese nivel y los posteriores. Para invalidar las opciones de configuración de EditorConfig para un código base o un proyecto concreto de modo que use convenciones diferentes a las del archivo .editorconfig de nivel superior, agregue un archivo .editorconfig a la raíz del repositorio o el directorio de proyecto del código base. Asegúrese de colocar la propiedad ```root=true``` en el archivo de manera que Visual Studio no busque ningún archivo .editorconfig hacia arriba en la estructura de directorios. La nueva configuración del archivo .editorconfig se aplicará al nivel en el que se encuentra y a los archivos de todos los subdirectorios.

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
- end_of_line
- charset
- raíz

Además, admite las [convenciones de estilo de código de .NET](../ide/editorconfig-code-style-settings-reference.md).  

Las opciones de configuración de EditorConfig se admiten en todos los lenguajes compatibles con Visual Studio excepto XML.

## <a name="intellisense"></a>IntelliSense
Visual Studio proporciona IntelliSense limitado para editar archivos .editorconfig. Si edita muchos archivos .editorconfig, puede resultarle útil la extensión del [servicio de lenguaje EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

## <a name="example"></a>Ejemplo
Este es un ejemplo que muestra el estado de la sangría de un fragmento de código de C# antes y después de agregar un archivo .editorconfig al proyecto. La configuración **Tabulaciones** del cuadro de diálogo **Opciones** del editor de texto de Visual Studio se establece para producir caracteres de espacio al presionar la tecla **Tabulador** en el código.

![Configuración de tabulaciones en el editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Como se esperaba, al presionar la tecla **Tabulador** en la línea siguiente, se aplica la sangría en la línea agregando cuatro caracteres de espacio en blanco adicionales.

![Código antes de usar EditorConfig](../ide/media/vside_editorconfig_before.png)

Agregaremos un nuevo archivo denominado .editorconfig al proyecto con el siguiente contenido. El valor `[*.cs]` significa que este cambio se aplicará solo en archivos .cs en este proyecto.  

![Archivo .editorconfig agregado al proyecto](../ide/media/vside_editorconfig_addconfig.png)

Ahora, cuando presiona la tecla **Tabulador**, obtiene caracteres de tabulación en lugar de espacios.

![TAB agrega caracteres de tabulación](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Agregar un archivo .editorconfig en su proyecto o código base no convertirá los estilos existentes en los nuevos, solo se aplicará a las líneas que se agreguen a partir de ese momento. Si quita un archivo .editorconfig de su proyecto o código base, debe volver a cargar los archivos de código para que la configuración del editor vuelva a la configuración global. Cualquier error en los archivos .editorconfig se notifica en la ventana Lista de errores de Visual Studio.

## <a name="troubleshooting-editorconfig-settings"></a>Solucionar problemas de las opciones de configuración de EditorConfig
Si hay un archivo EditorConfig en cualquier lugar de la estructura de directorios en la ubicación del proyecto o encima de esta, Visual Studio aplicará al editor la configuración del editor de ese archivo. En este caso, es posible que vea el siguiente mensaje en la barra de estado:

**"Las preferencias de usuario para este tipo de archivo se han invalidado por las convenciones de codificación de este proyecto."**

Esto significa que, si se especifica cualquier opción de configuración del editor en **Herramientas**, **Opciones** o **Editor de texto** (como el tamaño de sangría, el tamaño de tabulación, el estilo de sangría &mdash; tabulaciones o espacios o convenciones de codificación, como el uso de `var`) en un archivo EditorConfig en la estructura de directorios del proyecto o encima de esta, las convenciones del archivo EditorConfig invalidarán las opciones de configuración de Opciones. Para controlar este comportamiento, cambie la opción **Seguir las convenciones de codificación del proyecto** en **Herramientas**, **Opciones**, **Editor de texto**. Si desactiva la opción, se desactivará la compatibilidad de EditorConfig con Visual Studio.

![Opciones de herramientas: Seguir las convenciones de codificación del proyecto](media/coding_conventions_option.png)

Para buscar archivos .editorconfig en los directorios primarios, abra un símbolo del sistema y ejecute el siguiente comando desde la raíz del disco que contiene el proyecto:

```
dir .editorconfig /s
```

Para controlar el ámbito de las convenciones de EditorConfig, establezca la propiedad ```root=true``` en el archivo .editorconfig en la raíz del repositorio o en el directorio en el que se encuentra el proyecto. Visual Studio busca un archivo denominado .editorconfig en el directorio del archivo abierto y en todos los directorios principales. Visual Studio deja de buscar si se alcanza la ruta del archivo raíz o si se encuentra un archivo .editorconfig con ```root=true```.

## <a name="support-editorconfig-for-your-language-service"></a>Compatibilidad de EditorConfig con el servicio de lenguaje
En la mayoría de los casos, cuando se implementa un servicio de lenguaje de Visual Studio, no es necesario llevar a cabo ninguna tarea adicional para admitir las propiedades universales de EditorConfig. El editor principal detecta automáticamente y lee el archivo .editorconfig cuando los usuarios abren archivos, y establece el búfer de texto y las opciones de visualización adecuados. A pesar de ello, algunos servicios de lenguaje optan por usar una opción de visualización de texto contextual adecuada en vez de usar la configuración global para elementos como tabulaciones y espacios cuando un usuario edita un texto o le da formato. En estos casos, el servicio de lenguaje debe actualizarse para que admita archivos EditorConfig.

A continuación se muestran los cambios necesarios para actualizar un servicio de lenguaje para admitir los archivos EditorConfig. Para ello, se debe reemplazar una opción global _específica del lenguaje_ por una opción _contextual_:  

### <a name="indent-style"></a>Estilo de sangría
Reemplace:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
 _o_   
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

Por:  

!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
 _o_   
!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>Tamaño de sangría
Reemplace:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
 _o_   
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

Por:  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
 _o_   
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>Tamaño de tabulación
Reemplace:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
 _o_   
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

Por:  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
 _o_   
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>Vea también
[Convenciones de estilo de código de .NET](../ide/editorconfig-code-style-settings-reference.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Escribir código en el editor](writing-code-in-the-code-and-text-editor.md)