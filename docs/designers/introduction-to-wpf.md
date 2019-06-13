---
title: Introducción a WPF
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: 69ef227bb30703a41fe9519114a2bc9904e902f2
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714815"
---
# <a name="wpf-overview"></a>Información general sobre WPF

Windows Presentation Foundation (WPF) le permite crear aplicaciones de cliente de escritorio para Windows con experiencias de usuario visualmente impactantes.

![Ejemplo Contoso Healthcare UI](../designers/media/wpfintrofigure24.png)

El núcleo de WPF es un motor de representación basado en vectores e independiente de la resolución que está diseñado para sacar partido al moderno hardware gráfico. WPF amplía el núcleo con un conjunto completo de características de desarrollo de aplicaciones que incluyen Extensible Application Markup Language (XAML), controles, enlace de datos, diseño, gráficos en 2D y 3D, animación, estilos, plantillas, documentos, elementos multimedia, texto y tipografía. WPF es parte de. NET, lo que permite compilar aplicaciones que incorporan otros elementos de la API. NET.

Esta introducción está dirigida a personas que aún no conocen WPF, y en ella se abordan sus conceptos y capacidades principales.

## <a name="program-with-wpf"></a>Programar con WPF

WPF consisten en un subconjunto de tipos de .NET (la mayor parte) se encuentran en el <xref:System.Windows> espacio de nombres. Si ha compilado previamente aplicaciones con .NET mediante tecnologías administradas como ASP.NET y Windows Forms, la experiencia de programación de conceptos básicos de WPF deben resultarle familiares; crear instancias de clases, establecer propiedades, llamar a métodos y controlará eventos con el lenguaje de programación como favoritas de .NET C# o Visual Basic.

