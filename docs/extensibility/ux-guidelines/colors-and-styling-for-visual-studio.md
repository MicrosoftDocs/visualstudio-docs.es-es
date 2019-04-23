---
title: Colores y estilos para Visual Studio | Documentos de Microsoft
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ba49e1ab3e25e3f22a9ca8642673aa0a62869f6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114774"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colores y estilos para Visual Studio

## <a name="use-color-in-visual-studio"></a>Usar color en Visual Studio

En Visual Studio, el color se utiliza principalmente como una herramienta de comunicación, no solo como decoración. Usar color como mínimo y reservarlo para situaciones donde desee:

- Comunicar el significado o la afiliación (por ejemplo, los modificadores de plataforma o lenguaje)

- Atraer la atención (por ejemplo, que indica un cambio de estado)

- Mejorar la legibilidad y proporcionar puntos de referencia para navegar por la interfaz de usuario

- Aumentar la conveniencia

Existen varias opciones para asignar colores a los elementos de interfaz de usuario de Visual Studio. A veces puede ser difícil de figura qué opción se supone que para usar o cómo usarla correctamente. En este tema le ayudarán a:

- Comprender los diferentes servicios y sistemas que se usan para definir colores en Visual Studio.

- Seleccione la opción correcta para un elemento determinado.

- Usar correctamente la opción que ha elegido.

