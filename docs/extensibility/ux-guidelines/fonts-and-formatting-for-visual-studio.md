---
title: Fuentes y formato para Visual Studio | Microsoft Docs
description: Obtenga información sobre las fuentes y el formato de las nuevas características que diseñe Visual Studio, incluido cómo usar la fuente del entorno.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e6e26b18c838fc240d7fab398f8626890eed0d31
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901687"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fuentes y formato de Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Fuente del entorno
 Todas las fuentes Visual Studio deben exponerse al usuario para su personalización. Esto se realiza principalmente a través de la página **Fuentes y colores** del cuadro de diálogo Herramientas > **opciones.** Las tres categorías principales de configuración de fuentes son:

- **Fuente de entorno:** fuente principal del IDE (entorno de desarrollo integrado), que se usa para todos los elementos de interfaz, incluidos los cuadros de diálogo, los menús, las ventanas de herramientas y las ventanas de documentos. De forma predeterminada, la fuente del entorno está asociada a una fuente del sistema que aparece como 9 puntos Segoe UI en las versiones actuales de Windows. El uso de una fuente para todos los elementos de interfaz ayuda a garantizar una apariencia de fuente coherente en todo el IDE.

- **Editor de texto:** los elementos que se abren en código y otros editores basados en texto se pueden personalizar en la página Editor de texto de **Herramientas > opciones**.

- **Colecciones específicas: las** ventanas de diseñador que ofrecen personalización de usuario de sus elementos de interfaz pueden exponer fuentes específicas de su superficie de diseño en su propia página de configuración de **Herramientas > opciones**.

### <a name="editor-font-customization-and-resizing"></a>Personalización y tamaño de fuente del editor
 A menudo, los usuarios amplían o amplían el tamaño o el color del texto en el editor según sus preferencias, independientemente de la interfaz de usuario general. Dado que la fuente del entorno se usa en elementos que pueden aparecer dentro o como parte de un editor o diseñador, es importante tener en cuenta el comportamiento esperado cuando se cambia una de estas clasificaciones de fuentes.

 Al crear elementos de la interfaz de usuario que aparecen en el editor pero que no forman parte del contenido *,* es importante usar la fuente del entorno y no la fuente de texto para que los elementos cambien de tamaño de forma predecible.

1. Para el texto de código en el editor, cambie el tamaño con la configuración de fuente de texto de código y responda al nivel de zoom del texto del editor.

2. Todos los demás elementos de la interfaz deben estar vinculados a la configuración de fuente del entorno y responder a cualquier cambio global en el entorno. Entre otras cosas, esto incluye:

    - Texto en menús contextuales

    - Texto en un adorno del editor, como texto de menú de bombilla, panel del editor de búsqueda rápida y navegación al panel

    - Etiquetar texto en cuadros de diálogo, como **Buscar en archivos** o **Refactorizar**

### <a name="accessing-the-environment-font"></a>Acceso a la fuente del entorno
 En el código nativo o WinForms, se puede acceder a la fuente del entorno llamando al método después de consultar `IUIHostLocale::GetDialogFont` la interfaz desde el `SID_SUIHostLocale` servicio.

 Para Windows Presentation Foundation (WPF), derive la clase de ventana de diálogo de la clase del shell en `DialogWindow` lugar de la clase de `Window` WPF.

 En XAML, el código tiene el siguiente aspecto:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Código subyacente:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Reemplace `Microsoft.VisualStudio.Shell.11.0` por la versión actual del archivo DLL de MPF).

 Para mostrar el cuadro de diálogo, llame a " `ShowModal()` " en la clase sobre `ShowDialog()` . `ShowModal()` establece el estado modal correcto en el shell, garantiza que el cuadro de diálogo está centrado en la ventana primaria, y así sucesivamente.

 El código es el siguiente:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` devuelve un valor bool? (booleano que acepta valores NULL) con `DialogResult` , que se puede usar si es necesario. El valor devuelto es true si el cuadro de diálogo se cerró con **Aceptar.**

 Si necesita mostrar alguna interfaz de usuario de WPF que no es un cuadro de diálogo y se hospeda en su propia , como una ventana emergente o una ventana secundaria de WPF de una ventana primaria `HwndSource` Win32/WinForms, deberá establecer y en el elemento raíz del elemento `FontFamily` `FontSize` WPF. (El shell establece las propiedades en la ventana principal, pero no se heredarán después de `HWND` ). El shell proporciona recursos a los que se pueden enlazar las propiedades, de la siguiente forma:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Referencia de formato (escalado/negrita)
 Algunos diálogos requieren que el texto concreto esté en negrita o un tamaño distinto de la fuente del entorno. Anteriormente, las fuentes más grandes que la fuente del entorno se codificaban como " `environment font +2` " o similar. El uso de los fragmentos de código proporcionados admitirá monitores con valores altos de PPP y garantizará que el texto para mostrar siempre aparece con el tamaño y el peso correctos (como Light o Semilight).

> [!NOTE]
> Antes de aplicar el formato, asegúrese de seguir las instrucciones que se encuentran en [Estilo de texto.**](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

 Para escalar la fuente del entorno, establezca el estilo de TextBlock o Label como se indica. Cada uno de estos fragmentos de código, que se usan correctamente, generará la fuente correcta, incluidas las variaciones de tamaño y peso adecuadas.

 Donde " `vsui` " es una referencia al espacio de nombres `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>Fuente de entorno del 375 % + luz

