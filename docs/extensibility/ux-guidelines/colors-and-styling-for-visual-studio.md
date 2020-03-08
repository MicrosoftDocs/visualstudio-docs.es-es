---
title: Colores y estilos para Visual Studio | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408996"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colores y estilos para Visual Studio

## <a name="use-color-in-visual-studio"></a>Usar el color en Visual Studio

En Visual Studio, el color se usa principalmente como una herramienta de comunicación, no solo como decoración. Use el color mínima y Reserve este en situaciones en las que desee:

- Comunicar significado o afiliación (por ejemplo, modificadores de lenguaje o plataforma)

- Atraer la atención (por ejemplo, indica un cambio de estado)

- Mejorar la legibilidad y proporcionar puntos de referencia para navegar por la interfaz de usuario

- Aumentar la conveniencia

Existen varias opciones para asignar colores a los elementos de la interfaz de usuario en Visual Studio. A veces puede ser difícil averiguar qué opción se debe usar o cómo utilizarla correctamente. Este tema le ayudará a:

- Comprenda los distintos servicios y sistemas que se usan para definir los colores en Visual Studio.

- Seleccione la opción correcta para un elemento determinado.

- Use correctamente la opción que ha elegido.

> [!NOTE]
> Nunca codifique colores Hex, RGB o del sistema en los elementos de la interfaz de usuario. El uso de los servicios permite una mayor flexibilidad al ajustar el matiz. Además, sin el servicio, no podrá aprovechar las capacidades de cambio de tema del [servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para asignar colores a elementos de la interfaz de Visual Studio

Elija el método que mejor se adapte a los elementos de la interfaz de usuario.

| La interfaz de usuario | Método | ¿Qué son? |
| --- | --- | --- |
| Tiene cuadros de diálogo incrustados o independientes. | **Colores del sistema** | Nombres del sistema que permiten al sistema operativo definir el color y la apariencia de los elementos de la interfaz de usuario, como los controles de cuadro de diálogo comunes. |
| Tiene una interfaz de usuario personalizada que quiere que sea coherente con el entorno general de VS y tiene elementos de interfaz de usuario que coinciden con la categoría y el significado semántico de los tokens compartidos. | **Colores comunes compartidos** | Nombres de token de color predefinidos existentes para elementos específicos de la interfaz de usuario |
| Tiene una característica o un grupo de características individual y no hay ningún color compartido para elementos similares. | **Colores personalizados** | Nombres de tokens de color que son específicos de un área y no están diseñados para compartirse con otra interfaz de usuario |
| Desea permitir que el usuario final Personalice la interfaz de usuario o el contenido (por ejemplo, para editores de texto o ventanas de diseñador especializadas). | **Personalización del usuario final**<br /><br />**(Cuadro de diálogo herramientas &gt; opciones)** | Configuración definida en la página "fuentes y colores" del cuadro de diálogo **herramientas &gt; opciones** o en una página especializada específica de una característica de la interfaz de usuario. |

### <a name="visual-studio-themes"></a>Temas de Visual Studio

Visual Studio incluye tres temas de color diferentes: claro, oscuro y azul. También detecta el modo de contraste alto, que es un tema de color para todo el sistema diseñado para la accesibilidad.

A los usuarios se les pide que seleccionen un tema durante su primer uso de Visual Studio y puedan cambiar los temas más adelante. para ello, vaya a **herramientas &gt; opciones &gt; entorno &gt; general** y elija un nuevo tema en el menú desplegable "tema de color".

Los usuarios también pueden usar el panel de control para cambiar sus sistemas completos a uno de varios contraste alto temas. Si un usuario selecciona un tema de contraste alto, el selector de tema de color de Visual Studio ya no afecta a los colores de Visual Studio, aunque los cambios de tema se guardan para cuando el usuario sale de contraste alto modo. Para obtener más información sobre el modo de contraste alto, vea [elegir contraste alto colores](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>El servicio VSColor

Visual Studio proporciona un servicio de color del entorno, conocido como servicio VSColor, que le permite enlazar los valores de color de los elementos de la interfaz de usuario a una entrada con nombre que contenga valores de color para cada tema de Visual Studio. Esto garantiza que los colores cambien automáticamente para reflejar el tema seleccionado por el usuario actual o el modo de contraste alto del sistema. El uso del servicio significa que la implementación de todos los cambios de color relacionados con el tema se administra en un solo lugar y, si usa los colores compartidos comunes del servicio, la interfaz de usuario reflejará automáticamente los nuevos temas en versiones futuras de Visual Studio.

### <a name="implementation"></a>Implementación

El código fuente de Visual Studio incluye varios archivos de definición de paquete que contienen listas de nombres de token y los valores de color respectivos para cada tema. El servicio de color lee el VSColors definido en estos archivos de definición de paquete. Se hace referencia a estos colores en el marcado XAML o en el código y, a continuación, se cargan a través del método `IVsUIShell5.GetThemedColor` o de una asignación DynamicResource.

### <a name="system-colors"></a>Colores del sistema

Los controles comunes hacen referencia a los colores del sistema de forma predeterminada. Si desea que la interfaz de usuario Use los colores del sistema, como cuando se crea un diálogo incrustado o independiente, no es necesario hacer nada.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colores comunes compartidos en el servicio VSColor

Los elementos de la interfaz deben reflejar el entorno general de Visual Studio. Al reutilizar los colores compartidos comunes que son adecuados para el componente de interfaz de usuario que está diseñando, asegúrese de que la interfaz es coherente con otras interfaces de Visual Studio y que los colores se actualizarán automáticamente cuando se agreguen o actualicen temas.

Antes de usar los colores compartidos comunes, asegúrese de que sabe cómo usarlos correctamente. El uso incorrecto de los colores compartidos comunes puede dar lugar a una experiencia incoherente, frustrante o confusa para los usuarios.

### <a name="user-customizable-colors"></a>Colores personalizables por el usuario

Vea: [exponer colores para usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

A veces, querrá permitir que el usuario final Personalice la interfaz de usuario, como cuando se crea un editor de código o una superficie de diseño. Los componentes de interfaz de usuario personalizables se encuentran en la sección **fuentes y colores** del cuadro de diálogo **herramientas &gt; opciones** , donde los usuarios pueden elegir cambiar el color de primer plano, el color de fondo o ambos.

![Cuadro de diálogo herramientas &gt; opciones](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Cuadro de diálogo herramientas &gt; opciones

## <a name="BKMK_TheVSColorService"></a>El servicio VSColor

Visual Studio proporciona un servicio de color de entorno, también denominado servicio VSColor o servicio de color de Shell. Este servicio le permite enlazar los valores de color de los elementos de la interfaz de usuario a un conjunto de colores de nombre y valor que contiene colores para cada tema. El servicio VSColor se debe usar para todos los elementos de la interfaz de usuario, de modo que los colores cambien automáticamente para reflejar el tema seleccionado por el usuario actual, de modo que la interfaz de usuario enlazada al servicio de color del entorno se integre con nuevos temas en versiones futuras de Visual Studio.

### <a name="how-the-service-works"></a>Funcionamiento del servicio

El servicio de color del entorno Lee VSColors definido en el archivo. pkgdef para el componente de la interfaz de usuario. A estos VSColors se les hace referencia en el marcado XAML o en el código y se cargan a través de la `IVsUIShell5.GetThemedColor` o una asignación de `DynamicResource`.

![Arquitectura de servicio de color del entorno](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Arquitectura de servicio de color del entorno

### <a name="accessing-the-service"></a>Acceso al servicio

Hay varias maneras de tener acceso al servicio VSColor, en función del tipo de tokens de color que esté usando y del tipo de código que tenga.

#### <a name="predefined-environment-colors"></a>Colores predefinidos del entorno

##### <a name="from-native-code"></a>Desde código nativo

El Shell proporciona un servicio que proporciona acceso al `COLORREF` de los colores. La interfaz/servicio es:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

En el archivo VSShell80. idl, la enumeración `__VSSYSCOLOREX` tiene constantes de color de Shell. Para usarlo, pase como valor de índice uno de los valores de la `enum __VSSYSCOLOREX` documentada en MSDN o un número de índice normal que acepte la API del sistema de Windows, `GetSysColor`. De este modo, se devuelve el valor RGB del color que se debe usar en el segundo parámetro.

Si almacena un lápiz o un pincel con un nuevo color, debe `AdviseBroadcastMessages` (fuera de Visual Studio Shell) y escuchar los mensajes de `WM_SYSCOLORCHANGE` y `WM_THEMECHANGED`.

Para tener acceso al servicio de color en código nativo, realizará una llamada similar a esta:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Los `COLORREF` valores devueltos por `GetVSSysColorEx()` contienen solo los componentes R, G y B de un color del tema. Si una entrada de tema utiliza la transparencia, el valor del canal alfa se descarta antes de devolverse. Por lo tanto, si es necesario usar el color del entorno de interés en un lugar donde el canal de transparencia es importante, debe usar `IVsUIShell5.GetThemedColor` en lugar de `IVsUIShell2::GetVSSysColorEx`, como se describe más adelante en este tema.

##### <a name="from-managed-code"></a>Desde código administrado

El acceso al servicio VSColor a través de código nativo es bastante sencillo. Sin embargo, si está trabajando con código administrado, determinar cómo usar el servicio puede resultar complicado. Teniendo esto en cuenta, este es un C# fragmento de código que muestra este proceso:

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

Puede enlazar a los colores de Visual Studio a través de los valores exportados en la `ResourceDictionary`de la aplicación. A continuación se muestra un ejemplo del uso de recursos de la tabla de colores, así como el enlace a los datos de fuentes de entorno en XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Clases y métodos auxiliares para código administrado

En el caso de código administrado, la biblioteca de Managed Package Framework (`Microsoft.VisualStudio.Shell.12.0.dll`) del Shell contiene un par de clases auxiliares que facilitan el uso de los colores con los que se han importado.

Los métodos auxiliares de la clase `Microsoft.VisualStudio.Shell.VsColors` en MPF incluyen `GetThemedGDIColor()` y `GetThemedWPFColor()`. Estos métodos auxiliares devuelven el valor de color de una entrada de tema como `System.Drawing.Color` o `System.Windows.Media.Color`, que se usará en la interfaz de usuario de WinForms o WPF.

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

La clase también se puede usar para obtener los identificadores VSCOLOR para una clave de recurso de color WPF determinada, o viceversa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Los métodos de `VsColors` clase consultan el servicio VSColor para devolver el valor de color cada vez que se invocan. Para obtener un valor de color como `System.Drawing.Color`, una alternativa con un mejor rendimiento es usar en su lugar los métodos de la clase `Microsoft.VisualStudio.PlatformUI.VSThemeColor`, que almacena en memoria caché los valores de color obtenidos del servicio VSColor. La clase se suscribe internamente a los eventos de los mensajes de difusión de Shell y descarta el valor almacenado en caché cuando se produce un evento de cambio de tema. Además, la clase proporciona un. Evento compatible con NET para suscribirse a los cambios de tema. Use el evento `ThemeChanged` para agregar un nuevo controlador y use el método `GetThemedColor()` para obtener los valores de color para el `ThemeResourceKeys` de interés. Un código de ejemplo podría ser similar al siguiente:

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

## <a name="BKMK_ChoosingHighContrastColors"></a>Elegir contraste alto colores

### <a name="overview"></a>Información general

Windows usa varios temas de nivel de sistema de alto contraste que aumentan el contraste de color del texto, el fondo y las imágenes, lo que hace que los elementos parezcan más distintos en la pantalla. Por motivos de accesibilidad, es importante que los elementos de la interfaz de Visual Studio respondan correctamente cuando los usuarios cambien a un tema de contraste alto.

Solo se pueden usar un puñado de colores del sistema para contraste alto temas. Al elegir los nombres de colores del sistema, recuerde las siguientes sugerencias:

- **Elija los colores del sistema que tengan el mismo significado semántico** que el elemento al que va a colorear. Por ejemplo, si va a elegir un color de contraste alto para el texto dentro de una ventana, use WindowText y no ControlText.

- **Elija los pares de primer y segundo** plano juntos o no estará seguro de que su elección de color funcionará en todos los contraste alto temas.

- **Determine qué partes de la interfaz de usuario son las más importantes y asegúrese de que las áreas de contenido se destaquen.** Perderá muchos detalles que las sutiles diferencias en el matiz de color normalmente distinguirían, por lo que el uso de colores de borde fuertes es común para definir áreas de contenido, ya que no hay variantes de color para distintas áreas de contenido.

### <a name="system-color-set"></a>Conjunto de colores del sistema

La tabla en el [blog del equipo de WPF: referencia de SystemColors](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indica el conjunto completo de nombres de colores del sistema y los matices correspondientes que se muestran en cada tema.

Al aplicar este conjunto limitado de colores a la interfaz de usuario, *se espera que se pierdan los detalles sutiles que estaban presentes en los temas "normales"* . Este es un ejemplo de interfaz de usuario con colores de color gris sutiles que se usan para distinguir áreas dentro de una ventana de herramientas. Cuando se empareja con la misma ventana mostrada en el modo de contraste alto, puede ver que todos los niveles de fondo tienen el mismo matiz y que los bordes de esas áreas se indican solo con borde:

![Ejemplo de cómo se pierden los detalles sutiles en contraste alto](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Ejemplo de cómo se pierden los detalles sutiles en contraste alto

#### <a name="choosing-text-colors-in-an-editor"></a>Elegir colores de texto en un editor

El texto coloreado se usa en un editor o en una superficie de diseño para indicar el significado, como permitir la identificación sencilla de grupos de elementos similares. Sin embargo, en un tema de contraste alto, no tiene la capacidad de diferenciar entre más de tres colores de texto. WindowText, GrayText y HotTrackText son los únicos colores disponibles en las superficies de WindowBackground. Dado que no puede usar más de tres colores, elija cuidadosamente las diferencias más importantes que desea mostrar en el modo de contraste alto.

Matices para cada uno de los nombres de token permitidos en una superficie del editor, tal como aparecen en cada contraste alto tema:

![Comparación del editor de contraste alto](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparación de editor de contraste alto

Ejemplos de la superficie del editor en el tema azul:

![Editor en el tema azul](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor en el tema azul

![Editor en contraste alto tema de #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor en contraste alto tema de #1

### <a name="usage-patterns"></a>Patrones de uso

Muchos elementos de interfaz de usuario comunes ya tienen colores contraste alto definidos. Puede hacer referencia a estos patrones de uso al elegir sus propios nombres de colores del sistema, de modo que los elementos de la interfaz de usuario sean coherentes con componentes similares.

| Color del sistema | Uso |
| --- | --- |
| ActiveCaption | -Glifos de botón de ventana del IDE activo y de espacio compartido al mantener el mouse y presionar<br />-Fondo de la barra de título para las ventanas IDE y de espacio compartido<br />-Fondo de la barra de estado predeterminada |
| ActiveCaptionText | -IDE activo y ventanas de espacio compartido para el primer plano de la barra de título (texto y glifos)<br />-Fondo y borde de los botones de la ventana activa al mantener el mouse y presionar |
| Control | -Cuadro combinado, lista desplegable y fondo deshabilitado y predeterminado del control de búsqueda, incluido el botón desplegable<br />-Fondo del botón de destino de acoplamiento<br />-Fondo de la barra de comandos<br />-Fondo de la ventana de herramientas |
| ControlDark | -Fondo del IDE<br />-Separadores de menús y barras de comandos<br />-Borde de la barra de comandos<br />-Sombras del menú<br />-Pestaña de la ventana de herramientas y borde y separador de desplazamiento<br />-Fondo del botón de desbordamiento de documento<br />-Borde del glifo de destino de acoplamiento |
| ControlDarkDark |-Ventana de pestaña de documento seleccionada: sin foco |
| ControlLight |-Borde de la pestaña de ocultar automáticamente<br />-Cuadro combinado y borde de la lista desplegable<br />-Fondo y borde del destino de acoplamiento |
| ControlLightLight | -Seleccionado, borde provisional centrado |
| ControlText | -Cuadro combinado y glifo de la lista desplegable<br />-Texto de la pestaña de la ventana de herramientas no seleccionada |
| GrayText |-Cuadro combinado y lista desplegable borde deshabilitado, glifo desplegable, texto y texto del elemento de menú<br />-Texto de menú deshabilitado<br />-Texto de encabezado de "opciones de búsqueda" del control de búsqueda<br />-Separador de sección de control de búsqueda |
| Resaltar | -Todos los fondos y bordes presionados, excepto el botón desplegable del cuadro combinado y el borde del botón de desbordamiento del documento<br />-El fondo de los elementos seleccionados |
| HighlightText | -Todos los desplazamientos y presionados (texto y glifos)<br />Ventana de herramientas centrada en el control ventana de pestaña y documento<br />Borde de la barra de título de la ventana de herramientas enfocada<br />-Centrado, seleccionado en primer plano en la pestaña provisional<br />-Borde del botón de desbordamiento de documento al mantener el mouse y presionar<br />-Borde del icono seleccionado|
| HotTrack | -Fondo y borde del control de posición de la barra de desplazamiento al presionar<br />-Glifo de flecha de la barra de desplazamiento al presionar |
| InactiveCaption | -Glifos de botón de ventana del IDE inactivo y de espacio compartido al mantener el mouse<br />-Fondo de la barra de título para las ventanas IDE y de espacio compartido<br />-Fondo del control de búsqueda deshabilitado |
| InactiveCaptionText | -El IDE inactivo y la barra de título de Windows en primer plano (texto y glifos)<br />-Fondo y borde de botones de ventana inactivos al mantener el mouse<br />-Fondo y borde del botón de la ventana de herramientas sin foco<br />-Deshabilitar el control de búsqueda en primer plano |
| Menú | -Fondo del menú desplegable<br />-Fondo de marca de verificación activada y deshabilitada |
| MenuText | -Borde del menú desplegable<br />-Marcas de verificación<br />-Glifos de menú<br />-Texto de menú desplegable<br />-Borde del icono seleccionado |
| Barra de desplazamiento | -La barra de desplazamiento y el fondo de la flecha de la barra de desplazamiento, todos los Estados |
| Periodo | -Fondo de la pestaña de ocultar automáticamente<br />-Barra de menús y fondo de estante de comando<br />-Fondo de pestaña de la ventana de documento no enfocado o no seleccionado y borde del documento, para las pestañas abrir y provisional<br />-Fondo de la barra de título de la ventana de herramientas sin foco<br />-Fondo de pestaña de la ventana de herramientas, ambos seleccionados y no seleccionados |
| WindowFrame | -Borde del IDE |
| WindowText | -Ocultar automáticamente el primer plano de la pestaña<br />-Cuadro de la pestaña de la ventana de herramientas seleccionada<br />-Pestaña de la ventana de documento sin foco y no enfocada o no seleccionada en primer plano de la pestaña provisional<br />-Vista de árbol predeterminada en primer plano y mantener el mouse sobre el glifo no seleccionado<br />-Borde de pestaña seleccionado de la ventana de herramientas<br />-Fondo del control de posición de la barra de desplazamiento, borde y glifo |

## <a name="BKMK_ExposingColorsForEndUsers"></a>Exposición de los colores de los usuarios finales

### <a name="overview"></a>Información general

A veces querrá permitir que el usuario final Personalice la interfaz de usuario, como cuando se crea un editor de código o una superficie de diseño. La forma más común de hacerlo es mediante el cuadro de diálogo **herramientas &gt; opciones** . A menos que tenga una interfaz de usuario muy especializada que requiera controles especiales, la forma más fácil de presentar la personalización es a través de la página **fuentes y colores** de la sección **entorno** del cuadro de diálogo. Para cada elemento que exponga para la personalización, el usuario puede elegir cambiar el color de primer plano, el color de fondo o ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Compilar un VSPackage para los colores personalizables

Un VSPackage puede controlar las fuentes y los colores a través de las categorías personalizadas y mostrar los elementos en la página de propiedades fuentes y colores. Al utilizar este mecanismo, los VSPackages deben implementar la interfaz [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) y sus interfaces asociadas.

En principio, este mecanismo se puede usar para modificar todos los elementos de presentación existentes y las categorías que los contienen. Sin embargo, no debe usarse para modificar la categoría editor de texto o sus elementos para mostrar. Para obtener más información sobre la categoría editor de texto, consulte [información general sobre fuentes y colores](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Para implementar categorías personalizadas o mostrar los elementos, un VSPackage debe:

- **Cree o identifique categorías en el registro.** La implementación del IDE de la página de propiedades **fuentes y colores** usa esta información para consultar correctamente el servicio que admite una categoría determinada.

- **Cree o identifique grupos en el registro (opcional).** Puede ser útil definir un grupo, que representa la Unión de dos o más categorías. Si se define un grupo, el IDE combina automáticamente las subcategorías y distribuye los elementos que se muestran dentro del grupo.

- **Implementar la compatibilidad con el IDE.**

- **Controlar los cambios de fuente y color.**

#### <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías

Construya un tipo especial de entrada de registro de categoría en `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` donde `<Category>` es el nombre no traducido de la categoría.

Rellene el registro con dos valores:

| Nombre | Tipo | data | Descripción |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | GUID creado para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio VSPackage que admite la categoría |

 El servicio especificado en el registro debe proporcionar una implementación de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) para la categoría correspondiente.

#### <a name="to-create-or-identify-groups"></a>Para crear o identificar grupos

Construya un tipo especial de entrada de registro de categoría en `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` donde `<group>` es el nombre no traducido del grupo.

Rellene el registro con dos valores:

| Nombre | Tipo | data | Descripción |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | GUID creado para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio VSPackage que admite la categoría |

El servicio especificado en el registro debe proporcionar una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> para el grupo correspondiente.

![Implementación de encontrar](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementación de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Para implementar la compatibilidad con IDE

Implemente [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), que devuelve una interfaz [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) o una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> al IDE por cada categoría o grupo GUID proporcionado.

Para cada categoría que admite, un VSPackage implementa una instancia independiente de la interfaz [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) .

Los métodos implementados a través de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) deben proporcionar el IDE con:

- Listas de mostrar los elementos de la categoría

- Nombres localizables para mostrar elementos

- Mostrar información para cada miembro de la categoría

> [!NOTE]
> Cada categoría debe contener al menos un elemento de presentación.

El IDE usa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> para definir una Unión de varias categorías.

Su implementación proporciona el IDE con:

- Una lista de las categorías que componen un grupo determinado

- Acceso a las instancias de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) que admiten cada categoría del grupo

- Nombres de grupos localizables

#### <a name="updating-the-ide"></a>Actualización del IDE

El IDE almacena en caché información acerca de la configuración de fuente y color. Por lo tanto, después de cualquier modificación de la configuración de fuente y color del IDE, se recomienda asegurarse de que la memoria caché está actualizada.

La actualización de la memoria caché se realiza a través de la interfaz [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) y puede realizarse globalmente o solo en los elementos seleccionados.

### <a name="handling-font-and-color-changes"></a>Controlar los cambios de fuente y color

Para admitir correctamente la coloración del texto que muestra un VSPackage, el servicio de coloración que admite el VSPackage debe responder a los cambios iniciados por el usuario realizados a través de la página de propiedades fuentes y colores.

Para ello, un VSPackage debe:

- **controlar los eventos generados** por el IDE implementando la interfaz [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) . El IDE llama al método adecuado después de las modificaciones del usuario de la página fuentes y colores. Por ejemplo, llama al método [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) si se selecciona una nueva fuente.

  **OR**

- **sondee los cambios en el IDE**. Esto puede realizarse a través de la interfaz [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implementada por el sistema. Aunque principalmente para la compatibilidad con la persistencia, el método [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) puede obtener información de fuente y color para mostrar los elementos. Para obtener más información sobre la configuración de fuente y color, vea el artículo de MSDN [acceso a la configuración de fuente y color almacenados](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Para asegurarse de que los resultados del sondeo son correctos, use la interfaz [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) para determinar si es necesario un vaciado de caché y una actualización antes de llamar a los métodos de recuperación de la interfaz [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) .

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrar la categoría personalizada de fuentes y colores sin implementar interfaces

En el ejemplo de código siguiente se muestra cómo registrar la categoría de color y fuente personalizada sin implementar interfaces:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

En este ejemplo de código:

- `"NameID"` = el identificador de recurso del nombre de categoría adaptado en el paquete
- `"ToolWindowPackage"` = GUID del paquete
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` es simplemente un ejemplo y el valor real puede ser un GUID nuevo proporcionado por el implementador.

### <a name="set-the-font-and-color-property-category-guid"></a>Establecer el GUID de la categoría de propiedad Font y color

En el ejemplo de código siguiente se muestra cómo establecer los GUID de categoría.

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
