---
title: "Fuentes y formato de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Fuentes y formato de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> La fuente del entorno  
 Todas las fuentes dentro de Visual Studio se deben exponer al usuario para la personalización. Esto se realiza principalmente mediante el **fuentes y colores** página en el **Herramientas \> opciones** cuadro de diálogo. Las tres categorías principales de configuración de la fuente son:  
  
-   **Fuente del entorno** : la fuente principal para el IDE \(entorno de desarrollo integrado\), utilizada para todos los elementos de la interfaz, incluidos los cuadros de diálogo, menús, ventanas de herramientas y ventanas de documento. De forma predeterminada, la fuente del entorno está vinculada a una fuente del sistema que aparece como 9 pt Segoe UI en las versiones actuales de Windows. Uso de una fuente para todos los elementos de la interfaz ayuda a garantizar una apariencia coherente de fuente en todo el IDE.  
  
-   **Editor de texto** : página de elementos que expuesta en código y otros editores basados en texto se pueden personalizar en el Editor de texto en **Herramientas \> opciones**.  
  
-   **Colecciones concretas** : ventanas de diseñador que ofrecen la personalización de sus elementos de interfaz de usuario puede exponer fuentes específicas de su diseño de la superficie en su propia página de configuración de **Herramientas \> opciones**.  
  
### Personalización de fuente del Editor y el cambio de tamaño  
 Los usuarios a menudo ampliar o ampliar el tamaño o el color del texto en el editor según sus preferencias, independientemente de la interfaz de usuario general. Dado que la fuente del entorno se utiliza en los elementos que pueden aparecer dentro o como parte de un editor o diseñador, es importante tener en cuenta el comportamiento esperado cuando se cambia una de estas clasificaciones de fuente.  
  
 Al crear elementos de interfaz de usuario que aparecen en el editor pero son no forma parte de la *contenido*, es importante usar la fuente del entorno y no la fuente del texto para que cambie el tamaño de los elementos de una manera predecible.  
  
1.  Para el texto del código en el editor, el tamaño de la configuración de fuente del texto de código y responder al nivel de zoom del editor de texto.  
  
2.  Todos los demás elementos de la interfaz deben asociarse a la configuración de fuente del entorno y responden a los cambios en el entorno globales. Esto incluye \(pero no está limitado a\):  
  
    -   Texto en los menús contextuales  
  
    -   Texto en un elemento de gráfico del editor, como el texto de menú de bombilla, rápido buscar panel del editor y navegue al panel  
  
    -   Texto de la etiqueta en los cuadros de diálogo, como buscar en archivos o refactorizar  
  
### Obtener acceso a la fuente del entorno  
 En código nativo o de formularios Windows Forms, la fuente del entorno puede obtenerse llamando al método **IUIHostLocale::GetDialogFont** después de consultar la interfaz del servicio SID\_SUIHostLocale.  
  
 Para Windows Presentation Foundation \(WPF\), derive la clase de ventana de diálogo desde el shell **DialogWindow** clase en lugar de WPF **ventana** clase.  
  
 En XAML, el código tiene el siguiente aspecto:  
  
```  
<ui:DialogWindow x:Class"MyNameSpace.MyWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" ShowInTaskbar="False" WindowStartupLocation="CenterOwner" Title="My Dialog"> </ui:DialogWindow> code behind: internal partial class WebConfigModificationWindow : DialogWindow { }  
  
```  
  
 \(Reemplace `Microsoft.VisualStudio.Shell.11.0` con la versión actual de la dll MPF.\)  
  
 Para mostrar el cuadro de diálogo, llame a "**ShowModal\(\)**" en la clase sobre **OpenFileDialog**.**ShowModal\(\)** establece el estado modal correcto en el shell, se asegura de que el cuadro de diálogo se centra en la ventana primaria y así sucesivamente.  
  
 El código es como sigue:  
  
