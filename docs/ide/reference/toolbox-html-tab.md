---
title: "Cuadro de herramientas, HTML (Pestaña) | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: bc243e4d5ec1141244314109aa76fef86287d1c1
ms.contentlocale: es-es
ms.lasthandoff: 06/23/2017

---
# <a name="toolbox-html-tab"></a>Cuadro de herramientas, HTML (Pestaña)
La pestaña **HTML** del cuadro de herramientas proporciona componentes que resultan de gran utilidad en las páginas web y los formularios Web Forms. Para ver esta pestaña, abra primero un documento para editarlo en el Diseñador HTML. En el menú **Ver**, haga clic en **Cuadro de herramientas** y después haga clic en la pestaña **HTML** del cuadro de herramientas.  

 Para crear una instancia de una herramienta en la pestaña **HTML**, haga doble clic en la herramienta para agregarla al documento en el punto de inserción actual o seleccione la herramienta y arrástrela hasta la posición que quiera en la superficie de edición.  

## <a name="tasks"></a>Tareas  

-   [Usar el cuadro de herramientas](../../ide/using-the-toolbox.md)  

## <a name="ui-elements"></a>Elementos de interfaz de usuario  
 Las siguientes herramientas están disponibles de manera predeterminada en la pestaña HTML.  

 **Pointer**  
 ![Puntero de página HTML del Diseñador de ASP.NET Mobile](~/ide/reference/media/vxpointer.gif "vxPointer")  

 Esta herramienta está seleccionada de manera predeterminada cuando se abre cualquier pestaña del cuadro de herramientas. No se puede eliminar. El puntero le permite arrastrar objetos a la superficie de la vista Diseño, cambiar su tamaño y su ubicación en la página o formulario. Para obtener más información, vea [Usar el cuadro de herramientas](../../ide/using-the-toolbox.md).  

 **Input (Button)**  
 ![Botón de página web HTML](~/ide/reference/media/vxbutton.gif "vxButton")  

 Inserta un elemento `input` de `type="button"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Button1"` para el primer botón, `id="Button2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Button)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  

 **Input (Reset)**  
 ![Captura de pantalla de HTMLpageResetButton](~/ide/reference/media/vxreset.gif "vxReset")  

 Inserta un elemento `input` de `type="reset"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Reset1"` para el primer botón de reinicio, `id="Reset2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Reset)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  

 **Input (Submit)**  
 ![Captura de pantalla de HTMLpageToolbarSubmitButton](~/ide/reference/media/vxsubmit.gif "vxSubmit")  

 Inserta un elemento `input` de `type="submit"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Submit1"` para el primer botón de envío, `id="Submit2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Submit)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  

 **Input (Text)**  
 ![Captura de pantalla de HTMLpageToolbarTextField](~/ide/reference/media/vxtextfield.gif "vxTextfield")  

 Inserta un elemento `input` de `type="text"` en el documento. Para cambiar el texto predeterminado que se muestra, edite el atributo `value`. De manera predeterminada, se inserta `id="Text1"` para el primer campo de texto, `id="Text2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Text)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  

> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Input (File)**  
 ![Campo Archivo de página HTML](~/ide/reference/media/vxfilefield.gif "vxFilefield")  

 Inserta un elemento `input` de `type="file"` en el documento. De manera predeterminada, se inserta `id="File1"` para el primer campo de archivo, `id="File2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (File)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="File1" type="file" name="File1">  
```  

> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Input (Password)**  
 ![Campo de contraseña de Visual Studio](~/ide/reference/media/vxpassword.gif "vxPassword")  

 Inserta un elemento `input` de `type="password"`. De manera predeterminada, se inserta `id="Password1"` para el primer campo de contraseña, `id="Password2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Password)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Password1" type="password" name="Password1">  
```  

