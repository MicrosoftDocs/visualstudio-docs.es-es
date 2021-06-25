---
title: Colores y estilos para Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio usuario usa el color como herramienta de comunicación, en lugar de por motivos puramente éticos.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 307a4013c06258524c60619c6eff40e4d64740b6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904492"
---
# <a name="colors-and-styling-for-visual-studio"></a>Colores y estilos para Visual Studio

## <a name="use-color-in-visual-studio"></a>Usar color en Visual Studio

En Visual Studio, el color se usa principalmente como herramienta de comunicación, no solo como decoración. Use el color mínimamente y reservelo para situaciones en las que desee:

- Comunicar significado o afiliación (por ejemplo, modificadores de plataforma o lenguaje)

- Llamar la atención (por ejemplo, indicar un cambio de estado)

- Mejorar la legibilidad y proporcionar puntos de referencia para navegar por la interfaz de usuario

- Aumento de la deseabilidad

Existen varias opciones para asignar colores a elementos de la interfaz de usuario en Visual Studio. A veces puede ser difícil averiguar qué opción debe usar o cómo usarla correctamente. Este tema le ayudará a:

- Comprenda los diferentes servicios y sistemas que se usan para definir colores en Visual Studio.

- Seleccione la opción correcta para un elemento determinado.

- Use correctamente la opción que ha elegido.

> [!NOTE]
> No codificar nunca los colores hexadecimales, RGB o del sistema en los elementos de la interfaz de usuario. El uso de los servicios permite flexibilidad en la optimización del matiz. Además, sin el servicio , no podrá aprovechar las funcionalidades de cambio de tema [del servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para asignar color a elementos Visual Studio interfaz

Elija el método más adecuado para los elementos de la interfaz de usuario.

| La interfaz de usuario | Método | ¿Cuáles son? |
| --- | --- | --- |
| Tiene cuadros de diálogo incrustados o independientes. | **Colores del sistema** | Nombres de sistema que permiten al sistema operativo definir el color y la apariencia de los elementos de la interfaz de usuario, como los controles de diálogo comunes. |
| Tiene una interfaz de usuario personalizada que desea ser coherente con el entorno general de VS y tiene elementos de interfaz de usuario que coinciden con la categoría y el significado semántico de los tokens compartidos. | **Colores compartidos comunes** | Nombres de tokens de color predefinidos existentes para elementos de interfaz de usuario específicos |
| Tiene una característica individual o un grupo de características y no hay ningún color compartido para elementos similares. | **Colores personalizados** | Nombres de token de color que son específicos de un área y que no están diseñados para compartirse con otra interfaz de usuario |
| Quiere permitir que el usuario final personalice la interfaz de usuario o el contenido (por ejemplo, para editores de texto o ventanas de diseñador especializadas). | **Personalización del usuario final**<br /><br />**(Herramientas) &gt; Cuadro de diálogo Opciones)** | Configuración definida en la página "Fuentes **y &gt;** colores" del cuadro de diálogo Opciones de herramientas o una página especializada específica de una característica de interfaz de usuario. |

### <a name="visual-studio-themes"></a>Visual Studio temas

Visual Studio tres temas de color diferentes: claro, oscuro y azul. También detecta el modo contraste alto, que es un tema de color de todo el sistema diseñado para la accesibilidad.

Se pide a los usuarios que seleccionen un tema durante su primer uso de Visual Studio y que puedan cambiar de tema más adelante; para hacerlo, vaya a Tools Options Environment General (Entorno de opciones de herramientas **&gt; &gt; &gt; general)** y elija un nuevo tema en el menú desplegable "color theme" (Tema de color).

