---
title: Opciones, editor de texto, XAML, formato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 74495c068cbd476014fa2c10088239e096d42f02
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840940"
---
# <a name="options-text-editor-xaml-formatting"></a>Opciones, editor de texto, XAML, formato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la página de propiedades **Formato** para especificar cómo se aplica formato a los elementos y atributos en los documentos XAML. Para abrir el cuadro de diálogo **Opciones**, haga clic en el menú **Herramientas** y, después, en **Opciones**. Para acceder a la propiedad **Formato**, expanda el nodo **Editor de texto**, **XAML**, **Formato**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Eventos de formato automático
El formato automático puede producirse al detectarse cualquiera de los siguientes eventos.

- Al finalizar una etiqueta de cierre o sencilla.

- Al finalizar una etiqueta de inicio.

- Al pegar desde el Portapapeles.

- Al aplicar formato a los comandos de teclado.

  Puede especificar qué eventos provocan el formato automático.

|||
|-|-|
|**Al finalizar la etiqueta final o etiqueta sencilla**|El formato automático se produce cuando termina de escribir una etiqueta de cierre o una etiqueta sencilla. Una etiqueta sencilla no tiene atributos, por ejemplo `<Button />`.|
|**Al finalizar la etiqueta inicial**|El formato automático se produce cuando termina de escribir una etiqueta de inicio.|
|**Al pegar del Portapapeles**|El formato automático se produce al pegar XAML desde el Portapapeles en la vista XAML.|

## <a name="quotation-mark-style"></a>Estilo de comillas
Esta opción indica si los valores de atributo están entre comillas simples o dobles. El formato automático y la finalización automática de IntelliSense usan esta opción.

Una vez establecida esta opción, solo afecta a aquellos atributos agregados posteriormente mediante el diseñador o manualmente en la vista XAML.

|||
|-|-|
|**Comillas dobles (")**|Los valores de atributo están entre comillas dobles.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Comillas simples (')**|Los valores de atributo están entre comillas simples.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Ajuste de etiquetas
Puede especificar una longitud de línea para el ajuste de etiquetas. Cuando el ajuste de etiquetas está habilitado, cualquier elemento XAML agregado posteriormente mediante el diseñador se ajusta correctamente.

|||
|-|-|
|**Ajustar etiquetas que superen la longitud especificada**|Especifica si las líneas se ajustan a la longitud de línea especificada por **Longitud**.|
|**Longitud**|Número de caracteres que puede contener una línea. Si es necesario, algunas líneas XAML podrían superar la longitud de línea especificada.|

## <a name="attribute-spacing"></a>Espaciado de atributos
Use esta opción para controlar cómo se organizan los atributos en el documento XAML

|||
|-|-|
|**Mantener líneas nuevas y espacios entre atributos**|Las nuevas líneas y los espacios entre los atributos no se ven afectados por el formato automático.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Insertar un espacio entre atributos**|Los atributos ocupan una línea, con un espacio que separa los atributos adyacentes. Se aplica la configuración de ajuste de etiquetas.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Poner cada atributo en una línea diferente**|Cada atributo ocupa su propia línea. Esto resulta útil si hay muchos atributos.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Poner el primer atributo en la misma línea que la etiqueta inicial**|Cuando esta opción está activada, el primer atributo aparece en la misma línea que la etiqueta inicial del elemento.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Espaciado de elementos
Use esta opción para controlar cómo se organizan los elementos en el documento XAML

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Conservar líneas nuevas en el contenido**                             | No se quitan las líneas vacías del contenido del elemento.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **Contraer varias líneas vacías del contenido en una sola línea** | Las líneas vacías del contenido del elemento se contraen en una sola línea.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **Quitar líneas vacías del contenido**                             | Se quitan todas las líneas vacías del contenido del elemento.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Inserción automática
Use esta opción para controlar cuándo se generan automáticamente etiquetas y comillas.

|||
|-|-|
|**Etiquetas de cierre**|Especifica si la etiqueta de cierre de un elemento se genera automáticamente cuando se cierra la etiqueta de apertura con el carácter mayor que (>).|
|**Comillas de atributo**|Especifica si se generan comillas cuando se selecciona un valor de atributo en la lista desplegable de finalización de instrucciones.|
|**Llaves de cierre para MarkupExtensions**|Especifica si la llave de cierre (}) de una extensión de marcado se genera automáticamente cuando se escribe el carácter de llave de apertura ({).|
|**Comas para separar parámetros de MarkupExtension**|Especifica si se generan comas al escribir más de un parámetro en una extensión de marcado.|

## <a name="default-view"></a>Vista predeterminada
Use esta configuración para controlar si la vista de diseño aparece al cargar documentos XAML.

|||
|-|-|
|**Siempre se abren documentos en la vista XAML completa**|Especifica si los documentos XAML aparecen sólo en la vista XAML, sin la vista Diseño. Resulta útil para la carga de documentos de gran tamaño.|

## <a name="toolbox"></a>Cuadro de herramientas
Use esta opción para especificar si los controles de usuario y controles personalizados se muestran en el cuadro de herramientas.

|||
|-|-|
|**Rellenar automáticamente los elementos del cuadro de herramientas**|Especifica si los controles de usuario y los controles personalizados de la solución actual se muestran en el cuadro de herramientas automáticamente.|

## <a name="see-also"></a>Vea también
[XAML en WPF](http://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)  
[Cómo: Cambiar la configuración de la vista XAML](http://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47)  
[Tutoriales para el uso de XAML y código](http://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
