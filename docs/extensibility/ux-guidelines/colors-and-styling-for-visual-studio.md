---
title: Colores y estilos para Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
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
ms.openlocfilehash: 93bfad7dc919364770a7d225c09db8b432cf1be0
ms.contentlocale: es-es
ms.lasthandoff: 05/04/2017

---
# <a name="colors-and-styling-for-visual-studio"></a>Colores y estilos para Visual Studio
## <a name="using-color-in-visual-studio"></a>Con color en Visual Studio  
En Visual Studio, el color se utiliza principalmente como herramienta de comunicación, no solo como decoración. Usar color como mínimo y reservar para situaciones en que desea:  
  
-   Comunicar el significado o la afiliación (por ejemplo, los modificadores de plataforma o lenguaje)  
  
-   Llamar la atención (por ejemplo, que indica un cambio de estado)  
  
-   Mejorar la legibilidad y proporcionar hitos para navegar por la interfaz de usuario  
  
-   Aumentar la conveniencia  
  
Existen varias opciones para asignar colores a elementos de interfaz de usuario en Visual Studio. A veces puede ser difícil figura out qué opción se supone que utiliza, o cómo se usa correctamente. En este tema le ayudará a:  
  
1.  Comprender los distintos servicios y sistemas que se usan para definir colores en Visual Studio.  
  
2.  Seleccione la opción correcta para un elemento determinado.  
  
3.  Usar correctamente la opción que ha elegido.  
  
