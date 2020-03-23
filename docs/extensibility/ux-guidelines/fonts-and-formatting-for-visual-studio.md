---
title: Fuentes y formato para Visual Studio ? Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8634ab15a10b59fc21de390e0633d6d91793616d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301546"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fuentes y formato de Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>La fuente del entorno
 Todas las fuentes de Visual Studio deben exponerse al usuario para su personalización. Esto se hace principalmente a través de la página **Fuentes y colores** en el cuadro de diálogo **Herramientas > Opciones.** Las tres categorías principales de ajustes de fuente son:

- **Fuente** de entorno: la fuente principal para el IDE (entorno de desarrollo integrado), que se utiliza para todos los elementos de la interfaz, incluidos los cuadros de diálogo, los menús, las ventanas de herramientas y las ventanas de documentos. De forma predeterminada, la fuente del entorno está vinculada a una fuente del sistema que aparece como interfaz de usuario de Segoe de 9 pt en las versiones actuales de Windows. El uso de una fuente para todos los elementos de la interfaz ayuda a garantizar un aspecto de fuente coherente en todo el IDE.

- **Editor** de texto: los elementos que asolan el código y otros editores basados en texto se pueden personalizar en la página Editor de texto de **Herramientas > Opciones**.

- **Colecciones específicas:** las ventanas de diseño que ofrecen la personalización por parte del usuario de sus elementos de interfaz pueden exponer fuentes específicas de su superficie de diseño en su propia página de configuración en **Herramientas > Opciones**.

### <a name="editor-font-customization-and-resizing"></a>Personalización y cambio de tamaño de la fuente del editor
 Los usuarios a menudo ampliarán o amplían el tamaño y/o el color del texto en el editor según sus preferencias, independientemente de la interfaz de usuario general. Dado que la fuente de entorno se utiliza en elementos que pueden aparecer dentro o como parte de un editor o diseñador, es importante tener en cuenta el comportamiento esperado cuando se cambia una de estas clasificaciones de fuente.

 Al crear elementos de interfaz de usuario que aparecen en el editor pero no forman parte del *contenido,* es importante usar la fuente de entorno y no la fuente de texto para que los elementos cambian de tamaño de una manera predecible.

1. Para el texto de código en el editor, cambie el tamaño con la configuración de fuente de texto de código y responda al nivel de zoom del texto del editor.

2. Todos los demás elementos de la interfaz deben estar vinculados a la configuración de fuente del entorno y responder a cualquier cambio global en el entorno. Esto incluye (pero no se limita a):

    - Texto en menús contextuales

    - Texto en un adorno del editor, como el texto del menú de la bombilla, el panel del editor de búsqueda rápida y navegar hasta el panel

    - Etiquetar texto en cuadros de diálogo, como **Buscar en archivos** o **Refactorizar**

### <a name="accessing-the-environment-font"></a>Acceso a la fuente del entorno
 En código nativo o WinForms, se puede tener `IUIHostLocale::GetDialogFont` acceso a la `SID_SUIHostLocale` fuente de entorno llamando al método después de consultar la interfaz desde el servicio.

 Para Windows Presentation Foundation (WPF), derive la clase `DialogWindow` de ventana de `Window` cuadro de diálogo de la clase del shell en lugar de la clase de WPFWPF.

 En XAML, el código tiene este aspecto:

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

