---
title: Fuentes y formato de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a758c1e44f9f78f7dc2a225e641d91f97db72cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942834"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fuentes y formato de Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a> La fuente del entorno
 Todas las fuentes dentro de Visual Studio se deben exponer al usuario para la personalización. Esto se realiza principalmente mediante la **fuentes y colores** página en el **Herramientas > opciones** cuadro de diálogo. Las tres categorías principales de configuración de fuente son:  
  
-   **Fuente del entorno** -la fuente principal para el IDE (entorno de desarrollo integrado), utilizada para todos los elementos de interfaz, incluidos los cuadros de diálogo, menús, ventanas de herramientas y ventanas de documento. De forma predeterminada, la fuente del entorno está asociada a una fuente del sistema que aparece como 9 pt Segoe UI en las versiones actuales de Windows. Uso de fuentes para todos los elementos de la interfaz ayuda a garantizar una apariencia coherente de fuente en todo el IDE.  
  
-   **Editor de texto** -página de elementos que expuesta en el código y otros editores basados en texto se pueden personalizar en el Editor de texto en **Herramientas > opciones**.  
  
-   **Colecciones específicas** -ventanas del diseñador que ofrecen la personalización de sus elementos de interfaz de usuario puede exponer fuentes específicas de su diseño de surface en su propia página de configuración de **Herramientas > opciones**.  
  
### <a name="editor-font-customization-and-resizing"></a>Personalización de fuente del Editor y el cambio de tamaño  
 Los usuarios a menudo se ampliar o ampliar el tamaño o color del texto en el editor según sus preferencias, independientemente de la interfaz de usuario general. Dado que la fuente del entorno se usa en los elementos que pueden aparecer dentro de o como parte de un editor o diseñador, es importante tener en cuenta el comportamiento esperado cuando se cambia una de estas clasificaciones de la fuente.  
  
 Al crear los elementos de interfaz de usuario que aparecen en el editor pero son no forma parte de la *contenido*, es importante usar la fuente del entorno y no la fuente del texto para que cambie el tamaño de los elementos de una manera predecible.  
  
1.  Para el texto del código en el editor, cambiar el tamaño con la configuración de fuente del texto de código y responder a nivel de zoom del texto del editor.  
  
2.  Todos los demás elementos de la interfaz deben estar vinculados a la configuración de fuente del entorno y responden a los cambios en el entorno globales. Esto incluye (aunque no se limita a):  
  
    -   Texto en los menús contextuales  
  
    -   Texto en un elemento de gráfico del editor, como texto de menú de bombilla, panel del editor de la búsqueda rápida y vaya al panel  
  
    -   Etiqueta de texto en cuadros de diálogo, como **buscar en archivos** o **refactorizar**  
  
### <a name="accessing-the-environment-font"></a>Obtener acceso a la fuente del entorno  
 En código nativo o de formularios Windows Forms, se puede tener acceso a la fuente del entorno llamando al método `IUIHostLocale::GetDialogFont` después de consultar la interfaz desde el `SID_SUIHostLocale` service.  
  
 Para Windows Presentation Foundation (WPF), derive la clase de ventana de cuadro de diálogo desde el shell `DialogWindow` clase en lugar de WPF `Window` clase.  
  
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

código subyacente:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```
  
 (Reemplace `Microsoft.VisualStudio.Shell.11.0` con la versión actual de la dll MPF.)  
  
 Para mostrar el cuadro de diálogo, llame a "`ShowModal()`" en la clase a través de `ShowDialog()`. `ShowModal()` establece el estado modal correcto en el shell, asegura que el cuadro de diálogo se centra en la ventana primaria y así sucesivamente.  
  
 El código es como sigue:  
  
```csharp
MyWindow window = new MyWindow();  
window.ShowModal()  
```
  
 `ShowModal` ¿Devuelve un valor booleano? (un valor booleano que acepta valores NULL) con el `DialogResult`, que puede utilizarse si es necesario. El valor devuelto es true si se ha cerrado el cuadro de diálogo con **Aceptar**.  
  
 Si necesita mostrar algunos UI de WPF que no es un cuadro de diálogo y se hospeda en su propio `HwndSource`, como una ventana emergente o una ventana secundaria WPF de una ventana primaria de Win32/formularios Windows Forms, deberá establecer el `FontFamily` y `FontSize` en el elemento raíz del elemento WPF. (El shell establece las propiedades de la ventana principal, pero no se puede heredar más allá de un `HWND`). El shell proporciona recursos a los que se pueden enlazar las propiedades, similar al siguiente:  
  
```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```
  
###  <a name="BKMK_Formatting"></a> Formato de referencia (escalado o poner en negrita)  
 Algunos cuadros de diálogo requieren determinado texto esté en negrita o un tamaño distinto de la fuente del entorno. Anteriormente, las fuentes mayores que la fuente del entorno se codificaron como "`environment font +2`" o similar. Uso de los fragmentos de código proporcionado admitirá valores altos de PPP monitores y asegúrese de que el texto para mostrar aparece siempre en el tamaño correcto y peso (como la luz o Semilight).  
  
> **Nota: Antes de aplicar formato, asegúrese de que está siguiendo las directrices recogidas en [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Para escalar la fuente del entorno, establezca el estilo del TextBlock o Label como se indica. Cada uno de estos fragmentos de código, que se usan correctamente, generará la fuente correcta, incluidas las variaciones de tamaño y peso adecuadas.  
  
 Donde "`vsui`" es una referencia al espacio de nombres `Microsoft.VisualStudio.Shell`:  

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```
  
