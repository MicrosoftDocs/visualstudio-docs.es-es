---
title: Colores y estilo sin estilo para Visual Studio Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c7d8a02de9331f268cd06ad35e19faab6494fe0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699852"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colores y estilos para Visual Studio

## <a name="use-color-in-visual-studio"></a>Usar color en Visual Studio

En Visual Studio, el color se usa principalmente como una herramienta de comunicación, no solo como decoración. Utilice el color mínimamente y reservelo para situaciones en las que desee:

- Comunicar significado o afiliación (por ejemplo, modificadores de plataforma o idioma)

- Atraer la atención (por ejemplo, indicando un cambio de estado)

- Mejorar la legibilidad y proporcionar puntos de referencia para navegar por la interfaz de usuario

- Aumentar la deseabilidad

Existen varias opciones para asignar colores a elementos de interfaz de usuario en Visual Studio. A veces puede ser difícil averiguar qué opción se supone que debes usar o cómo usarla correctamente. Este tema le ayudará a:

- Comprender los diferentes servicios y sistemas utilizados para definir colores en Visual Studio.

- Seleccione la opción correcta para un elemento determinado.

- Utilice correctamente la opción que ha elegido.

> [!NOTE]
> Nunca codifique los colores hexadecimales, RGB o del sistema a los elementos de la interfaz de usuario. El uso de los servicios permite flexibilidad en el tono de afinación. Además, sin el servicio, no podrá aprovechar las capacidades de conmutación de temas [del servicio VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para asignar color a elementos de interfaz de Visual Studio

Elija el método que mejor se adapte a los elementos de la interfaz de usuario.

| Tu interfaz de usuario | Método | ¿Qué son? |
| --- | --- | --- |
| Tiene cuadros de diálogo incrustados o independientes. | **Colores del sistema** | Nombres de sistema que permiten al sistema operativo definir el color y la apariencia de los elementos de la interfaz de usuario, como los controles de cuadro de diálogo comunes. |
| Tiene una interfaz de usuario personalizada que desea que sea coherente con el entorno VS general y tiene elementos de interfaz de usuario que coinciden con la categoría y el significado semántico de los tokens compartidos. | **Colores compartidos comunes** | Nombres de token de color predefinidos existentes para elementos específicos de la interfaz de usuario |
| Tiene una entidad o grupo de entidades individual y no hay ningún color compartido para elementos similares. | **Colores personalizados** | Nombres de token de color que son específicos de un área y no están destinados a compartirse con otra interfaz de usuario |
| Desea permitir que el usuario final personalice la interfaz de usuario o el contenido (por ejemplo, para editores de texto o ventanas de diseñador especializadas). | **Personalización del usuario final**<br /><br />**(diálogo &gt; Opciones de herramientas)** | Configuración definida en la página "Fuentes y colores" del cuadro de diálogo ** &gt; Opciones** de herramientas o en una página especializada específica de una característica de interfaz de usuario. |

### <a name="visual-studio-themes"></a>Temas de Visual Studio

Visual Studio presenta tres temas de color diferentes: claro, oscuro y azul. También detecta el modo de alto contraste, que es un tema de color de todo el sistema diseñado para la accesibilidad.

Se pide a los usuarios que seleccionen un tema durante su primer uso de Visual Studio y podrán cambiar de tema más adelante yendo a **Opciones &gt; &gt; &gt; ** de herramientas Entorno general y eligiendo un nuevo tema en el menú desplegable "tema de color".

Los usuarios también pueden utilizar el Panel de control para cambiar todos sus sistemas en uno de varios temas de alto contraste. Si un usuario selecciona un tema de contraste alto, el selector de tema de color de Visual Studio ya no afecta a los colores en Visual Studio, aunque los cambios de tema se guardan para cuando el usuario sale del modo de contraste alto. Para obtener más información sobre el modo contraste alto, consulte [Elegir colores](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)de contraste alto .

### <a name="the-vscolor-service"></a>El servicio VSColor

Visual Studio proporciona un servicio de color de entorno, conocido como el servicio VSColor, que permite enlazar los valores de color de los elementos de interfaz de usuario a una entrada con nombre que contiene valores de color para cada tema de Visual Studio. Esto garantiza que los colores cambiarán automáticamente para reflejar el tema seleccionado por el usuario actual o el modo de contraste alto del sistema. El uso del servicio significa que la implementación de todos los cambios de color relacionados con el tema se controla en un solo lugar y, si usa colores compartidos comunes del servicio, la interfaz de usuario reflejará automáticamente nuevos temas en versiones futuras de Visual Studio.

### <a name="implementation"></a>Implementación

El código fuente de Visual Studio incluye varios archivos de definición de paquete que contienen listas de nombres de token y los valores de color respectivos para cada tema. El servicio de color lee los VSColors definidos en estos archivos de definición de paquete. Se hace referencia a estos colores en el `IVsUIShell5.GetThemedColor` marcado XAML o en el código y, a continuación, se cargan a través del método o una asignación DynamicResource.

### <a name="system-colors"></a>Colores del sistema

Los controles comunes hacen referencia a los colores del sistema de forma predeterminada. Si desea que la interfaz de usuario use colores del sistema, como cuando está creando un cuadro de diálogo incrustado o independiente, no es necesario hacer nada.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colores compartidos comunes en el servicio VSColor

Los elementos de la interfaz deben reflejar el entorno general de Visual Studio. Al reutilizar los colores compartidos comunes que son adecuados para el componente de interfaz de usuario que está diseñando, se asegura de que la interfaz es coherente con otras interfaces de Visual Studio y que los colores se actualizarán automáticamente cuando se agreguen o actualicen temas.

Antes de usar colores compartidos comunes, asegúrese de entender cómo usarlos correctamente. El uso incorrecto de colores compartidos comunes puede dar lugar a una experiencia incoherente, frustrante o confusa para los usuarios.

### <a name="user-customizable-colors"></a>Colores personalizables por el usuario

Consulte: [Exposición de colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

A veces, querrá permitir que el usuario final personalice la interfaz de usuario, como cuando está creando un editor de código o una superficie de diseño. Los componentes de interfaz de usuario personalizables se encuentran en la sección **Fuentes y colores** del cuadro de diálogo ** &gt; Opciones** de herramientas, donde los usuarios pueden elegir cambiar el color de primer plano, el color de fondo o ambos.

![Cuadro &gt; de diálogo Opciones de herramientas](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Cuadro &gt; de diálogo Opciones de herramientas

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>El servicio VSColor

Visual Studio proporciona un servicio de color de entorno, también denominado el servicio VSColor o el servicio de color de shell. Este servicio le permite enlazar los valores de color de los elementos de la interfaz de usuario a un conjunto de colores nombre-valor que contiene colores para cada tema. El servicio VSColor se debe usar para todos los elementos de la interfaz de usuario, de modo que los colores cambien automáticamente para reflejar el tema seleccionado por el usuario actual y para que la interfaz de usuario enlazada al servicio de color del entorno se integre con nuevos temas en versiones futuras de Visual Studio.

### <a name="how-the-service-works"></a>Funcionamiento del servicio

El servicio de color de entorno lee VSColors definidos en el .pkgdef para el componente de interfaz de usuario. A continuación, se hace referencia a estos VSColors `IVsUIShell5.GetThemedColor` en `DynamicResource` el código o marcado XAML y se cargan a través de la asignación o una.

![Arquitectura de servicio de color del entorno](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Arquitectura de servicio de color del entorno

### <a name="accessing-the-service"></a>Acceso al servicio

Hay varias maneras diferentes de tener acceso al servicio VSColor, dependiendo del tipo de tokens de color que esté utilizando y qué tipo de código tiene.

#### <a name="predefined-environment-colors"></a>Colores predefinidos del entorno

##### <a name="from-native-code"></a>Desde código nativo

El shell proporciona un servicio `COLORREF` que da acceso a los colores. El servicio/interfaz es:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

En el archivo VSShell80.idl, la enumeración `__VSSYSCOLOREX` tiene constantes de color de shell. Para usarlo, pase como valor de índice uno `enum __VSSYSCOLOREX` de los valores del documentado en MSDN `GetSysColor`o un número de índice normal que la API del sistema de Windows, , acepta. Al hacerlo, se recupera el valor RGB del color que se debe utilizar en el segundo parámetro.

Si almacena un lápiz o pincel con `AdviseBroadcastMessages` un nuevo color, debe (fuera del shell de Visual Studio) y escuchar `WM_SYSCOLORCHANGE` y `WM_THEMECHANGED` mensajes.

Para tener acceso al servicio de color en código nativo, hará una llamada similar a esta:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Los `COLORREF` valores `GetVSSysColorEx()` devueltos por contienen sólo componentes R,G,B de un color de tema. Si una entrada de tema utiliza transparencia, el valor de canal alfa se descarta antes de devolver. Por lo tanto, si el color del entorno de interés debe utilizarse en un lugar donde el canal de transparencia es importante, debe usar `IVsUIShell5.GetThemedColor` en lugar de `IVsUIShell2::GetVSSysColorEx`, como se describe más adelante en este tema.

##### <a name="from-managed-code"></a>Desde código administrado

El acceso al servicio VSColor a través de código nativo es bastante sencillo. Sin embargo, si está trabajando a través de código administrado, determinar cómo usar el servicio puede ser complicado. Teniendo esto en cuenta, aquí hay un fragmento de código de C- que demuestra este proceso:

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

Si está trabajando en Visual Basic, utilice:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Desde la interfaz de usuario de WPF

Puede enlazar a colores de Visual Studio `ResourceDictionary`a través de valores exportados a la aplicación . A continuación se muestra un ejemplo del uso de recursos de la tabla de colores, así como el enlace a los datos de fuente de entorno en XAML.

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

Para el código administrado, la biblioteca`Microsoft.VisualStudio.Shell.12.0.dll`de Managed Package Framework del shell ( ) contiene un par de clases auxiliares que facilitan el uso de colores temáticos.

Los métodos `Microsoft.VisualStudio.Shell.VsColors` auxiliares de `GetThemedGDIColor()` la `GetThemedWPFColor()`clase en MPF incluyen y . Esos métodos auxiliares devuelven el `System.Drawing.Color` valor `System.Windows.Media.Color`de color de una entrada de tema como o , que se usará en WinForms o WPF WPF UI.

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

La clase también se puede usar para obtener identificadores VSCOLOR para una clave de recurso de color WPFWPF determinada, o viceversa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Los métodos de `VsColors` clase consultan el servicio VSColor para devolver el valor de color cada vez que se invocan. Para obtener un `System.Drawing.Color`valor de color como , una alternativa `Microsoft.VisualStudio.PlatformUI.VSThemeColor` con un mejor rendimiento es utilizar en su lugar los métodos de la clase, que almacena en caché los valores de color obtenidos del servicio VSColor. La clase se suscribe internamente a los eventos de mensajes de difusión de shell y descarta el valor almacenado en caché cuando se produce un evento de cambio de tema. Además, la clase proporciona un archivo . Evento compatible con NET para suscribirse a los cambios de tema. Utilice `ThemeChanged` el evento para agregar un `GetThemedColor()` nuevo controlador y use `ThemeResourceKeys` el método para obtener valores de color para el de interés. Un código de ejemplo podría tener este aspecto:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Elegir colores de alto contraste

### <a name="overview"></a>Información general

Windows utiliza varios temas de alto contraste a nivel del sistema que aumentan el contraste de color del texto, los fondos y las imágenes, lo que hace que los elementos parezcan más distintos en la pantalla. Por razones de accesibilidad, es importante que los elementos de la interfaz de Visual Studio respondan correctamente cuando los usuarios cambian a un tema de contraste alto.

Solo se pueden utilizar un puñado de colores del sistema para temas de alto contraste. Al elegir los nombres de color del sistema, recuerde los siguientes consejos:

- **Elija los colores del sistema que tengan el mismo significado semántico** que el elemento que está coloreando. Por ejemplo, si elige un color de alto contraste para el texto dentro de una ventana, utilice WindowText y no ControlText.

- **Elija pares de primer plano/fondo** juntos o no estará seguro de que su elección de color funcionará en todos los temas de alto contraste.

- Determina qué partes de la interfaz de usuario son las más importantes y asegúrate de que las áreas de **contenido destaquen.** Perderá sin muchos detalles que las diferencias sutiles en el tono de color normalmente distinguirían, por lo que el uso de colores de borde fuertes es común para definir áreas de contenido, porque no hay variantes de color para diferentes áreas de contenido.

### <a name="system-color-set"></a>Conjunto de colores del sistema

La tabla en [WPF Team Blog: SystemColors Reference](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) indica el conjunto completo de nombres de color del sistema y los tonos correspondientes que se muestran en cada tema.

Al aplicar este conjunto limitado de colores a la interfaz de usuario, *se espera que pierda detalles sutiles que estaban presentes en los temas "normales".* Este es un ejemplo de la interfaz de usuario con colores grises sutiles que se utilizan para distinguir áreas dentro de una ventana de herramientas. Cuando se empareja con la misma ventana que se muestra en el modo de contraste alto, puede ver que todos los fondos son del mismo tono y los bordes de esas áreas se indican solo por borde:

![Ejemplo de cómo se pierden detalles sutiles en Contraste Alto](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Ejemplo de cómo se pierden detalles sutiles en Contraste Alto

#### <a name="choosing-text-colors-in-an-editor"></a>Elegir colores de texto en un editor

El texto coloreado se utiliza en un editor o en una superficie de diseño para indicar significado, como permitir una fácil identificación de grupos de elementos similares. En un tema de contraste alto, sin embargo, no tiene la capacidad de diferenciar entre más de tres colores de texto. WindowText, GrayText y HotTrackText son los únicos colores disponibles en las superficies WindowBackground. Puesto que no puede utilizar más de tres colores, elija cuidadosamente las diferencias más importantes que desea mostrar en el modo de contraste alto.

Tonos para cada uno de los nombres de token permitidos en una superficie del editor, tal como aparecen en cada tema de contraste alto:

![Comparación de editor de contraste alto](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparación de editor de contraste alto

Ejemplos de la superficie del editor en el tema Azul:

![Editor en el tema azul](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor en el tema azul

![Editor en tema #1 de alto contraste](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor en tema #1 de alto contraste

### <a name="usage-patterns"></a>Patrones de uso

Muchos elementos comunes de la interfaz de usuario ya tienen colores de contraste alto definidos. Puede hacer referencia a estos patrones de uso al elegir sus propios nombres de color del sistema, de modo que los elementos de la interfaz de usuario sean coherentes con componentes similares.

| Color del sistema | Uso |
| --- | --- |
| ActiveCaption | - IDE activo y glifos de botón de ventana en balsa al pasar el ratón y pulse<br />- Fondo de la barra de título para IDE y ventanas en balsa<br />- Fondo de la barra de estado predeterminada |
| ActiveCaptionText | - IDE activo y ventanas en balsadas para el primer plano de la barra de título (texto y glifos)<br />- Fondo y borde de los botones de la ventana activa al pasar el ratón y pulse |
| Control | - Cuadro combinado, lista desplegable, y el control de búsqueda por defecto y el fondo deshabilitado, incluyendo el botón desplegable<br />- Fondo del botón de destino del muelle<br />- Fondo de la barra de comandos<br />- Fondo de la ventana de la herramienta |
| ControlDark | - Antecedentes IDE<br />- Separadores de menú y barra de comandos<br />- Borde de la barra de comandos<br />- Sombras de menú<br />- Ventana de herramientas pestaña por defecto y pasar el ratón borde y separador<br />- Documento bien desbordado botón de fondo<br />- Borde del glifo objetivo del muelle |
| ControlDarkDark |- Desenfocado, ventana de la pestaña del documento seleccionado |
| ControlLight |- Ocultar automáticamente el borde de la pestaña<br />- Caja combinada y borde de lista desplegable<br />- Fondo y borde del objetivo del muelle |
| ControlLightLight | - Frontera provisional seleccionada y enfocada |
| ControlText | - Cuadro combinado y glifo de lista desplegable<br />- Ventana de herramientas de texto de pestaña no seleccionado |
| GrayText |- Cuadro combinado y lista desplegable de borde deshabilitado, glifo desplegable, texto y texto del elemento de menú<br />- Texto del menú deshabilitado<br />- Control de búsqueda 'opciones de búsqueda' texto de encabezado<br />- Separador de sección de control de búsqueda |
| Resaltar | - Todos los fondos y bordes flotantes y presionados, excepto el fondo del botón desplegable del cuadro combinado y el borde del botón de desbordamiento del documento bien<br />- Fondos de elementos seleccionados |
| HighlightText | - Todos los primeros planos flotantes y presionados (texto y glifos)<br />- Ventana de herramientas enfocada y control de la ventana de la pestaña del documento en primer plano<br />- Borde de la barra de título de la ventana de herramientas enfocada<br />- Enfocado, seleccionado en primer plano de la pestaña provisional<br />- Documentar bien borde del botón de desbordamiento en el hover y pulse<br />- Borde de icono seleccionado|
| HotTrack | - Desplazamiento de fondo del pulgar de la barra y borde en la prensa<br />- Glifo de flecha de barra de desplazamiento al presionar |
| InactiveCaption | - IDE inactivo y glifos de botón de ventana en balsa al pasar el ratón<br />- Fondo de la barra de título para IDE y ventanas en balsa<br />- Fondo de control de búsqueda deshabilitado |
| InactiveCaptionText | - IDE inactivo y ventanas en balsadas en primer plano de la barra de título (texto y glifos)<br />- Botones de ventana inactivos fondo y borde al pasar el ratón<br />- Desenfocado el fondo del botón de la ventana de la herramienta y el borde<br />- Pretexto de control de búsqueda deshabilitado |
| Menú | - Fondo del menú desplegable<br />- Fondo de la marca de verificación marcada marcada y desactivada |
| MenuText | - Borde del menú desplegable<br />- Marcas de verificación<br />- Menú glifos<br />- Texto del menú desplegable<br />- Borde de icono seleccionado |
| Barra de desplazamiento | - Barra de desplazamiento y fondo de flecha de la barra de desplazamiento, todos los estados |
| Periodo | - Ocultar automáticamente el fondo de la pestaña<br />- Barra de menús y fondo de estante de comandos<br />- Fondo de pestaña de la ventana del documento desenfocado o no seleccionado y borde del documento, tanto para las pestañas abiertas como para las provisionales<br />- Fondo de la barra de título de la ventana de herramientas desenfocada<br />- Fondo de la pestaña de la ventana de la herramienta, tanto seleccionado como no seleccionado |
| WindowFrame | - Borde IDE |
| WindowText | - Ocultar automáticamente el primer plano de la pestaña<br />- Seleccionado en primer plano de la pestaña de la ventana de herramientas<br />- Pestaña de la ventana del documento desenfocada y desenfocado o no seleccionado en primer plano de la pestaña provisional<br />- Vista de árbol por defecto de primer plano y pasar el ratón sobre el glifo no seleccionado<br />- Ventana de herramientas seleccionada borde de la pestaña<br />- Fondo del pulgar de la barra de desplazamiento, borde y glifo |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Exposición de colores para los usuarios finales

### <a name="overview"></a>Información general

A veces querrá permitir que el usuario final personalice la interfaz de usuario, como cuando crea un editor de código o una superficie de diseño. La forma más común de hacerlo es mediante el cuadro de diálogo ** &gt; Opciones** de herramientas. A menos que tenga una interfaz de usuario altamente especializada que requiera controles especiales, la forma más fácil de presentar la personalización es a través de la página **Fuentes y colores** dentro de la sección **Entorno** del cuadro de diálogo. Para cada elemento que expone para la personalización, el usuario puede elegir cambiar el color de primer plano, el color de fondo o ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creación de un VSPackage para sus colores personalizables

Un VSPackage puede controlar las fuentes y colores a través de categorías personalizadas y mostrar elementos en el fuentes y colores página de propiedad. Al usar este mecanismo, VSPackages debe implementar el [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) interfaz y sus interfaces asociadas.

En principio, este mecanismo se puede utilizar para modificar todos los elementos de visualización existentes y las categorías que los contienen. Sin embargo, no se debe utilizar para modificar la categoría Editor de texto o sus elementos de visualización. Para obtener más información sobre la categoría Editor de texto, consulte Información general sobre [fuentes y colores](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Para implementar categorías personalizadas o mostrar elementos, un VSPackage debe:

- **Crear o identificar categorías en el registro.** La implementación del IDE de la página de propiedades **Fuentes y colores** usa esta información para consultar correctamente el servicio que admite una categoría determinada.

- **Crear o identificar grupos en el registro (opcional).** Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE combina automáticamente subcategorías y distribuye elementos de visualización dentro del grupo.

- **Implementar compatibilidad con IDE.**

- **Controle los cambios de fuente y color.**

#### <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías

Construya un tipo especial de `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` `<Category>` entrada de registro de categoría en donde está el nombre no localizado de la categoría.

Rellene el registro con dos valores:

| Nombre | Tipo | data | Descripción |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Guid creado para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio VSPackage que admite la categoría |

 El servicio especificado en el registro debe proporcionar una implementación de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) para la categoría correspondiente.

#### <a name="to-create-or-identify-groups"></a>Para crear o identificar grupos

Construya un tipo especial de `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` `<group>` entrada de registro de categoría en donde está el nombre no localizado del grupo.

Rellene el registro con dos valores:

| Nombre | Tipo | data | Descripción |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Guid creado para identificar la categoría |
| Paquete | REG_SZ | GUID | El GUID del servicio VSPackage que admite la categoría |

El servicio especificado en el registro <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> debe proporcionar una implementación del grupo correspondiente.

![Implementación de IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementación de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Para implementar la compatibilidad con IDE

Implementar [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), que devuelve un [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaz o una <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaz al IDE para cada categoría o grupo GUID proporcionado.

Para cada categoría que admite, un VSPackage implementa una instancia independiente de la [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) interfaz.

Los métodos implementados a través de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) deben proporcionar el IDE con:

- Listas de elementos de visualización en la categoría

- Nombres localizables para elementos de visualización

- Mostrar información para cada miembro de la categoría

> [!NOTE]
> Cada categoría debe contener al menos un elemento de visualización.

El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> utiliza la interfaz para definir una unión de varias categorías.

Su implementación proporciona al IDE:

- Una lista de las categorías que componen un grupo determinado

- Acceso a instancias de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) que admiten cada categoría dentro del grupo

- Nombres de grupos localizables

#### <a name="updating-the-ide"></a>Actualización del IDE

El IDE almacena en caché información sobre la configuración de fuente y color. Por lo tanto, después de cualquier modificación de la configuración de fuente y color IDE, asegurarse de que la memoria caché está actualizada es una práctica recomendada.

La actualización de la memoria caché se realiza a través de la [ivsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaz y se puede realizar globalmente o simplemente en los elementos seleccionados.

### <a name="handling-font-and-color-changes"></a>Manejo de cambios de fuente y color

Para admitir correctamente la coloración del texto que muestra un VSPackage, el servicio de coloración que admite el VSPackage debe responder a los cambios iniciados por el usuario realizados a través de la fuentes y colores página de propiedades.

Para ello, un VSPackage debe:

- **Controlar eventos generados** por IDE mediante la implementación de la [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) interfaz. El IDE llama al método adecuado después de las modificaciones del usuario de la fuentes y colores página. Por ejemplo, llama al método [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) si se selecciona una nueva fuente.

  **O**

- **sondear el IDE en busca**de cambios . Esto se puede hacer a través de la interfaz [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implementada por el sistema. Aunque principalmente para admitir la persistencia, el [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) método puede obtener información de fuente y color para mostrar elementos. Para obtener más información sobre la configuración de fuentes y colores, consulte el artículo de MSDN Acceso a la configuración de [fuente almacenada y color](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015).

> [!NOTE]
> Para asegurarse de que los resultados de sondeo son correctos, utilice el [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) interfaz para determinar si se necesita un vaciado de caché y actualización antes de llamar a los métodos de recuperación de la [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) interfaz.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registro de fuente personalizada y categoría de color sin implementar interfaces

En el ejemplo de código siguiente se muestra cómo registrar la fuente personalizada y la categoría de color sin implementar interfaces:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Para este ejemplo de código:

- `"NameID"`• el identificador de recurso del nombre de categoría localizado en el paquete
- `"ToolWindowPackage"`• GUID del paquete
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`es sólo un ejemplo y el valor real puede ser un nuevo GUID proporcionado por el implementador.

### <a name="set-the-font-and-color-property-category-guid"></a>Establezca el GUID de la categoría de propiedades Fuente y Color

En el ejemplo de código siguiente se muestra cómo establecer GUID de categoría.

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