Los usuarios también pueden usar Panel de control para cambiar todos sus sistemas a uno de los contraste alto temas. Si un usuario selecciona un tema contraste alto, el selector de temas de color de Visual Studio ya no afecta a los colores de Visual Studio, aunque se guardan los cambios de tema para cuando el usuario sale del contraste alto. Para obtener más información sobre contraste alto, vea [Elegir contraste alto colores](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>El servicio VSColor

Visual Studio proporciona un servicio de color de entorno, conocido como servicio VSColor, que permite enlazar los valores de color de los elementos de la interfaz de usuario a una entrada con nombre que contiene valores de color para cada tema Visual Studio. Esto garantiza que los colores cambiarán automáticamente para reflejar el tema seleccionado por el usuario actual o el modo de contraste alto sistema. El uso del servicio significa que la implementación de todos los cambios de color relacionados con el tema se controla en un solo lugar y, si usa colores compartidos comunes del servicio, la interfaz de usuario reflejará automáticamente nuevos temas en versiones futuras de Visual Studio.

### <a name="implementation"></a>Implementación

El Visual Studio código fuente incluye varios archivos de definición de paquete que contienen listas de nombres de token y los valores de color correspondientes para cada tema. El servicio de color lee los VSColor definidos en estos archivos de definición de paquete. Se hace referencia a estos colores en el marcado XAML o en el código y, a continuación, se cargan mediante el `IVsUIShell5.GetThemedColor` método o una asignación DynamicResource.

### <a name="system-colors"></a>Colores del sistema

Los controles comunes hacen referencia a los colores del sistema de forma predeterminada. Si quiere que la interfaz de usuario use colores del sistema, como cuando crea un cuadro de diálogo insertado o independiente, no es necesario hacer nada.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Colores compartidos comunes en el servicio VSColor

Los elementos de la interfaz deben reflejar el entorno Visual Studio general. Al volver a usar los colores compartidos comunes que son adecuados para el componente de interfaz de usuario que está diseñando, se asegura de que la interfaz sea coherente con otras interfaces de Visual Studio y de que los colores se actualizarán automáticamente cuando se agregan o actualizan temas.

Antes de usar colores compartidos comunes, asegúrese de que comprende cómo usarlos correctamente. El uso incorrecto de colores compartidos comunes podría dar lugar a una experiencia incoherente, frustrante o confusa para los usuarios.

### <a name="user-customizable-colors"></a>Colores personalizables por el usuario

Vea: [Exposición de colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

A veces, querrá permitir que el usuario final personalice la interfaz de usuario, como cuando se crea un editor de código o una superficie de diseño. Los componentes personalizables  de la interfaz de usuario se encuentran en la sección Fuentes y colores del cuadro de diálogo Opciones de herramientas, donde los usuarios pueden elegir cambiar el color de primer plano, el color de fondo o ambos. **&gt;**

![Cuadro de &gt; diálogo Opciones de herramientas](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Cuadro de &gt; diálogo Opciones de herramientas

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> El servicio VSColor

Visual Studio proporciona un servicio de color de entorno, también denominado servicio VSColor o servicio de color de shell. Este servicio permite enlazar los valores de color de los elementos de la interfaz de usuario a un conjunto de colores nombre-valor que contiene colores para cada tema. El servicio VSColor debe usarse para todos los elementos de la interfaz de usuario, de modo que los colores cambien automáticamente para reflejar el tema seleccionado por el usuario actual y para que la interfaz de usuario enlazada al servicio de color del entorno se integre con nuevos temas en versiones futuras de Visual Studio.

### <a name="how-the-service-works"></a>Funcionamiento del servicio

El servicio de color del entorno lee VSColors definidos en .pkgdef para el componente de interfaz de usuario. A continuación, se hace referencia a estos VSColors en el marcado o código XAML y se cargan a través de `IVsUIShell5.GetThemedColor` o una `DynamicResource` asignación.

![Arquitectura de servicio de color del entorno](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Arquitectura de servicio de color del entorno

### <a name="accessing-the-service"></a>Acceso al servicio

Hay varias maneras de acceder al servicio VSColor, en función del tipo de tokens de color que use y del tipo de código que tenga.

#### <a name="predefined-environment-colors"></a>Colores de entorno predefinidos

##### <a name="from-native-code"></a>Desde código nativo

El shell proporciona un servicio que proporciona acceso al de `COLORREF` los colores. El servicio o interfaz es:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

En el archivo VSShell80.idl, la enumeración `__VSSYSCOLOREX` tiene constantes de color de shell. Para usarlo, pase como valor de índice uno de los valores del documentado en MSDN o un número de índice normal que acepte la API del sistema de `enum __VSSYSCOLOREX` Windows, `GetSysColor` . Al hacerlo, se obtiene el valor RGB del color que se debe usar en el segundo parámetro.

Si almacena un lápiz o pincel con un color nuevo, debe (fuera del shell de Visual Studio) y `AdviseBroadcastMessages` escuchar los mensajes y `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` .

Para acceder al servicio de color en código nativo, hará una llamada similar a esta:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Los `COLORREF` valores devueltos por `GetVSSysColorEx()` contienen solo componentes R,G,B de un color de tema. Si una entrada de tema usa transparencia, el valor del canal alfa se descarta antes de devolverse. Por lo tanto, si el color de entorno de interés debe usarse en un lugar donde el canal de transparencia sea importante, debe usar en lugar de , como se describe más adelante `IVsUIShell5.GetThemedColor` `IVsUIShell2::GetVSSysColorEx` en este tema.

##### <a name="from-managed-code"></a>Desde código administrado

El acceso al servicio VSColor a través de código nativo es bastante sencillo. Sin embargo, si está trabajando con código administrado, determinar cómo usar el servicio puede ser complicado. Con esto en mente, este es un fragmento de código de C# que muestra este proceso:

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

Puede enlazar a los Visual Studio a través de valores exportados en el de la `ResourceDictionary` aplicación. A continuación se muestra un ejemplo del uso de recursos de la tabla de colores, así como el enlace a los datos de fuente del entorno en XAML.

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

En el caso del código administrado, la biblioteca de Managed Package Framework del shell ( ) contiene un par de clases auxiliares que facilitan el uso `Microsoft.VisualStudio.Shell.12.0.dll` de colores con tema.

Los métodos auxiliares de `Microsoft.VisualStudio.Shell.VsColors` la clase en MPF incluyen y `GetThemedGDIColor()` `GetThemedWPFColor()` . Esos métodos auxiliares devuelven el valor de color de una entrada de tema como o , que `System.Drawing.Color` se usará en WinForms o en la interfaz `System.Windows.Media.Color` de usuario de WPF.

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

La clase también se puede usar para obtener identificadores VSCOLOR para una clave de recurso de color de WPF determinada, o viceversa.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Los métodos de `VsColors` clase consultan el servicio VSColor para devolver el valor de color cada vez que se invocan. Para obtener un valor de color como , una alternativa con un mejor rendimiento es usar en su lugar los métodos de la clase , que almacena en caché los valores de color obtenidos del `System.Drawing.Color` `Microsoft.VisualStudio.PlatformUI.VSThemeColor` servicio VSColor. La clase se suscribe internamente a eventos de difusión de shell y descarta el valor almacenado en caché cuando se produce un evento de cambio de tema. Además, la clase proporciona un . Evento descriptivo de NET para suscribirse a los cambios de tema. Use el `ThemeChanged` evento para agregar un nuevo controlador y use el método para obtener valores de color para el `GetThemedColor()` de `ThemeResourceKeys` interés. Un código de ejemplo podría tener este aspecto:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Elección de contraste alto colores

### <a name="overview"></a>Información general

Windows usa varios temas de alto contraste de nivel del sistema que aumentan el contraste de color de texto, fondos e imágenes, lo que hace que los elementos parezcan más distintos en la pantalla. Por motivos de accesibilidad, es importante que los Visual Studio de interfaz respondan correctamente cuando los usuarios cambien a un contraste alto tema.

Solo se pueden usar una serie de colores del sistema para contraste alto temas. Al elegir los nombres de color del sistema, recuerde las siguientes sugerencias:

- **Elija los colores del sistema que tengan el mismo significado** semántico que el elemento que está coloreando. Por ejemplo, si elige un color de contraste alto para el texto dentro de una ventana, use WindowText y no ControlText.

- **Elija pares de primer** plano y fondo juntos o no estará seguro de que su elección de color funcionará en todos los contraste alto temas.

- **Determine qué partes de la interfaz de usuario son las más importantes y asegúrese de que las áreas de contenido destacarán.** Perderá muchos detalles que las diferencias sutiles en el matiz de color normalmente distinguirían, por lo que el uso de colores de borde fuertes es común para definir áreas de contenido, ya que no hay variantes de color para las distintas áreas de contenido.

### <a name="system-color-set"></a>Conjunto de colores del sistema

La tabla del blog del equipo de WPF: Referencia de [SystemColors](/archive/blogs/wpf/systemcolors-reference) indica el conjunto completo de nombres de color del sistema y los matizs correspondientes que se muestran en cada tema.

Al aplicar este conjunto limitado de colores a la interfaz de usuario, se espera que pierda detalles sutiles que estaban presentes en los *temas "normales".* Este es un ejemplo de interfaz de usuario con colores grises sutiles que se usan para distinguir áreas dentro de una ventana de herramientas. Cuando se empareja con la misma ventana mostrada en modo contraste alto, puede ver que todos los fondos tienen el mismo matiz y que los bordes de esas áreas se indican solo por borde:

![Ejemplo de cómo se pierden detalles sutiles en contraste alto](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Ejemplo de cómo se pierden detalles sutiles en contraste alto

#### <a name="choosing-text-colors-in-an-editor"></a>Elección de colores de texto en un editor

El texto colorizado se usa en un editor o en una superficie de diseño para indicar el significado, como permitir la identificación sencilla de grupos de elementos similares. En un contraste alto tema, sin embargo, no tiene la capacidad de diferenciar entre más de tres colores de texto. WindowText, GrayText y HotTrackText son los únicos colores disponibles en las superficies WindowBackground. Puesto que no puede usar más de tres colores, elija cuidadosamente las diferencias más importantes que desea mostrar cuando esté contraste alto modo.

Matiz para cada uno de los nombres de token permitidos en una superficie del editor, tal como aparecen en cada tema contraste alto siguiente:

![Comparación de editor de contraste alto](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparación de editor de contraste alto

Ejemplos de la superficie del editor en el tema Azul:

![Editor en el tema azul](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor en el tema azul

![Editor en contraste alto #1 tema](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor en contraste alto #1 tema

### <a name="usage-patterns"></a>Patrones de uso

Muchos elementos comunes de la interfaz de usuario ya contraste alto definidos. Puede hacer referencia a estos patrones de uso al elegir sus propios nombres de color del sistema, de modo que los elementos de la interfaz de usuario sean coherentes con componentes similares.

| Color del sistema | Uso |
| --- | --- |
| ActiveCaption | - IDE activo y glifos de botones de ventana desfasadas al mantener el puntero y presionar<br />- Fondo de la barra de título para el IDE y las ventanas desfasadas<br />- Fondo de la barra de estado predeterminada |
| ActiveCaptionText | - IDE activo y ventanas en blanco para el primer plano de la barra de título (texto y glifos)<br />- Fondo y borde de los botones activos de la ventana al mantener el puntero y presionar |
| Control | - Cuadro combinado, lista desplegable y fondo predeterminado y deshabilitado del control de búsqueda, incluido el botón desplegable<br />- Fondo del botón de destino de acoplamiento<br />- Fondo de la barra de comandos<br />- Fondo de la ventana de herramientas |
| ControlDark | - Fondo del IDE<br />- Separadores de menú y barra de comandos<br />- Borde de la barra de comandos<br />- Sombras de menú<br />- Pestaña de la ventana de herramientas predeterminada y borde y separador del mouse<br />- Fondo del botón de desbordamiento de documentos<br />- Borde de glifo de destino de acoplamiento |
| ControlDarkDark |- Ventana de pestaña Desenfoque de documento seleccionada |
| ControlLight |- Ocultar automáticamente el borde de la pestaña<br />- Cuadro combinado y borde de lista desplegable<br />- Fondo y borde de destino de acoplamiento |
| ControlLightLight | - Borde provisional seleccionado y centrado |
| ControlText | - Glifo de cuadro combinado y lista desplegable<br />- Texto de pestaña no seleccionado de la ventana de herramientas |
| GrayText |- Cuadro combinado y lista desplegable de texto deshabilitado de borde, glifo desplegable, texto y elemento de menú<br />- Texto del menú Deshabilitado<br />- Texto de encabezado de "opciones de búsqueda" del control de búsqueda<br />- Separador de sección de control de búsqueda |
| Resaltar | - Todos los fondos y bordes presionados y al mantener el puntero, excepto el fondo del botón desplegable del cuadro combinado y el borde del botón de desbordamiento del área de trabajo del documento<br />- Fondos de elementos seleccionados |
| HighlightText | - Todos los primeros planos del mouse y presionados (texto y glifos)<br />- Primer plano de control de ventana de pestaña de documento y ventana de herramientas centradas<br />- Borde de la barra de título de la ventana de herramientas centrada<br />- Primer plano de tabulación provisional con foco seleccionado<br />- Document well overflow button border on hover and press (Documentar el borde del botón de desbordamiento de well al mantener el puntero y presionar)<br />- Borde del icono seleccionado|
| HotTrack | - Fondo y borde de la barra de desplazamiento al presionar<br />- Glifo de flecha de barra de desplazamiento al presionar |
| InactiveCaption | - Ide inactivo y glifos de botón de ventana desfasadas al mantener el puntero<br />- Fondo de la barra de título para el IDE y las ventanas desfasadas<br />- Fondo del control de búsqueda deshabilitado |
| InactiveCaptionText | - IDE inactivo y primer plano de la barra de título de ventanas en blanco (texto y glifos)<br />- Botones de ventana inactivos de fondo y borde al mantener el puntero<br />- Borde y fondo de botón de la ventana de herramientas sin foco<br />- Primer plano del control de búsqueda deshabilitado |
| Menú | - Fondo del menú desplegable<br />- Fondo de marca de verificación activada y deshabilitada |
| MenuText | - Borde del menú desplegable<br />- Marcas de verificación<br />- Glifos de menú<br />- Texto del menú desplegable<br />- Borde del icono seleccionado |
| Barra de desplazamiento | - Fondo de la barra de desplazamiento y de la flecha de la barra de desplazamiento, todos los estados |
| Periodo | - Ocultar automáticamente el fondo de la pestaña<br />- Fondo de la barra de menús y de la plataforma de comandos<br />- Fondo de la pestaña de la ventana de documento sin foco o no seleccionado y borde del documento, tanto para las pestañas abiertas como provisionales.<br />- Fondo de la barra de título de la ventana de herramientas sin foco<br />- Fondo de la pestaña de la ventana de herramientas, tanto seleccionado como no seleccionado |
| WindowFrame | - Borde del IDE |
| WindowText | - Ocultar automáticamente el primer plano de la pestaña<br />- Primer plano de la pestaña de la ventana de herramientas seleccionada<br />- Pestaña Ventana de documento sin foco y primer plano de pestaña provisional sin foco o no seleccionado<br />- Primer plano predeterminado de la vista de árbol y mantener el puntero sobre el glifo no seleccionado<br />- Borde de pestaña seleccionado de la ventana de herramientas<br />- Fondo, borde y glifo de la barra de desplazamiento |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Exposición de colores para los usuarios finales

### <a name="overview"></a>Información general

A veces querrá permitir que el usuario final personalice la interfaz de usuario, como cuando se crea un editor de código o una superficie de diseño. La manera más común de hacerlo es mediante el cuadro **de diálogo Opciones &gt; de** herramientas. A menos que tenga una interfaz de usuario altamente especializada que requiera controles  especiales, la manera más fácil de presentar la personalización es a través de la página Fuentes y **colores** de la sección Entorno del cuadro de diálogo. Para cada elemento que exponga para la personalización, el usuario puede elegir cambiar el color de primer plano, el color de fondo o ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Creación de un VSPackage para los colores personalizables

Un VSPackage puede controlar las fuentes y los colores a través de categorías personalizadas y mostrar elementos en la página de propiedades Fuentes y colores. Al usar este mecanismo, VSPackages debe implementar la [interfaz IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) y sus interfaces asociadas.

En principio, este mecanismo se puede usar para modificar todos los elementos de visualización existentes y las categorías que los contienen. Sin embargo, no debe usarse para modificar la categoría Editor de texto ni sus elementos para mostrar. Para obtener más información sobre la categoría Editor de texto, vea [Información general sobre fuentes y colores.](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)

Para implementar categorías personalizadas o mostrar elementos, un VSPackage debe:

- **Cree o identifique categorías en el Registro.** La implementación del IDE de la página de **propiedades Fuentes** y colores usa esta información para consultar correctamente el servicio que admite una categoría determinada.

- **Cree o identifique grupos en el Registro (opcional).** Puede ser útil definir un grupo, que representa la unión de dos o más categorías. Si se define un grupo, el IDE combina automáticamente las subcategorías y distribuye los elementos de presentación dentro del grupo.

- **Implemente la compatibilidad con IDE.**

- **Controle los cambios de fuente y color.**

#### <a name="to-create-or-identify-categories"></a>Para crear o identificar categorías

Construya un tipo especial de entrada del Registro de categorías en `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` donde es el nombre no localizado de la `<Category>` categoría.

Rellene el Registro con dos valores:

| Nombre | Tipo | Datos | Descripción |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID creado para identificar la categoría |
| Paquete | REG_SZ | GUID | GUID del servicio VSPackage que admite la categoría |

 El servicio especificado en el Registro debe proporcionar una implementación de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) para la categoría correspondiente.

#### <a name="to-create-or-identify-groups"></a>Para crear o identificar grupos

Construya un tipo especial de entrada del Registro de categoría en `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` donde es el nombre no localizado del `<group>` grupo.

Rellene el Registro con dos valores:

| Nombre | Tipo | Datos | Descripción |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Un GUID creado para identificar la categoría |
| Paquete | REG_SZ | GUID | GUID del servicio VSPackage que admite la categoría |

El servicio especificado en el Registro debe proporcionar una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> para el grupo correspondiente.

![Implementación de IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementación de `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Para implementar la compatibilidad con IDE

Implemente [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), que devuelve una interfaz [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) o una interfaz al IDE para cada GUID de categoría o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> grupo proporcionado.

Para cada categoría que admite, un VSPackage implementa una instancia independiente de la [interfaz IVsFontAndColorDefaults.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)

Los métodos implementados a [través de IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) deben proporcionar al IDE:

- Listas de elementos para mostrar de la categoría

- Nombres localizables para elementos para mostrar

- Mostrar información para cada miembro de la categoría

> [!NOTE]
> Cada categoría debe contener al menos un elemento para mostrar.

El IDE usa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfaz para definir una unión de varias categorías.

Su implementación proporciona al IDE lo siguiente:

- Una lista de las categorías que forma un grupo determinado

- Acceso a instancias de [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) que admiten cada categoría dentro del grupo

- Nombres de grupo localizables

#### <a name="updating-the-ide"></a>Actualización del IDE

El IDE almacena en caché información sobre la configuración de fuente y color. Por lo tanto, después de cualquier modificación de la configuración de fuente y color del IDE, es un procedimiento recomendado asegurarse de que la memoria caché está actualizada.

La actualización de la memoria caché se realiza a través de la [interfaz IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) y se puede realizar globalmente o solo en los elementos seleccionados.

### <a name="handling-font-and-color-changes"></a>Control de cambios de fuente y color

Para admitir correctamente la coloración del texto que muestra un VSPackage, el servicio de colorización que admite el VSPackage debe responder a los cambios iniciados por el usuario realizados a través de la página de propiedades Fuentes y colores.

Para ello, un VSPackage debe:

- **controlar eventos generados por ide** mediante la implementación de la [interfaz IVsFontAndColorEvents.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) El IDE llama al método adecuado después de las modificaciones del usuario de la página Fuentes y colores. Por ejemplo, llama al [método OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) si se selecciona una nueva fuente.

  **OR**

- **sondee el IDE en busca de cambios.** Esto se puede hacer a través de la interfaz [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) implementada por el sistema. Aunque principalmente para admitir la persistencia, el [método GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) puede obtener información de fuente y color para mostrar elementos. Para obtener más información sobre la configuración de fuentes y colores, vea el artículo de MSDN Acceso a la fuente almacenada y la [configuración de color.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015)

> [!NOTE]
> Para asegurarse de que los resultados de sondeo son correctos, use la interfaz [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) para determinar si se necesita un vaciado y una actualización de caché antes de llamar a los métodos de recuperación de la interfaz [IVsFontAndColorStorage.](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrar la fuente personalizada y la categoría de color sin implementar interfaces

En el ejemplo de código siguiente se muestra cómo registrar la fuente personalizada y la categoría de color sin implementar interfaces:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Para este ejemplo de código:

- `"NameID"` = el identificador de recurso del nombre de categoría localizado en el paquete
- `"ToolWindowPackage"` = GUID del paquete
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` es simplemente un ejemplo y el valor real puede ser un nuevo GUID proporcionado por el implementador.

### <a name="set-the-font-and-color-property-category-guid"></a>Establecer el GUID de la categoría de propiedades Fuente y Color

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