Código detrás:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Reemplazar `Microsoft.VisualStudio.Shell.11.0` con la versión actual de la DLL MPF.)

 Para mostrar el cuadro`ShowModal()`de diálogo, `ShowDialog()`llame a " " en la clase sobre . `ShowModal()`establece el estado modal correcto en el shell, garantiza que el cuadro de diálogo se centra en la ventana primaria, etc.

 El código es el siguiente:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`devuelve un bool? (booleano que acepta `DialogResult`valores NULL) con el , que se puede utilizar si es necesario. El valor devuelto es true si el cuadro de diálogo se cerró con **OK**.

 Si necesita mostrar alguna interfaz de usuario de WPF `HwndSource`que no es un cuadro de diálogo y se hospeda en su propio , como `FontFamily` `FontSize` una ventana emergente o una ventana secundaria WPF de una ventana primaria Win32/WinForms, deberá establecer el elemento raíz y en el elemento WPFWPF. (El shell establece las propiedades en la ventana principal, `HWND`pero no se heredarán más allá de a ). El shell proporciona recursos a los que se pueden enlazar las propiedades, de la siguiente manera:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Referencia de formato (escalado/bolding)
 Algunos cuadros de diálogo requieren que el texto en particular esté en negrita o un tamaño distinto de la fuente del entorno. Anteriormente, las fuentes más grandes que`environment font +2`la fuente del entorno se codificaban como " " o similares. El uso de los fragmentos de código proporcionados admitirá monitores de alto PPP y garantizará que el texto de visualización siempre aparezca con el tamaño y el peso correctos (como Light o Semilight).

> [!NOTE]
> Antes de aplicar formato, asegúrese de seguir las instrucciones que se encuentran en [Estilo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)de texto .**

 Para escalar la fuente del entorno, establezca el estilo de TextBlock o Label como se indica. Cada uno de estos fragmentos de código, utilizados correctamente, generará la fuente correcta, incluidas las variaciones de tamaño y peso adecuadas.

 Donde`vsui`" " es una `Microsoft.VisualStudio.Shell`referencia al espacio de nombres:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% Fuente de entorno + Luz

**Aparece como:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Usar para:** (rara) interfaz de usuario de marca única, como en la página de inicio

::: moniker-end

::: moniker range=">=vs-2019"

**Usar para:** (rara) interfaz de usuario de marca única

::: moniker-end

**Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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

#### <a name="310-environment-font--light"></a>310% Fuente de entorno + Luz
 **Aparece como:** 28 pt Segoe UI Light **Use for:** large signature dialog titles, main heading in reports

 **Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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

#### <a name="200-environment-font--semilight"></a>200% Fuente de entorno + Semilight
 **Aparece como:** 18 pt Segoe UI Semilight **Use for:** subheadings, titles in small and medium dialogs

 **Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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

#### <a name="155-environment-font"></a>155% Fuente de medio ambiente
 **Aparece como:** 14 pt Segoe UI **Use for:** section headings in document well UI or reports

 **Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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

#### <a name="133-environment-font"></a>133% Fuente Environment
 **Aparece como:** 12 pt Segoe UI **Use for:** subheadings más pequeños en los cuadros de diálogo de firma y documento bien UI

 **Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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

#### <a name="122-environment-font"></a>122% Fuente De entorno
 **Aparece como:** 11 pt Segoe UI **Use for:** section headings in signature dialogs, top nodes in tree view, vertical tab navigation

 **Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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
 **Aparece como:** bolded 9 pt Segoe UI **Use for:** labels and subheads in signature dialogs, reports, and document well UI

 **Código procesal:** Dónde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:

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
 En algunos casos, los localizadores tendrán que modificar los estilos de fuente para diferentes configuraciones regionales, como la eliminación de negritas del texto para idiomas de Asia oriental. Para que la localización de estilos de fuente sea posible, esos estilos deben estar dentro del archivo .resx. La mejor manera de lograr esto y seguir editando estilos de fuente en el Diseñador de formularios de Visual Studio es establecer explícitamente los estilos de fuente en tiempo de diseño. Aunque esto crea un objeto de fuente completo y puede parecer romper la herencia de fuentes primarias, solo el FontStyle propiedad se utiliza para establecer la fuente.

 La solución es enlazar el `FontChanged` evento del formulario de diálogo. En `FontChanged` el caso, pasee todos los controles y compruebe si su fuente está establecida. Si se establece, cámbielo a una nueva fuente basada en la fuente del formulario y el estilo de fuente anterior del control. Un ejemplo de esto en el código es:

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

 El uso de este código garantiza que cuando se actualiza la fuente del formulario, las fuentes de los controles también se actualizarán. Este método también debe llamarse desde el constructor del formulario, porque `IUIService` el `FontChanged` cuadro de diálogo podría no obtener una instancia de y el evento nunca se desencadenará. El `FontChanged` enlace permitirá que los cuadros de diálogo recojan dinámicamente la nueva fuente incluso si el cuadro de diálogo ya está abierto.

### <a name="testing-the-environment-font"></a>Probar la fuente del entorno
 Para asegurarse de que la interfaz de usuario utiliza la fuente de entorno y respeta la configuración de tamaño, abra **Herramientas > Opciones > Entorno > Fuentes y colores** y seleccione "Fuente de entorno" en el menú desplegable "Mostrar configuración para:".

 ![Configuración de fuentes y &gt; colores en el cuadro de diálogo Opciones de herramientas](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Configuración de fuentes y &gt; colores en el cuadro de diálogo Opciones de herramientas

 Establezca la fuente en algo muy diferente del valor predeterminado. Para que sea obvio qué interfaz de usuario no se actualiza, elija una fuente con serifs (como "Times New Roman") y establezca un tamaño muy grande. A continuación, pruebe la interfaz de usuario para asegurarse de que respeta el entorno. A continuación se muestra un ejemplo utilizando el cuadro de diálogo de licencia:

 ![Ejemplo de texto de interfaz de usuario que no respeta la fuente del entorno](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Ejemplo de texto de interfaz de usuario que no respeta la fuente del entorno

 En este caso, "Información del usuario" y "Información del producto" no respetan la fuente. En algunos casos, esto puede ser una opción de diseño explícita, pero puede ser un error si la fuente explícita no se especifica como parte de las especificaciones de línea roja.

 Para restablecer la fuente, haga clic en "Usar valores predeterminados" en **Herramientas > Opciones > Entorno > Fuentes y Colores**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Estilo de texto
 El estilo de texto hace referencia al tamaño de fuente, el peso y la carcasa. Para obtener instrucciones sobre la implementación, consulte [La fuente de entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Carcasa de texto

#### <a name="all-caps"></a>Todas las gorras
 No use todas las mayúsculas para títulos o etiquetas en Visual Studio.

#### <a name="all-lowercase"></a>Todas las minúsculas
 No use todas las minúsculas para títulos o etiquetas en Visual Studio.

#### <a name="sentence-and-title-case"></a>Sentencia y estuche de título
 El texto de Visual Studio debe usar mayúsculas y minúsculas de título o de frase, dependiendo de la situación.

|Utilice el caso de título para:|Use el caso de la sentencia para:|
|-------------------------|----------------------------|
|Títulos de diálogo|Etiquetas|
|Cajas de grupo|Casillas|
|Elementos de menú|Botones de radio|
|Elementos del menú contextual|Elementos del cuadro de lista|
|Botones|Barras de estado|
|Etiquetas de mesa||
|Encabezados de columna||
|Información sobre herramientas||

##### <a name="title-case"></a>Tipo título
 El caso de título es un estilo en el que las primeras letras de la mayoría o todas las palabras dentro de una frase están en mayúsculas. En Visual Studio, el caso de título se usa para muchos elementos, entre ellos:

- **Tooltips.** Ejemplo: "Vista previa de los elementos seleccionados"

- **Encabezados de columna.** Ejemplo: "Respuesta del sistema"

- **Elementos del menú.** Ejemplo: "Guardar todo"

  Al usar mayúsculas y minúsculas, estas son las pautas para cuándo poner las palabras en mayúsculas y cuándo dejarlas en minúsculas:

|Uppercase|Comentarios y ejemplos|
|---------------|---------------------------|
|Todos los sustantivos||
|Todos los verbos|Incluyendo "Is" y otras formas de "ser"|
|Todos los adverbios|Incluyendo "Than" y "When"|
|Todos los adjetivos|Incluyendo "Esto" y "Eso"|
|Todos los pronombres|Incluyendo el posesivo "Its" así como "It's", una contracción del pronombre "it" y el verbo "is"|
|Primera y última palabra, independientemente de las partes del habla||
|Preposiciones que forman parte de una frase verbal|"Cerrando todas las ventanas" o "Apagar el sistema"|
|Todas las letras de un acrónimo|HTML, XML, URL, IDE, RGB|
|La segunda palabra en una palabra compuesta si es un sustantivo o un adjetivo adecuado, o si las palabras tienen el mismo peso|Referencia cruzada, software de Pre-Microsoft, acceso de lectura/escritura, tiempo de ejecución|

|Minúsculas|Ejemplos|
|---------------|--------------|
|La segunda palabra en una palabra compuesta si es otra parte del habla o un participio modificando la primera palabra|Cómo hacerlo, despegue|
|Artículos, a menos que uno sea la primera palabra en el título|un, una, el, la|
|Coordinar conjunciones|y, pero, por, ni, o|
|Preposiciones con palabras de cuatro o menos letras fuera de una frase verbal|en, en, en, como para, fuera de, en la parte superior de|
|"Para" cuando se usa en una frase infinitiva|"Cómo formatear su disco duro"|

##### <a name="sentence-case"></a>Caso de sentencia
 El caso de la sentencia es el método de mayúsculas estándar para escribir en el que sólo la primera palabra de la oración está en mayúsculas, junto con cualquier sustantivo apropiado y el pronombre "I". En general, el caso de oraciones es más fácil de leer para una audiencia mundial, especialmente cuando el contenido será traducido por una máquina. Use el caso de la sentencia para:

1. **Mensajes de la barra de estado.** Estos son simples, cortos y proporcionan solo información de estado. Ejemplo: "Cargar archivo de proyecto"

2. **Todos los demás elementos**de la interfaz de usuario, incluidas las etiquetas, las casillas de verificación, los botones de opción y los elementos del cuadro de lista. Ejemplo: "Seleccionar todos los elementos de la lista"

### <a name="text-formatting"></a>Formato del texto
 El formato de texto predeterminado en Visual Studio 2013 se controla mediante [la fuente de entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Este servicio ayuda a garantizar una apariencia de fuente coherente en todo el IDE (entorno de desarrollo integrado) y debe usarlo para garantizar una experiencia coherente para los usuarios.

 El tamaño predeterminado utilizado por el servicio de fuentes de Visual Studio proviene de Windows y aparece como 9 pt.

 Puede aplicar formato a la fuente del entorno. En este tema se explica cómo y dónde usar estilos. Para obtener información sobre la implementación, consulte [La fuente de entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Texto en negrita
 El texto en negrita se usa con moderación en Visual Studio y debe reservarse para:

- etiquetas de preguntas en los magos

- designar el proyecto activo en el Explorador de soluciones

- valores anulados en la ventana de herramientas Propiedades

- ciertos eventos en las listas desplegables del editor de Visual Basic

- contenido generado por el servidor en el esquema del documento para las páginas web

- encabezados de sección en un cuadro de diálogo complejo o en la interfaz de usuario del diseñador

#### <a name="italics"></a>Cursiva
 Visual Studio no usa texto en cursiva o en cursiva en negrita.

#### <a name="color"></a>Color

- El azul está reservado para hipervínculos (navegación y comandos) y nunca se debe utilizar para la orientación.

- Los encabezados más grandes (fuente de entorno x 155% o superior) se pueden colorear para estos fines:

  - Para proporcionar atractivo visual a la interfaz de usuario de Visual Studio de firma

  - Para llamar la atención sobre un área específica

  - Para ofrecer alivio del color de texto estándar del entorno gris oscuro/negro

- El color en los encabezados debe aprovechar los colores de marca de Visual Studio existentes, principalmente el púrpura principal, #FF68217A.

- Al usar el color en los encabezados, debe cumplir las directrices de color de [Windows,](/windows/desktop/uxguide/vis-color)incluida la relación de contraste y otras consideraciones de accesibilidad.

### <a name="font-size"></a>Tamaño de fuente
 El diseño de la interfaz de usuario de Visual Studio presenta un aspecto más claro con más espacio en blanco. Siempre que sea posible, las barras de cromo y título se han reducido o eliminado. Aunque la densidad de la información es un requisito en Visual Studio, la tipografía sigue siendo importante, con énfasis en el espaciado de línea más abierto y una variación de los tamaños y pesos de fuente.

 Las tablas siguientes incluyen detalles de diseño y ejemplos visuales para las fuentes de presentación utilizadas en Visual Studio. Algunas variaciones de fuente de visualización tienen el tamaño y el peso, como Semilight o Light, codificados en su apariencia.

 Los fragmentos de código de implementación para todas las fuentes de visualización se pueden encontrar en [la referencia Formato (escalado/en negrita).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% Fuente de entorno + Luz

|||
|-|-|
|**Uso:** Raro. Solo interfaz de usuario de marca única.<br /><br /> **hacer:**<br /><br /> - Usar caso de sentencia<br />- Utilice siempre peso ligero<br /><br /> **No:**<br /><br /> - Uso para la interfaz de usuario que no sea la interfaz de usuario de firma, como la página de inicio<br />- Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 34 pt Segoe UI Light<br /><br /> **Ejemplo visual:**<br /><br /> *Actualmente no se utiliza. Se puede usar en la página de inicio de Visual Studio 2017.*|

#### <a name="310-environment-font--light"></a>310% Fuente de entorno + Luz

::: moniker range="vs-2017"

|||
|-|-|
|**Uso:**<br /><br /> - Encabezado más grande en los diálogos de firma<br />- Encabezado principal del informe<br /><br /> **hacer:**<br /><br /> - Usar caso de sentencia<br />- Utilice siempre peso ligero<br /><br /> **No:**<br /><br /> - Uso para la interfaz de usuario que no sea la interfaz de usuario de firma, como la página de inicio<br />- Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 28 pt Segoe UI Light<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente 310% Environment &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Uso:**<br /><br /> - Encabezado más grande en los diálogos de firma<br />- Encabezado principal del informe<br /><br /> **hacer:**<br /><br /> - Usar caso de sentencia<br />- Utilice siempre peso ligero<br /><br /> **No:**<br /><br /> - Usar para la interfaz de usuario que no sea la interfaz de usuario de firma<br />- Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 28 pt Segoe UI Light<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente 310% Environment &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% Fuente de entorno + Semilight

|||
|-|-|
|**Uso:**<br /><br /> - Subpartidas<br />- Títulos en diálogos pequeños y medianos<br /><br /> **hacer:**<br /><br /> - Usar caso de sentencia<br />- Utilice siempre el peso semiligero<br /><br /> **No:**<br /><br /> - Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en ventanas de herramientas|**Aparece como:** 18 pt Segoe UI Semillight<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de la fuente 200% Environment &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% Fuente de medio ambiente

|||
|-|-|
|**Uso:**<br /><br /> - Encabezados de sección en la interfaz de usuario de documentos bien<br />- Informes<br /><br /> **Hacer:** Usar caso de sentencia<br /><br /> **No:**<br /><br /> - Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en controles estándar de Visual Studio<br />- Uso en ventanas de herramientas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% Fuente Environment

|||
|-|-|
|**Uso:**<br /><br /> - Subpartidas más pequeñas en los diálogos de firmas<br />- Subpartidas más pequeñas en la interfaz de usuario de pozos de documentos<br /><br /> **Hacer:** Usar caso de sentencia<br /><br /> **No:**<br /><br /> - Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en controles estándar de Visual Studio<br />- Uso en ventanas de herramientas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% Fuente De entorno

|||
|-|-|
|**Uso:**<br /><br /> - Encabezados de sección en diálogos de firmas<br />- Nodos superiores en la vista de árbol<br />- Navegación vertical por pestañas<br /><br /> **Hacer:** Usar caso de sentencia<br /><br /> **No:**<br /><br /> - Negrita, cursiva o negrita cursiva<br />- Uso para el texto del cuerpo<br />- Uso en controles estándar de Visual Studio<br />- Uso en ventanas de herramientas|**Aparece como:** 11 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Fuente del entorno + negrita

|||
|-|-|
|**Uso:**<br /><br /> - Etiquetas y subjefes en diálogos de firma<br />- Etiquetas y subjefes en los informes<br />- Etiquetas y subjefes en la interfaz de usuario de documentos bien<br /><br /> **hacer:**<br /><br /> - Usar caso de sentencia<br />- Utilice el peso audaz<br /><br /> **No:**<br /><br /> - Cursiva o cursiva en negrita<br />- Uso para el texto del cuerpo<br />- Uso en controles estándar de Visual Studio<br />- Uso en ventanas de herramientas|**Aparece como:** bolded 9 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente Environment &#43; Encabezado Bold](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Fuente de entorno

|||
|-|-|
|**Uso:** El resto del texto<br /><br /> **Hacer:** Usar caso de sentencia<br /><br /> **No:** Cursiva o cursiva en negrita|**Aparece como:** 9 pt Segoe UI<br /><br /> **Ejemplo visual:**<br /><br /> ![Ejemplo de fuente del entorno](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Relleno y espaciado
 Los encabezados requieren espacio a su alrededor para darles el énfasis adecuado. Este espacio varía en función del tamaño del punto y de lo que esté cerca del encabezado, como una regla horizontal o una línea de texto en la fuente del entorno.

- El relleno ideal para un encabezado por sí mismo debe ser el 90% del espacio de altura del carácter capital. Por ejemplo, un encabezado Segoe UI Light de 28 pt tiene una altura de límite de 26 pt, y el relleno debe ser de aproximadamente 23 pt, o unos 31 píxeles.

- El espacio mínimo alrededor de un encabezado debe ser el 50% de la altura del carácter capital. Se puede utilizar menos espacio cuando un encabezado va acompañado de una regla u otro elemento de ajuste ajustado.

- El texto de fuente de entorno en negrita debe seguir el espaciado de altura de línea y el relleno predeterminados.

## <a name="see-also"></a>Consulte también

- [MSDN: Fuentes (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Texto de interfaz de usuario (Windows)](/windows/desktop/uxguide/text-ui)
