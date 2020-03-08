---
title: Fuentes y formato
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ede8844b34473e1c900bd6af040cac99ceee1514
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409899"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fuentes y formato de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_TheEnvironmentFont"></a>La fuente del entorno
 Todas las fuentes de Visual Studio deben exponerse al usuario para su personalización. Esto se realiza principalmente a través de la página **fuentes y colores** del cuadro de diálogo **Herramientas > opciones** . Las tres categorías principales de configuración de fuentes son:

- **Fuente del entorno** : la fuente principal del IDE (entorno de desarrollo integrado), que se usa para todos los elementos de la interfaz, incluidos los cuadros de diálogo, menús, ventanas de herramientas y ventanas de documento. De forma predeterminada, la fuente del entorno está ligada a una fuente del sistema que aparece como 9 pt Segoe UI en las versiones actuales de Windows. El uso de una fuente para todos los elementos de interfaz ayuda a garantizar un aspecto de fuente coherente en todo el IDE.

- **Editor de texto** : los elementos que se muestran en el código y en otros editores basados en texto se pueden personalizar en la página del editor de texto en **Herramientas > opciones**.

- **Colecciones específicas** : las ventanas del diseñador que ofrecen personalización del usuario de sus elementos de interfaz pueden exponer fuentes específicas de su superficie de diseño en su propia página de configuración en **Herramientas > opciones**.

### <a name="editor-font-customization-and-resizing"></a>Personalización de fuentes y cambio de tamaño del editor
 A menudo, los usuarios amplían o amplían el tamaño y el color del texto en el editor según sus preferencias, independientemente de la interfaz de usuario general. Dado que la fuente del entorno se usa en los elementos que pueden aparecer en o como parte de un editor o diseñador, es importante tener en cuenta el comportamiento esperado cuando se cambia una de estas clasificaciones de fuentes.

 Al crear elementos de interfaz de usuario que aparecen en el editor pero que no forman parte del *contenido*, es importante usar la fuente del entorno y no la fuente del texto para que los elementos cambien de tamaño de una manera predecible.

1. Para el texto de código en el editor, cambie el tamaño con la configuración fuente de texto de código y responda al nivel de zoom del texto del editor.

2. Todos los demás elementos de la interfaz deben estar vinculados a la configuración de la fuente del entorno y responder a los cambios globales en el entorno. Esto incluye (pero no se limita a):

    - Texto en menús contextuales

    - Texto en un elemento gráfico del editor, como texto de menú de bombilla de luz, panel del editor de búsqueda rápida y panel de navegación

    - Texto de etiqueta en los cuadros de diálogo, como buscar en archivos o refactorizar

### <a name="accessing-the-environment-font"></a>Obtener acceso a la fuente del entorno
 En código nativo o de WinForms, se puede tener acceso a la fuente del entorno llamando al método **IUIHostLocale:: GetDialogFont** después de consultar la interfaz desde el servicio de SID_SUIHostLocale.

 Para Windows Presentation Foundation (WPF), derive la clase de ventana de cuadro de diálogo de la clase **DialogWindow** del shell en lugar de la clase de **ventana** de WPF.

 En XAML, el código tiene el siguiente aspecto:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (Reemplace `Microsoft.VisualStudio.Shell.11.0` por la versión actual del archivo dll MPF).

 Para mostrar el cuadro de diálogo, llame a "**ShowModal ()** " en la clase sobre **ShowDialog ()** . **ShowModal ()** establece el estado modal correcto en el Shell, garantiza que el cuadro de diálogo esté centrado en la ventana primaria, etc.

 El código es el siguiente:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** devuelve un booleano? (booleano que acepta valores NULL) con **DialogResult**, que se puede usar si es necesario. El valor devuelto es true si el cuadro de diálogo se cerró **correctamente**.

 Si necesita mostrar una interfaz de usuario de WPF que no es un cuadro de diálogo y se hospeda en su propio **HwndSource**, como una ventana emergente o una ventana secundaria de WPF de una ventana de ventana primaria de Win32/WinForms, deberá establecer **FontFamily** y **FontSize** en el elemento raíz del elemento de WPF. (El Shell establece las propiedades en la ventana principal, pero no se heredarán más allá del HWND). El Shell proporciona recursos a los que se pueden enlazar las propiedades, de la siguiente manera:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="BKMK_Formatting"></a>Referencia de formato (escalado o negrita)
 Algunos cuadros de diálogo requieren que el texto determinado esté en negrita o un tamaño distinto de la fuente del entorno. Anteriormente, las fuentes mayores que la fuente del entorno se codificaban como "fuente de entorno + 2" o similares. El uso de los fragmentos de código proporcionados admitirá monitores de alta PPP y se asegurará de que el texto de la pantalla aparezca siempre con el tamaño y el peso correctos (como la luz o la semiluz).