```  
MyWindow window = new MyWindow(); window.ShowModal()  
  
```  
  
 ¿**ShowModal** devuelve un bool? \(un valor booleano que acepta valores NULL\) con el **DialogResult**, que puede utilizarse si es necesario. El valor devuelto es true si se ha cerrado el cuadro de diálogo con **Aceptar**.  
  
 Si necesita mostrar algunos UI de WPF que no es un cuadro de diálogo y se hospeda en su propio **HwndSource**, como una ventana emergente o una ventana secundaria WPF de una ventana de ventana de Win32\/WinForms principal, debe establecer el **FontFamily** y **FontSize** en el elemento raíz del elemento WPF. \(El shell establece las propiedades en la ventana principal, pero no se puede heredar más allá de un HWND\). El shell proporciona recursos a los que se pueden enlazar las propiedades, similar al siguiente:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> Formato de referencia \(escalado\/negrita\)  
 Algunos cuadros de diálogo requieren un tamaño distinto de la fuente del entorno o texto concreto esté en negrita. Anteriormente, las fuentes mayores que la fuente del entorno estaban codificada como "fuente del entorno \+ 2" o similar. Utilizar los fragmentos de código proporcionado se compatible con monitores de alta resolución y asegurarse de que el texto de presentación aparece en el tamaño correcto y el peso \(como la luz o Semilight\).  
  
> **Nota: Antes de aplicar formato, asegúrese de que esté siguiendo las instrucciones que se encuentran en [Estilo del texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Para escalar la fuente del entorno, establezca el estilo del TextBlock o la etiqueta, como se indica. Cada uno de estos fragmentos de código, que se utiliza correctamente, generará la fuente correcta, incluidas las variaciones de tamaño y peso adecuadas.  
  
 Donde "vsui" es una referencia al espacio de nombres Microsoft.VisualStudio.Shell:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### Fuente del entorno 375% \+ claro  
 **Aparece como:** pt 34 Segoe UI Light  
  
 **Usar para:** \(raras\) único IU, como se muestra en la página de inicio  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### Fuente del entorno 310% \+ claro  
 **Aparece como:** 28 pt Segoe UI Light  
  
 **Usar para:** títulos de cuadro de diálogo de firma grandes, principales de encabezado en los informes  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### Fuente del entorno 200% \+ Semiclaro  
 **Aparece como:** 18 pto Segoe UI Semilight  
  
 **Usar para:** subtítulos, títulos de los cuadros de diálogo pequeñas y medianas  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### Fuente del entorno 155%  
 **Aparece como:** 14 pt Segoe UI  
  
 **Usar para:** títulos de sección del documento bien UI o informes  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### Fuente del entorno 133%  
 **Aparece como:** 12 pt Segoe UI  
  
 **Usar para:** subtítulos más pequeños en los cuadros de diálogo de firma y documento bien la interfaz de usuario  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### Fuente del entorno 122%  
 **Aparece como:** 11 ptos Segoe UI  
  
 **Usar para:** sección encabezados en los cuadros de diálogo de firma, primeros nodos de la vista de árbol de navegación de tabulación vertical  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### Fuente del entorno \+ negrita  
 **Aparece como:** en negrita 9 pt Segoe UI  
  
 **Usar para:** etiquetas y subtítulos en documentos, informes y cuadros de diálogo de firma también la interfaz de usuario  
  
 **Código de procedimientos:** donde "textBlock" es un TextBlock previamente definido y "label" es una etiqueta definida previamente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironmentBoldStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### Estilos localizables  
 En algunos casos, los localizadores será necesario modificar los estilos de fuente para distintas configuraciones regionales, como la eliminación de negrita del texto de idiomas de Asia oriental. Para realizar la localización de los estilos de fuente, deben ser esos estilos dentro del archivo resx. Es la mejor manera de lograrlo y modificar los estilos de fuente en el Diseñador de formularios de Visual Studio establecer explícitamente los estilos de fuente en tiempo de diseño. Aunque esto crea un objeto de fuente completa y puede parecer a interrumpir la herencia de fuentes primario, solo la propiedad FontStyle se utiliza para establecer la fuente.  
  
 La solución consiste en enlazar el formulario de diálogo **FontChanged** eventos. En el **FontChanged** eventos, recorrer todos los controles y comprobar si se ha establecido su fuente. Si se establece, cámbiela a una fuente nueva basada en la fuente del formulario y el estilo de fuente anterior del control. Un ejemplo de este código es:  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e) { SetFontStyles(); } /// <summary> /// SetFontStyles - This function will iterate all controls on a page /// and recreate their font with the desired fontstyle. /// It should be called in the OnFontChanged handler (and also in the constructor /// in case the IUIService is not available so OnFontChange doesn't fire). /// This way, when the VS shell font is given to us the controls that have /// a different style for the font (bolded for example) will recreate their font /// and use the VS shell font but with a style variation (bolded ...). /// </summary> protected void SetFontStyles() { SetFontStyles(this, this, this.Font); } protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont) { foreach(Control c in parent.Controls) { if (c.Controls != null && c.Controls.Count > 0) { SetFontStyles(topControl, c, referenceFont); } if (c.Font != topControl.Font) { c.Font = new Font(referenceFont, c.Font.Style); } } }  