> [!IMPORTANT]
>  Si la aplicación transmite nombres de usuario y contraseñas, debe configurar su sitio web para que use la capa de sockets seguros (SSL) para cifrar la transmisión. Para obtener más información, consulte "Securing Connections with SSL" (Proteger conexiones con SSL) en la [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856) (Guía de operaciones de IIS). Además, se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Input (Check box)**  
 ![Opción de casilla del cuadro de herramientas de página web HTML](~/ide/reference/media/vxcheckbox.gif "vxCheckbox")  

 Inserta un elemento `input` de `type="checkbox"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Checkbox1"` para la primera casilla, `id="Checkbox2"` para la segunda y así sucesivamente.  

 Si arrastra **Input (Check box)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  

 **Input (Radio)**  
 ![Captura de pantalla de VisualStudioHTMLpageRadioButton](~/ide/reference/media/vxradio.gif "vxRadio")  

 Inserta un elemento `input` de `type="radio"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Radio1"` para el primer botón de selección, `id="Radio2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Radio)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Radio1" type="radio" name="Radio1">  
```  

 **Input (Hidden)**  
 ![Elemento oculto de página HTML](~/ide/reference/media/vxhidden.gif "vxhidden")  

 Inserta un elemento `input` de `type="hidden"`. De manera predeterminada, se inserta `id="Hidden1"` para el primer campo oculto, `id="Hidden2"` para el segundo y así sucesivamente.  

 Si arrastra **Input (Hidden)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  

 **Textarea**  
 ![Área de texto de la barra de herramientas de la página HTML](~/ide/reference/media/vxtextarea.gif "vxTextarea")  

 Inserta un elemento `textarea`. Puede cambiar el tamaño del área de texto o usar las barras de desplazamiento para ver el texto que se extiende más allá del área de visualización. Para cambiar el texto predeterminado que se muestra, edite el atributo `value`. De manera predeterminada, se inserta `id="textarea1"` para la primera área de texto, `id=" textarea 2"` para la segunda y así sucesivamente.  

 Si arrastra **Textarea** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  

> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, vea [Validar la información especificada por el usuario en sitios de ASP.NET Web Pages (Razor)](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Table**  
 ![Captura de pantalla de HTMLpageToolbarTable](~/ide/reference/media/vxtable.gif "vxTable")  

 Inserta un elemento `table`.  

 Si arrastra **Table** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  

**Image**  
 ![Elemento de imagen de página HTML](~/ide/reference/media/vximage.gif "vxImage")  

 Inserta un elemento `img`. Modifique este elemento para especificar su `src` y su texto `alt`.  

 Si arrastra **Image** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<img alt="" src="">  
```  

 **Seleccionar**  
 ![Cuadro de herramientas desplegable de la página HTML](~/ide/reference/media/vxdropdown.gif "vxDropdown")  

 Inserta un elemento `select` desplegable (sin atributo `size`). De manera predeterminada, se inserta `id="select1"` para el primer cuadro de lista, `id="select2"` para el segundo y así sucesivamente.  

 Si arrastra **Select** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<select id="select1" name="select1"><option selected></option></select>  
```  

 Para crear un elemento `select` multilínea, aumente el valor de la propiedad Size.  

 **Horizontal Rule**  
 ![Elemento de regla horizontal de página HTML](~/ide/reference/media/vxhorizontal.gif "vxHorizontal")  

 Inserta un elemento `hr`. Para aumentar el grosor de la línea, modifique el atributo `size`.  

 Si arrastra **Horizontal Rule** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<hr width="100%" size=1>   
```  

 **Div**  
 ![Etiqueta de página HTML](~/ide/reference/media/vxlabel.gif "vxLabel")  

 Inserta un elemento `div` que incluye un atributo `ms_positioning="FlowLayout"`. Excepto por el ancho y alto, este elemento es idéntico a un panel de diseño de flujo. Para dar formato al texto que se encuentra en el elemento `div`, agregue un atributo `class="stylename"` a la etiqueta de apertura.  

 Si arrastra **Div** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  

```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  

## <a name="see-also"></a>Vea también  
 [Cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Usar el cuadro de herramientas](../../ide/using-the-toolbox.md)   