> [!NOTE]
> Nunca codificar hexadecimal, RGB o colores del sistema para los elementos de interfaz de usuario. Mediante los servicios permite flexibilidad en el ajuste de tono. Además, sin que el servicio, no podrá aprovechar las capacidades de cambio de tema de [el servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para asignar color a elementos de la interfaz de Visual Studio

Elija el método que mejor se adapte a sus elementos de interfaz.

| La interfaz de usuario | Método | ¿Para qué es? |
| --- | --- | --- |
| Se han incrustado o cuadros de diálogo independiente. | **Colores del sistema** | Los nombres del sistema que permiten el sistema operativo definir el color y apariencia de los elementos de interfaz de usuario, como los controles de cuadro de diálogo común. |
| Tiene una interfaz de usuario personalizada que desea que sea coherente con el entorno de VS general y tiene elementos de interfaz de usuario que coinciden con la categoría y el significado semántico de los tokens compartidos. | **Colores comunes compartidos** | Los nombres de símbolo (token) de color predefinido para elementos específicos de la interfaz de usuario existentes |
| Tiene un grupo de funciones o características individuales y no hay ningún color compartida para elementos similares. | **Colores personalizados** | Nombres de token de color que son específicas de un área y no tiene pensado compartir con otras interfaces de usuario |
| Desea permitir que el usuario final personalizar la interfaz de usuario o el contenido (por ejemplo, para los editores de texto o ventanas del diseñador especializadas). | **Personalización del usuario final**<br /><br />**(Herramientas &gt; cuadro de diálogo Opciones)** | Configuración definida en la página "Fuentes y colores" de la **herramientas &gt; opciones** cuadro de diálogo o una página especializada específica para una característica de interfaz de usuario. |

### <a name="visual-studio-themes"></a>Temas visuales Studio

Visual Studio incluye tres temas de color diferente: azul, oscuro y claro. Asimismo, detecta el modo de contraste alto, que es un tema de color de todo el sistema diseñado para mejorar la accesibilidad.

Los usuarios se le pedirá que seleccione un tema durante su primer uso de Visual Studio y pueden cambiar los temas más adelante, vaya a **herramientas &gt; opciones &gt; entorno &gt; General** y elegir un nuevo tema de el menú desplegable "tema de color".

Los usuarios también pueden usar el Panel de Control para cambiar sus sistemas todos en uno de los diversos temas de contraste alto. Si un usuario selecciona un tema de contraste alto, a continuación, el selector de tema de color de Visual Studio ya no afecta a los colores en Visual Studio, aunque se guardan los cambios de tema para cuando el usuario sale del modo de contraste alto. Para obtener más información acerca del modo de contraste alto, consulte [colores de contraste alto elegir](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>El servicio VSColor

Visual Studio proporciona un servicio de color del entorno, conocido como el servicio VSColor, que le permite enlazar los valores de color los elementos de la interfaz de usuario a una entrada con nombre que contiene los valores de color para cada tema de Visual Studio. Esto garantiza que sus colores cambiará automáticamente para reflejar el actual seleccionado por el usuario tema o el sistema de modo de contraste alto. Uso del servicio significa que la implementación de todos los cambios relacionados con el tema de color se controla en un solo lugar y, si usa los colores comunes compartidos desde el servicio, la interfaz de usuario reflejará automáticamente nuevos temas en versiones futuras de Visual Studio.

### <a name="implementation"></a>Implementación

El código fuente de Visual Studio incluye varios archivos de definición de paquete que contienen listas de nombres de token y los valores de color correspondiente para cada tema. El servicio de color lee el VSColors definido en estos archivos de definición de paquete. Estos colores se hace referencia en el marcado XAML o en el código y, a continuación, se cargan a través del `IVsUIShell5.GetThemedColor` método o una asignación DynamicResource.

### <a name="system-colors"></a>Colores del sistema

Controles comunes de hacer referencia a los colores del sistema de forma predeterminada. Si desea que la interfaz de usuario para usar colores del sistema, como cuando se crea un cuadro de diálogo incrustado o independiente, no es necesario hacer nada.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colores comunes compartidos en el servicio VSColor

Los elementos de la interfaz deben reflejar el entorno general de Visual Studio. Mediante la reutilización de los colores comunes compartidos que son adecuados para el componente de interfaz de usuario que va a diseñar, asegúrese de que la interfaz es coherente con otras interfaces de Visual Studio, y que sus colores se actualizarán automáticamente cuando se agregan o actualizan los temas.

Antes de usar los colores comunes compartidos, asegúrese de que comprende cómo usarlas correctamente. Uso incorrecto de los colores comunes compartidos podría dar lugar a una experiencia incoherente, frustrante o confuso para los usuarios.

### <a name="user-customizable-colors"></a>Colores personalizables por el usuario

Vea: [Exposición de colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

A veces, desea permitir que el usuario final personalizar la interfaz de usuario, como cuando se crea un editor de código o la superficie de diseño. Componentes de interfaz de usuario personalizables que se encuentran en el **fuentes y colores** sección de la **herramientas &gt; opciones** cuadro de diálogo, donde los usuarios pueden elegir para cambiar el color de primer plano, color de fondo o ambos.

![Herramientas &gt; cuadro de diálogo Opciones](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />Herramientas &gt; cuadro de diálogo Opciones

## <a name="BKMK_TheVSColorService"></a> El servicio VSColor

Visual Studio proporciona un servicio de color de entorno, también denominado el servicio VSColor o el servicio de color de shell. Este servicio permite enlazar los valores de color los elementos de la interfaz de usuario a un conjunto que contiene los colores para cada tema de colores de nombre y valor. El servicio VSColor debe usarse para todos los elementos de interfaz de usuario, por lo que los colores automáticamente cambian para reflejar el tema seleccionado por el usuario actual y para que la interfaz de usuario enlazada al servicio de color de entorno integrarán con nuevos temas en futuras versiones de Visual Studio.

### <a name="how-the-service-works"></a>Cómo funciona el servicio

El servicio de color de entorno lee que vscolors definido en el .pkgdef para el componente de interfaz de usuario. Estos VSColors, a continuación, se hace referencia en código o marcado XAML y se cargan a través del `IVsUIShell5.GetThemedColor` o un `DynamicResource` asignación.

![Arquitectura del servicio de color de entorno](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Arquitectura de servicio de color del entorno

### <a name="accessing-the-service"></a>Obtener acceso al servicio

Hay varias formas de acceso usa el servicio VSColor, dependiendo de qué tipo de color de símbolos (token) y qué tipo de código tiene.

#### <a name="predefined-environment-colors"></a>Colores predefinidos del entorno

##### <a name="from-native-code"></a>Desde el código nativo

El shell proporciona un servicio que proporciona acceso a la `COLORREF` de los colores. Es la interfaz de servicio:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

En el archivo vsshell80.idl, la enumeración del explorador `__VSSYSCOLOREX` tiene shell color constantes. Para ello, pase como el valor de índice cualquiera de los valores de la `enum __VSSYSCOLOREX` documentadas en MSDN o un índice normal número que el sistema de Windows API, `GetSysColor`, acepta. Esto recibe el valor RGB del color que debe usarse en el segundo parámetro.

Si almacena un lápiz o un pincel con un nuevo color, deberá `AdviseBroadcastMessages` (fuera de Visual Studio shell) y escuchar `WM_SYSCOLORCHANGE` y `WM_THEMECHANGED` mensajes.

Para acceder al servicio de color en código nativo, podrá realizar una llamada similar a esta:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> El `COLORREF` valores devueltos por `GetVSSysColorEx()` contienen sólo R, G, componentes de un color de tema. Si una entrada de tema usa la transparencia, se descarta el valor de canal alfa antes de devolver. Por lo tanto, si el color del entorno de interés debe usarse en un lugar donde es importante la transparencia del canal, debe usar `IVsUIShell5.GetThemedColor` en lugar de `IVsUIShell2::GetVSSysColorEx`, como se describe más adelante en este tema.

##### <a name="from-managed-code"></a>Desde el código administrado

Acceder al servicio VSColor a través de código nativo es bastante sencillo. Si está trabajando a través de código administrado, sin embargo, determinar cómo usar el servicio puede ser complicado. Con eso en mente, este es un fragmento de código de C# que muestra este proceso:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Si está trabajando en Visual Basic, use:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Desde la interfaz de usuario de WPF

Puede enlazar a los colores de Visual Studio a través de los valores que se exportan a la aplicación `ResourceDictionary`. A continuación es un ejemplo de uso de recursos de la tabla de colores, así como enlazar a los datos de fuente del entorno en XAML.

```xml
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

Los métodos auxiliares en el `Microsoft.VisualStudio.Shell.VsColors` incluyen clases de MPF `GetThemedGDIColor()` y `GetThemedWPFColor()`. Esos métodos auxiliares devuelven el valor de color de una entrada de tema como `System.Drawing.Color` o `System.Windows.Media.Color`que se van a utilizar en formularios Windows Forms o WPF UI.

```csharp
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

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Los métodos de `VsColors` clase consultar el servicio de VSColor para devolver el valor de color de cada vez que se invocan. Para obtener un valor de color como `System.Drawing.Color`, una alternativa con un mejor rendimiento es en su lugar, use los métodos de la `Microsoft.VisualStudio.PlatformUI.VSThemeColor` (clase), que se almacena en caché los valores de color que se obtiene del servicio VSColor. La clase se suscribe internamente a eventos de mensajes de difusión de shell y descarta el valor almacenado en caché cuando se produce un evento de cambio de tema. Además, la clase proporciona un. Evento compatible con NET para suscribirse a los cambios de tema. Utilice la `ThemeChanged` eventos para agregar un nuevo controlador y usar el `GetThemedColor()` método para obtener el color de los valores de la `ThemeResourceKeys` de interés. Un código de ejemplo podría tener este aspecto:

```csharp
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

## <a name="BKMK_ChoosingHighContrastColors"></a> Selección de colores de contraste alto

### <a name="overview"></a>Información general

Windows usa varios temas de nivel de sistema de contraste alto que aumentan el contraste de color de texto, fondos e imágenes, parezca elementos distintos en la pantalla. Por motivos de accesibilidad, es importante que los elementos de interfaz de Visual Studio responden correctamente cuando los usuarios cambiar a un tema de contraste alto.

Solo un conjunto de colores del sistema puede usarse para los temas de contraste alto. Al elegir el sistema de nombres de colores, recuerde las siguientes sugerencias:

- **Elija los colores del sistema que tienen el mismo significado semántico** como el elemento que se colores. Por ejemplo, si elige un color de contraste alto para el texto dentro de una ventana, utilice WindowText y no ControlText.

- **Elija pares de primer plano y fondo** juntos o no podrá estar seguro de que la selección de color funcione en todos los temas de contraste alto.

- **Determinar qué partes de la interfaz de usuario son las más importantes y asegúrese de que se destaquen áreas de contenido.** Se perderá una gran cantidad de detalle que normalmente harían distinguir diferencias sutiles de matiz del color, por lo que es común para definir las áreas de contenido, el uso de colores de borde seguro porque no hay ningún variantes de color para varias áreas de contenido.

### <a name="system-color-set"></a>Conjunto de colores del sistema

La tabla en [WPF Team Blog: Referencia de SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indica el conjunto completo de los nombres de colores del sistema y los matices correspondientes aparece en cada tema.

Al aplicar este conjunto de colores para la interfaz de usuario limitado *se espera que perderá detalles sutiles que estaban presentes en los temas "normales"*. Este es un ejemplo de interfaz de usuario con colores gris sutiles que sirven para distinguir las áreas en una ventana de herramientas. Cuando se combina con la misma ventana que se muestra en el modo de contraste alto, puede ver que todos los fondos son el mismo matiz y se indican los bordes de esas áreas con borde por sí solo:

![Ejemplo de los detalles de cómo sutiles se pierden en contraste alto](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Ejemplo de los detalles de cómo sutiles se pierden en contraste alto

#### <a name="choosing-text-colors-in-an-editor"></a>Elegir los colores de texto en un editor

Texto con colores se usa en un editor o en una superficie de diseño para indicar el significado, como permitir para facilitar la identificación de los grupos de elementos similares. Sin embargo, en un tema de contraste alto, no tiene la capacidad de diferenciar entre más de tres colores de texto. WindowText, GrayText y HotTrackText son los colores solo disponibles en las superficies WindowBackground. Puesto que no se puede usar más de tres colores, elegir cuidadosamente las diferencias más importantes que se desean mostrar en el modo de contraste alto.

Tonos para cada uno de los nombres de token que se permiten en una superficie del editor, tal y como aparecen en cada tema de contraste alto:

![Comparación de editor de contraste alto](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Comparación de editor de contraste alto

Ejemplos de la superficie del editor en el tema azul:

![Editor en el tema azul](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Editor en el tema azul

![Editor en el tema de contraste alto 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Editor en el tema de contraste alto 1

### <a name="usage-patterns"></a>Patrones de uso

Muchos elementos comunes de la interfaz de usuario ya tienen definido de colores de contraste alto. Estos patrones de uso puede hacer referencia al elegir su propio sistema de nombres de colores, para que los elementos de interfaz de usuario son coherentes con los componentes similares.

| Color del sistema | Uso |
| --- | --- |
| ActiveCaption | -Active IDE y glifos de botón de ventana rafted en mantener el mouse y presione<br />-Fondo de la barra de título IDE y rafted windows<br />: Valor predeterminado fondo de la barra de estado |
| ActiveCaptionText | -Active IDE y rafted windows para primer plano de barra de título (texto y glifos)<br />-En segundo plano y de borde de los botones de la ventana activa de mantener el mouse y presione |
| Control | -Cuadro combinado lista desplegable y búsqueda controlan de forma predeterminada y fondo, incluidos el botón desplegable deshabilitado<br />: Fondo de botón de destino de acoplamiento<br />: Fondo de la barra de comandos<br />: Fondo de la ventana de herramienta |
| ControlDark | : En segundo plano IDE<br />-Menú y comandos separadores con barra<br />: Borde de la barra de comandos<br />: Las sombras del menú<br />-Herramienta de borde de predeterminado y mantenga el puntero de la ficha de ventana y el separador<br />-También documentar el fondo del botón de desbordamiento<br />-Borde de glifo de destino de acoplamiento |
| ControlDarkDark |-Ventana de documento sin foco y seleccionado de ficha |
| ControlLight |-Borde de ficha ocultación automática<br />-Borde de combinado desplegable y de cuadro de lista<br />-Acoplar en segundo plano de destino y el borde |
| ControlLightLight | -Borde provisional seleccionada, con foco |
| ControlText | -Glifo de combinado desplegable y de cuadro de lista<br />-Texto de la ventana sin seleccionar pestaña herramienta |
| GrayText |-Cuadro combinado y la lista desplegable deshabilitado borde, desplegable glifo, texto y el texto del elemento de menú<br />-Texto de menú deshabilitado<br />-Texto del encabezado de búsqueda control 'opciones de búsqueda'<br />: Separador de sección de control de búsqueda |
| Resaltar | -Todas al mantener el mouse y fondos presionados y bordes, excepto combinado botón desplegable en segundo plano y documento desbordamiento bien botón borde del cuadro<br />-Fondos de elemento seleccionado |
| HighlightText | -Todas al mantener el mouse y colorear presionado (texto y glifos)<br />-Herramienta documentos y ventanas ficha ventana control primer plano<br />-Borde de barra de título de ventana de herramientas centrado<br />-Primer plano de la pestaña provisional especializado y seleccionado<br />-También documentar borde de botón de desbordamiento al mantener el mouse y presione<br />-Borde del icono seleccionado|
| HotTrack | : En segundo plano de control de posición y el borde al presionar la barra de desplazamiento<br />-La barra de desplazamiento glifo de flecha en prensa |
| InactiveCaption | -IDE inactivo y los glifos de botón de ventana rafted al mantener el mouse<br />-Fondo de la barra de título IDE y rafted windows<br />-En segundo plano de control de búsqueda deshabilitado |
| InactiveCaptionText | -IDE inactiva y foreground de barra de título de windows rafted (texto y glifos)<br />-Fondo de los botones de ventana inactiva y el borde al mantener el mouse<br />-Borde y fondo de botón de ventana de herramientas sin foco<br />-Primer plano de control de búsqueda deshabilitado |
| Menú | -Fondo del menú lista desplegable<br />-Checked y fondo de marca de verificación deshabilitada |
| MenuText | -Borde del menú lista desplegable<br />: Marcas de verificación<br />-Glifos menú<br />-Texto del menú lista desplegable<br />-Borde del icono seleccionado |
| Barra de desplazamiento | -Desplazarse barra y fondo de la flecha, todos los Estados de la barra de desplazamiento |
| Ventana | Ocultar automáticamente el fondo de pestaña<br />-Menú de barras y fondo del estante de comandos<br />-Borde de documento, para las pestañas abiertas y provisionales y de fondo de ficha de ventana de documento sin foco o no seleccionado<br />-Fondo de barra de título de ventana de herramientas sin foco<br />-Fondo de pestaña de la ventana de herramientas, ambos seleccionado y no seleccionado |
| WindowFrame | : Borde IDE |
| WindowText | -Primer plano de pestaña ocultación automática<br />-Primer plano de ficha de ventana de herramienta seleccionada<br />-Pestaña de ventana de documento sin foco y de primer plano de la pestaña provisional seleccionado o sin foco<br />-Árbol predeterminado de primer plano de vista y al mantener el mouse sobre un glifo no seleccionado<br />: Borde de ficha seleccionada de ventana de herramientas<br />-La barra de desplazamiento glifo, borde y fondo de miniatura |

## <a name="BKMK_ExposingColorsForEndUsers"></a> Exposición de colores para los usuarios finales

### <a name="overview"></a>Información general

A veces quiera permitir que el usuario final personalizar la interfaz de usuario, como cuando se crea un editor de código o la superficie de diseño. La manera más común de hacerlo es mediante la **herramientas &gt; opciones** cuadro de diálogo. A menos que muy especializados interfaz de usuario que requiere controles especiales, es la manera más fácil para presentar la personalización a través de la **fuentes y colores** página dentro de la **entorno** sección del cuadro de diálogo. Para cada elemento que se expone para la personalización, el usuario puede cambiar el color de primer plano, color de fondo o ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creación de un VSPackage para los colores personalizables

Un VSPackage puede controlar las fuentes y colores a través de las categorías personalizadas y mostrar los elementos en la página de propiedades de fuentes y colores. Cuando se utiliza este mecanismo, los paquetes VSPackage deben implementar la [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) interfaz y sus interfaces asociadas.

En principio, este mecanismo puede usarse para modificar todos los elementos de visualización existentes y las categorías que los contienen. Sin embargo, no debe usarse para modificar la categoría del Editor de texto o sus elementos de visualización. Para obtener más información sobre la categoría del Editor de texto, consulte [información general de Color y fuente](../font-and-color-overview.md).

Para implementar categorías personalizadas o mostrar los elementos, un VSPackage debe:

- **Cree o identifique categorías en el registro.** Implementación del IDE de la **fuentes y colores** página de propiedades usa esta información para consultar correctamente para el servicio que admite una categoría determinada.

- **Cree o identifique los grupos en el registro (opcional).** Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE automáticamente combina las subcategorías y distribuye mostrar los elementos dentro del grupo.

- **Implementar la compatibilidad con IDE.**

- **Controlar los cambios de fuente y color.**

#### <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías

Construir un tipo especial de entrada de registro de la categoría bajo `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` donde `<Category>` es el nombre no traducido de la categoría.

Llenar el registro con dos valores:

| Name | Tipo | Datos | Descripción |
| --- | --- | --- | --- |
| Categoría | REG_SZ | GUID | Crea un GUID para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio de VSPackage que admite la categoría |

 El servicio especificado en el registro debe proporcionar una implementación de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) para la categoría correspondiente.

#### <a name="to-create-or-identify-groups"></a>Para crear o identificar grupos

Construir un tipo especial de entrada de registro de la categoría bajo `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` donde `<group>` es el nombre no traducido del grupo.

Llenar el registro con dos valores:

| Name | Tipo | Datos | Descripción |
|--- | --- | --- | --- |
| Categoría | REG_SZ | GUID | Crea un GUID para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio de VSPackage que admite la categoría |

El servicio especificado en el registro debe proporcionar una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> para el grupo correspondiente.

![Implementación de encontrar](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Implementación de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Para implementar la compatibilidad con IDE

Implemente [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), que devuelve un [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaz o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaz en el IDE para cada categoría o el grupo GUID proporcionado.

Para cada categoría admite, un VSPackage implementa una instancia independiente de la [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaz.

Los métodos se implementan a través de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) debe proporcionar el IDE con:

- Listas de elementos para mostrar en la categoría

- Nombres para mostrar los elementos localizables

- Mostrar la información de cada miembro de la categoría

> [!NOTE]
> Todas las categorías deben contener al menos un elemento de la pantalla.

El IDE usa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaz para definir una unión de varias categorías.

Su implementación proporciona el IDE con:

- Una lista de las categorías que componen un grupo determinado

- Acceso a las instancias de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) que admite cada categoría dentro del grupo

- Nombres de grupo localizable

#### <a name="updating-the-ide"></a>Actualizando el IDE

El IDE guarda información acerca de la configuración de fuente y Color. Por lo tanto, después de cualquier modificación de la configuración de Color y fuente de IDE, lo que garantiza que la memoria caché está actualizada es una práctica recomendada.

Actualizando la memoria caché se realiza a través del [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaz y se pueden realizados elementos seleccionados globalmente o solo en.

### <a name="handling-font-and-color-changes"></a>Gestionar los cambios de fuente y color

Para admitir correctamente la coloración de texto que muestra un paquete VSPackage, el servicio de coloración compatible con el paquete VSPackage debe responder a los cambios iniciados por el usuario a través de la página de propiedades de fuentes y colores.

Para ello, un VSPackage debe:

- **controlar eventos generados por el IDE** implementando la [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) interfaz. El IDE llama al método apropiado siguiendo las modificaciones de usuario de la página fuentes y colores. Por ejemplo, llama a la [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) método si se selecciona una nueva fuente.

  **O**

- **sondear el IDE para cambios**. Esto puede hacerse a través del sistema implementado [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaz. Aunque principalmente por compatibilidad con la persistencia, el [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) método puede obtener la información de fuente y color para mostrar los elementos. Para obtener más información sobre la configuración de fuente y color, vea el artículo de MSDN [acceso a fuente de almacenados y la configuración de Color](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Para asegurarse de que los resultados de sondeo son correctos, use el [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaz para determinar si se necesitan un vaciado de la caché y la actualización antes de llamar a los métodos de recuperación de la [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaz.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrando la categoría de color y fuente personalizada sin necesidad de implementar interfaces

El ejemplo de código siguiente muestra cómo registrar la fuente personalizada y categoría de color sin necesidad de implementar las interfaces:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

En este ejemplo de código:

- `"NameID"` = el identificador de recurso del nombre de categoría localizados en el paquete
- `"ToolWindowPackage"` = GUID del paquete
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` es solo un ejemplo y el valor real puede ser un nuevo GUID proporcionado por el implementador.

### <a name="set-the-font-and-color-property-category-guid"></a>Establecer el Color y fuente propiedad GUID de categoría

El ejemplo de código siguiente muestra cómo establecer los GUID de categoría.

```csharp
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