WPF incluye construcciones de programación adicionales que mejoran las propiedades y los eventos: las [propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview) y los [eventos enrutados](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Marcado y código subyacente

WPF permite desarrollar una aplicación que use tanto *marcado* como *código subyacente*, una experiencia que les resultará familiar a los desarrolladores de ASP.NET. En general, se usa marcado XAML para implementar la apariencia de una aplicación y lenguajes de programación administrados (código subyacente) para implementar su comportamiento. Esta separación entre la apariencia y el comportamiento tiene las ventajas siguientes:

- Se reducen los costes de desarrollo y mantenimiento porque el marcado específico de la apariencia no está asociado estrechamente al código específico del comportamiento.

- La programación es más eficaz porque los diseñadores pueden implementar la apariencia de una aplicación al mismo tiempo que los programadores implementan su comportamiento.

- La[globalización y localización](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) de las aplicaciones WPF se ha simplificado.

### <a name="markup"></a>marcado

XAML es un lenguaje de marcado basado en XML que se usa para implementar la apariencia de una aplicación mediante declaración. Se suele usar para crear ventanas, cuadros de diálogo, páginas y controles de usuario, así como para rellenarlos con controles, formas y gráficos.

En el ejemplo siguiente se usa XAML para implementar la apariencia de una ventana que contiene un solo botón.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

En concreto, este código XAML define una ventana y un botón mediante el uso de los elementos `Window` y `Button` , respectivamente. Cada elemento se configura con atributos como, por ejemplo, el atributo `Window` del elemento `Title` para especificar el texto de la barra de título de la ventana. En tiempo de ejecución, WPF convierte los elementos y los atributos que se definen en el marcado en instancias de clases de WPF. Por ejemplo, el elemento `Window` se convierte en una instancia de la clase <xref:System.Windows.Window> cuya propiedad <xref:System.Windows.Window.Title%2A> es el valor del atributo `Title` .

En la ilustración siguiente se muestra la interfaz de usuario definida mediante el código XAML del ejemplo anterior.

![Ventana que contiene un botón](../designers/media/wpfintrofigure10.png)

Dado que XAML se basa en XML, la interfaz de usuario que se crea con este lenguaje se ensambla en una jerarquía de elementos anidados, que se denomina [árbol de elementos](/dotnet/framework/wpf/advanced/trees-in-wpf). El árbol de elementos proporciona una manera lógica e intuitiva para crear y administrar las interfaces de usuario.

### <a name="code-behind"></a>Código subyacente

El comportamiento principal de una aplicación consiste en implementar la funcionalidad que responde a las interacciones del usuario, lo que incluye controlar los eventos (por ejemplo, hacer clic en un menú, una barra de herramientas o un botón) y llamar, en respuesta, a la lógica de negocios y al acceso a los datos. En WPF, este comportamiento se implementa en el código que está asociado al marcado. Este tipo de código se conoce como código subyacente. En el ejemplo siguiente se muestra el marcado actualizado del ejemplo anterior y el código subyacente.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

En este ejemplo, el código subyacente implementa una clase que deriva de la clase <xref:System.Windows.Window> . El atributo `x:Class` se usa para asociar el marcado a la clase de código subyacente. Se llama a `InitializeComponent` desde el constructor de la clase de código subyacente para combinar la interfaz de usuario que se define en el marcado con la clase de código subyacente. (`InitializeComponent` se genera al compilar la aplicación, por lo que no se requiere su implementación manual). La combinación de `x:Class` y `InitializeComponent` garantiza de que la implementación se inicializa correctamente cada vez que se crea. La clase de código subyacente también implementa un controlador de eventos para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> del botón. Cuando se hace clic en el botón, el controlador de eventos muestra un cuadro de mensaje mediante una llamada al método <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> .

En la siguiente ilustración se muestra el resultado de hacer clic en el botón.

![MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Controles

Las experiencias de usuario proporcionadas por el modelo de aplicación son controles construidos. En WPF, *control* es un término genérico que se aplica a una categoría de clases de WPF que se hospedan en una ventana o una página, tienen una interfaz de usuario e implementan un comportamiento determinado.

Para obtener más información, consulte [Controles](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>Controles de WPF por función

A continuación se muestra la lista de controles WPF integrados.

- **Botones**: <xref:System.Windows.Controls.Button> y <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Presentación de datos**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>y <xref:System.Windows.Controls.TreeView>.

- **Presentación y selección de fechas**: <xref:System.Windows.Controls.Calendar> y <xref:System.Windows.Controls.DatePicker>.

- **Cuadros de diálogo**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>y <xref:Microsoft.Win32.SaveFileDialog>.

- **Entrada de lápiz digital**: <xref:System.Windows.Controls.InkCanvas> y <xref:System.Windows.Controls.InkPresenter>.

- **Documentos**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>y <xref:System.Windows.Controls.StickyNoteControl>.

- **Entrada**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>y <xref:System.Windows.Controls.PasswordBox>.

- **Diseño**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>y <xref:System.Windows.Controls.WrapPanel>.

- **Multimedia**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>y <xref:System.Windows.Controls.SoundPlayerAction>.

- **Menús**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>y <xref:System.Windows.Controls.ToolBar>.

- **Navegación**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>y <xref:System.Windows.Controls.TabControl>.

- **Selección**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>y <xref:System.Windows.Controls.Slider>.

- **Información del usuario**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>y <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Entrada y comandos

Los controles casi siempre detectan las acciones del usuario y responden a ellas. El [sistema de entrada de WPF](/dotnet/framework/wpf/advanced/input-overview) usa eventos directos y enrutados para admitir la entrada de texto, la administración del enfoque y la posición del mouse.

Las aplicaciones a menudo tienen tener requisitos de entrada complejos. WPF proporciona un [sistema de comandos](/dotnet/framework/wpf/advanced/commanding-overview) que separa las acciones de entrada del usuario del código que responde a esas acciones.

## <a name="layout"></a>Diseño

Al crear crear una interfaz de usuario, se organizan los controles según su ubicación y tamaño para crear un diseño. Un requisito fundamental de cualquier diseño es adaptarse a los cambios de tamaño de la ventana y de configuración de pantalla. En lugar de obligarle a escribir código que adapte el diseño en estas circunstancias, WPF le proporciona un sistema de diseño extensible de primera clase.

La piedra angular del sistema de diseño es la posición relativa, que aumenta la capacidad de adaptación a los cambios en la configuración de las ventanas y la pantalla. Además, el sistema de diseño administra la negociación entre los controles para determinar el diseño. La negociación es un proceso de dos pasos: en primer lugar, el control indica a su elemento primario qué ubicación y tamaño necesita; en segundo lugar, el elemento primario indica al control cuánto espacio dispone.

El sistema de diseño se expone a los controles secundarios mediante las clases base de WPF. Para los diseños comunes, como las cuadrículas, el apilamiento y el acoplamiento, WPF incluye varios controles de diseño:

- <xref:System.Windows.Controls.Canvas>: Los controles secundarios proporcionan su propio diseño.

- <xref:System.Windows.Controls.DockPanel>: Los controles secundarios se alinean con los bordes del panel.

- <xref:System.Windows.Controls.Grid>: Los controles secundarios se colocan por filas y columnas.

- <xref:System.Windows.Controls.StackPanel>: Los controles secundarios se apilan vertical u horizontalmente.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Los controles secundarios se virtualizan y se organizan en una sola línea en sentido horizontal o vertical.

- <xref:System.Windows.Controls.WrapPanel>: Los controles secundarios se sitúan en orden de izquierda a derecha y se ajustan a la línea siguiente cuando hay más controles de los que caben en la línea actual.

En el ejemplo siguiente se usa un control <xref:System.Windows.Controls.DockPanel> para situar varios controles <xref:System.Windows.Controls.TextBox>.

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

<xref:System.Windows.Controls.DockPanel> permite que los controles secundarios <xref:System.Windows.Controls.TextBox> le indiquen cómo se deben organizar. Para ello, <xref:System.Windows.Controls.DockPanel> implementa una propiedad adjunta `Dock` que se expone a los controles secundarios para permitir que cada uno de ellos especifique un estilo de acoplamiento.

> [!NOTE]
> Una propiedad implementada por un control principal para que la usen los controles secundarios es una construcción de WPF denominada [propiedad adjunta](/dotnet/framework/wpf/advanced/attached-properties-overview).

En la siguiente ilustración se muestra el resultado del marcado XAML del ejemplo anterior.

![Página de DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Enlace de datos

La mayoría de las aplicaciones se crean para proporcionar a los usuarios recursos que les permitan ver y editar datos. Para las aplicaciones de WPF, el trabajo de almacenamiento de datos y el acceso a ellos ya se proporciona mediante tecnologías existentes, como SQL Server y ADO .NET. Una vez que se tiene acceso a los datos y se cargan en los objetos administrados de la aplicación, comienza la tarea ardua de las aplicaciones WPF. En esencia, esto implica dos cosas:

1. Copiar los datos de los objetos administrados a los controles, donde los datos se pueden mostrar y editar.

2. Asegurarse de que los cambios realizados en los datos mediante los controles se vuelvan a copiar a los objetos administrados.

Para simplificar el desarrollo de aplicaciones, WPF ofrece un motor de enlace de datos que sigue estos pasos automáticamente. La unidad que constituye el núcleo del motor de enlace de datos es la clase <xref:System.Windows.Data.Binding> , que se encarga de enlazar un control (el destino de enlace) a un objeto de datos (el origen de enlace). Esta relación se muestra en la ilustración siguiente:

![Diagrama de enlace de datos básico](../designers/media/databindingmostbasic.png)

En el ejemplo siguiente, se muestra cómo enlazar un control <xref:System.Windows.Controls.TextBox> a una instancia de un objeto `Person` personalizado. La implementación de `Person` se muestra en el código siguiente:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

El siguiente marcado enlaza el control <xref:System.Windows.Controls.TextBox> a una instancia de un objeto `Person` personalizado.

 ```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
 ```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]

En este ejemplo, se crea una instancia de la clase `Person` en el código subyacente y se establece como el contexto de datos para `DataBindingWindow`. En el marcado, la propiedad <xref:System.Windows.Controls.TextBox.Text%2A> de <xref:System.Windows.Controls.TextBox> se enlaza a la propiedad `Person.Name` (mediante la sintaxis "`{Binding ... }`" de XAML). Este código XAML indica a WPF que enlace el control <xref:System.Windows.Controls.TextBox> al objeto `Person` almacenado en la propiedad <xref:System.Windows.FrameworkElement.DataContext%2A> de la ventana.

El motor de enlace de datos de WPF proporciona compatibilidad adicional que incluye validación, ordenación, filtrado y agrupación. Además, el enlace de datos admite el uso de plantillas de datos para crear una interfaz de usuario personalizada para los datos enlazados cuando la interfaz de usuario mostrada por los controles estándar de WPF no es adecuada.

Para obtener más información, vea [Información general sobre el enlace de datos](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Gráficos

WPF incluye un conjunto extenso, escalable y flexible de características de gráficos que tienen las siguientes ventajas:

- **Gráficos independientes de la resolución e independientes del dispositivo**. La unidad de medida básica del sistema de gráficos de WPF es el píxel independiente del dispositivo, que es 1/96 de pulgada (sea cual fuere la resolución de pantalla real), y proporciona la base para la representación independiente de la resolución y del dispositivo. Cada píxel independiente del dispositivo se escala automáticamente para que coincida con la configuración de puntos por pulgada (ppp) del sistema en que se representa.

- **Precisión mejorada**. El sistema de coordenadas de WPF se mide con números de punto flotante de precisión doble en lugar de precisión sencilla. Las transformaciones y los valores de opacidad también se expresan como de precisión doble. WPF admite, además, una gama de color amplia (scRGB) y ofrece compatibilidad integrada para la administración de entradas de diferentes espacios de color.

- **Compatibilidad con gráficos y animación avanzados**. WPF simplifica la programación de gráficos administrando automáticamente las escenas de animación. No tendrá que preocuparse por el procesamiento de escenas, los bucles de presentación ni la interpolación bilineal. Además, WPF admite la prueba de clics y proporciona compatibilidad plena con la composición alfa.

- **Aceleración de hardware**. El sistema de gráficos de WPF saca partido del hardware de gráficos para minimizar el uso de la CPU.

### <a name="2d-shapes"></a>Formas en 2D

WPF proporciona una biblioteca de formas en 2D comunes dibujadas mediante vectores, como los rectángulos y las elipses que se muestran en la ilustración siguiente:

![Elipses y rectángulos](../designers/media/wpfintrofigure4.PNG)

Una función interesante de las formas es que no sirven únicamente para su presentación; las formas implementan muchas de las características que cabe esperar de los controles, incluida la entrada de datos desde el teclado y el mouse. El ejemplo siguiente se muestra el evento <xref:System.Windows.UIElement.MouseUp> que se controla con la forma <xref:System.Windows.Shapes.Ellipse> .

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

La siguiente ilustración muestra lo que genera el código anterior.

![Ventana con el texto "You clicked the ellipse&#33;" (Ha hecho clic en la elipse)](../designers/media/wpfintrofigure12.png)

Para obtener más información, vea [Información general sobre formas y dibujo básico en WPF](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>Geometrías en 2D

Las formas en 2D que proporciona WPF abarcan el conjunto estándar de formas básicas. Pero tal vez sea necesario crear formas personalizadas para facilitar el diseño de una interfaz de usuario personalizada. Para ello, WPF proporciona las geometrías. En la siguiente ilustración se muestra el uso de geometrías para crear una forma personalizada que se puede dibujar directamente, usar como un pincel o usar para recortar otras formas y controles.

Los objetos<xref:System.Windows.Shapes.Path> se pueden usar para dibujar formas cerradas o abiertas, varias formas o incluso formas curvas.

Los objetos <xref:System.Windows.Media.Geometry> se pueden usar para el recorte, la prueba de posicionamiento y la representación de datos de gráficos en 2D.

![Varios usos de una ruta de acceso](../designers/media/wpfintrofigure5.png)

Para obtener más información, vea [Información general sobre geometría](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>Efectos en 2D

Un subconjunto de funciones en 2D de WPF incluye los efectos visuales, tales como degradados, mapas de bits, dibujos, pintar con vídeos, rotación, escala y sesgado. Todos ellos se realizan con pinceles. En la siguiente ilustración se muestran algunos ejemplos.

![Ilustración de diferentes pinceles](../designers/media/wpfintrofigure6.png)

Para obtener más información, vea [Información general sobre pinceles de WPF](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>Representación en 3D

WPF también incluye funciones de representación en 3D que se integran con los gráficos en 2D para permitir la creación de interfaces de usuario más atractivas e interesantes. Por ejemplo, en la siguiente ilustración se muestran imágenes en 2D representadas en formas en 3D.

![Captura de pantalla de ejemplo Visual3D](../designers/media/wpfintrofigure13.png)

Para obtener más información, vea [Información general sobre gráficos 3D](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animación

El soporte de animación de WPF permite hacer que los controles crezcan, tiemblen, giren o se desvanezcan, crear transiciones de página interesantes y mucho más. Se puede animar la mayoría de las clases de WPF, incluso las clases personalizadas. En la siguiente ilustración se muestra una animación simple en acción.

![Imágenes de un cubo animado](../designers/media/wpfintrofigure7.png)

Para obtener más información, vea [Información general sobre animaciones](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Multimedia

Una manera de mostrar contenido enriquecido es mediante el uso de medios audiovisuales (multimedia). WPF proporciona compatibilidad especial con imágenes, vídeo y audio.

### <a name="images"></a>Imágenes

Las imágenes son comunes a la mayoría de las aplicaciones y WPF proporciona varias maneras de usarlas. La siguiente ilustración muestra una interfaz de usuario con un cuadro de lista que contiene imágenes en miniatura. Cuando se selecciona una miniatura, aparece la imagen a tamaño completo.

![Imágenes en miniatura e imagen a tamaño completo](../designers/media/wpfintrofigure8.png)

Para obtener más información, vea [Información general sobre imágenes](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Vídeo y audio

El control <xref:System.Windows.Controls.MediaElement> es capaz de reproducir vídeo y audio, y es lo suficientemente flexible como para ser la base de un reproductor multimedia personalizado. El marcado XAML siguiente implementa un reproductor multimedia.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

La ventana en la siguiente figura muestra el control <xref:System.Windows.Controls.MediaElement> en acción.

![Control MediaElement con audio y vídeo](../designers/media/wpfintrofigure1.png)

Para obtener más información, vea [Gráficos y multimedia](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Texto y tipografía

Para facilitar la representación de texto de alta calidad, WPF ofrece las siguientes características:

- Compatibilidad con fuentes OpenType.

- Mejoras de ClearType.

- Alto rendimiento que saca partido de la aceleración de hardware.

- Integración de texto con multimedia, gráficos y animación.

- Compatibilidad con fuentes internacionales y mecanismos de reserva.

A modo de demostración de la integración del texto con gráficos, en la siguiente ilustración se muestra la implementación de decoraciones en el texto.

![Texto con diversas decoraciones de texto](../designers/media/wpfintrofigure23.png)

Para obtener más información, consulte [Tipografía en Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Personalización de aplicaciones de WPF

Hasta este punto, hemos estudiado los bloques de creación de WPF fundamentales para desarrollar aplicaciones. El modelo de aplicación se usa para hospedar y distribuir el contenido de las aplicaciones, que está compuesto principalmente de controles. Para simplificar la organización de los controles de una interfaz de usuario y asegurarse de que la organización se conserve aunque se modifiquen el tamaño de la ventana y la configuración de pantalla, se usa el sistema de diseño de WPF. Debido a que la mayoría de las aplicaciones permiten a los usuarios interactuar con los datos, se usa el enlace de datos para reducir el trabajo de la integración de la interfaz de usuario con los datos. Para mejorar la apariencia visual de la aplicación, se usa la amplia gama de gráficos, animación y multimedia compatibilidad que proporciona WPF.

Sin embargo, a menudo los conceptos básicos no bastan para crear y administrar realmente una experiencia del usuario diferenciada y visualmente impactante. Es posible que los controles estándar de WPF no se integren con la apariencia deseada de la aplicación. Es posible que los datos no se muestren del modo más eficaz. La apariencia y el funcionamiento predeterminados de los temas de Windows pueden no ser adecuados para proporcionar la experiencia global del usuario con respecto a la aplicación. En muchos aspectos, una tecnología de presentación requiere de extensibilidad visual tanto como cualquier otro tipo de extensibilidad.

Por este motivo, WPF proporciona una variedad de mecanismos para crear experiencias del usuario únicas, incluido un modelo de contenido enriquecido para los controles, desencadenadores, control y plantillas de datos, estilos, recursos de interfaz de usuario y temas y máscaras.

### <a name="content-model"></a>Modelo de contenido

El propósito principal de la mayoría de los controles de WPF es mostrar el contenido. En WPF, el tipo y el número de elementos que pueden constituir el contenido de un control se conoce como *modelo de contenido*del control. Algunos controles pueden contener un solo elemento y tipo de contenido. Por ejemplo, el contenido de un control <xref:System.Windows.Controls.TextBox> es un valor de cadena que se asigna a la propiedad <xref:System.Windows.Controls.TextBox.Text%2A> . En el siguiente ejemplo se establece el contenido de un control <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

En la siguiente ilustración se muestra el resultado.

![Control TextBox que contiene texto](../designers/media/wpfintrofigure21.png)

Otros controles, sin embargo, pueden contener varios elementos de diferentes tipos de contenido. El contenido de un control <xref:System.Windows.Controls.Button>, especificado por la propiedad <xref:System.Windows.Controls.ContentControl.Content%2A>, puede contener diversos elementos, incluidos los controles de diseño, texto, imágenes y formas. En el siguiente ejemplo se muestra un control <xref:System.Windows.Controls.Button> con contenido que incluye los controles <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>y <xref:System.Windows.Controls.MediaElement>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

En la siguiente ilustración se muestra el contenido de este botón.

![Botón que tiene varios tipos de contenido](../designers/media/wpfintrofigure22.png)

Para obtener más información sobre los tipos de contenido admitidos por los diversos controles, vea [Modelo de contenido de WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Desencadenadores

Aunque el propósito principal del marcado XAML es implementar la apariencia de la aplicación, también se puede usar XAML para implementar algunos aspectos del comportamiento de la aplicación. Un ejemplo es el uso de desencadenadores para cambiar la apariencia de una aplicación según las interacciones del usuario. Para obtener más información, vea [Aplicar estilos y plantillas](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="control-templates"></a>Plantillas de control

Normalmente, las interfaces de usuario predeterminadas para los controles de WPF se construyen a partir de otros controles y formas. Por ejemplo, un control <xref:System.Windows.Controls.Button> está compuesto por los controles <xref:Microsoft.Windows.Themes.ButtonChrome> y <xref:System.Windows.Controls.ContentPresenter> . <xref:Microsoft.Windows.Themes.ButtonChrome> proporciona la apariencia del botón estándar, mientras que <xref:System.Windows.Controls.ContentPresenter> muestra el contenido del botón, según lo especificado por la propiedad <xref:System.Windows.Controls.ContentControl.Content%2A> .

A veces, la apariencia predeterminada de un control puede ser incongruente con la apariencia general de una aplicación. En este caso, se puede usar un control <xref:System.Windows.Controls.ControlTemplate> para cambiar la apariencia de la interfaz de usuario del control sin modificar su contenido ni su comportamiento.

En el ejemplo siguiente se muestra cómo cambiar la apariencia de un control <xref:System.Windows.Controls.Button> mediante <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

En este ejemplo, la interfaz de usuario del botón predeterminado se ha reemplazado por una forma <xref:System.Windows.Shapes.Ellipse> que tiene un borde azul marino y se rellena mediante <xref:System.Windows.Media.RadialGradientBrush>. El control <xref:System.Windows.Controls.ContentPresenter> muestra el contenido de <xref:System.Windows.Controls.Button>, "Click Me!". Cuando se hace clic en <xref:System.Windows.Controls.Button> , el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> todavía se provoca como parte del comportamiento predeterminado del control <xref:System.Windows.Controls.Button> . El resultado se muestra en la ilustración siguiente:

![Botón elíptico y una segunda ventana](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Plantillas de datos

Mientras que una plantilla de control permite especificar la apariencia de un control, una plantilla de datos permite especificar la apariencia del contenido del control. Las plantillas de datos se usan con frecuencia para mejorar la manera de mostrar los datos enlazados. En la siguiente ilustración se muestra la apariencia predeterminada de un control <xref:System.Windows.Controls.ListBox> que está enlazado a una colección de objetos `Task`, donde cada tarea tiene un nombre, una descripción y una prioridad.

![Cuadro de lista con el aspecto predeterminado](../designers/media/wpfintrofigure18.png)

La apariencia predeterminada es la que cabría esperar de un control <xref:System.Windows.Controls.ListBox>. Sin embargo, la apariencia predeterminada de cada tarea contiene únicamente el nombre de tarea. Para mostrar el nombre de la tarea, la descripción y la prioridad, la apariencia predeterminada de los elementos de lista enlazados al control <xref:System.Windows.Controls.ListBox> se debe modificar mediante una plantilla de datos <xref:System.Windows.DataTemplate>. En el código XAML siguiente se define tal plantilla de datos <xref:System.Windows.DataTemplate>, que se aplica a cada tarea mediante el atributo <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

En la siguiente ilustración se muestra el efecto de este código.

![Cuadro de lista que usa una plantilla de datos](../designers/media/wpfintrofigure19.png)

Observe que el control <xref:System.Windows.Controls.ListBox> conserva su comportamiento y apariencia general; sólo se modificó la apariencia del contenido mostrado por el cuadro de lista.

Para obtener más información, vea [Información general sobre plantillas de datos](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Estilos

Los estilos permiten que los desarrolladores y diseñadores estandaricen un aspecto determinado de su producto. WPF proporciona un modelo de estilo eficaz, cuya base es el elemento <xref:System.Windows.Style> . En el siguiente ejemplo se crea un estilo que establece el color de fondo de todos los controles <xref:System.Windows.Controls.Button> de una ventana en `Orange`.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Dado que este estilo tiene como destino todos los controles <xref:System.Windows.Controls.Button>, se aplica automáticamente a todos los botones de la ventana, tal como se muestra en la ilustración siguiente:

![Dos botones de color naranja](../designers/media/wpfintrofigure20.png)

Para obtener más información, vea [Aplicar estilos y plantillas](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="resources"></a>Recursos

Los controles de una aplicación deben compartir la misma apariencia, que puede incluir todo tipo de recursos, desde fuentes y colores de fondo hasta plantillas de control, plantillas de datos y estilos. Se puede usar la compatibilidad de WPF con los recursos de la interfaz de usuario para encapsular estos recursos en una ubicación única y poder reutilizarlos.

En el ejemplo siguiente se define un color de fondo común que comparten los controles <xref:System.Windows.Controls.Button> y <xref:System.Windows.Controls.Label>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

En este ejemplo se implementa un recurso de color de fondo mediante el elemento de propiedad `Window.Resources` . Este recurso está disponible para todos los elementos secundarios de <xref:System.Windows.Window>. Hay una gran variedad de ámbitos de recursos, incluidos los siguientes, que se muestran en el orden en que se resuelven:

1. Un control individual (mediante la propiedad <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> heredada).

2. <xref:System.Windows.Window> o <xref:System.Windows.Controls.Page> (también mediante la propiedad <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> heredada).

3. <xref:System.Windows.Application> (mediante la propiedad <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> ).

La variedad de ámbitos aporta flexibilidad al desarrollador con respecto a la manera de definir y compartir los recursos.

Como alternativa para asociar directamente los recursos a un ámbito determinado, se puede empaquetar uno o varios recursos mediante un <xref:System.Windows.ResourceDictionary> independiente al que puede hacer referencia en otras partes de una aplicación. En el ejemplo siguiente se define un color de fondo predeterminado en un diccionario de recursos.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

 En el ejemplo siguiente se hace referencia al diccionario de recursos definido en el ejemplo anterior para compartirlo en toda la aplicación.

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Los recursos y los diccionarios de recursos constituyen la base de la compatibilidad de WPF con los temas y las máscaras.

Para obtener más información, consulte [Recursos](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Controles personalizados

Aunque WPF proporciona una amplísima compatibilidad con funciones de personalización, puede encontrar situaciones en que los controles existentes de WPF no satisfagan las necesidades de la aplicación o de los usuarios. Esto puede suceder si:

- La UI que se necesita no puede crearse personalizando la apariencia y el funcionamiento de las implementaciones de WPF existentes.

- Las implementaciones de WPF existentes no admiten el comportamiento que se necesita (o lo admiten, pero no fácilmente).

Sin embargo, en este punto puede sacar partido de uno de los tres modelos de WPF para crear un nuevo control. Cada modelo está destinado a un escenario concreto y necesita que el control personalizado se derive de una clase base de WPF determinada. A continuación se muestran los tres modelos:

- **Modelo de control de usuario**. El control personalizado se deriva de <xref:System.Windows.Controls.UserControl> y se crea a partir de uno o varios controles.

- **Modelo de control**. El control personalizado se deriva de <xref:System.Windows.Controls.Control> y se usa para crear implementaciones que separan su comportamiento de su apariencia mediante plantillas, de un modo muy similar a la mayoría de los controles de WPF. Al derivarse de <xref:System.Windows.Controls.Control> , permite mayor libertad para la creación de una UI personalizada que los controles de usuario, pero puede requerir más esfuerzo.

- **Modelo de elemento de marco de trabajo**. Un control personalizado se deriva de <xref:System.Windows.FrameworkElement> cuando su apariencia se define mediante la lógica de representación personalizada (no mediante plantillas).

En el ejemplo siguiente se muestra un control numérico personalizado de arriba/abajo derivado de <xref:System.Windows.Controls.UserControl>.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

En el ejemplo siguiente se muestra el código XAML necesario para incorporar el control de usuario a una ventana ( <xref:System.Windows.Window>).

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

En la ilustración siguiente se muestra el control `NumericUpDown` hospedado en una <xref:System.Windows.Window>.

![UserControl personalizado](../designers/media/wpfintrofigure3.png)

Para obtener más información sobre los controles personalizados, vea [Información general sobre la creación de controles](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>Procedimientos recomendados en WPF

Como sucede con cualquier plataforma de desarrollo, WPF se puede usar de diversas maneras para lograr el resultado deseado. Para asegurarse de que las aplicaciones de WPF proporcionen la experiencia del usuario necesaria y satisfagan las exigencias del público en general, existen procedimientos recomendados de accesibilidad, globalización y localización, y rendimiento. Para obtener más información, consulte:

- [Accesibilidad](/dotnet/framework/ui-automation/accessibility-best-practices)
- [Globalización y localización de WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Rendimiento de aplicaciones de WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Seguridad de WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Pasos siguientes

Hemos analizado las principales características de WPF. Ahora es el momento de que compile su primera aplicación de WPF.

> [!div class="nextstepaction"]
> [Tutorial: Mi primera aplicación de escritorio de WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>Vea también

- [Introducción a WPF](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Recursos de la comunidad de WPF](/dotnet/framework/wpf/getting-started/community-feedback)