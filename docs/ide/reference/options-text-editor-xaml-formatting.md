---
title: Opciones, editor de texto, XAML, formato
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4686760625062fea7984cdc05386284f8f98c4ee
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388993"
---
# <a name="options-text-editor-xaml-formatting"></a>Opciones, editor de texto, XAML, formato

Use la página de propiedades **Formato** para especificar cómo se aplica formato a los elementos y atributos en los documentos XAML. Para abrir el cuadro de diálogo **Opciones**, haga clic en el menú **Herramientas** y, después, en **Opciones**. Para acceder a la página de propiedades **Formato**, expanda el nodo **Editor de texto** > **XAML** > **Formato**.

## <a name="auto-formatting-events"></a>Eventos de formato automático

El formato automático puede producirse al detectarse cualquiera de los siguientes eventos.

-   Al finalizar una etiqueta de cierre o sencilla.

-   Al finalizar una etiqueta de inicio.

-   Al pegar desde el Portapapeles.

-   Al aplicar formato a los comandos de teclado.

Puede especificar qué eventos desencadenan el formato automático.

**Al finalizar la etiqueta final o etiqueta sencilla**

El formato automático se produce cuando se termina de escribir una etiqueta de cierre o una etiqueta sencilla. Una etiqueta sencilla no tiene atributos, por ejemplo `<Button />`.

**Al finalizar la etiqueta inicial**

El formato automático se produce cuando se termina de escribir una etiqueta de inicio.

**Al pegar del Portapapeles**

El formato automático se produce al pegar XAML desde el Portapapeles en la vista XAML.

## <a name="quotation-mark-style"></a>Estilo de comillas

Esta opción indica si los valores de atributo están entre comillas simples o dobles. Autoformato y la finalización automática de IntelliSense usan esta opción.

Una vez establecida esta opción, solo afecta a aquellos atributos agregados posteriormente mediante el diseñador o manualmente en la vista XAML.

**Comillas dobles (")**

Los valores de atributo están entre comillas dobles.
`<Button Name="button1">Hello</Button>`

**Comillas simples (')**

Los valores de atributo están entre comillas simples.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Ajuste de etiquetas

Puede especificar una longitud de línea para el ajuste de etiquetas. Cuando el ajuste de etiquetas está habilitado, cualquier elemento XAML agregado posteriormente mediante el diseñador se ajusta correctamente.

**Ajustar etiquetas que superen la longitud especificada**

Especifica si las líneas se ajustan a la longitud de línea especificada por **Longitud**.

**Longitud**

Número de caracteres que puede contener una línea. Si es necesario, algunas líneas XAML podrían superar la longitud de línea especificada.

## <a name="attribute-spacing"></a>Espaciado de atributos

Use esta opción para controlar cómo se organizan los atributos en el documento XAML

**Mantener líneas nuevas y espacios entre atributos**

Las nuevas líneas y los espacios entre los atributos no se ven afectados por el formato automático.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Insertar un espacio entre atributos**

Los atributos ocupan una línea, con un espacio que separa los atributos adyacentes. Se aplica la configuración de ajuste de etiquetas.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Poner cada atributo en una línea diferente**

Cada atributo ocupa su propia línea, lo que resulta útil cuando hay muchos atributos.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Poner el primer atributo en la misma línea que la etiqueta inicial**

Cuando esta opción está activada, el primer atributo aparece en la misma línea que la etiqueta inicial del elemento.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Espaciado de elementos

Use esta opción para controlar cómo se organizan los elementos en el documento XAML.

**Conservar líneas nuevas en el contenido**

No se quitan las líneas vacías del contenido del elemento.

```xml
<Grid>


<Button Name="button1">Hello</Button>

</Grid>
```

**Contraer varias líneas vacías del contenido en una sola línea**

Las líneas vacías del contenido del elemento se contraen en una sola línea.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Quitar líneas vacías del contenido**

Se quitan todas las líneas vacías del contenido del elemento.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Vea también

- [XAML en WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)