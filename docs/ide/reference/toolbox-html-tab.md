---
title: "Cuadro de herramientas, HTML (Pesta&#241;a) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolbox.html"
helpviewer_keywords: 
  - "Diseñador HTML, establecer opciones"
  - "HTML (ficha del Cuadro de herramientas)"
  - "cuadro de herramientas, HTML (ficha)"
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Cuadro de herramientas, HTML (Pesta&#241;a)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La ficha **HTML** del Cuadro de herramientas proporciona componentes útiles para las páginas y los formularios Web.  Para ver esta ficha, abra primero un documento para editarlo en el diseñador de HTML.  En el menú **Ver**, haga clic en **Cuadro de herramientas** y, a continuación, haga clic en la ficha **HTML** del Cuadro de herramientas.  
  
 Para crear una instancia de una herramienta en la ficha **HTML**, haga doble clic en la herramienta para agregarla al documento en el punto de inserción actual o seleccione la herramienta y arrástrela a la posición que desee de la superficie de edición.  
  
## Tareas  
  
-   [How to: Manage the Toolbox Window](http://msdn.microsoft.com/es-es/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## Elementos de interfaz de usuario  
 De forma predeterminada, en la ficha HTML están disponibles las siguientes herramientas.  
  
 **Pointer**  
 Esta es la herramienta seleccionada de forma predeterminada cuando se abre cualquier ficha del Cuadro de herramientas.  No se puede eliminar.  El puntero permite arrastrar objetos a la superficie de la vista Diseño, cambiar su tamaño y su ubicación en la página o formulario.  Para obtener más información, vea [How to: Manage the Toolbox Window](http://msdn.microsoft.com/es-es/a022c3fe-298c-4a59-a48f-b050da90ebc2) y [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Input \(Button\)**  
 Inserta un elemento `input` de `type="button"`.  Para cambiar el texto que se muestra, modifique la propiedad `name`.  De forma predeterminada, se inserta `id="Button1"` para el primer botón, `id="Button2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Button\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputButton](http://msdn.microsoft.com/es-es/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: How to: Create Scripts and Edit Event Handlers](http://msdn.microsoft.com/es-es/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Button Web Server Controls Content Map](../Topic/Button%20Web%20Server%20Controls%20Content%20Map.md), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> y <xref:System.Web.UI.WebControls.Button>.  
  
 **Input \(Reset\)**  
 Inserta un elemento `input` de `type="reset"`.  Para cambiar el texto que se muestra, modifique la propiedad `name`.  De forma predeterminada, se inserta `id="Reset1"` para el primer botón Restablecer, `id="Reset2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Reset\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputReset](http://msdn.microsoft.com/es-es/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> y <xref:System.Web.UI.WebControls.Button>.  
  
 **Input \(Submit\)**  
 Inserta un elemento `input` de `type="submit"`.  Para cambiar el texto que se muestra, modifique la propiedad `name`.  De forma predeterminada, se inserta `id="Submit1"` para el primer botón Enviar, `id="Submit2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Submit\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputSubmit](http://msdn.microsoft.com/es-es/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> y <xref:System.Web.UI.WebControls.Button>.  
  
 **Input \(Text\)**  
 Inserta un elemento `input` de `type="text"` en el documento.  Para cambiar el texto predeterminado que se muestra, modifique el atributo `value`.  De forma predeterminada, se inserta `id="Text1"` para el primer campo de texto, `id="Text2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Text\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputText](http://msdn.microsoft.com/es-es/87060d90-a11c-434d-9fc9-b03a8487041e), [TextBox Web Server Control Overview](../Topic/TextBox%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlInputText> y <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario.  Para obtener más información, vea [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Input \(File\)**  
 Inserta un elemento `input` de `type="file"` en el documento.  De forma predeterminada, se inserta `id="File1"` para el primer campo de archivo, `id="File2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(File\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputFile](http://msdn.microsoft.com/es-es/a817b4a0-056f-4c17-a696-b9fdcde43db6) y <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario.  Para obtener más información, vea [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Input \(Password\)**  
 Inserta un elemento `input` de `type="password"`.  De forma predeterminada, se inserta `id="Password1"` para el primer campo de contraseña, `id="Password2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Password\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputPassword](http://msdn.microsoft.com/es-es/df703dd0-1624-4e5a-a547-c97f2f331b9f), [How to: Set a TextBox Web Server Control for Password Entry](../Topic/How%20to:%20Set%20a%20TextBox%20Web%20Server%20Control%20for%20Password%20Entry.md) y [Walkthrough: Validating User Input in a Web Forms Page](../Topic/Walkthrough:%20Validating%20User%20Input%20in%20a%20Web%20Forms%20Page.md).  
  
> [!IMPORTANT]
>  Si la aplicación transmite nombres de usuario y contraseñas, debe configurar el sitio Web con el fin de utilizar Capa de sockets seguros \(SSL\) para cifrar la transmisión.  Para obtener más información, vea el tema "Asegurar las conexiones con SSL" en [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856).  Además, se recomienda que valide todos los datos proporcionados por el usuario.  Para obtener más información, vea [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Input \(Check box\)**  
 Inserta un elemento `input` de `type="checkbox"`.  Para cambiar el texto que se muestra, modifique la propiedad `name`.  De forma predeterminada, se inserta `id="Checkbox1"` para la primera casilla, `id="Checkbox2"` para la segunda, etc.  
  
 Cuando se arrastra **Input \(Check box\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputCheckBox](http://msdn.microsoft.com/es-es/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox and CheckBoxList Web Server Controls Overview](../Topic/CheckBox%20and%20CheckBoxList%20Web%20Server%20Controls%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> y <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Input \(Radio\)**  
 Inserta un elemento `input` de `type="radio"`.  Para cambiar el texto que se muestra, modifique la propiedad `name`.  De forma predeterminada, se inserta `id="Radio1"` para el primer botón de radio, `id="Radio2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Radio\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputRadioButton](http://msdn.microsoft.com/es-es/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton and RadioButtonList Web Server Controls Overview](../Topic/RadioButton%20and%20RadioButtonList%20Web%20Server%20Controls%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> y <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Input \(Hidden\)**  
 Inserta un elemento `input` de `type="hidden"`.  De forma predeterminada, se inserta `id="Hidden1"` para el primer campo oculto, `id="Hidden2"` para el segundo, etc.  
  
 Cuando se arrastra **Input \(Hidden\)** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Para obtener más información, vea [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Sintaxis declarativa del control de servidor HtmlInputHidden](http://msdn.microsoft.com/es-es/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) y <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Textarea**  
 Inserta un elemento `textarea`.  Puede cambiar el tamaño del control Text Area o utilizar sus barras de desplazamiento para ver el texto que ocupa más espacio que el área de presentación.  Para cambiar el texto predeterminado que se muestra, modifique el atributo `value`.  De forma predeterminada, se inserta `id="textarea1"` para el primer área de texto, `id=" textarea 2"` para el segundo, etc.  
  
 Cuando se arrastra **Textarea** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Para obtener más información, vea [Sintaxis declarativa del control de servidor HtmlTextArea](http://msdn.microsoft.com/es-es/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> y <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Se recomienda que valide todos los datos proporcionados por el usuario.  Para obtener más información, vea [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Tabla**  
 Inserta un elemento `table`.  
  
 Cuando se arrastra **Tabla** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Para obtener más información, vea [Sintaxis declarativa del control de servidor HtmlTable](http://msdn.microsoft.com/es-es/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Table, TableRow, and TableCell Web Server Control Overview](../Topic/Table,%20TableRow,%20and%20TableCell%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlTable> y <xref:System.Web.UI.WebControls.Table>.  
  
 **Image**  
 Inserta un elemento `img`.  Modifique este elemento para especificar su `src` y su texto `alt`.  
  
 Cuando se arrastra **Image** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<img alt="" src="">  
```  
  
 Para obtener más información, vea [Sintaxis declarativa del control de servidor HtmlImage](http://msdn.microsoft.com/es-es/528430e8-ced1-47d1-8db2-942e734a61f6), [Image Web Server Control Overview](../Topic/Image%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> y <xref:System.Web.UI.WebControls.Image>.  
  
 **Select**  
 Inserta un elemento `select` desplegable \(sin atributo `size`\).  De forma predeterminada, se inserta `id="select1"` para el primer cuadro de lista, `id="select2"` para el segundo, etc.  
  
 Cuando se arrastra **Seleccionar** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Puede crear un elemento `select` multilínea aumentando el valor de la propiedad de tamaño.  
  
 Para obtener más información, vea [Sintaxis declarativa del control de servidor HtmlSelect](http://msdn.microsoft.com/es-es/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: How to: Create Scripts and Edit Event Handlers](http://msdn.microsoft.com/es-es/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [DropDownList Web Server Control Overview](../Topic/DropDownList%20Web%20Server%20Control%20Overview.md), [ListBox Web Server Control Overview](../Topic/ListBox%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlSelect> y <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Horizontal Rule**  
 Inserta un elemento `hr`.  Para aumentar el grosor de la línea, modifique el atributo `size`.  
  
 Cuando se arrastra **Horizontal Rule** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<hr width="100%" size=1>   
```  
  
 Para obtener más información, vea [HTML Horizontal Rule Control](../Topic/HTML%20Horizontal%20Rule%20Control.md).  
  
 **Div**  
 Inserta un elemento `div` que incluye un atributo `ms_positioning="FlowLayout"`.  Excepto por WIDTH y HEIGHT, este elemento es idéntico a un control Flow Layout Panel.  Para dar formato al texto contenido en un elemento `div`, agregue un atributo `class="stylename"` a la etiqueta de apertura.  
  
 Cuando se arrastra **Div** a la superficie de la vista Diseño, en el documento se inserta código HTML similar al siguiente:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Para obtener más información, vea [HTML Div Control](../Topic/HTML%20Div%20Control.md), [Label Web Server Control Overview](../Topic/Label%20Web%20Server%20Control%20Overview.md) y <xref:System.Web.UI.WebControls.Label>.  
  
## Vea también  
 [cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Estándar \(Ficha\), Cuadro de herramientas](../Topic/Standard%20Tab,%20Toolbox.md)   
 [HTML Controls](../Topic/HTML%20Controls%20for%20ASP.NET%20Web%20Pages.md)