**Aparece como:** 34 pt Segoe UI Claro

::: moniker range="vs-2017"

**Use para:** (poco frecuente) interfaz de usuario única de marca, como en la página de inicio

::: moniker-end

::: moniker range=">=vs-2019"

**Uso para:** (poco frecuente) interfaz de usuario única de marca

::: moniker-end

**Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Establezca el estilo de TextBlock o Label como se muestra.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>Fuente de entorno del 310 % + luz
 **Aparece como:** 28 pt Segoe UI Light **Use for:** large signature dialog titles, main heading in reports

 **Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Establezca el estilo de TextBlock o Label como se muestra.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>Fuente de entorno 200 % + Semilight
 **Aparece como:** 18 pt Segoe UI Semilight **Use for:** subheadings, titles in small and medium dialogs

 **Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Establezca el estilo de TextBlock o Label como se muestra:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>Fuente de entorno del 155 %
 **Aparece como:** 14 pt Segoe UI **Use for:** section headings in document well UI or reports

 **Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Establezca el estilo de TextBlock o Label como se muestra:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>Fuente de entorno del 133 %
 **Aparece como:** 12 pt Segoe UI **Use for:** smaller subheadings in signature dialogs and document well UI

 **Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Establezca el estilo de TextBlock o Label como se muestra:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>Fuente de entorno del 122 %
 **Aparece como:** 11 pt Segoe UI **Use for:** section headings in signature dialogs, top nodes in tree view, vertical tab navigation

 **Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Establezca el estilo de TextBlock o Label como se muestra:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Fuente del entorno + negrita
 **Aparece como: 9** pt en negrita Segoe UI **usar para:** etiquetas y subheads en los cuadros de diálogo de firma, informes y la interfaz de usuario del documento.

 **Código de procedimiento:** Donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Establezca el estilo de TextBlock o Label como se muestra:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Estilos localizables
 En algunos casos, los localizadores tendrán que modificar los estilos de fuente para diferentes configuraciones regionales, como quitar la negrita del texto para idiomas de Este de Asia. Para que la localización de estilos de fuente sea posible, esos estilos deben estar dentro del archivo .resx. La mejor manera de lograr esto y editar los estilos de fuente en el diseñador de formularios Visual Studio es establecer explícitamente los estilos de fuente en tiempo de diseño. Aunque esto crea un objeto de fuente completo y puede parecer interrumpir la herencia de fuentes primarias, solo se usa la propiedad FontStyle para establecer la fuente.

 La solución es enlazar el evento del formulario de `FontChanged` diálogo. En el `FontChanged` caso de que se deba, revise todos los controles y compruebe si su fuente está establecida. Si se establece, cámbiese a una nueva fuente según la fuente del formulario y el estilo de fuente anterior del control. Un ejemplo de esto en el código es:

