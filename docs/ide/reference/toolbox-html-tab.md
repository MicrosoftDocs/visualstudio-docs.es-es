---
title: Cuadro de herramientas, HTML (Pestaña)
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 420a65fb8b91495c5fbba228e190b5589019c99f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926780"
---
# <a name="toolbox-html-tab"></a>Cuadro de herramientas, HTML (Pestaña)

La pestaña **HTML** del cuadro de herramientas proporciona componentes que resultan de gran utilidad en las páginas y los formularios web. Para ver esta pestaña, abra primero un documento para editarlo en el Diseñador HTML. En el menú **Ver**, haga clic en **Cuadro de herramientas** y después haga clic en la pestaña **HTML** del cuadro de herramientas.

 Para crear una instancia de una herramienta en la pestaña **HTML**, haga doble clic en la herramienta para agregarla al documento en el punto de inserción actual o seleccione la herramienta y arrástrela hasta la posición que quiera en la superficie de edición.

## <a name="ui-elements"></a>Elementos de interfaz de usuario

Las siguientes herramientas están disponibles de manera predeterminada en la pestaña HTML.

**Pointer**

![Puntero de página HTML del Diseñador de ASP.NET Mobile](../../ide/reference/media/vxpointer.gif)

Esta herramienta está seleccionada de manera predeterminada cuando se abre cualquier pestaña del cuadro de herramientas. No se puede eliminar. El puntero le permite arrastrar objetos a la superficie de la vista Diseño, cambiar su tamaño y su ubicación en la página o formulario. Para obtener más información, vea [Cuadro de herramientas](../../ide/reference/toolbox.md).

**Input (Button)**

![Botón de página Web HTML](../../ide/reference/media/vxbutton.gif)

Inserta un elemento `input` de `type="button"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Button1"` para el primer botón, `id="Button2"` para el segundo y así sucesivamente.

Si arrastra **Input (Button)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Input (Reset)**

![Captura de pantalla de HTMLpageResetButton](../../ide/reference/media/vxreset.gif)

Inserta un elemento `input` de `type="reset"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Reset1"` para el primer botón de reinicio, `id="Reset2"` para el segundo y así sucesivamente.

Si arrastra **Input (Reset)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Input (Submit)**

![Captura de pantalla de HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif)

Inserta un elemento `input` de `type="submit"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Submit1"` para el primer botón de envío, `id="Submit2"` para el segundo y así sucesivamente.

Si arrastra **Input (Submit)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Input (Text)**

![Captura de pantalla de HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif)

Inserta un elemento `input` de `type="text"` en el documento. Para cambiar el texto predeterminado que se muestra, edite el atributo `value`. De manera predeterminada, se inserta `id="Text1"` para el primer campo de texto, `id="Text2"` para el segundo y así sucesivamente.

Si arrastra **Input (Text)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (File)**

![Campo Archivo de paginación HTML](../../ide/reference/media/vxfilefield.gif)

Inserta un elemento `input` de `type="file"` en el documento. De manera predeterminada, se inserta `id="File1"` para el primer campo de archivo, `id="File2"` para el segundo y así sucesivamente.

Si arrastra **Input (File)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (Password)**

![Campo de contraseña de Visual Studio](../../ide/reference/media/vxpassword.gif)

Inserta un elemento `input` de `type="password"`. De manera predeterminada, se inserta `id="Password1"` para el primer campo de contraseña, `id="Password2"` para el segundo y así sucesivamente.

Si arrastra **Input (Password)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Si la aplicación transmite nombres de usuario y contraseñas, debe configurar su sitio web para que use Capa de sockets seguros (SSL) para cifrar la transmisión. Para obtener más información, vea [Securing Connections](/previous-versions/tn-archive/bb418917(v=technet.10)) (Proteger las conexiones). Además, se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Input (Check box)**

![Opción de casilla de cuadro de herramientas de página Web HTML](../../ide/reference/media/vxcheckbox.gif)

Inserta un elemento `input` de `type="checkbox"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Checkbox1"` para la primera casilla, `id="Checkbox2"` para la segunda y así sucesivamente.

Si arrastra **Input (Check box)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Input (Radio)**

![Captura de pantalla de VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif)

Inserta un elemento `input` de `type="radio"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Radio1"` para el primer botón de selección, `id="Radio2"` para el segundo y así sucesivamente.

Si arrastra **Input (Radio)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Input (Hidden)**

![Elemento oculto de página HTML](../../ide/reference/media/vxhidden.gif)

Inserta un elemento `input` de `type="hidden"`. De manera predeterminada, se inserta `id="Hidden1"` para el primer campo oculto, `id="Hidden2"` para el segundo y así sucesivamente.

Si arrastra **Input (Hidden)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Textarea**

![Área de texto de la barra de herramientas de la página HTML](../../ide/reference/media/vxtextarea.gif)

Inserta un elemento `textarea`. Puede cambiar el tamaño del área de texto o usar las barras de desplazamiento para ver el texto que se extiende más allá del área de visualización. Para cambiar el texto predeterminado que se muestra, edite el atributo `value`. De manera predeterminada, se inserta `id="textarea1"` para la primera área de texto, `id=" textarea 2"` para la segunda y así sucesivamente.

Si arrastra **Textarea** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Table**

![Captura de pantalla de HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif)

Inserta un elemento `table`.

Si arrastra **Table** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Image**

![Elemento de imagen de página HTML](../../ide/reference/media/vximage.gif)

Inserta un elemento `img`. Modifique este elemento para especificar su `src` y su texto `alt`.

Si arrastra **Image** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<img alt="" src="">
```

**Seleccionar**

![Cuadro de herramientas desplegable de la página HTML](../../ide/reference/media/vxdropdown.gif)

Inserta un elemento `select` desplegable (sin atributo `size`). De manera predeterminada, se inserta `id="select1"` para el primer cuadro de lista, `id="select2"` para el segundo y así sucesivamente.

Si arrastra **Select** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Para crear un elemento `select` multilínea, aumente el valor de la propiedad Size.

**Horizontal Rule**

![Elemento de la regla horizontal de página HTML](../../ide/reference/media/vxhorizontal.gif)

Inserta un elemento `hr`. Para aumentar el grosor de la línea, modifique el atributo `size`.

Si arrastra **Horizontal Rule** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<hr width="100%" size=1>
```

**Div**

![Etiqueta de página HTML](../../ide/reference/media/vxlabel.gif)

Inserta un elemento `div` que incluye un atributo `ms_positioning="FlowLayout"`. Excepto por el ancho y alto, este elemento es idéntico a un panel de diseño de flujo. Para dar formato al texto que se encuentra en el elemento `div`, agregue un atributo `class="stylename"` a la etiqueta de apertura.

Si arrastra **Div** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Vea también

- [Cuadro de herramientas](../../ide/reference/toolbox.md)