> **Nota:** nunca codificar hexadecimal, RGB o colores del sistema para los elementos de interfaz de usuario. Usar los servicios permite flexibilidad para optimizar el matiz. Además, sin que el servicio, no podrá aprovechar las capacidades de cambio de tema de [el servicio de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para asignar colores a elementos de la interfaz de Visual Studio  
Elija el método que mejor se adapte a sus elementos de interfaz de usuario.  
  
| La interfaz de usuario | Método | ¿Qué son? |  
| --- | --- | --- |  
| Se han incrustado o cuadros de diálogo independiente. | **Colores del sistema** | Nombres de sistema que permitir que el sistema operativo definir el color y la apariencia de los elementos de interfaz de usuario, al igual que los controles de cuadro de diálogo común. |
| Tiene una interfaz de usuario personalizada que desea que sea coherente con el entorno general de VS y tiene elementos de interfaz de usuario que coinciden con la categoría y el significado semántico de los tokens compartidos. | **Colores comunes compartidos** | Nombres de token de colores predefinidos existentes para los elementos de interfaz de usuario específicos |
| Tiene una característica individual o un grupo de características y no hay ningún color compartido para elementos similares. | **Colores personalizados** | Nombres de símbolo (token) de colores que son específicos de un área y no tiene pensado compartir con otra interfaz de usuario |
| Desea permitir que el usuario final personalizar la interfaz de usuario o el contenido (por ejemplo, para los editores de texto o ventanas del diseñador especializados). | **Personalización del usuario final**<br /><br />**(Herramientas &gt; cuadro de diálogo Opciones)** | Configuración definida en la página "Fuentes y colores" de la **herramientas &gt; opciones** cuadro de diálogo o una página especializada específica de una característica de interfaz de usuario. |
| Tiene interfaz de usuario que se crearon en HTML. | **Daytona** | Permite la interfaz de usuario creado en HTML para tener acceso al servicio de color y fuente. |
  
### <a name="visual-studio-themes"></a>Temas visuales Studio  
Visual Studio incluye tres temas de color diferente: azul, claro y oscuro. Asimismo, detecta el modo de contraste alto, que es un tema de color de todo el sistema diseñado para mejorar la accesibilidad.  
  
Los usuarios le pedirá que seleccione un tema durante el primer uso de Visual Studio y pueden cambiar los temas más tarde, vaya a **herramientas &gt; opciones &gt; entorno &gt; General** y elegir un nuevo tema en el menú desplegable de "tema de color".  
  
Los usuarios también pueden usar el Panel de Control para cambiar sus sistemas todos en uno de los diversos temas de contraste alto. Si un usuario selecciona un tema de contraste alto, a continuación, el selector de tema de color de Visual Studio ya no afecta a los colores en Visual Studio, aunque se guardan los cambios de tema para cuando el usuario sale del modo de contraste alto. Para obtener más información acerca del modo de contraste alto, consulte [colores de contraste alto elegir](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).
  
### <a name="the-vscolor-service"></a>El servicio VSColor  
Visual Studio proporciona un servicio de color de entorno, conocido como el servicio VSColor, que le permite enlazar los valores de color de los elementos de interfaz de usuario a una entrada con nombre que contiene los valores de color para cada tema de Visual Studio. Esto garantiza que sus colores cambiará automáticamente para reflejar la actual seleccionado por el usuario tema o un sistema de modo de contraste alto. Uso del servicio significa que la implementación de todos los cambios relacionados con el tema de color se controla en un solo lugar y, si está utilizando los colores comunes compartidos desde el servicio, la interfaz de usuario reflejará automáticamente nuevos temas en versiones futuras de Visual Studio.  
  
### <a name="implementation"></a>Implementación  
El código fuente de Visual Studio incluye varios archivos de definición de paquete que contienen listas de los nombres de símbolo (token) y los valores de color correspondiente para cada tema. El servicio de color lee el VSColors definido en estos archivos de definición de paquete. Estos colores se hace referencia en el marcado XAML o en el código y, a continuación, se cargan a través del `IVsUIShell5.GetThemedColor` método o una asignación DynamicResource.  
  
### <a name="system-colors"></a>Colores del sistema  
Controles comunes de hacer referencia a los colores del sistema de forma predeterminada. Si desea que la interfaz de usuario para usar colores del sistema, como cuando se crea un cuadro de diálogo independiente o incrustado, no es necesario hacer nada.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Colores comunes compartidos en el servicio de VSColor  
Los elementos de la interfaz deben reflejar el entorno general de Visual Studio. Si se reutiliza los colores comunes compartidos que son adecuados para el componente de interfaz de usuario que está diseñando, asegúrese de que la interfaz sea coherente con otras interfaces de Visual Studio y que sus colores se actualizarán automáticamente cuando se agregan o actualizan los temas.  
  
Antes de usar los colores comunes compartidos, asegúrese de que comprende cómo usarlas correctamente. Uso incorrecto de los colores comunes compartidos podría dar lugar a una experiencia incoherente, frustrante o confusa para los usuarios.  
  
### <a name="user-customizable-colors"></a>Colores personalizables por el usuario  
Véase: [exponer colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
A veces, desea permitir que el usuario final personalizar la interfaz de usuario, como cuando se crea un editor de código o la superficie de diseño. Componentes de interfaz de usuario personalizables se encuentran en el **fuentes y colores** sección de la **herramientas &gt; opciones** cuadro de diálogo, donde los usuarios pueden elegir para cambiar el color de primer plano, color de fondo o ambos.  
  
![Herramientas &gt; cuadro de diálogo Opciones](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Herramientas &gt; cuadro de diálogo Opciones
  
### <a name="web-ui-colors"></a>Colores de la interfaz de usuario de Web  
Últimamente es habitual al crear componentes de interfaz de usuario mediante HTML, por lo que puede usarse en Visual Studio Online y en Visual Studio. Interfaz de usuario que se escriben en formato HTML deberá seguir usando el servicio de VSColor cuando se ejecuta en el entorno de Visual Studio. Para obtener información acerca de Daytona y cómo utilizarlo, vea [Daytona y la interfaz de usuario web](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a>El servicio VSColor  
Visual Studio proporciona un servicio de color de entorno, también denominado el servicio VSColor o el servicio de color de shell. Este servicio le permite enlazar los valores de color de los elementos de interfaz de usuario para un conjunto que contiene colores para cada tema de colores de nombre y valor. El servicio VSColor debe usarse para todos los elementos de interfaz de usuario, por lo que colores automáticamente cambian para reflejar el tema seleccionado por el usuario actual y para que la interfaz de usuario enlazada al servicio de color de entorno integrarán con nuevos temas en futuras versiones de Visual Studio.  
  
### <a name="how-the-service-works"></a>Cómo funciona el servicio  
El servicio de color de entorno lee que vscolors definido en el .pkgdef para el componente de interfaz de usuario. Estos VSColors, a continuación, se hace referencia en el marcado XAML o en código y se cargan a través del `IVsUIShell5.GetThemedColor` o un `DynamicResource` asignación.  
  
![Arquitectura de servicio de color de entorno](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Arquitectura de servicio de color del entorno
  
### <a name="accessing-the-service"></a>Obtener acceso al servicio
Hay varias formas de acceso que se está usando el servicio VSColor, dependiendo de qué tipo de color de símbolos (token) y qué tipo de código tiene.  

#### <a name="predefined-environment-colors"></a>Colores del entorno predefinidos  
  
##### <a name="from-native-code"></a>Desde el código nativo  
El shell proporciona un servicio que proporciona acceso a la `COLORREF` de los colores. Es la interfaz de servicio:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
En el archivo VSShell80.idl, la enumeración `__VSSYSCOLOREX` tiene constantes de color de shell. Para usarla, pasa como el valor de índice cualquiera de los valores de la `enum __VSSYSCOLOREX` documentadas en MSDN o un índice normal que el número del sistema de Windows API, `GetSysColor`, acepta. Esto vuelve el valor RGB del color que se debe usar en el segundo parámetro.  
  
Si almacena un lápiz o un pincel con un color nuevo, debe `AdviseBroadcastMessages` (en el shell de Visual Studio) y escuchar `WM_SYSCOLORCHANGE` y `WM_THEMECHANGED` mensajes.  
  
  
Para tener acceso al servicio de color en código nativo, realizará una llamada similar a esto: 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **Nota:** el `COLORREF` valores devueltos por `GetVSSysColorEx()` contienen solo R, G, B componentes de color del tema. Si una entrada de tema usa transparencias, se descarta el valor de máscara de canal alfa antes de devolver. Por lo tanto, si el color de entorno de interés debe usarse en un lugar donde es importante la transparencia del canal, debe usar `IVsUIShell5.GetThemedColor` en lugar de `IVsUIShell2::GetVSSysColorEx`, como se describe más adelante en este tema.  
  
##### <a name="from-managed-code"></a>Desde el código administrado  
Obtener acceso al servicio de VSColor a través de código nativo es bastante sencilla. Si trabaja a través de código administrado, sin embargo, la determinación de cómo utilizar el servicio puede ser complicada. Con esto en mente, aquí es un fragmento de código de C# que muestra este proceso:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
Si está trabajando en Visual Basic, use:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>Desde la interfaz de usuario de WPF  
Puede enlazar a los colores de Visual Studio a través de los valores que se exportan a la aplicación `ResourceDictionary`. A continuación se muestra un ejemplo de uso de recursos de la tabla de colores, así como enlazar a los datos de fuente del entorno en XAML.  
  
```  
<Style TargetType="{x:Type Button}">  
    <Setter Property="TextBlock.FontFamily"  
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
    <Setter Property="TextBlock.FontSize"  
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
    <Setter Property="Background"  
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />  
</Style>  
```  
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>Clases auxiliares y métodos para código administrado  
Para código administrado, la biblioteca de Managed Package Framework del shell (`Microsoft.VisualStudio.Shell.12.0.dll`) contiene un par de clases auxiliares que facilita el uso de colores con temas.  
  
Los métodos auxiliares en el `Microsoft.VisualStudio.Shell.VsColors` clase MPF incluyen `GetThemedGDIColor()` y `GetThemedWPFColor()`. Los métodos auxiliares devuelve el valor de color de una entrada de tema como `System.Drawing.Color` o `System.Windows.Media.Color`, que se usará en formularios Windows Forms o WPF UI.  
  
```  
IVsUIShell5 shell5;  
Button button = new Button();  
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);  
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);  
  
/// <summary>  
/// Gets a System.Drawing.Color value from the current theme for the given color key.  
/// </summary>  
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>  
/// <param name="themeResourceKey">The key to find the color for.</param>  
/// <returns>The current theme's value of the named color.</returns>  
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);  
  
   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR  
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}  
  
private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Guid category = themeResourceKey.Category;  
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground  
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)  
   {  
      colorType = __THEMEDCOLORTYPE.TCT_Background;  
   }  
  
   // This call will throw an exception if the color is not found  
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);  
   return BitConverter.GetBytes(rgbaColor);  
}  
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);  
  
    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}    
```  
  
La clase también puede usarse para obtener los identificadores VSCOLOR para una clave de recurso de color WPF determinada, o viceversa.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
Los métodos de `VsColors` clase consultar al servicio VSColor para devolver el valor de color cada vez que se invoquen. Para obtener un valor de color como `System.Drawing.Color`, una alternativa con un mejor rendimiento es en su lugar, use los métodos de la `Microsoft.VisualStudio.PlatformUI.VSThemeColor` (clase), que almacena en memoria caché los valores de color obtenidos en el servicio VSColor. La clase se suscribe internamente a eventos de mensajes de difusión de shell y descarta el valor almacenado en caché cuando se produce un evento de cambio de tema. Además, la clase proporciona un. NET compatible con el evento que se va a suscribir a los cambios de tema. Utilice la `ThemeChanged` eventos para agregar un nuevo controlador y usar el `GetThemedColor()` método para obtener el color de los valores para el `ThemeResourceKeys` de interés. Código de ejemplo podría ser similar al siguiente:  
  
```  
public MyWindowPanel()  
{  
    InitializeComponent();  
  
    // Subscribe to theme changes events so we can refresh the colors  
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;  
  
    RefreshColors();  
}  
  
private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)  
{  
    RefreshColors();  
  
    // Also post a message to all the children so they can apply the current theme appropriately  
    foreach (System.Windows.Forms.Control child in this.Controls)  
    {  
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);  
    }  
}  
  
private void RefreshColors()  
{  
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);  
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);  
}  
  
protected override void Dispose(bool disposing)  
{  
    if (disposing)  
    {  
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;  
        base.Dispose(disposing);}  
}  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>Elegir los colores de contraste alto  
  
### <a name="overview"></a>Información general  
Windows usa diversos temas de nivel de sistema de contraste alto que aumentan el contraste de color de texto, fondos e imágenes, parezca que los elementos más distintos en la pantalla. Por motivos de accesibilidad, es importante que elementos de la interfaz de Visual Studio responden correctamente cuando los usuarios cambiar a un tema de contraste alto.  
  
Solo un conjunto de colores del sistema puede usarse para los temas de contraste alto. Al elegir el sistema de nombres de colores, recuerde las siguientes sugerencias:  
  
1.  **Elija los colores del sistema que tienen el mismo significado semántico** como el elemento que se color. Por ejemplo, si elige un color de alto contraste para el texto dentro de una ventana, utilice WindowText y no ControlText.  
  
2.  **Elija pares de primer plano y fondo** juntos o no podrá estar seguro de que la selección de color funcione en todos los temas de contraste alto.  
  
3.  **Determinar qué partes de la interfaz de usuario son los más importantes y asegúrese de que se resaltan las áreas de contenido.** Perderá una gran cantidad de detalle que normalmente se distinguen sutiles diferencias en el matiz del color, por lo que es común para definir las áreas de contenido, el uso de colores de borde seguro porque no hay ningún variantes de color para varias áreas de contenido.  
  
### <a name="system-color-set"></a>Conjunto de colores del sistema  
La tabla en [Blog del equipo de WPF: referencia SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indica el conjunto completo de nombres de colores del sistema y los matices correspondientes que se muestran en cada tema.  
  
Cuando se aplica esto limita el conjunto de colores para la interfaz de usuario, *se espera que perderá detalles sutiles que estaban presentes en los temas "normales"*. Este es un ejemplo de interfaz de usuario con sutiles color gris que sirven para distinguir las distintas áreas de una ventana de herramientas. Cuando se emparejan con la misma ventana que se muestra en el modo de contraste alto, puede ver que todos los fondos son el mismo matiz y los bordes de esas áreas se indican mediante borde independiente:  
  
![Ejemplo de los detalles de cómo sutiles se pierden en contraste alto](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Ejemplo de los detalles de cómo sutiles se pierden en contraste alto
  
#### <a name="choosing-text-colors-in-an-editor"></a>Elegir los colores de texto en un editor  
Los de texto se utiliza en un editor o en una superficie de diseño para indicar el significado, como permitir para facilitar la identificación de los grupos de elementos similares. Sin embargo, en un tema de contraste alto, no tiene la capacidad de diferenciar entre más de tres colores de texto. WindowText, GrayText y HotTrackText son los colores solo disponibles en superficies WindowBackground. Ya que no puede utilizar más de tres colores, elegir cuidadosamente las diferencias más importantes que desea mostrar en el modo de contraste alto.  
  
Matices para cada uno de los nombres de token que se permiten en una superficie del editor, tal y como aparecen en cada tema de contraste alto:  
  
![Comparación de editor de contraste alto](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparación de editor de contraste alto
  
Ejemplos de la superficie del editor en el tema azul:  
  
![Editor en el tema azul](~/extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor en el tema azul
  
![Editor en el tema de alto contraste nº 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor en el tema de alto contraste nº 1
  
### <a name="usage-patterns"></a>Patrones de uso
Muchos elementos de interfaz de usuario común ya ha definido de colores de contraste alto. Estos patrones de uso puede hacer referencia al elegir su propio sistema de nombres de colores, para que sus elementos de interfaz de usuario son coherentes con componentes similares.  
  
| Color del sistema | Uso |
| --- | --- |
| ActiveCaption | -Active IDE y ventana rafted botón glifos en al mantener el mouse y presione<br />-Fondo de la barra de título IDE y windows rafted<br />-Fondo predeterminado de la barra de estado |
| ActiveCaptionText | -Active IDE y las ventanas rafted de primer plano de barra de título (texto y glifos)<br />-En segundo plano y de borde de los botones de la ventana activa al mantener el mouse y presione |
| Control | -Cuadro combinado, lista desplegable y busque controlan de forma predeterminada y deshabilitada fondo, incluidos el botón de lista desplegable<br />-Acoplar el fondo del botón de destino<br />: Fondo de la barra de comandos<br />: Fondo de la ventana de herramienta |
| ControlDark | -Fondo IDE<br />-Menú y comando separadores con barra<br />: Borde de la barra de comandos<br />-Las sombras menú<br />-Herramienta de borde de predeterminado y al mantener el mouse de la pestaña de ventana y el separador<br />-Bien documentar el fondo del botón de desbordamiento<br />-Borde de glifo de destino acoplar |
| ControlDarkDark |: Ventana de la ficha de documento seleccionada sin foco |
| ControlLight |-Borde de pestaña ocultación automática<br />-Borde de combinado desplegable y de cuadro de lista<br />-Acoplar borde y fondo de destino |
| ControlLightLight | -Borde provisional seleccionada, con foco |
| ControlText | -Glifo de combinado desplegable y de cuadro de lista<br />-Anular la selección de pestaña texto de la ventana |
| GrayText |-Cuadro combinado y lista desplegable deshabilitan borde, el glifo de la lista desplegable, el texto y el texto del elemento de menú<br />-Texto de menú deshabilitado<br />-Texto de encabezado de búsqueda control "opciones de búsqueda"<br />: Separador de secciones de control de búsqueda |
| Resaltar | -Todos los al mantener el mouse y fondos presionados y bordes, excepto combinado cuadro botón desplegable fondo y documento desbordamiento bien borde de botón<br />-Fondos de elemento seleccionado |
| HighlightText | -Todos los al mantener el mouse y primeros planos presionados (texto y glifos)<br />-Tiene el foco herramienta documentos y ventanas ficha ventana control primer plano<br />-Borde de barra de título de ventana de herramienta tiene el foco<br />-Primer plano de la pestaña provisional tiene el foco, seleccionada<br />-Borde de botón de desbordamiento well documento al mantener el mouse y presione<br />-Borde de icono seleccionado|
| HotTrack | -Barra de desplazamiento thumb fondo y borde en presione<br />-La barra de desplazamiento en presione glifo de flecha |
| InactiveCaption | -Inactiva IDE y ventana rafted glifos de botón al mantener el mouse<br />-Fondo de la barra de título IDE y windows rafted<br />-Fondo del control de búsqueda deshabilitado |
| InactiveCaptionText | -Inactiva IDE y frontal de barra de título de windows rafted (texto y glifos)<br />-Fondo de botones de ventana inactiva y un borde al mantener el mouse<br />-Borde y fondo del botón de ventana de herramienta sin foco<br />-Primer plano del control de búsqueda deshabilitado |
| Menú | -Fondo del menú lista desplegable<br />-Comprueba y fondo de marca de verificación deshabilitada |
| MenuText | -Borde del menú lista desplegable<br />: Marcas de verificación<br />-Glifos menú<br />-Texto del menú lista desplegable<br />-Borde de icono seleccionado |  
| Barra de desplazamiento | -Desplácese barra y barra fondo de flecha, todos los Estados de desplazamiento |
| Ventana | -Fondo de ficha ocultación automática<br />-Menú de barras y fondo del área de comandos<br />: Fondo de pestaña de ventana de documento sin foco o no seleccionados y el borde de documento, para las pestañas abiertas y provisionales<br />-Fondo de barra de título de ventana de herramienta sin foco<br />-Fondo de la pestaña de ventana de herramienta, ambos seleccionada y anular la selección |
| Marco de ventana | : Borde IDE |
| WindowText | -Primer plano de pestaña ocultación automática<br />-Primer plano de pestaña de ventana de herramienta seleccionada<br />: Pestaña de ventana de documento no enfocado y de primer plano de la pestaña provisional seleccionado o sin foco<br />-Árbol predeterminado de primer plano de vista y al mantener el mouse sobre un glifo no seleccionado<br />: Borde de subpestaña seleccionado de la ventana<br />-La barra de desplazamiento thumb fondo, borde y glifo |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>Exposición de colores para los usuarios finales  
  
### <a name="overview"></a>Información general  
En ocasiones, deseará permiten al usuario final personalizar la interfaz de usuario, al igual que al crear un editor de código o la superficie de diseño. La manera más común de hacerlo es mediante la **herramientas &gt; opciones** cuadro de diálogo. A menos que se dispone de muy especializado interfaz de usuario que requiere controles especiales, la manera más fácil para presentar la personalización es a través de la **fuentes y colores** página dentro de la **entorno** sección del cuadro de diálogo. Para cada elemento que expone para la personalización, el usuario puede cambiar el color de primer plano, el color de fondo o ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creación de un paquete VSPackage para sus colores personalizables  
Un VSPackage puede controlar las fuentes y colores a través de categorías personalizadas y mostrar los elementos en la página de propiedades de fuentes y colores. Cuando se utiliza este mecanismo, paquetes VSPackage deben implementar la [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interfaz y sus interfaces asociadas.  
  
En principio, este mecanismo puede utilizarse para modificar todos los elementos de presentación existente y las categorías que los contienen. Sin embargo, no debe utilizarse para modificar la categoría del Editor de texto o sus elementos de visualización. Para obtener más información sobre la categoría del Editor de texto, consulte [información general de Color y fuente](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
Para implementar categorías personalizadas o mostrar los elementos, un VSPackage debe:  
  
-   **Cree o identifique categorías en el registro.** Implementación del IDE de la **fuentes y colores** página de propiedades usa esta información para consultar correctamente para el servicio que admite una determinada categoría.  
  
-   **Cree o identifique los grupos en el registro (opcional).** Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE combina subcategorías automáticamente y distribuye elementos para mostrar dentro del grupo.  
  
-   **Implementar la compatibilidad con IDE.**  
  
-   **Controlar los cambios de fuente y color.**  
  
#### <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías  
Construir un tipo especial de entrada de registro de la categoría en `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` donde `<Category>` es el nombre no traducido de la categoría.
  
Rellenar el registro con dos valores:  

| Name | Tipo | Datos | Descripción |
| --- | --- | --- | --- |
| Categoría | REG_SZ | GUID | Crea un GUID para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio de VSPackage que admite la categoría |
  
 El servicio especificado en el registro debe proporcionar una implementación de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) para la categoría correspondiente.  
  
#### <a name="to-create-or-identify-groups"></a>Para crear o identificar los grupos  
Construir un tipo especial de entrada de registro de la categoría en `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` donde `<group>` es el nombre no traducido del grupo.  
  
Rellenar el registro con dos valores:

| Name | Tipo | Datos | Descripción |
|--- | --- | --- | --- |
| Categoría | REG_SZ | GUID | Crea un GUID para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio de VSPackage que admite la categoría |
  
El servicio especificado en el registro debe proporcionar una implementación de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` para el grupo correspondiente.

![Implementación de encontrar](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementación de`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>Para implementar la compatibilidad IDE  
Implemente [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), que devuelve un [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaz o un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` de la interfaz en el IDE para cada categoría o grupo GUID proporcionado.  
  
Para cada categoría admite, un VSPackage implementa una instancia independiente de la [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaz.  
  
Los métodos que se implementan a través de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) debe proporcionar el IDE con:  
  
-   Listas de elementos para mostrar en la categoría  
  
-   Localizables nombres para mostrar los elementos  
  
-   Mostrar la información de cada miembro de la categoría  
  
 > **Nota:** todas las categorías deben contener al menos un elemento para mostrar.
  
El IDE usa la `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaz para definir una unión de varias categorías.

Su implementación proporciona el IDE con:

-   Una lista de las categorías que componen un grupo determinado  
  
-   Acceso a las instancias de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) admitir cada categoría dentro del grupo  
  
-   Nombres de grupos localizable  
  
#### <a name="updating-the-ide"></a>Actualizando el IDE  
El IDE se almacena en caché información acerca de la configuración de fuente y Color. Por lo tanto, después de cualquier modificación de la configuración de Color y fuente de IDE, asegurándose de que la memoria caché está actualizada es una práctica recomendada.  
  
Actualización de la memoria caché se efectúa a través de la [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) de interfaz y puede estar compuesta por elementos seleccionado globalmente o simplemente en realizada.  
  
### <a name="handling-font-and-color-changes"></a>Gestionar los cambios de fuente y color  
Para ser compatibles con el color del texto que muestra un paquete VSPackage, el servicio de colores que admite el VSPackage debe responder a los cambios iniciada por el usuario que se realizan a través de la página de propiedades de fuentes y colores.  
  
Para ello, un VSPackage debe:  
  
-   **controlar los eventos generados por el IDE** implementando la [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interfaz. El IDE llama al método adecuado después de las modificaciones de usuario de la página fuentes y colores. Por ejemplo, llama a la [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) método si se selecciona una fuente nueva.  
  
 **OR**  
  
-   **sondear el IDE para cambios**. Esto puede hacerse mediante el implementado por el sistema [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaz. Aunque principalmente para la compatibilidad de persistencia, el [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) método puede obtener información de fuente y color para mostrar los elementos. Para obtener más información sobre la configuración de fuente y color, vea el artículo MSDN [acceso a fuentes almacenados y la configuración de Color](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
> **Nota:** para asegurarse de que los resultados de sondeo son correctos, use la [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interfaz para determinar si se necesitan un vaciado de la caché y la actualización antes de llamar a los métodos de recuperación de la [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaz.
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrar la fuente personalizada y categoría de color sin necesidad de implementar interfaces  
En el ejemplo de código siguiente se muestra cómo registrar la fuente personalizada y categoría de color sin necesidad de implementar interfaces:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

En este ejemplo de código:   
-   `"NameID"` = el identificador de recurso del nombre de categoría adaptada en el paquete
-   `"ToolWindowPackage"` = GUID del paquete
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`es solo un ejemplo y el valor real puede ser un nuevo GUID proporcionado por el implementador.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Establecer la fuente y Color propiedad GUID de categoría  
El ejemplo de código siguiente muestra cómo establecer el valor de GUID de categoría.  
  
```  
// m_pView is your IVsTextView  
IVsTextEditorPropertyCategoryContainer spPropCatContainer =  
(IVsTextEditorPropertyCategoryContainer)m_pView;  
if (spPropCatContainer != null)  
{  
IVsTextEditorPropertyContainer spPropContainer;  
Guid GUID_EditPropCategory_View_MasterSettings =  
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");  
hr = spPropCatContainer.GetPropertyCategory(  
ref GUID_EditPropCategory_View_MasterSettings,  
out spPropContainer);  
if(hr == 0)  
{  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,  
catGUID);  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,  
catGUID);  
}  
}  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a>Daytona y la interfaz de usuario web  
  
### <a name="overview"></a>Información general  
"Daytona" es un conjunto de API, herramientas y servicios que permiten a un usuario crear complementos con HTML, CSS y JavaScript que puede utilizarse en una gran variedad de hosts, como Visual Studio o F12. Complementos se componen de un componente portátil, que se escribe en HTML, CSS y JavaScript, y los componentes opcionales de específico del host. Cada host Daytona puede tener su propio conjunto de convenciones de la interfaz de usuario, implícitas o explícitas, que un complemento debe cumplir para que aparezca nativo para su entorno. Algunos de los hosts, como Visual Studio, permitir que los usuarios finales realizar cambios en el tema"predeterminado" para que los aspectos visuales del host no se puede destinar estáticamente al crear una hoja de estilos. Esto supone un desafío para los desarrolladores que crean complementos portátil. Este tema explica cómo crear la interfaz de usuario en Visual Studio usando el host Daytona de forma que sea completamente compatible con temas y contraste alto web.  
  
### <a name="daytona-theming-mechanism"></a>Mecanismo de temas Daytona  
El runtime Daytona proporciona un conjunto de servicios que abstrae las convenciones de la interfaz de usuario y las capacidades de creación de temas del host. Estos servicios aseguran de que los complementos automáticamente se ajustan a las expectativas del usuario según el entorno que se hospedan en visual. Este comportamiento proporciona tres características principales:  
  
1.  Una hoja de estilos insertado en tiempo de ejecución (plugin.css) que se aplica un conjunto de reglas CSS a la interfaz de usuario del complemento de forma transparente y estilos el conjunto predeterminado de los controles HTML (por ejemplo, HTMLInputElement y HTMLButtonElement  
  
2.  Un conjunto de tokens proporcionada por el host que puede utilizarse para elementos de interfaz de usuario de estilo con los valores que se basan en el tema en lugar de codificado de forma rígida  
  
    -  sintaxis declarativa para tener acceso a estos tokens con CSS  
  
    -  una API para el acceso mediante programación a los tokens de tema desde JavaScript  
  
3.  Notificación de cambios de tema  
  
#### <a name="runtime-injected-style-sheet"></a>Hoja de estilos insertado en tiempo de ejecución  
Las coordenadas de Daytona en tiempo de ejecución con el host para insertar un estilo de hojas es automáticamente temas de los elementos de interfaz de usuario estándares de un complemento. Esto incluye estilos para los siguientes conceptos:  
  
-   Fuente del entorno  
  
-   Colores de fondo  
  
-   Hipervínculos  
  
-   Controles de formulario (por ejemplo: `<select>`, `<input>`,`<button>`  
  
-   Tablas  
  
-   Encabezados  
  
-   Barras de desplazamiento  
  
Esto significa que si la interfaz de usuario se compone únicamente de los controles de IU de HTML estándar, a continuación, realizar ningún trabajo adicional debería ser necesario para responder correctamente a los cambios de tema y admitir contraste alto.  
  
#### <a name="custom-ui"></a>Interfaces de usuario personalizadas  
En casi todos los casos no triviales, será suficiente para proporcionar una experiencia completa para un complemento en el estándar de controles de IU de HTML y se debe introducir la interfaz de usuario personalizada. Para admitir el uso de elección y el color de fuente adecuada, **tokens de tema** debe utilizarse mediante declaración en CSS o de forma imperativa a través de la API de JavaScript se describe a continuación. El tiempo de ejecución Daytona se encargará de actualización de las hojas de estilos que usan estos tokens en la carga del complemento y en los cambios de tema.  
  
##### <a name="theme-tokens"></a>Tokens de tema  
Ambos tokens tema estándar y específicas del host están disponibles. Los tokens estándares son insertado por el host y siempre está disponible. Es preferible utilizar los tokens estándares siempre que sea posible. Tokens estándares se garantiza que sea a probado por todos los hosts de Daytona y su uso hace que el complemento sea inherentemente más portátil. El conjunto de tokens estándares está sujeta a cambios, aunque se deben agregar sólo nuevos tokens y ninguno debe quitarse. La versión de Visual Studio 2013 se documenta a continuación:  
  
| Nombre del token | Descripción |
| --- | --- |
| `plugin-background-color` | El color de fondo predeterminado para el complemento |
| `plugin-color` | El color de primer plano predeterminado para el complemento |
| `plugin-contextmenu-active-color` | El color de selección de primer plano predeterminado para los menús contextuales cuando están activas (tiene el foco) |
| `plugin-contextmenu-background-color` | El color de fondo predeterminado para los menús contextuales |
| `plugin-contextmenu-border-color` | El color del borde predeterminado para los menús contextuales |
| `plugin-contextmenu-color` | El color de primer plano predeterminado para los menús contextuales |
| `plugin-contextmenu-hover-color` | El color de fondo predeterminado al mantener el mouse para los menús contextuales |
| `plugin-contextmenu-hover-text-color` | El color de primer plano al mantener el mouse predeterminado para los menús contextuales |
| `plugin-contextmenu-icon-checkbox` | El color del icono de casilla de verificación predeterminado para los menús contextuales |
| `plugin-contextmenu-inactive-text-color` | El color de selección de primer plano predeterminado para los menús contextuales cuando están inactivos |
| `plugin-contextmenu-separator-color` | El color del separador predeterminado para los menús contextuales |
| `plugin-font-family` | La familia de fuentes predeterminada que se usará para el complemento |
  
En Visual Studio, el siguiente `plugin-font` tokens se basan en la configuración de fuente del entorno:  
  
-   `plugin-font-size`  
  
-   `plugin-font-weight`  
  
-   `plugin-highlight-background-color`  
  
-   `plugin-highlight-color`  
  
-   `plugin-inactive-color` 
  
El siguiente `plugin-link` símbolos (tokens) se utiliza para estilo `HTMLElements` (hipervínculos):
  
-   `plugin-link-color`  
  
-   `plugin-link-active-color`  
  
-   `plugin-link-hover-color`  
  
Plugin.CSS estilos barras de desplazamiento de forma predeterminada con los tokens siguientes para admitir mejor los temas en los distintos hosts (en particular, Visual Studio):
  
-   `plugin-scrollbar-arrow-color`  
  
-   `plugin-scrollbar-background-color`  
  
-   `plugin-scrollbar-face-color`  
  
El siguiente `plugin-select` símbolos (tokens) se utiliza para el estilo de la `HTMLSelectElement` (combinado cuadro desplegable):  
  
-   `plugin-select-option-background-color` 
  
-   `plugin-select-option-color`  
  
-   `plugin-select-option-checked-background-color`  
  
-   `plugin-select-option-checked-border-color`  
  
-   `plugin-select-option-checked-foreground-color`  
  
-   `plugin-select-option-hover-background-color`  
  
-   `plugin-select-option-hover-border-color`  
  
-   `plugin-select-option-hover-foreground-color`  
  
-   `plugin-select-border-color`  
  
-   `plugin-select-background-color`  
  
-   `plugin-select-foreground-color`  
  
-   `plugin-select-hover-background-color`  
  
-   `plugin-select-hover-border-color`  
  
-   `plugin-select-hover-foreground-color`  
  
-   `plugin-table-border-color`  
  
-   `plugin-table-header-background-color`  
  
-   `plugin-table-header-color`  
  
-   `plugin-textbox-border-color`  
  
-   `plugin-textbox-background-color`  
  
-   `plugin-textbox-color`  
  
-   `plugin-textbox-disabled-background-color`  
  
-   `plugin-textbox-disabled-border-color`  
  
-   `plugin-textbox-disabled-color`  
  
Estos tokens se deben usar para *todos los* árbol vistas y tablas, ya que tienen los valores predeterminados correctos configurar en los distintos hosts para que admita temas y contraste alto:  
  
-   `plugin-treeview-content-background-color`  
  
-   `plugin-treeview-content-color` 
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-mouseover-background-color`  
  
-   `plugin-treeview-content-mouseover-color`  
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-selected-background-color`  
  
-   `plugin-treeview-content-selected-border-color`  
  
-   `plugin-treeview-content-selected-color`  
  
##### <a name="host-specific-tokens"></a>Tokens específico del host  
Además de admitir el conjunto estándar de tokens, hosts también pueden proporcionar tokens no estándar. Para ello, el host de Visual Studio que permite el complemento especificar alias de token de tema en una sección de específicos de Visual Studio del manifiesto. Por ejemplo:
  
```  
"vs": {  
    "theme_token_aliases": {   
        "diagnostics-host-border": {   
            "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22",   
            "key_type": "BackgroundColor",   
            "name": "Border"   
        },   
        ...   
    }   
}    
```  
  
 Este ejemplo presenta un token de tema, denominado `diagnostics-host-border`, que puede hacer referencia exactamente igual a los tokens estándares mencionados anteriormente. El `category`, `key_type`, y `name` se utilizan para resolver el color de la `IVsFontAndColorStorage` interfaz. En muchos casos, es posible buscar colores adecuados (junto con la `category`, `key_type`, y `name` información) en los archivos XML ubicados en `VSCommonContent\themes`. Este mismo mecanismo se utiliza si el paquete presenta nuevos colores configurables: coincide con el `category`, `key_type`, y `name` en el color que desea usar. Los autores del complemento deben intentan usar tokens estándar siempre que sea posible y solo utilizan tokens de específico del host cuando sea absolutamente necesario.  
  
##### <a name="using-theme-tokens-in-css"></a>Uso de tokens de tema en CSS  
 Tokens de tema se conocen a través de una sintaxis de comentario con formato especial. Las reglas para el análisis de símbolo (token):  
  
1.  La expresión de comentario se debe incluir entre corchetes (`[ ]`).  
  
2.  Todos los espacios en blanco en los comentarios, pero fuera de la expresión, se omite.  
  
3.  La expresión de comentario debe siguen directamente a la propiedad que reemplaza.  
  
4.  Se eliminarán los espacios en blanco iniciales ni finales dentro de la expresión.  
  
5.  Cada nombre de símbolo (token) dentro de la expresión debe incluirse entre llaves (por ejemplo, `{font-family}` y `{button-hover-color}`). En caso contrario, se tratará como un valor literal.  
  
 Los siguientes son ejemplos de cómo el analizador token reemplazará los valores CSS, suponiendo que el `plugin-background-color` símbolo (token) tiene el valor de `#000` y `plugin-font-family` símbolo (token) tiene el valor de `Verdana`.
  
| CSS creados | CSS analizada | Notas |  
| --- | --- | --- |
| `background-color: #fff; /*[{plugin-background-color}]*/` | `background-color: #000;` | El valor predeterminado se reemplaza con el valor específico del host dinámico. |  
| `background-color: #fff; /*   [{plugin-background-color}]   */` | `background-color: #000;` | Se omite el espacio en blanco fuera de la expresión. |  
| `background-color: #fff; /*[   {plugin-background-color}   ]*/` | `background-color: #000;` | Se recorta el espacio en blanco inicial y final dentro de la expresión. |
| `background-color: #fff; /*{plugin-background-color}*/` | `background-color: #fff;` | La expresión no está entre corchetes y, por lo tanto, se omitirá el comentario. |
| `background-color: #fff; /*[plugin-background-color]*/` | `background-color: plugin-background-color;` | El token no está entre llaves y, por tanto, se trata como un valor literal. |
| `/*[{plugin-background-color}]*/ background-color: #fff;` | `background-color: #fff;` | Los comentarios no cumple el valor de propiedad y, por tanto, se omiten. |
| `background-color: #fff;  /*[{plugin-background-color}]*/` | `background-color: #fff;`| *Igual que arriba* |
| `/*[{plugin-background-color}]*/  background-color: #fff;` | `background-color: #fff;` | *Igual que arriba* |
| `font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/` | `font-family: Verdana, sans-serif;` | Se reemplaza el símbolo (token) y se mantiene el contenido literal. |
| `background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/` | `background-image: linear-gradient(0% #000, 100% #000);` | *Igual que arriba* |
  
Si un archivo CSS incluye tokens de tema debe estar marcado por el `data-plugin-theme` del atributo en el `link` elemento en el archivo HTML. Por ejemplo:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```

##### <a name="using-theme-tokens-from-javascript"></a>Uso de tokens de tema desde JavaScript  
Mientras la interfaz de usuario personalizada debe estar con temas por CSS siempre que sea posible, hay escenarios cuando el valor de un tema de símbolo (token) debe tener acceso mediante programación. Por ejemplo, si la interfaz de usuario personalizada que se va a dibujar en un `CanvasElement` que no hereda los estilos de CSS, o si un elemento de interfaz de usuario que se crean dinámicamente como se opone a que se hace referencia a hojas de estilos. Los escenarios se habilitan mediante la API de Daytona `Plugin.Theme.getValue`. Esta función devuelve un valor de tema proporcionada por el host cuando se especifica un nombre de símbolo (token).  
  
| No con temas | Con temas |
| --- | --- |
| `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = "#ccc";  surface.fillRect(0, 0, 200, 200);` | `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = ("plugin-background-color");  surface.fillRect(0, 0, 200, 200);` |
| `var el = document.createElement("div");  el.style.backgroundColor = "#ccc";` | `var el = document.createElement("div");  el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");` |  
  
Si se usa símbolos (tokens) de JavaScript, **debe usarse con el evento de cambio de tema para responder a las actualizaciones**. Esto no es necesario para los tokens de tema utilizados de forma declarativa en CSS, como el tiempo de ejecución Daytona se encarga de ello para el complemento. Se puede controlar el evento de tema de la manera siguiente:

**Miembro (controlador único)**
```
Plugin.Theme.onchange = function () 
{
    // re-draw dynamic UI here
}
```

**Evento de DOM (varios controladores)**
```
Plugin.Theme.addEventListener("change", function () 
{
    // re-draw dynamic UI here
});
```
  
En este caso, sería muy común para volver a llamar a `Plugin.Theme.getValue` en estos controladores, como el valor de los tokens de tema es probable que cambia cuando cambia el tema.  
  
##### <a name="standard-token-mapping"></a>Asignación de símbolo (token) estándar  
Los tokens estándares se asignan a los colores de entorno y el Shell. La lista siguiente proporciona un tipo de cuáles son esas asignaciones.  
  
| Nombre del token | FRENTE a asignación (`EnvironmentColors`) |  
| --- | --- |  
| `plugin-color` | `ToolWindowTextColorKey` |
| `plugin-background-color` | `ToolWindowBackgroundColorKey` |
| `plugin-link-color` | `ControlLinkTextColorKey` |
| `plugin-link-hover-color` | `ControlLinkTextHoverColorKey` |
| `plugin-link-active-color` | `ControlLinkTextPressedColorKey` |
| `plugin-highlight-color` | `HighlightTextColorKey` |
| `plugin-highlight-background-color` | `HighlightColorKey` |
| `plugin-table-header-background-color` | `GridHeadingBackgroundColorKey` |
| `plugin-table-header-color` | `GridHeadingTextColorKey` |
| `plugin-table-border-color` | `GridLineColorKey` |
| `plugin-button-background-color` | `ButtonFaceColorKey` |
| `plugin-button-hover-background-color` | `ButtonHighlightColorKey` | 
| `plugin-button-color` | `ButtonTextColorKey` |
| `plugin-button-border-color` | `ButtonBorderColorKey` |
  
##### <a name="theme-changes"></a>Cambios de tema  
Los desencadenadores de host de Visual Studio complemento el tema de cambios cuando un usuario final se realiza cambios en las siguientes opciones:  
  
**Tema de color:**  
  
![Cambios de tema de color](~/extensibility/ux-guidelines/media/0305-a_colortheme.png "0305-a_ColorTheme")<br />Cambios de tema de color  
  
**Tema del entorno:**  
  
![Cambios de tema del entorno](~/extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305-b_EnvironmentTheme")<br />Cambios de tema del entorno  
  
**Tema del sistema operativo** (sólo al cambiar a y desde el contraste alto):  
  
![Cambios de tema del sistema operativo](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305-c_OSTheme")<br />Cambios de tema del sistema operativo