```  
  
 Mediante este código garantiza que cuando se actualiza la fuente del formulario, también se actualizarán las fuentes de controles. Este método también debe llamarse desde el constructor del formulario, porque podría producir un error el cuadro de diálogo obtener una instancia de **IUIService** y **FontChanged** evento nunca se activará. Enlace **FontChanged** permitirá a los cuadros de diálogo Seleccionar dinámicamente la nueva fuente incluso si ya está abierto el cuadro de diálogo.  
  
### Pruebas de la fuente del entorno  
 Para asegurarse de que la interfaz de usuario está usando la fuente del entorno y respeta la configuración de tamaño, abra **Herramientas \> Opciones \> entorno \> fuentes y colores** y seleccione "Fuente del entorno" en la "Mostrar valores para:" menú desplegable.  
  
 ![Fonts and Colors page in Tools &#62; Options dialog](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201\-a\_OptionsFonts")  
  
 **Configuración de fuentes y colores en las herramientas \> cuadro de diálogo Opciones**  
  
 Establezca la fuente en algo muy diferente al predeterminado. Para que sea evidente que no actualiza la interfaz de usuario, elija una fuente de gracias \(por ejemplo, "Times New Roman"\) y establezca un tamaño muy grande. A continuación, pruebe la interfaz de usuario para asegurarse de que respeta el medio ambiente. Este es un ejemplo utilizando el cuadro de diálogo de licencia:  
  
 ![Example of dialog not using the environment font](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201\-b\_WrongFontDialog")  
  
 **Ejemplo de texto de la interfaz de usuario que no se respetan la fuente del entorno**  
  
 En este caso, "Información de usuario" y "Información de producto" no respetan la fuente. En algunos casos quizás sea una opción de diseño explícito, pero puede ser un error si no se especifica la fuente explícita como parte de las especificaciones de límite.  
  
 Para restablecer la fuente, haga clic en "Usar valores predeterminados" en **Herramientas \> Opciones \> entorno \> fuentes y colores**.  
  
##  <a name="BKMK_TextStyle"></a> Estilo del texto  
 Estilo de texto hace referencia a mayúsculas y minúsculas, el peso y el tamaño de fuente. Para obtener instrucciones de implementación, consulte [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### Mayúsculas y minúsculas del texto  
  
#### Todo en mayúsculas  
 No utilice mayúsculas para los títulos o etiquetas en Visual Studio.  
  
#### Todas las minúsculas  
 No utilice minúsculas para los títulos o etiquetas en Visual Studio.  
  
#### Caso frase y título  
 Título o caso de oración, según la situación, debe usar texto en Visual Studio.  
  
|Utilice mayúsculas para:|Caso de uso frase:|  
|------------------------------|------------------------|  
|Títulos de cuadro de diálogo|Etiquetas|  
|Cuadros de grupo|Casillas de verificación|  
|Elementos de menú|Botones de radio|  
|Elementos de menú contextual|Elementos de cuadro de lista|  
|Botones|Barras de estado|  
|Etiquetas de tabla||  
|Encabezados de columna||  
|Información sobre herramientas||  
  
##### Tipo título  
 Tipo título es un estilo en el que se escriben las primeras letras de la mayoría o todas las palabras en una frase. En Visual Studio, el título se utiliza para muchos elementos, incluidos:  
  
-   **Información sobre herramientas.** Ejemplo: "vista previa de los elementos seleccionados"  
  
-   **Encabezados de columna.** Ejemplo: "respuesta del sistema"  
  
-   **Elementos de menú.** Ejemplo: "Guardar todo"  
  
 Cuando se utiliza el título, estas son las instrucciones para cuándo poner en mayúsculas palabras y dejarlos en minúscula:  
  
|Mayúsculas|Comentarios y ejemplos|  
|----------------|----------------------------|  
|Todos los nombres||  
|Todos los verbos|Incluyendo "Es" y otras formas de "para ser"|  
|Todos los adverbios|Como "De" y "When"|  
|Todos los adjetivos|Como "Este" y "Que"|  
|Todos los pronombres|Incluido el possessive "Su" así como "Es", una contracción de la pronombre "," y el verbo "is"|  
|Palabras de la primeros y últimas, independientemente de partes de la oración||  
|Preposiciones que forman parte de una frase|"Cerrar todas las ventanas" o "Apagar el sistema"|  
|Todas las letras de un acrónimo.|HTML, XML, DIRECCIÓN URL, IDE, RGB|  
|La segunda palabra en una palabra compuesta si es un sustantivo o adjetivo adecuado, o si las palabras tienen el mismo peso|Referencia cruzada, Software preliminar de Microsoft, acceso de lectura y escritura, tiempo de ejecución|  
  
|Minúsculas|Ejemplos|  
|----------------|--------------|  
|La segunda palabra en una palabra compuesta si es otra parte de la oración o un participio modificando la primera palabra|Procedimientos, despegue|  
|Los artículos, a menos que uno es la primera palabra en el título|una, una, el|  
|Coordinar conjunciones|y, sin embargo, para, ni, o|  
|Preposiciones con palabras de cuatro o menos letras fuera de una frase|en, en, como de fuera de, en la parte superior del|  
|"A" cuando se utiliza en una frase infinita|"Cómo formatear el disco duro"|  
  
##### Oración  
 Oración es el método estándar de mayúsculas y minúsculas para escribir en que solo la primera palabra de la oración aparece en mayúsculas, junto con los nombres propios y el pronombre "I". En general, la frase es más fácil para un público internacional de leer, especialmente cuando el contenido se traducirá en una máquina. Caso de uso frase:  
  
1.  **Mensajes de la barra de estado.** Estos son simples, resumen y proporcionan información de estado. Ejemplo: "cargar archivo de proyecto"  
  
2.  **Todos los demás elementos de la interfaz de usuario**, incluidas las etiquetas, casillas de verificación, botones de radio y elementos de cuadro de lista. Ejemplo: "seleccionar todos los elementos de lista"  
  
### Formato de texto  
 Formato de Visual Studio 2013 de texto predeterminado se controla mediante un [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Este servicio ayuda a garantizar una apariencia coherente de fuente en todo el IDE \(entorno de desarrollo integrado\) y debe utilizar para garantizar una experiencia coherente para los usuarios.  
  
 El tamaño predeterminado utilizado por el servicio de la fuente de Visual Studio proviene de Windows y aparece como 9 pt.  
  
 Puede aplicar formato a la fuente del entorno. Este tema se trata cómo y dónde se utilizan los estilos. Para obtener información de implementación, consulte [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### Texto en negrita  
 Texto en negrita se usa con moderación en Visual Studio y debe reservarse para:  
  
-   etiquetas de pregunta en asistentes  
  
-   designa el proyecto activo en el Explorador de soluciones  
  
-   invalida los valores en la ventana Propiedades  
  
-   ciertos eventos en las listas desplegables de editor de Visual Basic  
  
-   contenido generado por el servidor en el esquema del documento para páginas web  
  
-   encabezados de sección en el cuadro de diálogo complejo o diseñador de interfaz de usuario  
  
#### Cursiva  
 Visual Studio no utiliza texto en cursiva o en negrita cursiva.  
  
#### Color  
  
-   Azul está reservado para los hipervínculos \(navegación y comandos\) y nunca debe utilizarse para la orientación.  
  
-   Encabezados de mayor \(fuente del entorno x 155% o superior\) pueden ser coloreados para estos fines:  
  
    -   Para proporcionar el atractivo visual a la firma de interfaz de usuario de Visual Studio  
  
    -   Para llamar la atención sobre un área específica  
  
    -   Para ofrecer un alivio del color del texto de entorno estándar de negro o gris oscuro  
  
-   Color de los encabezados debe aprovechar Visual Studio marca colores existentes, principalmente el principal púrpura, FF68217A \#.  
  
-   Cuando se utiliza el color en encabezados, debe cumplir la [directrices de colores de Windows](https://msdn.microsoft.com/en-us/library/dn742482.aspx), incluidas las de contraste y otras consideraciones de accesibilidad.  
  
### Tamaño de fuente  
 Diseño de Visual Studio UI presenta un aspecto más claro con más espacio en blanco. Siempre que sea posible, barras de título y chrome se han reducido o eliminado. Aunque la densidad de la información es un requisito en Visual Studio, tipografía sigue siendo importante, con énfasis en interlineado más abierto y variedad de tamaños de fuente y pesos.  
  
 Las tablas siguientes se incluye detalles de diseño y ejemplos para las fuentes de pantalla utilizadas en Visual Studio. Algunas variaciones de fuente de la pantalla tienen el tamaño y el peso, como Semilight o luz, codificado en su aspecto.  
  
 Fragmentos de código de implementación para mostrar todas las fuentes pueden encontrarse en [Formato de referencia (escalado/negrita)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### Fuente del entorno 375% \+ claro  
  
|||  
|-|-|  
|**Uso:** excepcionales. Interfaz de usuario de la marca sólo UNIQUE.<br /><br /> **Hacer:**<br /><br /> -   Utilice la oración<br />-   Utilice siempre ligero<br /><br /> **No:**<br /><br /> -   Uso de la interfaz de usuario que no sea de interfaz de usuario como página de inicio de la firma<br />-   Negrita, cursiva o negrita cursiva<br />-   Uso de texto<br />-   Utilizar ventanas de herramientas|**Aparece como:** pt 34 Segoe UI Light<br /><br /> **Ejemplo Visual:**<br /><br /> *No se usa actualmente. Puede utilizarse en la página de inicio.*|  
  
#### Fuente del entorno 310% \+ claro  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -   Mayor de encabezado en los cuadros de diálogo de firma<br />-   Título del informe principal<br /><br /> **Hacer:**<br /><br /> -   Utilice la oración<br />-   Utilice siempre ligero<br /><br /> **No:**<br /><br /> -   Uso de la interfaz de usuario que no sea de interfaz de usuario como página de inicio de la firma<br />-   Negrita, cursiva o negrita cursiva<br />-   Uso de texto<br />-   Utilizar ventanas de herramientas|**Aparece como:** 28 pt Segoe UI Light<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of 310% Environment font &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202\-a\_EF310")|  
  
#### Fuente del entorno 200% \+ Semiclaro  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -   Subtítulos<br />-   Títulos de los cuadros de diálogo pequeñas y medianas<br /><br /> **Hacer:**<br /><br /> -   Utilice la oración<br />-   Utilice siempre el peso de Semiclaro<br /><br /> **No:**<br /><br /> -   Negrita, cursiva o negrita cursiva<br />-   Uso de texto<br />-   Utilizar ventanas de herramientas|**Aparece como:** 18 pto Segoe UI Semillight<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of 200% Environment font &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202\-b\_EF200")|  
  
#### Fuente del entorno 155%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -   Títulos de sección del documento bien la interfaz de usuario<br />-   Informes<br /><br /> **Hacer:** usar oración<br /><br /> **No:**<br /><br /> -   Negrita, cursiva o negrita cursiva<br />-   Uso de texto<br />-   Usar estándar de que controles de Visual Studio<br />-   Utilizar ventanas de herramientas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of 155% Environment font heading](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202\-c\_EF155")|  
  
#### Fuente del entorno 133%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -   Subtítulos más pequeños en los cuadros de diálogo de firma<br />-   Menor subtítulos en documento bien interfaz de usuario<br /><br /> **Hacer:** usar oración<br /><br /> **No:**<br /><br /> -   Negrita, cursiva o negrita cursiva<br />-   Uso de texto<br />-   Usar estándar de que controles de Visual Studio<br />-   Utilizar ventanas de herramientas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of 133% Environment font heading](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202\-d\_EF133")|  
  
#### Fuente del entorno 122%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -   Títulos de sección en los cuadros de diálogo de firma<br />-   Nodos principales en la vista de árbol<br />-   Exploración de tabulación vertical<br /><br /> **Hacer:** usar oración<br /><br /> **No:**<br /><br /> -   Negrita, cursiva o negrita cursiva<br />-   Uso de texto<br />-   Usar estándar de que controles de Visual Studio<br />-   Utilizar ventanas de herramientas|**Aparece como:** 11 ptos Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of 122% Environment font heading](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202\-e\_EF122")|  
  
#### Fuente del entorno \+ negrita  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -   Las etiquetas y los subtítulos en cuadros de diálogo de firma<br />-   Las etiquetas y los subtítulos en los informes<br />-   Etiquetas y subtítulos en documento también la interfaz de usuario<br /><br /> **Hacer:**<br /><br /> -   Utilice la oración<br />-   Utilice el grosor de negrita<br /><br /> **No:**<br /><br /> -   Cursiva o negrita cursiva<br />-   Uso de texto<br />-   Usar estándar de que controles de Visual Studio<br />-   Utilizar ventanas de herramientas|**Aparece como:** en negrita 9 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of Environment font &#43; Bold heading](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202\-f\_EFB")|  
  
#### Fuente del entorno  
  
|||  
|-|-|  
|**Uso:** todo el texto<br /><br /> **Hacer:** usar oración<br /><br /> **No:** cursiva o negrita cursiva|**Aparece como:** 9 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Example of Environment font](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202\-g\_EF")|  
  
### Relleno y espaciado  
 Encabezados requieren espacio alrededor de ellas para darles un énfasis adecuado. Este espacio varía según el tamaño de punto y lo está cerca del encabezado, por ejemplo, una regla horizontal o una línea de texto en la fuente del entorno.  
  
-   El relleno ideal para un encabezado por sí mismo debe ser el 90% del espacio de alto de caracteres de capital. Por ejemplo, un encabezado de Segoe UI Light de 28 pt tiene un alto de cap de 26 pto y el relleno debe ser aproximadamente 23 pt o unos 31 píxeles.  
  
-   El espacio mínimo en torno a un encabezado debe ser el 50% del alto del carácter de capital. Cuando un encabezado viene acompañado por una regla u otro elemento de una estrecha conexión, puede utilizarse menos espacio.  
  
-   Texto en negrita de la fuente de entorno debe seguir relleno y espaciado de alto de línea predeterminado.  
  
## Vea también  
 [MSDN: Fuentes \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Texto \(Windows\) de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)