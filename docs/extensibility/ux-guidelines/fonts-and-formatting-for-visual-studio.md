---
title: Las fuentes y el formato de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: c55c135034f5b3b2dd09ccf94e22e56e8f04797e
ms.contentlocale: es-es
ms.lasthandoff: 05/04/2017

---
# <a name="fonts-and-formatting-for-visual-studio"></a>Las fuentes y el formato de Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a>La fuente del entorno  
 Todas las fuentes dentro de Visual Studio se deben exponer al usuario para la personalización. Esto se realiza principalmente mediante la **fuentes y colores** página en el **Herramientas > opciones** cuadro de diálogo. Las tres categorías principales de configuración de fuente son:  
  
-   **Fuente del entorno** : la fuente principal para el IDE (entorno de desarrollo integrado), utilizada para todos los elementos de interfaz, incluidos los cuadros de diálogo, menús, ventanas de herramientas y ventanas de documento. De forma predeterminada, la fuente del entorno está asociada a una fuente del sistema que se muestra como 9 pt Segoe UI en las versiones actuales de Windows. Uso de fuentes para todos los elementos de la interfaz ayuda a garantizar una apariencia coherente de fuente en todo el IDE.  
  
-   **Editor de texto** : página de elementos que expuesta en código y otros editores basados en texto se pueden personalizar en el Editor de texto en **Herramientas > opciones**.  
  
-   **Recopilaciones específicas** : ventanas del diseñador que ofrecen la personalización de sus elementos de interfaz de usuario puede exponer fuentes específicas de su diseño expuesta en su propia página de configuración de **Herramientas > opciones**.  
  
### <a name="editor-font-customization-and-resizing"></a>Personalización de fuente del Editor y el cambio de tamaño  
 Los usuarios a menudo se ampliar o alejar el tamaño o el color del texto en el editor según sus preferencias, independientemente de la interfaz de usuario general. Dado que la fuente del entorno se usa en los elementos que pueden aparecer dentro de o como parte de un editor o diseñador, es importante tener en cuenta el comportamiento esperado cuando se cambia una de estas clasificaciones de fuente.  
  
 Al crear elementos de interfaz de usuario que aparecen en el editor pero que no forman parte de la *contenido*, es importante usar la fuente del entorno y no la fuente del texto, por lo que cambiar el tamaño de los elementos de una manera predecible.  
  
1.  Para el texto del código en el editor, cambiar el tamaño con el valor de fuente del texto de código y responder al nivel de zoom del texto del editor.  
  
2.  Todos los demás elementos de la interfaz deben asociarse a la configuración de fuente del entorno y responden a los cambios en el entorno globales. Esto incluye (pero no está limitado a):  
  
    -   Texto en los menús contextuales  
  
    -   Texto en un elemento de gráfico del editor, como texto de menú de bombilla, panel del editor de la búsqueda rápida y vaya al panel  
  
    -   Etiqueta de texto en cuadros de diálogo, como **buscar en archivos** o **refactorizar**  
  
### <a name="accessing-the-environment-font"></a>Obtener acceso a la fuente del entorno  
 En código nativo o de formularios Windows Forms, la fuente del entorno son accesibles mediante una llamada al método `IUIHostLocale::GetDialogFont` después de consultar la interfaz desde el `SID_SUIHostLocale` service.  
  
 Para Windows Presentation Foundation (WPF), derive su clase de ventana de cuadro de diálogo desde el shell `DialogWindow` clase en lugar de WPF `Window` clase.  
  
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
  
 (Reemplace `Microsoft.VisualStudio.Shell.11.0` con la versión actual de la dll MPF.)  
  
 Para mostrar el cuadro de diálogo, llame a "`ShowModal()`" en la clase sobre `ShowDialog()`. `ShowModal()`establece el estado modal correcto en el shell, asegura que el cuadro de diálogo se centra en la ventana primaria y así sucesivamente.  
  
 El código es como sigue:  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
```  
  
 `ShowModal`¿Devuelve un tipo bool? (un valor booleano que acepta valores NULL) con el `DialogResult`, que puede utilizarse si es necesario. El valor devuelto es true si se ha cerrado el cuadro de diálogo con **Aceptar**.  
  
 Si se necesitan para mostrar algunos UI de WPF que no es un cuadro de diálogo y se hospeda en su propio `HwndSource`, como una ventana emergente o una ventana secundaria WPF de una ventana de ventana primaria de Win32/formularios Windows Forms, debe establecer el `FontFamily` y `FontSize` en el elemento raíz del elemento WPF. (El shell establece las propiedades en la ventana principal, pero no se puede heredar más allá de un `HWND`). El shell proporciona recursos a los que se pueden enlazar las propiedades, como el siguiente:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```  
  
