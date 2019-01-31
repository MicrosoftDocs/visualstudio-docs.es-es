---
title: Cuadro de herramientas, HTML (Pestaña) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd9b728ee8537f5668914f05f05481fd3fe56d92
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780429"
---
# <a name="toolbox-html-tab"></a>Cuadro de herramientas, HTML (Pestaña)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
La pestaña **HTML** del cuadro de herramientas proporciona componentes que resultan de gran utilidad en las páginas web y los formularios Web Forms. Para ver esta pestaña, abra primero un documento para editarlo en el Diseñador HTML. En el menú **Ver**, haga clic en **Cuadro de herramientas** y después haga clic en la pestaña **HTML** del cuadro de herramientas.  
  
 Para crear una instancia de una herramienta en la pestaña **HTML**, haga doble clic en la herramienta para agregarla al documento en el punto de inserción actual o seleccione la herramienta y arrástrela hasta la posición que quiera en la superficie de edición.  
  
## <a name="tasks"></a>Tareas  
  
-   [Cómo: Administrar la ventana del cuadro de herramientas](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [Cómo: Manipular las fichas del cuadro de herramientas](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Elementos de interfaz de usuario  
 Las siguientes herramientas están disponibles de manera predeterminada en la pestaña HTML.  
  
 **Pointer**  
 ![Puntero de página HTML del Diseñador de ASP.NET Mobile](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Esta herramienta está seleccionada de manera predeterminada cuando se abre cualquier pestaña del cuadro de herramientas. No se puede eliminar. El puntero le permite arrastrar objetos a la superficie de la vista Diseño, cambiar su tamaño y su ubicación en la página o formulario. Para obtener más información, vea [Cómo: Administrar la ventana del cuadro de herramientas](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) y [Cómo: Manipular las fichas del cuadro de herramientas](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Input (Button)**  
 ![Botón de página web HTML](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Inserta un elemento `input` de `type="button"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Button1"` para el primer botón, `id="Button2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Button)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputButton](http://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: Procedimiento Crear secuencias de comandos y editar controladores de eventos](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [mapa de contenido de controles de botón de servidor Web](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton>, y <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Reset)**  
 ![Captura de pantalla de HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Inserta un elemento `input` de `type="reset"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Reset1"` para el primer botón de reinicio, `id="Reset2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Reset)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputReset](http://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, y <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Submit)**  
 ![Captura de pantalla de HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Inserta un elemento `input` de `type="submit"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Submit1"` para el primer botón de envío, `id="Submit2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Submit)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputSubmit](http://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, y <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Text)**  
 ![Captura de pantalla de HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Inserta un elemento `input` de `type="text"` en el documento. Para cambiar el texto predeterminado que se muestra, edite el atributo `value`. De manera predeterminada, se inserta `id="Text1"` para el primer campo de texto, `id="Text2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Text)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputText](http://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [información general sobre el Control de servidor Web TextBox](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText>, y <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, consulte [Validar la información especificada por el usuario en ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (File)**  
 ![Campo Archivo de página HTML](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Inserta un elemento `input` de `type="file"` en el documento. De manera predeterminada, se inserta `id="File1"` para el primer campo de archivo, `id="File2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (File)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputFile](http://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6), y <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, consulte [Validar la información especificada por el usuario en ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Password)**  
 ![Campo Contraseña de Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Inserta un elemento `input` de `type="password"`. De manera predeterminada, se inserta `id="Password1"` para el primer campo de contraseña, `id="Password2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Password)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputPassword](http://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Cómo: Establecer un Control de servidor Web de cuadro de texto para escribir contraseñas](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310), y [Tutorial: Validar la entrada del usuario en un sitio Web Forms página](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Si la aplicación transmite nombres de usuario y contraseñas, debe configurar su sitio web para que use la capa de sockets seguros (SSL) para cifrar la transmisión. Para obtener más información, consulte "Securing Connections with SSL" (Proteger conexiones con SSL) en la [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856) (Guía de operaciones de IIS). Además, se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, consulte [Validar la información especificada por el usuario en ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Check box)**  
 ![Opción de casilla del cuadro de herramientas de página web HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Inserta un elemento `input` de `type="checkbox"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Checkbox1"` para la primera casilla, `id="Checkbox2"` para la segunda y así sucesivamente.  
  
 Si arrastra **Input (Check box)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputCheckBox](http://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox y CheckBoxList Web Server Controls Overview](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox>, y <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Input (Radio)**  
 ![Captura de pantalla de VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Inserta un elemento `input` de `type="radio"`. Para cambiar el texto que se muestra, edite la propiedad `name`. De manera predeterminada, se inserta `id="Radio1"` para el primer botón de selección, `id="Radio2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Radio)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputRadioButton](http://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton y RadioButtonList Web Server Controls Overview](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton>, y <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Input (Hidden)**  
 ![Elemento oculto de página HTML](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Inserta un elemento `input` de `type="hidden"`. De manera predeterminada, se inserta `id="Hidden1"` para el primer campo oculto, `id="Hidden2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Input (Hidden)** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Para obtener más información, consulte [controles de entrada HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [sintaxis declarativa del Control de servidor HtmlInputHidden](http://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9), y <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Textarea**  
 ![Área de texto de la barra de herramientas de la página HTML](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Inserta un elemento `textarea`. Puede cambiar el tamaño del área de texto o usar las barras de desplazamiento para ver el texto que se extiende más allá del área de visualización. Para cambiar el texto predeterminado que se muestra, edite el atributo `value`. De manera predeterminada, se inserta `id="textarea1"` para la primera área de texto, `id=" textarea 2"` para la segunda y así sucesivamente.  
  
 Si arrastra **Textarea** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Para obtener más información, consulte [sintaxis declarativa del Control de servidor HtmlTextArea](http://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea>, y <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario. Para obtener más información, consulte [Validar la información especificada por el usuario en ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Table**  
 ![Captura de pantalla de HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Inserta un elemento `table`.  
  
 Si arrastra **Table** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Para obtener más información, consulte [sintaxis declarativa del Control de servidor HtmlTable](http://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Table, TableRow y TableCell Web Server Control Overview](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable>, y <xref:System.Web.UI.WebControls.Table>.  
  
 **Image**  
 ![Elemento de imagen de página HTML](../../ide/reference/media/vximage.gif "vxImage")  
  
 Inserta un elemento `img`. Modifique este elemento para especificar su `src` y su texto `alt`.  
  
 Si arrastra **Image** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<img alt="" src="">  
```  
  
 Para obtener más información, consulte [sintaxis declarativa del Control de servidor HtmlImage](http://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [información general sobre el Control de servidor Web imagen](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage>, y <xref:System.Web.UI.WebControls.Image>.  
  
 **Seleccionar**  
 ![Cuadro de herramientas desplegable de la página HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Inserta un elemento `select` desplegable (sin atributo `size`). De manera predeterminada, se inserta `id="select1"` para el primer cuadro de lista, `id="select2"` para el segundo y así sucesivamente.  
  
 Si arrastra **Select** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Para crear un elemento `select` multilínea, aumente el valor de la propiedad Size.  
  
 Para obtener más información, consulte [sintaxis declarativa del Control de servidor HtmlSelect](http://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: Procedimiento Crear secuencias de comandos y editar controladores de eventos](http://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [información general sobre el Control de servidor Web DropDownList](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [información general sobre el Control de servidor Web ListBox](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect>, y <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Horizontal Rule**  
 ![Elemento de regla horizontal de página HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Inserta un elemento `hr`. Para aumentar el grosor de la línea, modifique el atributo `size`.  
  
 Si arrastra **Horizontal Rule** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<hr width="100%" size=1>   
```  
  
 Para obtener más información, consulte [Control de regla horizontal HTML](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **Div**  
 ![Etiqueta de página HTML](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Inserta un elemento `div` que incluye un atributo `ms_positioning="FlowLayout"`. Excepto por el ancho y alto, este elemento es idéntico a un panel de diseño de flujo. Para dar formato al texto que se encuentra en el elemento `div`, agregue un atributo `class="stylename"` a la etiqueta de apertura.  
  
 Si arrastra **Div** a la superficie de la vista Diseño, se inserta código HTML similar al siguiente en el documento:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Para obtener más información, consulte [Div Control de HTML](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [información general sobre el Control de servidor Web Label](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac), y <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Estándar (Ficha), Cuadro de herramientas](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [Controles HTML](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