#### <a name="375-environment-font--light"></a>Fuente del entorno 375% + claro  
 **Aparece como:** Segoe UI Light de 34 pt  
 **Uso de:** (poco frecuente) única con marca la interfaz de usuario, como en la página de inicio

 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```
  
#### <a name="310-environment-font--light"></a>Fuente del entorno 310% + claro  
 **Aparece como:** Segoe UI Light de 28 pt   
 **Uso de:** títulos de cuadro de diálogo de firma grandes, principales de encabezado en los informes  
  
 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```
  
#### <a name="200-environment-font--semilight"></a>Fuente del entorno 200% + Semiclaro  
 **Aparece como:** 18 ptos Segoe UI Semilight    
 **Uso de:** subtítulos, títulos en los cuadros de diálogo pequeñas y medianas  
  
 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente: 
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```
  
#### <a name="155-environment-font"></a>Fuente del entorno 155%  
 **Aparece como:** 14 pt Segoe UI    
 **Uso de:** títulos de sección en documento bien la interfaz de usuario o los informes  
  
 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```
  
#### <a name="133-environment-font"></a>Fuente del entorno 133%  
 **Aparece como:** 12 pt Segoe UI    
 **Uso de:** subtítulos más pequeños en los cuadros de diálogo de firma y documento bien la interfaz de usuario  
  
 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```
  
#### <a name="122-environment-font"></a>Fuente del entorno 122%  
 **Aparece como:** 11 pt Segoe UI    
 **Uso de:** sección encabezados en los cuadros de diálogo de firma, mejores nodos en la vista de árbol, navegación por tabulación vertical  
  
 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```
  
#### <a name="environment-font--bold"></a>Fuente del entorno + negrita  
 **Aparece como:** en negrita 9 pt Segoe UI    
 **Uso de:** etiquetas y subtítulos en los cuadros de diálogo de firma, informes y documentos también la interfaz de usuario  
  
 **Código de procedimientos:** donde `textBlock` hay un TextBlock definido previamente y `label` es una etiqueta definida anteriormente:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```
  
 **XAML:** establecer el estilo del TextBlock o Label tal como se muestra:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```
  
### <a name="localizable-styles"></a>Estilos localizables  
 En algunos casos, los localizadores deberá modificar los estilos de fuente para diferentes configuraciones regionales, como la eliminación de poner en negrita del texto de idiomas de Asia oriental. Para que sea posible la localización de los estilos de fuente, deben ser esos estilos dentro del archivo resx. Es la mejor manera de lograr esto y modificar los estilos de fuente en el Diseñador de formularios de Visual Studio establecer explícitamente los estilos de fuente en tiempo de diseño. Aunque esto crea un objeto de fuente completa y puede parecer que interrumpan la herencia de fuentes del elemento primario, solo la propiedad FontStyle se usa para establecer la fuente.  
  
 La solución consiste en enlazar el formulario de cuadro de diálogo `FontChanged` eventos. En el `FontChanged` eventos, recorrer todos los controles y comprobar si se ha establecido su fuente. Si se establece, cámbiela a una nueva fuente en función de la fuente del formulario y el estilo de fuente anterior del control. Es un ejemplo de esto en el código:  
  
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
  
 Mediante este código garantiza que cuando se actualiza la fuente del formulario, también se actualizarán las fuentes de controles. Este método también debe llamarse desde el constructor del formulario, ya que el cuadro de diálogo puede producir un error al obtener una instancia de `IUIService` y `FontChanged` nunca se desencadenará el evento. Enlace `FontChanged` permitirá que los cuadros de diálogo Seleccionar dinámicamente la nueva fuente incluso si ya está abierto el cuadro de diálogo.  
  