> **Nota: antes de aplicar el formato, asegúrese de seguir las instrucciones que se encuentran en [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**

 Para escalar la fuente del entorno, establezca el estilo del TextBlock o de la etiqueta como se indica. Cada uno de estos fragmentos de código, que se usan correctamente, generará la fuente correcta, incluidas las variaciones de tamaño y peso apropiadas.

 Donde "vsui" es una referencia al espacio de nombres Microsoft. VisualStudio. Shell:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>375% de fuente de entorno + claro
 **Aparece como:** 34 PT Segoe UI claro

 **Use para** una interfaz de usuario de marca única (poco frecuente), como en la página de inicio.

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>310% de fuente de entorno + claro
 **Aparece como:** 28 PT Segoe UI luz

 **Usar para: títulos de** cuadro de diálogo de firma grande, encabezado principal en informes

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>fuente de entorno de 200% + semiligera
 **Aparece como:** 18 PT Segoe UI semilight

 **Usar para:** subtítulos, títulos en cuadros de diálogo pequeños y medianos

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>155% de la fuente del entorno
 **Aparece como:** 14 PT Segoe UI

 **Usar para:** encabezados de sección en la interfaz de usuario o los informes de documentos

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>133% de la fuente del entorno
 **Aparece como:** 12 pt Segoe UI

 **Usar para:** subtítulos más pequeños en los cuadros de diálogo de firma y la interfaz de usuario del documento

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>122% de la fuente del entorno
 **Aparece como:** 11 pt Segoe UI

 **Usar para:** encabezados de sección en cuadros de diálogo de firma, nodos principales en la vista de árbol, navegación por tabulación vertical

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Fuente de entorno + negrita
 **Aparece como:** Bolded 9 pt Segoe UI

 **Usar para:** etiquetas y subencabezados en cuadros de diálogo de firma, informes y interfaz de usuario de documentos

 **Código de procedimientos:** Donde "textBlock" es un TextBlock definido previamente y "Label" es una etiqueta definida previamente.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** Establezca el estilo del TextBlock o la etiqueta como se muestra.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Estilos localizables
 En algunos casos, los localizadores deberán modificar los estilos de fuente para diferentes configuraciones regionales, como quitar el texto en negrita para los idiomas de Asia oriental. Para que la localización de los estilos de fuente sea posible, dichos estilos deben estar dentro del archivo. resx. La mejor manera de lograrlo y editar los estilos de fuente en el diseñador de formularios de Visual Studio es establecer explícitamente los estilos de fuente en tiempo de diseño. Aunque esto crea un objeto de fuente completo y podría parecer interrumpir la herencia de fuentes primarias, solo se usa la propiedad FontStyle para establecer la fuente.

 La solución consiste en enlazar el evento **FontChanged** del formulario de cuadro de diálogo. En el evento **FontChanged** , recorra todos los controles y compruebe si se ha establecido su fuente. Si se establece, cámbielo a una nueva fuente basada en la fuente del formulario y el estilo de fuente anterior del control. Un ejemplo de esto en el código es:

```
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 El uso de este código garantiza que cuando se actualice la fuente del formulario, las fuentes de controles también se actualizarán. También se debe llamar a este método desde el constructor del formulario, porque el cuadro de diálogo podría no obtener una instancia de **IUIService** y el evento **FontChanged** nunca se activará. El enlace de **FontChanged** permitirá que los cuadros de diálogo recojan dinámicamente la nueva fuente incluso si el cuadro de diálogo ya está abierto.

### <a name="testing-the-environment-font"></a>Probar la fuente del entorno
 Para asegurarse de que la interfaz de usuario usa la fuente del entorno y respeta la configuración de tamaño, Abra **herramientas > opciones > entorno > fuentes y colores** y seleccione "fuente de entorno" en el menú desplegable "Mostrar configuración para:".

 ![Página fuentes y colores del cuadro &#62; de diálogo Opciones de herramientas](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **Configuración de fuentes y colores en el cuadro de diálogo Herramientas > Opciones**

 Establezca la fuente en un valor muy diferente al predeterminado. Para que sea obvio qué interfaz de usuario no se actualiza, elija una fuente con serifs (por ejemplo, "Times New Roman") y establezca un tamaño muy grande. A continuación, pruebe la interfaz de usuario para asegurarse de que respeta el entorno. Este es un ejemplo de uso del cuadro de diálogo de licencia:

 ![Ejemplo de cuadro de diálogo que no usa la fuente del entorno](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno**

 En este caso, "información de usuario" e "información del producto" no respetan la fuente. En algunos casos, puede tratarse de una opción de diseño explícita, pero puede ser un error si la fuente explícita no se especifica como parte de las especificaciones de la referencia de la característica.

 Para restablecer la fuente, haga clic en "usar valores predeterminados" en **herramientas > opciones > entorno > fuentes y colores**.

## <a name="BKMK_TextStyle"></a>Estilo de texto
 El estilo de texto hace referencia al tamaño, el peso y la grafía de la fuente. Para obtener instrucciones sobre la implementación, consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Grafía de texto

#### <a name="all-caps"></a>Todo mayúsculas
 No use mayúsculas para títulos o etiquetas en Visual Studio.

#### <a name="all-lowercase"></a>Todo en minúsculas
 No use todo en minúsculas para títulos o etiquetas en Visual Studio.

#### <a name="sentence-and-title-case"></a>Mayúsculas y minúsculas de oraciones
 El texto de Visual Studio debe usar mayúsculas o minúsculas de título, en función de la situación.

|Usar el caso de título para:|Usar el caso de oración para:|
|-------------------------|----------------------------|
|Títulos de diálogo|Etiquetas|
|Cuadros de grupo|Casillas de verificación|
|Elementos de menú|Botones de radio|
|Elementos del menú contextual|Elementos del cuadro de lista|
|Botones|Barras de estado|
|Etiquetas de tabla||
|Encabezados de columna||
|Información sobre herramientas||

##### <a name="title-case"></a>Tipo título
 El uso de mayúsculas y minúsculas es un estilo en el que las primeras letras de la mayoría o todas las palabras de una frase se escriben en mayúsculas. En Visual Studio, el caso de título se usa para muchos elementos, incluidos:

- **Información sobre herramientas.** Ejemplo: "vista previa de los elementos seleccionados"

- **Encabezados de columna.** Ejemplo: "respuesta del sistema"

- **Elementos de menú.** Ejemplo: "guardar todo"

  Cuando se usan las mayúsculas y minúsculas de título, estas son las directrices sobre cuándo poner en mayúsculas las palabras y cuándo dejarlas en minúsculas:

|Uppercase|Comentarios y ejemplos|
|---------------|---------------------------|
|Todos los nombres||
|Todos los verbos|Incluir "es" y otras formas de "para"|
|Todos los adverbios|Incluir "es" y "When"|
|Todos los adjetivos|Incluir "this" y "eso"|
|Todos los pronombres|Al incluir el Possessive "su", así como "es", una contracción del pronombres "it" y el verbo "is"|
|Primera y última palabra, independientemente de las partes de la voz||
|Preposiciones que forman parte de una frase de verbo|"Cerrar todas las ventanas" o "apagar el sistema"|
|Todas las letras de un acrónimo|HTML, XML, URL, IDE, RGB|
|La segunda palabra de una palabra compuesta si es un sustantivo o un adjetivo adecuado, o si las palabras tienen el mismo peso.|Referencia cruzada, software anterior a Microsoft, acceso de lectura y escritura, tiempo de ejecución|

|Minúsculas|Ejemplos|
|---------------|--------------|
|La segunda palabra de una palabra compuesta si es otra parte de la voz o un participio modificando la primera palabra|Procedimientos, desactivación|
|Artículos, a menos que uno sea la primera palabra del título|un,, el|
|Coordenadas de coordenadas|y, pero, para, y, o|
|Coloca las preposiciones con palabras de cuatro o menos letras fuera de una frase verbal|en, en, como para, fuera de, en la parte superior de|
|"A" cuando se usa en una frase infinita|"Cómo formatear el disco duro"|

##### <a name="sentence-case"></a>Caso de oración
 El caso de oración es el método de uso de mayúsculas estándar para escribir en el que solo se pone en mayúscula la primera palabra de la frase, junto con los nombres propios y el pronombres "I". En general, el caso de la oración es más fácil de leer para un público internacional, especialmente cuando el contenido se traducirá en una máquina. Usar el caso de oración para:

1. **Mensajes de la barra de estado.** Estos son simples, cortos y solo proporcionan información de estado. Ejemplo: "cargando el archivo del proyecto"

2. **Todos los demás elementos**de la interfaz de usuario, incluidas las etiquetas, las casillas, los botones de radio y los elementos del cuadro de lista. Ejemplo: "seleccionar todos los elementos de la lista"

### <a name="text-formatting"></a>Formato del texto
 [La fuente del entorno controla el](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)formato de texto predeterminado en Visual Studio 2013. Este servicio ayuda a garantizar una apariencia de fuente coherente en todo el IDE (entorno de desarrollo integrado) y debe usarlo para garantizar una experiencia coherente para los usuarios.

 El tamaño predeterminado que usa el servicio de fuentes de Visual Studio procede de Windows y aparece como 9 pt.

 Puede aplicar formato a la fuente del entorno. En este tema se explica cómo y dónde usar los estilos. Para obtener información de implementación, consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Texto en negrita
 El texto en negrita se usa con moderación en Visual Studio y se debe reservar para:

- Etiquetas de preguntas en los asistentes

- designar el proyecto activo en Explorador de soluciones

- valores invalidados en la ventana de herramientas propiedades

- algunos eventos de las listas desplegables del editor de Visual Basic

- contenido generado por el servidor en el esquema del documento para páginas web

- encabezados de sección en interfaz de usuario de diseñador o cuadro de diálogo complejos

#### <a name="italics"></a>Cursiva
 Visual Studio no usa texto en cursiva o en negrita.

#### <a name="color"></a>Color

- Blue está reservado para hipervínculos (navegación y comandos) y nunca se debe usar para la orientación.

- Los encabezados mayores (fuente de entorno x 155% o superior) se pueden colorear para estos propósitos:

  - Para proporcionar una apelación visual de la firma de la interfaz de usuario de Visual Studio

  - Para llamar la atención sobre un área específica

  - Para ofrecer alivio en el color del texto del entorno gris oscuro/negro oscuro

- El color de los encabezados debe aprovechar los colores existentes de la marca de Visual Studio, principalmente el Purple principal #FF68217A.

- Al usar el color en los encabezados, debe cumplir las instrucciones de [color de Windows](https://msdn.microsoft.com/library/dn742482.aspx), incluida la relación de contraste y otras consideraciones de accesibilidad.

### <a name="font-size"></a>Tamaño de fuente
 El diseño de la interfaz de usuario de Visual Studio presenta un aspecto más claro con más espacio en blanco. Siempre que sea posible, los cromos y las barras de título se han reducido o quitado. Aunque la densidad de la información es un requisito de Visual Studio, la tipografía sigue siendo importante, con énfasis en el interlineado más abierto y en una variación de los tamaños de fuente y pesos.

 En las tablas siguientes se incluyen los detalles del diseño y los ejemplos visuales de las fuentes de presentación usadas en Visual Studio. Algunas variaciones de fuente de la pantalla tienen el tamaño y el peso, como semilight o Light, codificados en su apariencia.

 Los fragmentos de código de implementación para todas las fuentes de presentación se pueden encontrar en [referencia de formato (escalado y negrita)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>375% de fuente de entorno + claro

|||
|-|-|
|**Uso:** Menos. Solo interfaz de usuario con marca única.<br /><br /> **No**<br /><br /> -Usar el caso de oración<br />-Usar siempre el peso claro<br /><br /> **No:**<br /><br /> -Se usa para la interfaz de usuario distinta de la interfaz de usuario de firma como la página de inicio<br />-Negrita, cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Usar en ventanas de herramientas|**Aparece como:** 34 PT Segoe UI claro<br /><br /> **Ejemplo visual:**<br /><br /> *No se usa actualmente. Se puede usar en la página de inicio.*|

#### <a name="310-environment-font--light"></a>310% de fuente de entorno + claro

|||
|-|-|
|**Uso:**<br /><br /> -Encabezado más grande en los cuadros de diálogo de firma<br />-Encabezado del informe principal<br /><br /> **No**<br /><br /> -Usar el caso de oración<br />-Usar siempre el peso claro<br /><br /> **No:**<br /><br /> -Se usa para la interfaz de usuario distinta de la interfaz de usuario de firma como la página de inicio<br />-Negrita, cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Usar en ventanas de herramientas|**Aparece como:** 28 PT Segoe UI luz<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado de luz de &#43; fuente del entorno 310%](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>fuente de entorno de 200% + semiligera

|||
|-|-|
|**Uso:**<br /><br /> -Subtítulos<br />-Títulos en cuadros de diálogo pequeños y medianos<br /><br /> **No**<br /><br /> -Usar el caso de oración<br />-Usar siempre el peso semiclaro<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Usar en ventanas de herramientas|**Aparece como:** 18 PT Segoe UI Semillight<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de la fuente &#43; del entorno de 200% semiligera](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% de la fuente del entorno

|||
|-|-|
|**Uso:**<br /><br /> -Encabezados de sección en la interfaz de usuario del documento<br />-Informes<br /><br /> **Haga lo siguiente:** Usar el caso de oración<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Se usa en controles estándar de Visual Studio<br />-Usar en ventanas de herramientas|**Aparece como:** 14 PT Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado de fuente del entorno 155%](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% de la fuente del entorno

|||
|-|-|
|**Uso:**<br /><br /> -Subtítulos más pequeños en los cuadros de diálogo de firma<br />-Subtítulos más pequeños en la interfaz de usuario del documento<br /><br /> **Haga lo siguiente:** Usar el caso de oración<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Se usa en controles estándar de Visual Studio<br />-Usar en ventanas de herramientas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado de fuente del entorno 133%](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% de la fuente del entorno

|||
|-|-|
|**Uso:**<br /><br /> -Encabezados de sección en los cuadros de diálogo de firma<br />-Nodos superiores en la vista de árbol<br />-Navegación por tabulación vertical<br /><br /> **Haga lo siguiente:** Usar el caso de oración<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Se usa en controles estándar de Visual Studio<br />-Usar en ventanas de herramientas|**Aparece como:** 11 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado de fuente del entorno 122%](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Fuente de entorno + negrita

|||
|-|-|
|**Uso:**<br /><br /> -Etiquetas y subencabezados en los cuadros de diálogo de firma<br />-Etiquetas y subencabezados en informes<br />-Etiquetas y subencabezados en la interfaz de usuario del documento<br /><br /> **No**<br /><br /> -Usar el caso de oración<br />-Usar el grosor de negrita<br /><br /> **No:**<br /><br /> -Cursiva o negrita cursiva<br />-Se usa para el texto del cuerpo<br />-Se usa en controles estándar de Visual Studio<br />-Usar en ventanas de herramientas|**Aparece como:** Bolded 9 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado de &#43; negrita de fuente de entorno](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Fuente del entorno

|||
|-|-|
|**Uso:** El resto del texto<br /><br /> **Haga lo siguiente:** Usar el caso de oración<br /><br /> **No:** Cursiva o negrita cursiva|**Aparece como:** 9 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente de entorno](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Relleno y espaciado
 Los encabezados requieren espacio alrededor de ellos para darles el énfasis adecuado. Este espacio varía en función del tamaño del punto y de lo que está cerca del encabezado, como una regla horizontal o una línea de texto en la fuente del entorno.

- El relleno ideal para un encabezado solo debe ser el 90% del espacio de alto de los caracteres de mayúsculas. Por ejemplo, un encabezado de luz de 28 PT Segoe UI tiene un alto de 26 PT y el relleno debe ser aproximadamente 23 PT o aproximadamente 31 píxeles.

- El espacio mínimo alrededor de un encabezado debe ser el 50% del alto del carácter de mayúscula. Se puede usar menos espacio cuando un encabezado está acompañado por una regla u otro elemento de ajuste estrecho.

- El texto de la fuente de entorno en negrita debe seguir el espaciado y relleno de alto de línea predeterminados.

## <a name="see-also"></a>Consulte también
 [MSDN: Fonts (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: texto de la interfaz de usuario (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
