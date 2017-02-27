---
title: "Colores y estilos para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Colores y estilos para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Usar color en Visual Studio  
 En Visual Studio, color se utiliza principalmente como una herramienta de comunicación, no sólo como decoración. Usar color como mínimo y reservar para las situaciones donde desea:  
  
-   Comunicar el significado o la afiliación \(por ejemplo, los modificadores de plataforma o lenguaje\)  
  
-   Atraer la atención sobre \(por ejemplo, que indica un cambio de estado\)  
  
-   Mejorar la legibilidad y proporcionar puntos de referencia para navegar por la interfaz de usuario  
  
-   Aumentar la conveniencia  
  
 Existen varias opciones para asignar colores a elementos de interfaz de usuario en Visual Studio. A veces puede ser difícil de figura qué opción debe para utilizar o cómo usarla correctamente. Este tema le ayudará a:  
  
1.  Comprender los diferentes servicios y sistemas que se usan para definir colores en Visual Studio.  
  
2.  Seleccione la opción correcta para un elemento determinado.  
  
3.  Utilizar correctamente la opción seleccionada.  
  
 **Importante:** nunca codificar hexadecimal, RGB o colores del sistema para los elementos de interfaz de usuario. Uso de los servicios permite una flexibilidad del ajuste de tono. Además, sin que el servicio, no podrá aprovechar las capacidades de cambio de tema de la [El servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
### Métodos para asignar colores a elementos de la interfaz de Visual Studio  
 Elija el método que mejor se adapte a sus elementos de interfaz de usuario.  
  
|La interfaz de usuario|Método|¿Qué son?|  
|----------------------------|------------|---------------|  
|Se han incrustado o cuadros de diálogo independiente.|**Colores del sistema**|Nombres de sistema que permiten que el sistema operativo definir el color y la apariencia de los elementos de la interfaz de usuario, como para los controles de cuadro de diálogo común.|  
|Tiene una interfaz de usuario personalizada que desea que sea coherente con el entorno de VS general y tiene elementos de interfaz de usuario que coinciden con la categoría y el significado semántico de los tokens compartidos.|**Colores comunes compartidos**|Los nombres de símbolo \(token\) de colores predefinidos para elementos de interfaz de usuario específicos existentes|  
|Tiene una característica individual o un grupo de características y no hay ningún color compartida para elementos similares.|**Colores personalizados**|Nombres de símbolo \(token\) de colores que son específicos de un área y no compartirse con otras interfaces de usuario|  
|Desea permitir al usuario final personalizar la interfaz de usuario o el contenido \(por ejemplo, para los editores de texto o ventanas de diseñador especializadas\).|**Personalización del usuario final**<br /><br /> **\(Herramientas \> cuadro de diálogo Opciones\)**|Opciones de configuración definidas en la página "Fuentes y colores" de la **Herramientas \> opciones** cuadro de diálogo o una página especializada específica de una característica de interfaz de usuario.|  
|Tiene interfaz de usuario que se crearon en HTML.|**Daytona**|Permite la interfaz de usuario creado en HTML para tener acceso al servicio de color y fuente.|  
  
### Temas visuales Studio  
 Visual Studio incluye tres temas de color diferente: azul, oscuro y claro. También detecta el modo de contraste alto, que es un tema de color de todo el sistema diseñado para mejorar la accesibilidad.  
  
 Los usuarios le pedirá que seleccione un tema durante su primer uso de Visual Studio y pueden cambiar los temas más tarde, vaya a **Herramientas \> Opciones \> entorno \> General** y elegir un nuevo tema en el menú desplegable "tema de color".  
  
 Los usuarios también pueden utilizar el Panel de Control para cambiar sus sistemas todos en uno de los diversos temas de contraste alto. Si un usuario selecciona un tema de contraste alto, a continuación, el selector de tema de color de Visual Studio ya no afecta al color en Visual Studio, aunque se guardan los cambios de tema para cuando el usuario sale del modo de contraste alto. Para obtener más información acerca del modo de contraste alto, consulte [Selección de colores de contraste alto](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).  
  
### El servicio VSColor  
 Visual Studio proporciona un servicio de color del entorno, conocido como el servicio VSColor, que permite enlazar los valores de color de los elementos de interfaz de usuario a una entrada con nombre que contiene los valores de color para cada tema de Visual Studio. Esto garantiza que sus colores cambiará automáticamente para reflejar la actual seleccionado por el usuario el tema o el sistema de modo de contraste alto. Uso del servicio significa que la implementación de todos los cambios relacionados con el tema de color se controla en un lugar y, si usa los colores comunes compartidos desde el servicio, la interfaz de usuario refleja automáticamente los nuevos temas en versiones futuras de Visual Studio.  
  
### Implementación  
 El código fuente de Visual Studio incluye varios archivos de definición de paquete que contienen listas de nombres de los tokens y los valores de color correspondiente para cada tema. El servicio de color lee el VSColors definida en estos archivos de definición de paquete. Estos colores se hace referencia en el marcado XAML o en el código y, a continuación, se cargan a través del **IVsUIShell5.GetThemedColor** método o una asignación DynamicResource.  
  
### Colores del sistema  
 Controles comunes de hacer referencia a los colores del sistema de forma predeterminada. Si desea que la interfaz de usuario para usar colores del sistema, como cuando se crea un cuadro de diálogo incrustado o independiente, no es necesario hacer nada.  
  
### Colores comunes compartidos en el servicio de VSColor  
 Los elementos de la interfaz deben reflejar el entorno general de Visual Studio. Mediante la reutilización de los colores compartidos comunes que son adecuados para el componente de interfaz de usuario que va a diseñar, asegúrese de que la interfaz es coherente con otras interfaces de Visual Studio y que sus colores se actualizarán automáticamente cuando se agregan o actualizan los temas.  
  
 Antes de usar los colores comunes compartidos, asegúrese de que comprende cómo usarlas correctamente. Uso incorrecto de los colores comunes compartidos podría dar lugar a una experiencia incoherente, frustrante o confusa para los usuarios.  
  
### Colores personalizables por el usuario  
 Vea: [Exposición de colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 A veces, desea permitir al usuario final personalizar la interfaz de usuario, como cuando se crea un editor de código o la superficie de diseño. Componentes de interfaz de usuario personalizables que se encuentran en el **fuentes y colores** sección de la **Herramientas \> opciones** cuadro de diálogo, donde los usuarios pueden elegir para cambiar el color de primer plano o color de fondo.  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **Herramientas \> cuadro de diálogo Opciones**  
  
### Colores de la interfaz de usuario de Web  
 Se está convirtiendo en común para la creación de componentes de interfaz de usuario mediante HTML, por lo que puede utilizarse en Visual Studio Online y Visual Studio. Escrita en HTML de la interfaz de usuario deberá utilizar el servicio de VSColor cuando se ejecuta en el entorno de Visual Studio. Para obtener información sobre Daytona y cómo utilizarlo, vea [Daytona y la interfaz de usuario web](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a> El servicio VSColor  
 Visual Studio proporciona un servicio de color del entorno, que también se denomina el servicio VSColor o el servicio de color de shell. Este servicio permite enlazar los valores de color de los elementos de interfaz de usuario a un grupo que contenga colores para cada tema de colores de nombre y valor. El servicio VSColor debe utilizarse para todos los elementos de interfaz de usuario, para que los colores automáticamente cambian para reflejar el tema seleccionado por el usuario actual y para que la interfaz de usuario enlazada al servicio de color del entorno integrarán con nuevos temas en futuras versiones de Visual Studio.  
  
### Cómo funciona el servicio  
 El servicio de color de entorno lee que vscolors definido en el .pkgdef para el componente de interfaz de usuario. Estos VSColors, a continuación, se hace referencia en código o marcado XAML y se cargan a través del **IVsUIShell5.GetThemedColor** o una asignación DynamicResource.  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **Arquitectura de servicio de color del entorno**  
  
### Obtener acceso al servicio  
 Hay varias formas de acceso que utiliza el servicio VSColor, dependiendo de qué tipo de color símbolos \(token\) y qué tipo de código tiene.  
  
#### Colores predefinidos del entorno  
  
##### Desde el código nativo  
 El shell proporciona un servicio que proporciona acceso a la COLORREF de los colores. Es la interfaz de servicio:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 En el archivo VSShell80.idl, la enumeración **\_\_VSSYSCOLOREX** tiene constantes de color de shell. Para usarlo, se pasa como el índice de valor cualquiera de los valores de la \_\_VSSYSCOLOREX enum documentado en MSDN o un índice normal de número que el sistema de Windows API, **GetSysColor**, acepta. Esto recibe el valor RGB del color que se debe utilizar en el segundo parámetro.  
  
 Si almacena un lápiz o un pincel con un color nuevo, debe AdviseBroadcastMessages \(fuera de Visual Studio shell\) y escuchar mensajes WM\_SYSCOLORCHANGE y WM\_THEMECHANGED.  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **Nota:** valores COLORREF la devuelta por **GetVSSysColorEx\(\)** contienen sólo R, G, componentes de un color de tema. Si una entrada de tema usa la transparencia, se descarta el valor de canal alfa antes de devolver. Por lo tanto, si el color del entorno de interés debe utilizarse en un lugar donde es importante la transparencia del canal, debe utilizar IVsUIShell5.GetThemedColor en lugar de IVsUIShell2::GetVSSysColorEx, como se describe más adelante en este tema.  
  
##### Desde el código administrado  
 Obtener acceso al servicio de VSColor por el código nativo es bastante sencillo. Si trabaja con código administrado, sin embargo, la determinación de cómo utilizar el servicio puede ser complicada. Con eso en mente, aquí es un fragmento de código de C\# que muestra este proceso:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 Si está trabajando en Visual Basic, utilice:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### Desde la interfaz de usuario de WPF  
 Puede enlazar a los colores de Visual Studio a través de los valores que se exportan a ResourceDictionary la aplicación. A continuación se muestra un ejemplo de uso de recursos desde la tabla de colores, así como enlazar a los datos de fuente del entorno en XAML.  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### Clases auxiliares y métodos para código administrado  
 Código administrado, biblioteca de Managed Package Framework del shell \(Microsoft.VisualStudio.Shell.12.0.dll\) contiene un par de clases auxiliares que facilita el uso de colores con temas.  
  
 Los métodos auxiliares en el **Microsoft.VisualStudio.Shell.VsColors** clase MPF incluyen **GetThemedGDIColor\(\)** y **GetThemedWPFColor\(\)**. Estos métodos auxiliares devuelven el valor de color de una entrada de tema System.Drawing.Color o System.Windows.Media.Color, que se utilizará en los formularios Windows Forms o WPF UI.  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 La clase también puede usarse para obtener los identificadores VSCOLOR para una clave de recurso de color WPF determinada, o viceversa.  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 Los métodos de **VsColors** clase consultar el servicio de VSColor para devolver el valor de color cada vez que se invocan. Para obtener un valor de color como **System.Drawing.Color**, una alternativa con un mejor rendimiento es usar los métodos de la **Microsoft.VisualStudio.PlatformUI.VSThemeColor** \(clase\), que almacena en caché los valores de color obtenidos del servicio VSColor. La clase se suscribe internamente a eventos de mensajes de difusión de shell y descarta el valor almacenado en caché cuando se produce un evento de cambio de tema. Además, la clase proporciona un. Evento de NET\-friendly para suscribirse a los cambios de tema. Utilice la **ThemeChanged** eventos para agregar un nuevo controlador y utilizar el **GetThemedColor\(\)** método para obtener el color de los valores para la **ThemeResourceKeys** de interés. Un código de ejemplo podría tener este aspecto:  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> Selección de colores de contraste alto  
  
### Información general  
 Windows usa varios temas de nivel de sistema de contraste alto que aumentan el contraste de color de texto, fondos e imágenes, parezca elementos distintos en la pantalla. Por motivos de accesibilidad, es importante que elementos de la interfaz de Visual Studio respondan correctamente cuando los usuarios cambiar a un tema de contraste alto.  
  
 Sólo un puñado de colores del sistema se puede utilizar para los temas de contraste alto. Al elegir el sistema de nombres de colores, recuerde las siguientes sugerencias:  
  
1.  **Elegir los colores del sistema que tienen el mismo significado semántico** como el elemento que se colorear. Por ejemplo, si elige un color de alto contraste para el texto dentro de una ventana, utilice WindowText y no ControlText.  
  
2.  **Elija pares de primer y segundo plano** juntos o no podrá estar seguro de que la selección de color funcione en todos los temas de contraste alto.  
  
3.  **Determinar qué partes de la interfaz de usuario son los más importantes y asegúrese de que se destaquen áreas de contenido.** Perderá mucho detalle, que normalmente harían distinguir sutiles diferencias en el matiz del color, por lo que es común para definir las áreas de contenido, el uso de colores de borde seguro porque no hay ningún variantes de color para varias áreas de contenido.  
  
### Conjunto de colores del sistema  
 La tabla [Blog del equipo de WPF: referencia SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indica el conjunto completo de nombres de colores del sistema y los matices correspondientes aparece en cada tema.  
  
 Al aplicar esto limita el conjunto de colores para la interfaz de usuario, *se espera que pierda detalles sutiles que estaban presentes en los temas "normales"*. Aquí es un ejemplo de interfaz de usuario con color gris sutiles que se utilizan para distinguir las áreas en una ventana de herramientas. Cuando se emparejan con la misma ventana que se muestra en el modo de contraste alto, puede ver que todos los fondos son el mismo matiz y los bordes de las áreas se indican mediante borde únicamente:  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **Ejemplo de detalles sutiles en cómo se pierden cuando en contraste alto**  
  
#### Elegir los colores de texto en un editor  
 Color de texto se utiliza en un editor o en una superficie de diseño para indicar el significado, como permitir para facilitar la identificación de los grupos de elementos similares. En un tema de contraste alto, sin embargo, no tiene la capacidad de diferenciar entre más de tres colores de texto. WindowText, GrayText y HotTrackText son sólo de los colores disponible en superficies WindowBackground. Puesto que no puede usar más de tres colores, elija cuidadosamente las diferencias más importantes que desea mostrar en el modo de contraste alto.  
  
 Tonos para cada uno de los nombres de símbolo \(token\) permitidos en una superficie del editor, tal y como aparecen en cada tema de contraste alto:  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **Comparación de editor de contraste alto**  
  
 Ejemplos de la superficie del editor en el tema azul:  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **Editor en el tema azul**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **Editor en el tema de alto contraste \#1**  
  
### Patrones de uso  
 Muchos elementos comunes de interfaz de usuario ya tienen definido de colores de contraste alto. Estos patrones de uso puede hacer referencia al elegir su propio sistema de nombres de colores, para que los elementos de interfaz de usuario son coherentes con componentes similares.  
  
|Color del sistema|Uso|  
|-----------------------|---------|  
|ActiveCaption|-   Active IDE y ventana rafted glifos de botón al mantener el mouse y presione<br />-   Fondo de la barra de título para el IDE y windows rafted<br />-   Fondo predeterminado de la barra de estado|  
|ActiveCaptionText|-   Active IDE y windows rafted de primer plano de barra de título \(texto y glifos\)<br />-   Fondo y borde de botones de la ventana activa de mantener el mouse y presione|  
|Control|-   Cuadro combinado de lista desplegable y búsqueda predeterminado y deshabilitado fondo del control, incluidos el botón de lista desplegable<br />-   Acoplar el fondo del botón de destino<br />-   Fondo de la barra de comandos<br />-   Fondo de la ventana de herramienta|  
|ControlDark|-   Fondo IDE<br />-   Separadores de barra de menús y comandos<br />-   Borde de la barra de comandos<br />-   Sombras de menú<br />-   Separador y herramienta ventana ficha predeterminado y al mantener el mouse border<br />-   Documentar bien el fondo del botón de desbordamiento<br />-   Borde de glifo de destino de acoplamiento|  
|ControlDarkDark|-   Ventana de la ficha de documento seleccionada no enfocada|  
|ControlLight|-   Borde de ficha de ocultación automática<br />-   Cuadro combinado y el borde de la lista desplegable<br />-   Acoplamiento del fondo y borde|  
|ControlLightLight|-   Borde provisional seleccionado, centrado|  
|ControlText|-   Cuadro combinado y el glifo de la lista desplegable<br />-   Texto de ficha de ventana Anular la selección de herramientas|  
|GrayText|-   Cuadro combinado y borde de lista desplegable lista deshabilitado, glifo de la lista desplegable, texto y el texto del elemento de menú<br />-   Texto de menú deshabilitado<br />-   Texto de encabezado de 'opciones de búsqueda' control de búsqueda<br />-   Separador de secciones de control de búsqueda|  
|Resaltar|-   Todos mantenga presionado fondos y bordes, excepto el cuadro combinado desplegable de documento y el fondo del botón también desbordamiento y borde del botón<br />-   Fondo del elemento seleccionado|  
|HighlightText|-   Todos los activable y presionados primeros planos \(texto y glifos\)<br />-   Herramienta documentos y ventanas ficha ventana primer plano<br />-   Borde de barra de título de ventana de herramienta<br />-   Primer plano de la pestaña provisional especializado y seleccionado<br />-   Documentar bien borde de botón de desbordamiento al mantener el mouse y presione<br />-   Borde de icono seleccionado|  
|HotTrack|-   Bordes en prensa y fondo del control de posición de ScrollBar<br />-   Glifo de flecha de barra de desplazamiento en prensa|  
|InactiveCaption|-   IDE inactiva y ventana rafted glifos de botón al mantener el mouse<br />-   Fondo de la barra de título para el IDE y windows rafted<br />-   Fondo del control de búsqueda deshabilitado|  
|InactiveCaptionText|-   IDE inactiva y foreground de barra de título de windows rafted \(texto y glifos\)<br />-   Fondo de botones de la ventana inactiva y el borde al mantener el mouse<br />-   Borde y fondo del botón de ventana de herramientas no enfocado<br />-   Primer plano del control de búsqueda deshabilitado|  
|Menú|-   Fondo del menú desplegable<br />-   Fondo de marca de verificación activada y deshabilitada|  
|MenuText|-   Borde del menú desplegable<br />-   Comprobación de la marca de verificación<br />-   Glifos de menú<br />-   Texto del menú desplegable<br />-   Borde de icono seleccionado|  
|Barra de desplazamiento|-   Fondo flecha de barra de desplazamiento y la barra de desplazamiento, todos los Estados|  
|Ventana|-   Fondo de la ficha de ocultación automática<br />-   Menú de barras y fondo estante de comandos<br />-   Fondo de ficha de ventana de documento seleccionado o no enfocado y borde de documento, para las fichas abiertas y provisionales<br />-   Fondo de barra de título de ventana herramienta no enfocado<br />-   Fondo de la ficha de ventana de herramienta, ambos seleccionado y no seleccionado|  
|Marco de ventana|-   Borde IDE|  
|WindowText|-   Primer plano de pestaña de ocultación automática<br />-   Primer plano de ficha de ventana de herramienta seleccionada<br />-   Ficha de la ventana de documento no enfocado y de primer plano de la pestaña provisional seleccionado o no enfocado<br />-   Mantenga el mouse sobre un glifo no seleccionado y primer plano predeterminado de la vista de árbol<br />-   Borde de ficha seleccionada de ventana de herramienta<br />-   Glifo, borde y fondo del control de posición de Scrollbar|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> Exposición de colores para los usuarios finales  
  
### Información general  
 A veces desea permitir al usuario final personalizar la interfaz de usuario, como cuando se crea un editor de código o la superficie de diseño. La manera más común de hacerlo es mediante la **Herramientas \> opciones** cuadro de diálogo. A menos que se dispone de muy especializado interfaz de usuario que requiere controles especiales, es la forma más sencilla para presentar la personalización a través de la **fuentes y colores** página dentro de la **entorno** sección del cuadro de diálogo. Para cada elemento que se expone para la personalización, el usuario puede cambiar el color de primer plano o color de fondo.  
  
### Creación de un paquete VSPackage para sus colores personalizables  
 Un VSPackage puede controlar las fuentes y colores mediante categorías personalizadas y mostrar los elementos en la página de propiedades de fuentes y colores. Cuando se utiliza este mecanismo, VSPackages debe implementar la [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interfaz y sus interfaces asociadas.  
  
 En principio, este mecanismo puede utilizarse para modificar todos los elementos de pantalla existentes y las categorías que contienen. Sin embargo, no debe usarse para modificar la categoría del Editor de texto o sus elementos de visualización. Para obtener más información sobre la categoría del Editor de texto, consulte [Introducción de Color y fuente](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
 Para implementar las categorías personalizadas o mostrar elementos, un VSPackage debe:  
  
-   **Cree o identifique categorías en el registro.** Implementación del IDE de la **fuentes y colores** página de propiedades usa esta información para consultar correctamente el servicio admite una categoría determinada.  
  
-   **Cree o identifique los grupos en el registro \(opcional\).** Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE automáticamente combina subcategorías y distribuye mostrar los elementos dentro del grupo.  
  
-   **Implementar la compatibilidad con IDE.**  
  
-   **Controlar los cambios de fuente y color.**  
  
#### Para crear o identificar categorías  
 Crear un tipo especial de entrada de registro de la categoría bajo \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< versión de Visual Studio \> \\FontAndColors\\ \< categoría \>\]. \< categoría \> es el nombre no traducido de la categoría.  
  
 Llenar el registro con dos valores:  
  
|Nombre|Tipo|Datos|Descripción|  
|------------|----------|-----------|-----------------|  
|Categoría|REG\_SZ|GUID|Crea un GUID para identificar la categoría|  
|Paquete|REG\_SZ|GUID|El GUID del servicio de VSPackage que admite la categoría|  
  
 El servicio especificado en el registro debe proporcionar una implementación de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) para la categoría correspondiente.  
  
#### Para crear o identificar grupos  
 Crear un tipo especial de entrada de registro de la categoría bajo \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< versión de Visual Studio \> \\FontAndColors\\ \< grupo \>\]. \< grupo \> es el nombre no traducido del grupo.  
  
 Llenar el registro con dos valores:  
  
|Nombre|Tipo|Datos|Descripción|  
|------------|----------|-----------|-----------------|  
|Categoría|REG\_SZ|GUID|Crea un GUID para identificar la categoría|  
|Paquete|REG\_SZ|GUID|El GUID del servicio de VSPackage que admite la categoría|  
  
 El servicio especificado en el registro debe proporcionar una implementación de **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** para el grupo correspondiente.  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### Implementar la compatibilidad con IDE  
 Implemente [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), que devuelve una [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaz o un **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** en el IDE para cada categoría de la interfaz o el grupo GUID proporcionado.  
  
 Para cada categoría que admite, un VSPackage implementa una instancia independiente de la [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaz.  
  
 Los métodos se implementan a través de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) debe proporcionar el IDE con:  
  
-   Listas de elementos de visualización en la categoría  
  
-   Nombres para mostrar los elementos localizables  
  
-   Mostrar la información de cada miembro de la categoría  
  
 **Nota:** cada categoría debe contener al menos un elemento de la pantalla.  
  
 El IDE utiliza la **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** interfaz para definir una unión de varias categorías.  
  
 Su implementación proporciona el IDE con:  
  
-   Una lista de las categorías que componen un grupo determinado  
  
-   Acceso a las instancias de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) compatible con cada categoría dentro del grupo  
  
-   Nombres de grupo localizables  
  
#### Actualizar el IDE  
 El IDE se almacena en caché información acerca de la configuración de fuente y Color. Por lo tanto, después de cualquier modificación de la configuración de Color y fuente de IDE, asegurándose de que la caché está actualizada es una práctica recomendada.  
  
 Actualizar la caché se realiza a través del [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) de la interfaz y se puede realizados elementos seleccionados globalmente o sólo en.  
  
### Controlar los cambios de fuente y color  
 Para ser compatibles con el color del texto que muestra un paquete VSPackage, el servicio de colores que admite el VSPackage debe responder a los cambios iniciados por el usuario a través de la página de propiedades de fuentes y colores.  
  
 Para ello, un VSPackage debe:  
  
-   **controlar eventos generados por el IDE** implementando la [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interfaz. El IDE llama al método apropiado que se sigue las modificaciones de usuario de la página fuentes y colores. Por ejemplo, llama a la [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) método si se selecciona una fuente nueva.  
  
 **O**  
  
-   **sondear el IDE para cambios**. Esto puede hacerse mediante el sistema implementado [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaz. Aunque principalmente por compatibilidad con la persistencia, la [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) método puede obtener información de fuente y color para mostrar los elementos. Para obtener más información sobre la configuración de fuente y color, vea el artículo MSDN [acceso a fuentes almacenado y la configuración de Color](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
 **Nota:** para asegurarse de que los resultados de sondeo son correctos, use la [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interfaz para determinar si es necesario un vaciado de la caché y la actualización antes de llamar a los métodos de recuperación de la [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaz.  
  
#### Registro de categoría de color y fuente personalizada sin necesidad de implementar interfaces  
 En el ejemplo de código siguiente se muestra cómo registrar la fuente personalizada y la categoría de color sin necesidad de implementar interfaces:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **NOTA:**  
  
-   "NameID" \= el identificador de recurso del nombre de categoría adaptada en el paquete  
  
-   "ToolWindowPackage" \= GUID del paquete  
  
-   "Categoría" \= "{9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE}" es sólo un ejemplo y el valor real puede ser un nuevo GUID proporcionado por el implementador.  
  
### Establecer la fuente y Color propiedad GUID de categoría  
 El ejemplo de código siguiente muestra cómo establecer el GUID de categoría.  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona y la interfaz de usuario web  
  
### Información general  
 "Daytona" es un conjunto de API, herramientas y servicios que permiten al usuario crear complementos con HTML, CSS y JavaScript que puede utilizarse en una gran variedad de hosts, como Visual Studio o F12. Los complementos se componen de un componente portátil, que está escrito en HTML, CSS y JavaScript, y componentes opcionales de host específico. Cada host Daytona puede tener su propio conjunto de convenciones de interfaz de usuario, implícitas o explícitas, que un complemento debe cumplir para que aparezcan nativo a su entorno. Algunos hosts, como Visual Studio, que los usuarios puedan realizar cambios en el tema"predeterminado" para que los aspectos visuales del host no puede destinarse estáticamente al crear una hoja de estilos. Esto supone un desafío para los desarrolladores que crean complementos portátiles. Este tema explica cómo crear la interfaz de usuario en Visual Studio mediante el host Daytona de forma que sea completamente compatible con temas y contraste alto web.  
  
### Mecanismo de temas Daytona  
 El tiempo de ejecución Daytona proporciona un conjunto de servicios que abstrae las convenciones de la interfaz de usuario y las capacidades de creación de temas del host. Estos servicios aseguran que los complementos se ajustan automáticamente las expectativas del usuario en función del entorno en que están hospedados visual. Este comportamiento proporciona tres características principales:  
  
1.  Una hoja de estilos insertados en tiempo de ejecución \(plugin.css\) que se aplica un conjunto de reglas CSS a la interfaz de usuario de un complemento de forma transparente y estilos el conjunto predeterminado de los controles HTML \(por ejemplo, HTMLInputElement y HTMLButtonElement  
  
2.  Un conjunto de tokens proporcionados por el host que puede utilizarse para elementos de interfaz de usuario de estilo con los valores que se basan en el tema en lugar de codificado de forma rígida  
  
    1.  una sintaxis declarativa para tener acceso a estos tokens con CSS  
  
    2.  una API para tener acceso a los tokens de tema desde JavaScript  
  
3.  Notificación de cambios de tema  
  
#### Hoja de estilos insertados en tiempo de ejecución  
 Las coordenadas de tiempo de ejecución Daytona con el host para insertar un estilo de hoja que automáticamente temas de los elementos de interfaz de usuario estándares de un complemento. Esto incluye estilos para los siguientes conceptos:  
  
-   Fuente del entorno  
  
-   Colores de fondo  
  
-   Hipervínculos  
  
-   Controles de formulario \(por ejemplo: \< Seleccionar \>, \< input \>, \< botón \>  
  
-   Tablas  
  
-   Encabezados  
  
-   Barras de desplazamiento  
  
 Esto significa que si la interfaz de usuario se compone completamente de los controles de interfaz de usuario HTML estándar, a continuación, realizar ningún trabajo adicional debería ser necesario para responder correctamente a los cambios de tema y admitir contraste alto.  
  
#### Interfaces de usuario personalizadas  
 En casi todos los casos no triviales, el estándar de controles de interfaz de usuario HTML será suficiente para proporcionar una experiencia completa para un complemento y se debe introducir la interfaz de usuario personalizada. Para admitir el uso de elección y el color de fuente adecuada, **tokens tema** debe utilizarse mediante declaración en CSS o de forma imperativa a través de la API de JavaScript se describe a continuación. El tiempo de ejecución Daytona se encargará de la actualización de las hojas de estilos que usan estos tokens en la carga del complemento y en los cambios de tema.  
  
##### Tokens de tema  
 Ambos tokens tema específico del host y estándar están disponibles. Tokens estándar son insertados por el host y siempre está disponible. Es preferible utilizar los tokens estándares siempre que sea posible. Tokens estándar se garantiza que todos los hosts Daytona proporciona y su uso hace que el complemento inherentemente más portátil. El conjunto de símbolos estándares está sujeta a cambios, aunque se deben agregar sólo nuevos tokens y ninguno se debe quitar. La versión de Visual Studio 2013 se describe más abajo:  
  
|Nombre del token|Descripción|  
|----------------------|-----------------|  
|color de fondo del complemento|El color de fondo predeterminado para el complemento|  
|complemento de color|El color de primer plano predeterminado para el complemento|  
|complemento de contextmenu activo color|El color de selección de primer plano predeterminado para los menús contextuales cuando están activas \(tiene el foco\)|  
|complemento\-contextmenu: color de fondo|El color de fondo predeterminado para los menús contextuales|  
|complemento de contextmenu borde de color|El color de borde predeterminado para los menús contextuales|  
|complemento de color de contextmenu|El color de primer plano predeterminado para los menús contextuales|  
|complemento de contextmenu activable color|El color de fondo predeterminado al mantener el mouse para los menús contextuales|  
|complemento de contextmenu hover texto colores|El color de primer plano al mantener el mouse predeterminado para los menús contextuales|  
|complemento\-contextmenu\-icono de casilla de verificación|El color del icono de casilla de verificación predeterminado para los menús contextuales|  
|complemento de contextmenu\-inactiva\-color de texto|El color de selección de primer plano predeterminado para los menús contextuales cuando están inactivos|  
|complemento de contextmenu separador de color|El color del separador predeterminado para los menús contextuales|  
|familia de fuentes del complemento|La familia de fuentes predeterminada que se utilizará para el complemento|  
  
 En Visual Studio, los tokens del complemento de fuentes siguientes se basan en la configuración de fuente del entorno:  
  
-   tamaño de fuente de complemento  
  
-   espesor de fuente de complemento  
  
-   complemento\-resaltado de color de fondo  
  
-   color de resaltado de complemento  
  
-   complemento de color inactivo  
  
 Los tokens de vínculo de complemento siguiente se utilizan para definir el estilo HTMLElements \(hipervínculos\):  
  
-   color de los vínculos de complemento  
  
-   complemento de vínculo activo color  
  
-   complemento de vínculo activable color  
  
 Plugin.CSS estilos barras de desplazamiento de forma predeterminada con los tokens siguientes para una mejor compatibilidad con los temas en los distintos hosts \(en particular, Visual Studio\):  
  
-   complemento de barra de desplazamiento flecha de color  
  
-   complemento de barra de desplazamiento: color de fondo  
  
-   complemento de barra de desplazamiento cara color  
  
 Los tokens de selección de complemento siguientes se utilizan para definir el estilo del HTMLSelectElement \(cuadro combinado desplegable\):  
  
-   complemento seleccione opción fondo de color  
  
-   complemento seleccione opción color  
  
-   plugin\-Select\-Option\-Checked\-background\-color  
  
-   plugin\-Select\-Option\-Checked\-Border\-color  
  
-   plugin\-Select\-Option\-Checked\-Foreground\-color  
  
-   plugin\-Select\-Option\-Hover\-background\-color  
  
-   plugin\-Select\-Option\-Hover\-Border\-color  
  
-   plugin\-Select\-Option\-Hover\-Foreground\-color  
  
-   complemento\-Seleccione\-color de borde  
  
-   complemento\-seleccione: color de fondo  
  
-   complemento\-Seleccione\-color de primer plano  
  
-   complemento seleccione activable fondo de color  
  
-   complemento seleccione activable borde de color  
  
-   complemento seleccione activable foreground color  
  
-   complemento tabla borde de color  
  
-   complemento tabla encabezado fondo de color  
  
-   complemento de tabla de encabezado de color  
  
-   complemento\-cuadro de texto y color de borde  
  
-   complemento de cuadro de texto: color de fondo  
  
-   color del cuadro de texto de complemento  
  
-   complemento de cuadro de texto deshabilitado fondo de color  
  
-   complemento de cuadro de texto deshabilitado borde de color  
  
-   complemento de cuadro de texto deshabilitado color  
  
 Estos tokens se deberían utilizar para *todos los* árbol vistas y tablas, ya que tienen los valores predeterminados correctos establecidos en los distintos hosts que admiten los temas y contraste alto:  
  
-   complemento de treeview contenido fondo de color  
  
-   complemento de treeview contenido color  
  
-   plugin\-TreeView\-Content\-inactive\-Selected\-color  
  
-   plugin\-TreeView\-Content\-MouseOver\-background\-color  
  
-   complemento de treeview contenido mouseover color  
  
-   plugin\-TreeView\-Content\-inactive\-Selected\-color  
  
-   plugin\-TreeView\-Content\-Selected\-background\-color  
  
-   plugin\-TreeView\-Content\-Selected\-Border\-color  
  
-   complemento de treeview\-contenido\-\-color seleccionado  
  
##### Tokens de host específico  
 Además de admitir el conjunto estándar de tokens, los hosts también pueden proporcionar tokens no estándares. Para ello, el host de Visual Studio que permite el complemento especificar alias de token de tema en una sección específico de Visual Studio del manifiesto. Por ejemplo:  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 Este ejemplo presenta un token de tema denominado "diagnóstico\-host\-borde", que puede hacer referencia de forma idéntica a los tokens estándares mencionados anteriormente. Key\_type, la categoría y el nombre que se utilizan para resolver el color a través de la **IVsFontAndColorStorage** interfaz. En muchos casos, es posible encontrar los colores adecuados \(junto con la categoría, el key\_type y la información de nombre\) en los archivos XML ubicados en vscommon\\themes. Este mismo mecanismo se usa si el paquete incorpora nuevos colores configurables: coincide con la categoría, key\_type y nombre en el color que desea utilizar. Autores de complemento deben intentar usar tokens estándar siempre que sea posible y sólo utilizar tokens de host específico cuando sea absolutamente necesario.  
  
##### Uso de tokens de tema en CSS  
 Tokens de tema se conocen a través de una sintaxis de comentario con formato especial. Las reglas de análisis de tokens:  
  
1.  La expresión de comentario debe ir entre corchetes \(**\[\]**\).  
  
2.  Se omiten todos los espacios en blanco en el comentario, pero fuera de la expresión.  
  
3.  La expresión de comentario debe seguir directamente la propiedad que reemplaza.  
  
4.  Se eliminarán los espacios en blanco iniciales ni finales dentro de la expresión.  
  
5.  Cada nombre de símbolo \(token\) dentro de la expresión debe ir entre llaves \(por ejemplo, **{font\-family}** y **{color de desplazamiento de botón}**\). De lo contrario, se tratará como un valor literal.  
  
 Los siguientes son ejemplos de cómo el analizador token reemplazará los valores CSS, suponiendo que el **color de fondo del complemento** token tiene el valor de \#000 y el **familia de fuentes del complemento** token tiene el valor de "Verdana".  
  
|CSS creados|CSS analizada|Notas|  
|-----------------|-------------------|-----------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|El valor predeterminado se reemplaza con el valor dinámico de host específico.|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|Se omite el espacio en blanco fuera de la expresión.|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|Se recorta el espacio en blanco inicial y final de la expresión.|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|La expresión no está incluida entre corchetes y, por tanto, se omite el comentario.|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|El token no está entre llaves y, por tanto, se trata como un valor literal.|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|El comentario no sigue el valor de propiedad y, por tanto, se omite.|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*Igual que el anterior*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*Igual que el anterior*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|Se reemplaza el token y se mantiene el contenido literal.|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*Igual que el anterior*|  
  
 Si un archivo CSS incluye tokens de tema que debe estar marcada por el atributo de tema del complemento de datos en el elemento de vínculo en el archivo HTML. Por ejemplo:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### Uso de tokens de tema desde JavaScript  
 Interfaz de usuario personalizada debe ser con temas de CSS, siempre que sea posible, hay escenarios cuando el valor de un tema de símbolo \(token\) debe tener acceso mediante programación. Por ejemplo, si la interfaz de usuario personalizada que se va a dibujar en un CanvasElement que no hereda el estilo de CSS, o si se va dinámicamente a un elemento de interfaz de usuario creados en lugar de hacer referencia a hojas de estilos. Los escenarios se habilitan mediante la API Daytona **Plugin.Theme.getValue**. Esta función devuelve un valor de tema proporcionada por el host al proporcionar un nombre de símbolo \(token\).  
  
|No aplicar un tema|Aplicar un tema|  
|------------------------|---------------------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 Si se usa símbolos \(tokens\) de JavaScript**, debe administrarse el evento de cambio de tema para responder a las actualizaciones de**. Esto no es necesario para los tokens de tema utilizados mediante declaración en CSS, como el tiempo de ejecución Daytona se encarga de ello para el complemento. El evento de tema se puede administrar de la siguiente manera:  
  
|Miembros \(controlador único\)|Evento de DOM \(varios controladores\)|  
|------------------------------------|--------------------------------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 En este caso, sería muy común para volver a llamar a **Plugin.Theme.getValue** en estos controladores, como el valor de los tokens de tema probables cambiado cuando cambia el tema.  
  
##### Asignación de token estándar  
 Los tokens estándares se asignan a los colores de entorno y el Shell. La lista siguiente proporciona un sabor de ¿cuáles son esas asignaciones.  
  
|Nombre del token|Asignación de VS \(EnvironmentColors\)|  
|----------------------|--------------------------------------------|  
|complemento de color|ToolWindowTextColorKey|  
|color de fondo del complemento|ToolWindowBackgroundColorKey|  
|color de los vínculos de complemento|ControlLinkTextColorKey|  
|complemento de vínculo activable color|ControlLinkTextHoverColorKey|  
|complemento de vínculo activo color|ControlLinkTextPressedColorKey|  
|color de resaltado de complemento|HighlightTextColorKey|  
|complemento\-resaltado de color de fondo|HighlightColorKey|  
|complemento tabla encabezado fondo de color|GridHeadingBackgroundColorKey|  
|complemento de tabla de encabezado de color|GridHeadingTextColorKey|  
|complemento tabla borde de color|GridLineColorKey|  
|complemento\-botón: color de fondo|ButtonFaceColorKey|  
|complemento de botón al mantener el mouse fondo de color|ButtonHighlightColorKey|  
|color del botón de complemento|ButtonTextColorKey|  
|complemento\-botón de color de borde|ButtonBorderColorKey|  
  
##### Cambios de tema  
 El host desencadenadores complemento tema cambios en Visual Studio cuando un usuario final realiza cambios en las siguientes opciones:  
  
 **Tema de color:**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **Tema del entorno:**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **Tema del sistema operativo** \(sólo al cambiar a y de alto contraste\):  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")