### <a name="testing-the-environment-font"></a>Las pruebas de la fuente del entorno  
 Para asegurarse de que la interfaz de usuario está usando la fuente del entorno y respeta la configuración de tamaño, abra **Herramientas > Opciones > entorno > fuentes y colores** y seleccione "Fuente del entorno" en la "Mostrar valores para:" menú desplegable.  
  
 ![Configuración de fuentes y colores en las herramientas de &gt; cuadro de diálogo Opciones](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />Configuración de fuentes y colores en las herramientas de &gt; cuadro de diálogo Opciones
  
 Establezca la fuente en algo muy diferente al predeterminado. Para que resulte evidente que no se actualiza la interfaz de usuario, elija una fuente con serifs (por ejemplo, "Times New Roman") y establezca un tamaño muy grande. A continuación, pruebe la interfaz de usuario para asegurarse de que respeta el medio ambiente. Este es un ejemplo mediante el cuadro de diálogo de licencia:  
  
 ![Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno
  
 En este caso, no respetan la fuente "Información de usuario" e "Información de producto". En algunos casos este podría ser una opción de diseño explícito, pero puede ser un error si la fuente explícita no se especifica como parte de las especificaciones de límite.  
  
 Para restablecer la fuente, haga clic en "Usar valores predeterminados" bajo **Herramientas > Opciones > entorno > fuentes y colores**.  
  
##  <a name="BKMK_TextStyle"></a> Estilo de texto  
 Estilo de texto hace referencia a mayúsculas y minúsculas, el peso y tamaño de fuente. Para obtener instrucciones sobre la implementación, consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Mayúsculas y minúsculas del texto  
  
#### <a name="all-caps"></a>Todo en mayúsculas  
 No use todo en mayúsculas para títulos o etiquetas en Visual Studio.  
  
#### <a name="all-lowercase"></a>Todo minúsculas  
 No use todo en minúsculas para los títulos o etiquetas en Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Caso de las frases y título  
 Tipo título o caso de oración, según la situación, debe usar texto en Visual Studio.  
  
|Use mayúscula inicial para:|Caso de uso oración:|  
|-------------------------|----------------------------|  
|Títulos del cuadro de diálogo|Etiquetas|  
|Cuadros de grupo|Casillas de verificación|  
|Elementos de menú|Botones de radio|  
|Elementos de menú contextual|Elementos del cuadro de lista|  
|Botones|Barras de estado|  
|Etiquetas de tabla||  
|Encabezados de columna||  
|Información sobre herramientas||  
  
##### <a name="title-case"></a>Mayúscula inicial  
 Mayúscula inicial es un estilo en el que se escriben las primeras letras de la mayoría o todas las palabras dentro de una frase. En Visual Studio, mayúscula inicial se usa para muchos elementos, incluidos:  
  
- **Información sobre herramientas.** Ejemplo: "vista previa de los elementos seleccionados"  
  
- **Encabezados de columna.** Ejemplo: "respuesta del sistema"  
  
- **Elementos de menú.** Ejemplo: "Guardar todo"  
  
  Al usar mayúscula inicial, estas son las instrucciones para cuándo aprovechar las palabras y dejarlas en minúsculas:  
  
|Mayúsculas|Comentarios y ejemplos|  
|---------------|---------------------------|  
|Todos los nombres||  
|Todos los verbos|Como otras formas de "para ser" y "Es"|  
|Todos los adverbios|Incluido "De" y "Cuando"|  
|Todos los adjetivos|Como "This" y "Que"|  
|Todos los pronombres|Incluido el posesivo "Su", así como la"," una contracción de los pronombres "it" y el verbo "es"|  
|Palabras primeros y últimas, independientemente de las partes de la oración||  
|Preposiciones que forman parte de una frase verbal|"Cerrar todos los Windows" o "Apagar el sistema"|  
|Todas las letras de un acrónimo.|HTML, XML, DIRECCIÓN URL, IDE, RGB|  
|La segunda palabra de una palabra compuesta, si es un sustantivo o adjetivo adecuada, o si las palabras tienen el mismo peso|Referencia cruzada, Software preliminar de Microsoft, acceso de lectura/escritura, tiempo de ejecución|  
  
|Minúsculas|Ejemplos|  
|---------------|--------------|  
|La segunda palabra en una palabra compuesta, si es un participio modificación de la primera palabra u otra parte de la oración|Tema de procedimientos, despegue|  
|Artículos, a menos que uno es la primera palabra en el título|una, una,|  
|Coordinar conjunciones|y, pero, ni, o|  
|Preposiciones con palabras de cuatro o menos caracteres no recogidos en una frase verbal|en, en, como para directamente, en la parte superior de|  
|"A" cuando se usa en una frase infinita|"Cómo formatear el disco duro"|  
  
##### <a name="sentence-case"></a>Tipo oración  
 Oración es el método estándar de mayúsculas y minúsculas para escribir en el que aparece con mayúsculas solo la primera palabra de la oración, junto con los nombres propios y los pronombres "I". En general, el tipo oración es más fácil para un público internacional leer, especialmente cuando el contenido se traducirá en una máquina. Caso de uso oración:  
  
1.  **Mensajes de la barra de estado.** Estos son sencillos, resumen y facilitar solo información de estado. Ejemplo: "cargar archivo de proyecto"  
  
2.  **Todos los demás elementos de interfaz de usuario**, incluidas las etiquetas, las casillas de verificación, botones de radio y los elementos del cuadro de lista. Ejemplo: "seleccionar todos los elementos de lista"  
  
### <a name="text-formatting"></a>Formato de texto  
 Texto predeterminado de formato en Visual Studio 2013 se controla mediante [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Este servicio ayuda a garantizar una apariencia coherente de fuente en todo el IDE (entorno de desarrollo integrado), y se debe usar para garantizar una experiencia coherente para los usuarios.  
  
 El tamaño predeterminado utilizado por el servicio de la fuente de Visual Studio procede de Windows y aparece como 9 pt.  
  
 Puede aplicar formato a la fuente del entorno. Este tema se explica cómo y dónde se utilizan los estilos. Para obtener más información, consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Texto en negrita  
 Texto en negrita se usa con moderación en Visual Studio y se debe reservar para:  
  
-   etiquetas de pregunta en los asistentes  
  
-   que designa el proyecto activo en el Explorador de soluciones  
  
-   invalida los valores en la ventana de herramientas de propiedades  
  
-   determinados eventos en las listas desplegables de editor de Visual Basic  
  
-   contenido generado por el servidor en el esquema del documento para páginas web  
  
-   encabezados de sección en el cuadro de diálogo complejo o el Diseñador de interfaz de usuario  
  
#### <a name="italics"></a>Cursiva  
 Visual Studio no utiliza el texto en cursiva o en negrita cursiva.  
  
#### <a name="color"></a>Color  
  
-   Azul está reservado para los hipervínculos (navegación y comandos) y nunca debe utilizarse para la orientación.  
  
-   Los encabezados de mayor tamaño (fuente del entorno x 155% o superior) se pueden colorear para estos propósitos:  
  
    -   Para proporcionar el atractivo visual a la firma de la interfaz de usuario de Visual Studio  
  
    -   Para llamar la atención sobre un área específica  
  
    -   Para ofrecer un alivio de color del texto de entorno oscuro de gris o negro estándar  
  
-   Color en los encabezados debe aprovechar existente Visual Studio marca colores, principalmente el principal púrpura, FF68217A #.  
  
-   Cuando se usa el color en títulos, debe cumplir la [directrices de color de Windows](/windows/desktop/uxguide/vis-color), incluida la relación de contraste y otras consideraciones de accesibilidad.  
  
### <a name="font-size"></a>Tamaño de fuente  
 Diseño de Visual Studio la interfaz de usuario presenta un aspecto más claro con más espacio en blanco. Siempre que sea posible, barras de título y chrome se han reducido o eliminado. Mientras la densidad de la información es un requisito en Visual Studio, tipografía sigue siendo importante, con énfasis en interlineado más abierto y una variación de ponderaciones y los tamaños de fuente.  
  
 Las tablas siguientes ofrecen detalles de diseño y ejemplos visuales para las fuentes de pantalla usadas en Visual Studio. Algunas variaciones de fuente de la pantalla tienen el tamaño y el peso, como Semilight o claro, codificado en su apariencia.  
  
 Fragmentos de código de implementación para mostrar todas las fuentes pueden encontrarse en [formato de referencia (escalado o poner en negrita)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Fuente del entorno 375% + claro  
  
|||  
|-|-|  
|**Uso:** poco frecuentes. Interfaz de usuario de la marca solo UNIQUE.<br /><br /> **Hacer:**<br /><br /> -Use oración<br />-Use siempre ligero<br /><br /> **No:**<br /><br /> -El uso de la interfaz de usuario que no sea de interfaz de usuario como página de inicio de la firma<br />-En negrita, cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar ventanas de herramientas|**Aparece como:** Segoe UI Light de 34 pt<br /><br /> **Ejemplo Visual:**<br /><br /> *Actualmente no usa. Puede usarse en la página de inicio.*|  
  
#### <a name="310-environment-font--light"></a>Fuente del entorno 310% + claro  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Título más grande en los cuadros de diálogo de firma<br />: Encabezado de informe principal<br /><br /> **Hacer:**<br /><br /> -Use oración<br />-Use siempre ligero<br /><br /> **No:**<br /><br /> -El uso de la interfaz de usuario que no sea de interfaz de usuario como página de inicio de la firma<br />-En negrita, cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar ventanas de herramientas|**Aparece como:** Segoe UI Light de 28 pt<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno 310% &#43; encabezado claro](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Fuente del entorno 200% + Semiclaro  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Subtítulos<br />-Títulos de los cuadros de diálogo pequeñas y medianas<br /><br /> **Hacer:**<br /><br /> -Use oración<br />-Use siempre Semilight peso<br /><br /> **No:**<br /><br /> -En negrita, cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar ventanas de herramientas|**Aparece como:** 18 ptos Segoe UI Semillight<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>Fuente del entorno 155%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Sección títulos de documento bien la interfaz de usuario<br />: Informes<br /><br /> **Realice:** oración caso de uso<br /><br /> **No:**<br /><br /> -En negrita, cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar controles estándar de Visual Studio<br />-Usar ventanas de herramientas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>Fuente del entorno 133%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Subtítulos más pequeños en los cuadros de diálogo de firma<br />-Menores subtítulos en documento bien la interfaz de usuario<br /><br /> **Realice:** oración caso de uso<br /><br /> **No:**<br /><br /> -En negrita, cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar controles estándar de Visual Studio<br />-Usar ventanas de herramientas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>Fuente del entorno 122%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> : Encabezados de sección en los cuadros de diálogo de firma<br />-Nodos superior en la vista de árbol<br />-Navegación por tabulación vertical<br /><br /> **Realice:** oración caso de uso<br /><br /> **No:**<br /><br /> -En negrita, cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar controles estándar de Visual Studio<br />-Usar ventanas de herramientas|**Aparece como:** 11 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>Fuente del entorno + negrita  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Las etiquetas y subtítulos en los cuadros de diálogo de firma<br />-Las etiquetas y subtítulos en los informes<br />-Las etiquetas y subtítulos en el documento bien la interfaz de usuario<br /><br /> **Hacer:**<br /><br /> -Use oración<br />-Usar el peso en negrita<br /><br /> **No:**<br /><br /> -Cursiva o negrita cursiva<br />-Use para el texto de cuerpo<br />-Usar controles estándar de Visual Studio<br />-Usar ventanas de herramientas|**Aparece como:** en negrita 9 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno &#43; encabezado en negrita](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|  
  
#### <a name="environment-font"></a>Fuente del entorno  
  
|||  
|-|-|  
|**Uso:** todo el texto<br /><br /> **Realice:** oración caso de uso<br /><br /> **No:** cursiva o negrita cursiva|**Aparece como:** 9 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|  
  
### <a name="padding-and-spacing"></a>Relleno y espaciado  
 Encabezados requieren espacio alrededor de ellas para darles el énfasis adecuado. Este espacio varía según el tamaño de punto y lo está cerca del encabezado, por ejemplo, una regla horizontal o una línea de texto en la fuente del entorno.  
  
-   El relleno ideal para un encabezado de por sí solo debe ser 90% del espacio de capital del carácter alto. Por ejemplo, un encabezado de Segoe UI Light de 28 pt tiene un alto de límite de 26 pt, y la cantidad de relleno debe ser aproximadamente 23 pt, o aproximadamente 31 píxeles.  
  
-   El espacio mínimo en torno a un encabezado debe ser un 50% del alto del carácter de capital. Cuando un encabezado está acompañado por una regla u otro elemento de ajuste estrecha, se puede usar menos espacio.  
  
-   Texto en negrita de la fuente de entorno debe seguir relleno y espaciado de alto de línea predeterminado.  
  
## <a name="see-also"></a>Vea también  
 [MSDN: Fuentes (Windows)](/windows/desktop/uxguide/vis-fonts)   
 [MSDN: Texto (Windows) de la interfaz de usuario](/windows/desktop/uxguide/text-ui)