```csharp
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

 El uso de este código garantiza que, cuando se actualice la fuente del formulario, también se actualizarán las fuentes de los controles. También se debe llamar a este método desde el constructor del formulario, ya que es posible que el cuadro de diálogo no obtenga una instancia de y el `IUIService` `FontChanged` evento nunca se desen marcha. El enlace permitirá a los diálogos seleccionar `FontChanged` dinámicamente la nueva fuente, incluso si el diálogo ya está abierto.

### <a name="testing-the-environment-font"></a>Prueba de la fuente del entorno
 Para asegurarse de que la interfaz de usuario usa la fuente del entorno y respeta la configuración de tamaño, abra Herramientas > Opciones > Entorno **>** Fuentes y colores y seleccione "Fuente del entorno" en el menú desplegable "Mostrar configuración para:".

 ![Configuración de fuentes y colores en el cuadro de &gt; diálogo Opciones de herramientas](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Configuración de fuentes y colores en el cuadro de &gt; diálogo Opciones de herramientas

 Establezca la fuente en algo muy diferente del valor predeterminado. Para que sea obvio qué interfaz de usuario no se actualiza, elija una fuente con serifas (como "Times New Roman") y establezca un tamaño muy grande. A continuación, pruebe la interfaz de usuario para asegurarse de que respeta el entorno. Este es un ejemplo de uso del cuadro de diálogo de licencia:

 ![Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno

 En este caso, "Información de usuario" e "Información del producto" no respetan la fuente. En algunos casos, podría ser una opción de diseño explícita, pero puede ser un error si no se especifica la fuente explícita como parte de las especificaciones de línea roja.

 Para restablecer la fuente, haga clic en "Usar valores predeterminados" en Herramientas > opciones > **Environment > Fuentes y colores.**

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Estilo de texto
 El estilo de texto hace referencia al tamaño, el peso y las mayúsculas y minúsculas de la fuente. Para obtener instrucciones de implementación, vea [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Mayúsculas y minúsculas de texto

#### <a name="all-caps"></a>Todos los límites
 No use todos los límites para títulos o etiquetas en Visual Studio.

#### <a name="all-lowercase"></a>Todo en minúsculas
 No use todas las minúsculas para títulos o etiquetas en Visual Studio.

#### <a name="sentence-and-title-case"></a>Mayúsculas y minúsculas de oración y título
 El texto de Visual Studio debe usar mayúsculas y minúsculas de título o frase, en función de la situación.

|Use el caso de título para:|Use el caso de oración para:|
|-------------------------|----------------------------|
|Títulos de diálogo|Etiquetas|
|Cuadros de grupo|Casillas|
|Elementos de menú|Botones de radio|
|Elementos del menú contextual|Elementos de cuadro de lista|
|Botones|Barras de estado|
|Etiquetas de tabla||
|Encabezados de columna||
|Información sobre herramientas||

##### <a name="title-case"></a>Tipo título
 El caso de título es un estilo en el que se escriben en mayúsculas las primeras letras de la mayoría o todas las palabras de una frase. En Visual Studio, el título se usa para muchos elementos, entre los que se incluyen:

- **Tooltips.** Ejemplo: "Vista previa de los elementos seleccionados"

- **Encabezados de columna.** Ejemplo: "Respuesta del sistema"

- **Elementos de menú.** Ejemplo: "Guardar todo"

  Al usar mayúsculas y minúsculas, estas son las directrices para saber cuándo se van a usar las palabras en mayúsculas y cuándo dejarlas en minúsculas:

|Mayúsculas|Comentarios y ejemplos|
|---------------|---------------------------|
|Todos los nombres||
|Todos los verbos|Incluir "Is" y otras formas de "ser"|
|Todos los adverbs|Incluir "Than" y "When"|
|Todos los adjetivos|Incluir "This" y "That"|
|Todos los pronombres|Incluir el posesivo "Its" y "It's", una contracción del pronombre "it" y el verbo "is"|
|Primera y última palabra, independientemente de las partes de la voz||
|Preposiciones que forman parte de una frase verbal|"Cerrar todas las ventanas" o "Apagar el sistema"|
|Todas las letras de un acrónimo|HTML, XML, URL, IDE, RGB|
|La segunda palabra de una palabra compuesta si es un sustantivo o un adjetivo adecuado, o si las palabras tienen el mismo peso|Referencia cruzada, software anterior a Microsoft, acceso de lectura y escritura, Run-Time|

|Minúsculas|Ejemplos|
|---------------|--------------|
|La segunda palabra de una palabra compuesta si es otra parte de la voz o un participio que modifica la primera palabra.|Cómo, Despegar|
|Artículos, a menos que uno sea la primera palabra del título|un, una, el, la|
|Conjunciones de coordenadas|y, pero, para, ni, o|
|Preposiciones con palabras de cuatro o menos letras fuera de una frase verbal|en, en, como para, fuera de, encima de|
|"To" cuando se usa en una frase infinitiva|"Cómo dar formato al disco duro"|

##### <a name="sentence-case"></a>Caso de oración
 El caso de oración es el método de mayúsculas estándar para escribir en el que solo se escribe en mayúscula la primera palabra de la frase, junto con los nombres propios y el pronombre "I". En general, el caso de oración es más fácil de leer para una audiencia mundial, especialmente cuando un equipo traducirá el contenido. Use el caso de oración para:

1. **Mensajes de la barra de estado.** Son simples, breves y solo proporcionan información de estado. Ejemplo: "Carga del archivo de proyecto"

2. **Todos los demás elementos de la interfaz de** usuario, incluidas las etiquetas, las casillas, los botones de radio y los elementos del cuadro de lista. Ejemplo: "Seleccionar todos los elementos de la lista"

### <a name="text-formatting"></a>Formato del texto
 El formato de texto predeterminado en Visual Studio 2013 se controla mediante [la fuente de entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Este servicio ayuda a garantizar una apariencia de fuente coherente en todo el IDE (entorno de desarrollo integrado) y debe usarlo para garantizar una experiencia coherente para los usuarios.

 El tamaño predeterminado utilizado por el servicio Visual Studio fuente procede de Windows y aparece como 9 puntos.

 Puede aplicar formato a la fuente del entorno. En este tema se explica cómo y dónde usar estilos. Para obtener información sobre la implementación, consulte [La fuente de entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Texto en negrita
 El texto en negrita se usa con moderación Visual Studio y debe reservarse para:

- etiquetas de preguntas en asistentes

- designación del proyecto activo en Explorador de soluciones

- valores reemplazados en la ventana de herramientas Propiedades

- determinados eventos en las listas desplegables Visual Basic editor de archivos

- contenido generado por el servidor en el esquema del documento para páginas web

- encabezados de sección en diálogo complejo o interfaz de usuario del diseñador

#### <a name="italics"></a>Cursiva
 Visual Studio texto cursiva o cursiva en negrita.

#### <a name="color"></a>Color

- El azul está reservado para hipervínculos (navegación y comandos) y nunca debe usarse para la orientación.

- Los encabezados más grandes (fuente del entorno x 155 % o superior) se pueden colorear con estos fines:

  - Para proporcionar un atractivo visual a la interfaz de usuario Visual Studio firma

  - Para llamar la atención sobre un área específica

  - Para ofrecer relieve del color de texto estándar del entorno gris oscuro/negro

- El color de los encabezados debe aprovechar los Visual Studio de marca existentes, principalmente el púrpura principal, #FF68217A.

- Al usar el color en los encabezados, debe cumplir las directrices de color de [Windows,](/windows/desktop/uxguide/vis-color)incluida la relación de contraste y otras consideraciones de accesibilidad.

### <a name="font-size"></a>Tamaño de fuente
 Visual Studio diseño de la interfaz de usuario presenta una apariencia más ligera con más espacio en blanco. Siempre que sea posible, las barras de chrome y title se han reducido o quitado. Aunque la densidad de la información es un requisito en Visual Studio, la tipografía sigue siendo importante, con un énfasis en un espaciado de línea más abierto y una variación de los tamaños y pesos de las fuentes.

 En las tablas siguientes se incluyen detalles de diseño y ejemplos visuales de las fuentes para mostrar usadas Visual Studio. Algunas variaciones de fuente de presentación tienen el tamaño y el peso, como Semilight o Light, codificados en su apariencia.

 Los fragmentos de código de implementación para todas las fuentes para mostrar se pueden encontrar en la referencia formato [(escalado/negrita).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>Fuente de entorno del 375 % + luz

|Uso|Aspecto|
|-|-|
|**Uso:** Raro. Solo interfaz de usuario de marca única.<br /><br /> **hacer:**<br /><br /> - Uso de mayúsculas y minúsculas<br />- Usar siempre peso ligero<br /><br /> **No:**<br /><br /> - Se usa para la interfaz de usuario que no sea la de firma, como la página de inicio.<br />- Negrita, cursiva o cursiva en negrita<br />- Usar para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 34 pt Segoe UI Light<br /><br /> **Ejemplo visual:**<br /><br /> *Actualmente no se usa. Se puede usar en la Visual Studio inicio de 2017.*|

#### <a name="310-environment-font--light"></a>Fuente de entorno del 310 % + luz

::: moniker range="vs-2017"

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Encabezado más grande en los diálogos de firma<br />- Encabezado del informe principal<br /><br /> **hacer:**<br /><br /> - Uso de mayúsculas y minúsculas<br />- Usar siempre peso ligero<br /><br /> **No:**<br /><br /> - Se usa para la interfaz de usuario que no sea la de firma, como la página de inicio.<br />- Negrita, cursiva o cursiva en negrita<br />- Usar para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 28 pt Segoe UI Claro<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente de entorno del 310 % &#43; encabezado Light](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Encabezado más grande en los diálogos de firma<br />- Encabezado del informe principal<br /><br /> **hacer:**<br /><br /> - Uso de mayúsculas y minúsculas<br />- Usar siempre peso ligero<br /><br /> **No:**<br /><br /> - Usar para la interfaz de usuario que no sea la interfaz de usuario de firma<br />- Negrita, cursiva o cursiva en negrita<br />- Usar para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 28 pt Segoe UI Claro<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente de entorno del 310 % &#43; encabezado Light](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>Fuente de entorno 200 % + Semilight

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Subpartidas<br />- Títulos en diálogos pequeños y medianos<br /><br /> **hacer:**<br /><br /> - Uso de mayúsculas y minúsculas<br />- Use siempre el peso Semilight<br /><br /> **No:**<br /><br /> - Negrita, cursiva o cursiva en negrita<br />- Usar para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 18 pt Segoe UI Semillight<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente de entorno del 200 % &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>Fuente de entorno del 155 %

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Encabezados de sección en la interfaz de usuario del área de trabajo del documento<br />- Informes<br /><br /> **Haga lo siguiente:** Uso de mayúsculas y minúsculas<br /><br /> **No:**<br /><br /> - Negrita, cursiva o cursiva en negrita<br />- Usar para el texto del cuerpo<br />- Uso en controles Visual Studio estándar<br />- Uso en ventanas de herramientas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>Fuente de entorno del 133 %

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Subpartidas más pequeñas en cuadros de diálogo de firma<br />- Subpartidas más pequeñas en la interfaz de usuario del área de documentos<br /><br /> **Haga lo siguiente:** Uso de mayúsculas y minúsculas<br /><br /> **No:**<br /><br /> - Negrita, cursiva o cursiva en negrita<br />- Usar para el texto del cuerpo<br />- Uso en controles Visual Studio estándar<br />- Uso en ventanas de herramientas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>Fuente de entorno del 122 %

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Encabezados de sección en cuadros de diálogo de firma<br />- Nodos superiores en la vista de árbol<br />- Navegación por pestañas verticales<br /><br /> **Haga lo siguiente:** Uso de mayúsculas y minúsculas<br /><br /> **No:**<br /><br /> - Negrita, cursiva o negrita cursiva<br />- Usar para el texto del cuerpo<br />- Uso en controles Visual Studio estándar<br />- Uso en ventanas de herramientas|**Aparece como:** 11 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Fuente del entorno + negrita

|Uso|Aspecto|
|-|-|
|**Uso:**<br /><br /> - Etiquetas y subheads en cuadros de diálogo de firma<br />- Etiquetas y subheads en informes<br />- Etiquetas y subheads en la interfaz de usuario del documento<br /><br /> **hacer:**<br /><br /> - Uso de mayúsculas y minúsculas<br />- Usar el peso en negrita<br /><br /> **No:**<br /><br /> - Cursiva o negrita cursiva<br />- Usar para el texto del cuerpo<br />- Uso en controles Visual Studio estándar<br />- Uso en ventanas de herramientas|**Aparece como: 9** puntos en negrita Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente de entorno &#43; de negrita](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Fuente del entorno

|Uso|Aspecto|
|-|-|
|**Uso:** El resto del texto<br /><br /> **Haga lo siguiente:** Uso de mayúsculas y minúsculas<br /><br /> **No:** Cursiva o negrita cursiva|**Aparece como:** 9 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente del entorno](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Relleno y espaciado
 Los encabezados requieren espacio alrededor de ellos para darles el énfasis adecuado. Este espacio varía en función del tamaño del punto y de lo que esté cerca del encabezado, como una regla horizontal o una línea de texto en la fuente del entorno.

- El relleno ideal para un encabezado por sí solo debe ser el 90 % del espacio de altura del carácter de mayúscula. Por ejemplo, un encabezado light de 28 pt Segoe UI tiene una altura máxima de 26 pt y el relleno debe ser de aproximadamente 23 pt o unos 31 píxeles.

- El espacio mínimo alrededor de un encabezado debe ser el 50 % de la altura del carácter de mayúscula. Se puede usar menos espacio cuando un encabezado va acompañado de una regla u otro elemento de ajuste estricto.

- El texto de fuente del entorno en negrita debe seguir el espaciado y el relleno predeterminados del alto de línea.

## <a name="see-also"></a>Consulta también

- [Fuentes (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Interfaz de usuario texto (Windows)](/windows/desktop/uxguide/text-ui)