###  <a name="BKMK_Formatting"></a>Formato de referencia (ajuste de escala/negrita)  
 Algunos cuadros de diálogo requieren un texto determinado esté en negrita o un tamaño distinto de la fuente del entorno. Anteriormente, las fuentes mayores que la fuente del entorno se codificación como "`environment font +2`" o similar. Uso de fragmentos de código que se proporcionan admitirá a monitores valores altos de PPP y asegurarse de que siempre aparece texto de presentación en el tamaño correcto y el peso (como la luz o Semilight).  
  
> **Nota: Antes de aplicar formato, asegúrese de que esté siguiendo las directrices recogidas en [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Para escalar la fuente del entorno, establecer el estilo del TextBlock o la etiqueta, como se indica. Cada uno de estos fragmentos de código, que se usan correctamente, generará la fuente correcta, incluidas las variaciones de tamaño y peso adecuadas.  
  
 Donde "`vsui`" es una referencia al espacio de nombres `Microsoft.VisualStudio.Shell`:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```  
  
#### <a name="375-environment-font--light"></a>Fuente del entorno 375% + claro  
 **Aparece como:** Segoe UI Light de pt 34  
 **Uso de:** (poco frecuente) único con la marca la interfaz de usuario, al igual que en la página de inicio

 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```  
  
#### <a name="310-environment-font--light"></a>Fuente del entorno 310% + claro  
 **Aparece como:** Segoe UI Light de pt 28   
 **Uso de:** títulos de cuadro de diálogo firma grandes, principales de encabezado en los informes  
  
 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```  
  
#### <a name="200-environment-font--semilight"></a>Fuente del entorno 200% + Semiclaro  
 **Aparece como:** 18 pto Segoe UI Semilight    
 **Uso de:** subtítulos, títulos de los cuadros de diálogo pequeñas y medianas  
  
 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente: 
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```  
  
#### <a name="155-environment-font"></a>Fuente del entorno 155%  
 **Aparece como:** 14 pt Segoe UI    
 **Uso de:** encabezados de las secciones en el documento bien la interfaz de usuario o los informes  
  
 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```  
  
#### <a name="133-environment-font"></a>Fuente del entorno 133%  
 **Aparece como:** 12 pto Segoe UI    
 **Uso de:** subtítulos más pequeños en los cuadros de diálogo de firma y documento bien la interfaz de usuario  
  
 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```  
  
#### <a name="122-environment-font"></a>Fuente del entorno 122%  
 **Aparece como:** 11 ptos Segoe UI    
 **Uso de:** sección encabezados en los cuadros de diálogo de firma, mejores nodos en la vista de árbol de navegación de tabulación vertical  
  
 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```  
  
#### <a name="environment-font--bold"></a>Fuente del entorno + negrita  
 **Aparece como:** en negrita 9 pt Segoe UI    
 **Uso de:** las etiquetas y los subtítulos en los cuadros de diálogo de firma, informes y documento bien la interfaz de usuario  
  
 **Código de procedimiento:** donde `textBlock` es un TextBlock definido previamente y `label` es una etiqueta definida previamente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```  
  
 **XAML:** establecer el estilo del TextBlock o la etiqueta, tal como se muestra:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```  
  
### <a name="localizable-styles"></a>Estilos localizables  
 En algunos casos, los localizadores será necesario modificar los estilos de fuente para diferentes configuraciones regionales, como quitar negrita de texto para idiomas de Asia oriental. Para que sea posible la localización de los estilos de fuente, los estilos deben ser en el archivo .resx. Es la mejor manera de lograr esto y modificar los estilos de fuente en el Diseñador de formularios de Visual Studio establecer explícitamente los estilos de fuente en tiempo de diseño. Aunque esto crea un objeto de fuente completa y puede parecer que interrumpir la herencia de fuentes del elemento primario, solo la propiedad FontStyle se utiliza para establecer la fuente.  
  
 La solución consiste en enlazar el formulario de cuadro de diálogo `FontChanged` eventos. En el `FontChanged` eventos, recorra todos los controles y comprobar si se ha establecido su fuente. Si se establece, cámbiela a una fuente nueva en función de la fuente del formulario y el estilo de fuente anterior del control. Es un ejemplo de esto en el código:  
  
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
  
 Con este código garantiza que cuando se actualiza la fuente del formulario, también se actualizarán las fuentes de los controles. Este método también debe llamarse desde el constructor del formulario, porque podría producirá un error en el cuadro de diálogo obtener una instancia de `IUIService` y `FontChanged` nunca se desencadenará el evento. Enlazar `FontChanged` permitirá a los cuadros de diálogo recoger dinámicamente la nueva fuente incluso si ya está abierto el cuadro de diálogo.  
  
### <a name="testing-the-environment-font"></a>Probar la fuente del entorno  
 Para asegurarse de que la interfaz de usuario está usando la fuente del entorno y respeta la configuración de tamaño, abra **Herramientas > Opciones > entorno > fuentes y colores** y seleccione "Fuente del entorno" en la "Mostrar valores para:" menú desplegable.  
  
 ![Configuración de fuentes y colores en las herramientas de &gt; cuadro de diálogo Opciones](~/extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Configuración de fuentes y colores en las herramientas de &gt; cuadro de diálogo Opciones
  
 Establezca la fuente en algo muy diferente al predeterminado. Para que sea obvio que no actualiza la interfaz de usuario, elija una fuente con gracias (por ejemplo, "Times New Roman") y establezca un tamaño muy grande. A continuación, pruebe la interfaz de usuario para asegurarse de que respeta el entorno. Este es un ejemplo de cómo utilizar el cuadro de diálogo de licencia:  
  
 ![Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno](~/extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Ejemplo de texto de la interfaz de usuario que no respeta la fuente del entorno
  
 En este caso, "Información de usuario" e "Información de producto" no respetan la fuente. En algunos casos esto podría ser una opción de diseño explícito, pero puede ser un error si la fuente explícita no se especifica como parte de las especificaciones de límite.  
  
 Para restablecer la fuente, haga clic en "Usar valores predeterminados" en **Herramientas > Opciones > entorno > fuentes y colores**.  
  
##  <a name="BKMK_TextStyle"></a>Estilo de texto  
 Estilo de texto hace referencia a mayúsculas y minúsculas, el peso y el tamaño de fuente. Para obtener instrucciones de implementación, consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Mayúsculas y minúsculas del texto  
  
#### <a name="all-caps"></a>Todo en mayúsculas  
 No utilice mayúsculas para los títulos o etiquetas en Visual Studio.  
  
#### <a name="all-lowercase"></a>Todas las minúsculas  
 Debe usarse en minúsculas para los títulos o etiquetas en Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Caso de las frases y título  
 Tipo título o caso de oración, dependiendo de la situación, debe usar texto en Visual Studio.  
  
|Utilice mayúsculas para:|Caso de frase de uso de:|  
|-------------------------|----------------------------|  
|Títulos de cuadro de diálogo|Etiquetas|  
|Cuadros de grupo|Casillas de verificación|  
|Elementos de menú|Botones de radio|  
|Elementos de menú contextual|Elementos de cuadro de lista|  
|Botones|Barras de estado|  
|Etiquetas de tabla||  
|Encabezados de columna||  
|Información sobre herramientas||  
  
##### <a name="title-case"></a>Tipo título  
 Tipo título es un estilo en el que están en mayúscula las primeras letras de la mayoría o todas las palabras en una frase. En Visual Studio, mayúscula inicial se utiliza para muchos elementos, incluidos:  
  
-   **Información sobre herramientas.** Ejemplo: "vista previa de los elementos seleccionados"  
  
-   **Encabezados de columna.** Ejemplo: "respuesta del sistema"  
  
-   **Elementos de menú.** Ejemplo: "Guardar todo"  
  
 Cuando se usa mayúscula inicial, estas son las instrucciones para cuándo aprovechar palabras y dejarlos en minúsculas:  
  
|Mayúsculas|Comentarios y ejemplos|  
|---------------|---------------------------|  
|Todos los nombres||  
|Todos los verbos|Incluyendo "Es" y otras formas de "para ser"|  
|Todos adverbios|Incluye "De" y la "Fecha"|  
|Todos los adjetivos|Como "Esto" y "Que"|  
|Todos los pronombres|Incluidas la posesivo "Su", así como la"," una contracción de la pronombre "," y el verbo "es"|  
|Primera y la última palabra, independientemente de partes de la oración||  
|Preposiciones que forman parte de una frase|"Cerrar todas las ventanas" o "Apagado del sistema"|  
|Todas las letras de un acrónimo|HTML, XML, DIRECCIÓN URL, IDE, RGB|  
|El segundo de palabras de una palabra compuesta si es un sustantivo o adjetivo apropiado, o si las palabras tienen el mismo peso|Referencia cruzada, Software de Microsoft anterior, acceso de lectura/escritura, tiempo de ejecución|  
  
|Minúsculas|Ejemplos|  
|---------------|--------------|  
|La segunda palabra de una palabra compuesta si es un participio modificando la primera palabra o en otra parte de la oración|"Cómo...", despegue|  
|Los artículos, a menos que uno es la primera palabra en el título|una, una, el|  
|Coordinar conjunciones|y, sin embargo, para, ni, o|  
|Preposiciones con palabras de cuatro o menos caracteres no recogidos en una frase de verbo|en, en, como para salir del modo de, en la parte superior de|  
|"A" cuando se utiliza en una frase infinitivo|"Cómo formatear el disco duro"|  
  
##### <a name="sentence-case"></a>Tipo oración  
 Oración es el método estándar de mayúsculas y minúsculas para escribir en la que aparece con mayúsculas solo la primera palabra de la frase, junto con los nombres propios y el pronombre "I". En general, el tipo oración es más fácil para una audiencia mundial leer, especialmente cuando el contenido se traducirá por una máquina. Caso de frase de uso de:  
  
1.  **Mensajes de la barra de estado.** Estos son simples, resumen y proporcionan información de estado. Ejemplo: "cargar archivo de proyecto"  
  
2.  **Todos los demás elementos de interfaz de usuario**, incluidas las etiquetas, casillas de verificación, los botones de radio y elementos de cuadro de lista. Ejemplo: "seleccionar todos los elementos de lista"  
  
### <a name="text-formatting"></a>Formato de texto  
 Formato de Visual Studio 2013 de texto predeterminado se controla mediante [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Este servicio ayuda a garantizar una apariencia coherente de fuente en todo el IDE (entorno de desarrollo integrado), y se debe usar para garantizar una experiencia coherente para los usuarios.  
  
 El tamaño predeterminado utilizado por el servicio de la fuente de Visual Studio proviene de Windows y aparece como 9 pt.  
  
 Puede aplicar formato a la fuente del entorno. Este tema se explica cómo y dónde se utilizan los estilos. Para obtener más información, consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Texto en negrita  
 Texto en negrita se usa con moderación en Visual Studio y que debe reservarse para:  
  
-   etiquetas de pregunta en asistentes  
  
-   designación del proyecto activo en el Explorador de soluciones  
  
-   invalida los valores en la ventana de herramientas de propiedades  
  
-   determinados eventos en las listas desplegables de editor de Visual Basic  
  
-   contenido generado por el servidor en el esquema del documento para páginas web  
  
-   encabezados de sección en el cuadro de diálogo complejo o el Diseñador de interfaz de usuario  
  
#### <a name="italics"></a>Cursiva  
 Visual Studio no utiliza texto en cursiva cursiva o en negrita.  
  
#### <a name="color"></a>Color  
  
-   Azul está reservado para los hipervínculos (navegación y comandos) y nunca debe utilizarse para la orientación.  
  
-   Pueden ser coloreados de encabezados de mayor (fuente del entorno x 155% o superior) para estos fines:  
  
    -   Para proporcionar atractivo visual a la firma de interfaz de usuario de Visual Studio  
  
    -   Para llamar la atención sobre un área específica  
  
    -   Para ofrecer relieve del color de texto estándar entorno gris y negro oscuro  
  
-   Color de encabezados debe aprovechar existente Visual Studio marca colores, principalmente el púrpura principal, #FF68217A.  
  
-   Cuando se utiliza el color en encabezados, debe cumplir la [directrices de colores de Windows](https://msdn.microsoft.com/en-us/library/dn742482.aspx), incluidos los de contraste y otras consideraciones de accesibilidad.  
  
### <a name="font-size"></a>Tamaño de fuente  
 Diseño de Visual Studio interfaz de usuario presenta un aspecto más claro con más espacio en blanco. Siempre que sea posible, barras de título y chrome se han reducido o eliminado. Mientras la densidad de la información es un requisito en Visual Studio, tipografía sigue siendo importante, con énfasis en interlineado más abierto y una variedad de tamaños de fuente y pesos.  
  
 Las tablas siguientes se incluye detalles de diseño y ejemplos visuales de las fuentes de presentación que se usa en Visual Studio. Algunas variaciones de fuente de pantalla tienen el tamaño y el peso, como Semilight o claro, codificado en su apariencia.  
  
 Fragmentos de código de implementación para todas las fuentes de pantalla pueden encontrarse en [formato (ajuste de escala/negrita) referencia](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Fuente del entorno 375% + claro  
  
|||  
|-|-|  
|**Uso:** poco frecuentes. Interfaz de usuario de la marca solo UNIQUE.<br /><br /> **Hacer:**<br /><br /> -Use el tipo oración<br />-Use siempre ligero<br /><br /> **No:**<br /><br /> -Uso de la interfaz de usuario que no sea de interfaz de usuario como página de inicio de firma<br />-Negrita, cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en las ventanas de herramientas|**Aparece como:** Segoe UI Light de pt 34<br /><br /> **Ejemplo Visual:**<br /><br /> *Actualmente no utilizado. Puede usarse en la página de inicio.*|  
  
#### <a name="310-environment-font--light"></a>Fuente del entorno 310% + claro  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Encabezado mayor en los cuadros de diálogo de firma<br />-Encabezado de informe principal<br /><br /> **Hacer:**<br /><br /> -Use el tipo oración<br />-Use siempre ligero<br /><br /> **No:**<br /><br /> -Uso de la interfaz de usuario que no sea de interfaz de usuario como página de inicio de firma<br />-Negrita, cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en las ventanas de herramientas|**Aparece como:** Segoe UI Light de pt 28<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno 310% &#43; Encabezado claro](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Fuente del entorno 200% + Semiclaro  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Subtítulos<br />-Títulos de los cuadros de diálogo pequeñas y medianas<br /><br /> **Hacer:**<br /><br /> -Use el tipo oración<br />-Use siempre Semilight peso<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en las ventanas de herramientas|**Aparece como:** 18 pto Segoe UI Semillight<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|  
  
#### <a name="155-environment-font"></a>Fuente del entorno 155%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Section títulos de documento bien la interfaz de usuario<br />: Informes<br /><br /> **Realice:** frase caso de uso<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en los controles estándar de Visual Studio<br />-Usar en las ventanas de herramientas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 155%](~/extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|  
  
#### <a name="133-environment-font"></a>Fuente del entorno 133%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Menores subtítulos en los cuadros de diálogo de firma<br />-Menores subtítulos en documento bien la interfaz de usuario<br /><br /> **Realice:** frase caso de uso<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en los controles estándar de Visual Studio<br />-Usar en las ventanas de herramientas|**Aparece como:** 12 pto Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|  
  
#### <a name="122-environment-font"></a>Fuente del entorno 122%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Encabezados de sección en los cuadros de diálogo de firma<br />-Nodos superior en la vista de árbol<br />-Exploración por fichas vertical<br /><br /> **Realice:** frase caso de uso<br /><br /> **No:**<br /><br /> -Negrita, cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en los controles estándar de Visual Studio<br />-Usar en las ventanas de herramientas|**Aparece como:** 11 ptos Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de encabezado con fuente del entorno 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|  
  
#### <a name="environment-font--bold"></a>Fuente del entorno + negrita  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Las etiquetas y subtítulos en los cuadros de diálogo de firma<br />-Las etiquetas y subtítulos en informes<br />-Las etiquetas y subtítulos en documento bien la interfaz de usuario<br /><br /> **Hacer:**<br /><br /> -Use el tipo oración<br />-Use peso negrita<br /><br /> **No:**<br /><br /> -Cursiva o negrita cursiva<br />-Uso para el texto principal<br />-Usar en los controles estándar de Visual Studio<br />-Usar en las ventanas de herramientas|**Aparece como:** en negrita 9 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno &#43; Encabezado en negrita](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|  
  
#### <a name="environment-font"></a>Fuente del entorno  
  
|||  
|-|-|  
|**Uso:** todo el texto<br /><br /> **Realice:** frase caso de uso<br /><br /> **No:** cursiva o negrita cursiva|**Aparece como:** 9 pt Segoe UI<br /><br /> **Ejemplo Visual:**<br /><br /> ![Ejemplo de fuente del entorno](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|  
  
### <a name="padding-and-spacing"></a>Relleno y espaciado  
 Encabezados requieren espacio alrededor de ellas para darles el énfasis adecuado. Este espacio varía según el tamaño de punto y lo está cerca del encabezado, por ejemplo, una regla horizontal o una línea de texto en la fuente del entorno.  
  
-   El relleno ideal para un encabezado de por sí solo debe ser 90% del espacio de alto de caracteres de capital. Por ejemplo, un encabezado de Segoe UI Light de 28 pt tiene un alto de límite de 26 pt y el relleno debe ser aproximadamente pt 23 o 31 unos píxeles.  
  
-   El espacio mínimo alrededor de un encabezado debe ser el 50% del alto del carácter de capital. Cuando un encabezado está acompañado por una regla u otro elemento de una estrecha conexión, puede utilizarse menos espacio.  
  
-   Texto en negrita de la fuente de entorno debe seguir relleno y espaciado de alto de línea predeterminado.  
  
## <a name="see-also"></a>Vea también  
 [MSDN: Fuentes (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Texto (Windows) de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)
