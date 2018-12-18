---
title: Direccionamiento PPP problemas2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542676de0efabcfa58945fc1572fc5539f52c209
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752530"
---
# <a name="addressing-dpi-issues"></a>Solución de problemas de PPP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un número creciente de dispositivos se entrega con pantallas "alta resolución". Estas pantallas suelen tengan más de 200 píxeles por pulgada (PPP). Trabajar con una aplicación en estos equipos necesitará contenido necesario escalar verticalmente para satisfacer las necesidades de ver el contenido a una distancia de visualización normal para el dispositivo. A partir de 2014, el destino principal para las pantallas de alta densidad es dispositivos (teléfonos, equipos portátiles de ostra y tabletas) de informática móvil.  
  
 Windows 8.1 y versiones posterior contiene varias características para habilitar estas máquinas trabajar con entornos donde la máquina esté conectada a ambos alta densidad y densidad estándar que se muestra al mismo tiempo y los muestra.  
  
- Windows pueden ayudarle a ajustar el contenido al dispositivo con el "que el texto y otros elementos mayores o menores" configuración (disponible desde Windows XP).  
  
- Windows 8.1 y versiones posteriores se ajusta automáticamente contenido para la mayoría de las aplicaciones para que sea coherente cuando se mueve entre pantallas de diferentes densidades de píxeles. Cuando la pantalla principal es alta densidad (ajuste de escala de 200%) y la pantalla secundaria es densidad estándar (100%), Windows ajusta automáticamente el contenido de la ventana de aplicación hacia abajo en la pantalla secundaria (1 píxel que se muestra para cada 4 píxeles representados por el aplicación).  
  
- Windows predeterminada será el derecho de escalado para la densidad de píxeles y visualización de distancia para la pantalla (Windows 7 y versiones posteriores, configurable por el OEM).  
  
- Windows pueden escalar automáticamente contenido de hasta 250% en nuevos dispositivos que superan 280 ppi (a partir de Windows 8.1 S14).  
  
  Windows tiene una manera de trabajar con el escalado de la interfaz de usuario para aprovechar las ventajas de recuentos de píxel mayor. Una aplicación no participa en este sistema mediante la declara a sí mismo "PPP del sistema". Las aplicaciones que esta operación no se escalen verticalmente por el sistema. Esto puede dar lugar a una experiencia de usuario "aproximada" donde toda la aplicación es el ajusta uniformemente en el píxel. Por ejemplo:  
  
  ![PPP emite aproximada](../extensibility/media/dpi-issues-fuzzy.png "PPP emite aproximada")  
  
  Visual Studio decida en que se va a escalar reconocimiento de PPP y, por tanto, no está "virtualizada."  
  
  Windows (y Visual Studio) aprovechan varias tecnologías de interfaz de usuario, que tienen diferentes maneras de abordar establecidos por el sistema de factores de escala. Por ejemplo:  
  
- WPF mide los controles de una manera independiente del dispositivo (unidades, no en píxeles). UI de WPF se escala automáticamente para el valor de PPP actual.  
  
- Todos los tamaños de texto independientemente del marco de interfaz de usuario se expresan en puntos y, por lo que se tratan por el sistema como independiente de los PPP. Texto de WPF, WinForms y Win32 ya escale correctamente cuando se dibuja en el dispositivo de pantalla.  
  
- Ventanas y cuadros de diálogo Win32/formularios Windows Forms tienen medios para habilitar el diseño que cambia de tamaño con texto: por ejemplo, a través de la cuadrícula, flow y paneles de diseño de tabla. Estas permiten evitar las ubicaciones de píxel codificado de forma rígida que no se escalan cuando aumentan los tamaños de fuente.  
  
- Iconos proporcionados por el sistema o recursos basándose en las métricas del sistema (por ejemplo, SM_CXICON y SM_CXSMICON) ya se escalen verticalmente.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 anteriores (GDI, GDI +) y la interfaz de usuario basada en formularios Windows Forms  
 Aunque WPF ya es alto con reconocimiento de PPP, gran parte de nuestro código basado en Win32/GDI no se escribió originalmente con reconocimiento de PPP en mente. Windows ha proporcionado las API de escala de PPP. Correcciones para problemas de Win32 deben utilizar coherente en todo el producto. Visual Studio ha proporcionado una aplicación auxiliar de biblioteca de clases para evitar duplicar la funcionalidad y garantizar la coherencia en todo el producto.  
  
## <a name="high-resolution-images"></a>Imágenes de alta resolución  
 En esta sección es principalmente para los desarrolladores extender Visual Studio 2013. Para Visual Studio 2015, use el servicio de imágenes que está integrado en Visual Studio. También es posible que necesite soporte técnico y muchas versiones de Visual Studio de destino y, por tanto, mediante el servicio de imágenes en 2015 no es una opción porque no existe en las versiones anteriores. En esta sección también es para usted, a continuación.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Escalado vertical de las imágenes que son demasiado pequeñas  
 Las imágenes que son demasiado pequeñas pueden ser "escalar verticalmente" y procesa en GDI y WPF con algunos métodos comunes. Clases auxiliares de PPP administradas están disponibles para los integradores de Visual Studio internos y externos a dirección escalado iconos, mapas de bits, imagestrips y imagelists. Basado en Win32 nativo C / C ++ aplicaciones auxiliares están disponibles para el escalado HICON, HBITMAP, HIMAGELIST y VsUI::GdiplusImage. Normalmente, el escalado de un mapa de bits, sólo requiere un cambio de una línea después de incluir una referencia a la biblioteca auxiliar. Por ejemplo:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Escalado de una lista de imágenes depende de si el componente imagelist completada en tiempo de carga o se anexa en tiempo de ejecución. Si completa en tiempo de carga, llame a LogicalToDeviceUnits() con el componente imagelist como lo haría en un mapa de bits. Cuando el código necesita cargar un mapa de bits individual antes de crear la lista de imágenes, asegúrese de escalar el tamaño de la imagen de la lista de imágenes:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 En código nativo, las dimensiones se pueden escalar al crear la lista de imágenes como sigue:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funciones de la biblioteca permiten especificar el algoritmo de cambio de tamaño. Cuando escala imágenes colocarse en imagelists, asegúrese de especificar el color de fondo que se usa para la transparencia o usar NearestNeighbor escalado (que hará que las distorsiones en 125% y 150%).  
  
 Consulte la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentación en MSDN.  
  
 En la tabla siguiente se muestra ejemplos de cómo se deben escalar imágenes a PPP correspondiente factores de escala. Las imágenes en verde indican nuestra práctica recomendada a partir de Visual Studio 2013 (escala de PPP de 100 a 200%):  
  
 ![Escalado de problemas de PPP](../extensibility/media/dpi-issues-scaling.png "escalado de problemas de PPP")  
  
## <a name="layout-issues"></a>Problemas de diseño  
 Problemas comunes de diseño pueden evitarse principalmente manteniendo puntos en la escala de la interfaz de usuario y relacionadas entre sí en lugar de utilizar las ubicaciones absolutas (específicamente, en unidades de píxeles). Por ejemplo:  
  
- Las posiciones de diseño o texto tenga que ajustar a la cuenta para las imágenes de escalados.  
  
- Las columnas de las cuadrículas deben tener anchos ajustados para el texto escalados.  
  
- Tamaños de disco duro de forma rígida o espacio entre los elementos también debe aumentarse. Los tamaños que se basan únicamente en las dimensiones del texto son suelen funcionar correctamente, ya que las fuentes automáticamente se escalen verticalmente.  
  
  Funciones auxiliares están disponibles en el <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> clase para permitir el escalado en el eje X e Y:  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funciones de permiten el escalado en X o eje Y)  
  
- espacio de int = DpiHelper.LogicalToDeviceUnitsX (10);  
  
- alto de int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
  Hay sobrecargas LogicalToDeviceUnits para permitir el escalado de objetos como Rect, punto y tamaño.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Uso de la clase/biblioteca de DPIHelper a escalar imágenes y diseño  
 La biblioteca auxiliar de PPP de Visual Studio está disponible en los formularios nativos y administrados y puede usarse por otras aplicaciones fuera de Visual Studio shell.  
  
 Para usar la biblioteca, vaya a la [ejemplos de extensibilidad de Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) y clonar el ejemplo de alta DPI_Images_Icons  
  
 En archivos de origen, incluya VsUIDpiHelper.h y llamar a las funciones estáticas de la clase VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  No use las funciones auxiliares en variables estáticas de nivel de clase o módulo. La biblioteca también utiliza variables estáticas para la sincronización de subprocesos y pueden surgir problemas de inicialización de orden. Convertir esas variables estáticas a las variables de miembro no estáticas, o agruparlos en una función (por lo que crearse en el primer acceso).  
  
 Para obtener acceso a las funciones auxiliares de PPP desde código administrado que se ejecutará dentro del entorno de Visual Studio:  
  
-   El proyecto de consumo debe hacer referencia a la versión más reciente de MPF de Shell. Por ejemplo:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Asegúrese de que el proyecto tiene referencias a **System.Windows.Forms**, **PresentationCore**, y **PresentationUI**.  
  
-   En el código, utilice el **Microsoft.VisualStudio.PlatformUI** espacio de nombres y llamar a funciones estáticas de la clase DpiHelper. Para los tipos compatibles (puntos, tamaños, rectángulos etc.), hay siempre escalan de las funciones de extensión que devuelven nuevos objetos. Por ejemplo:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Trabajar con tolerancia de la imagen WPF en la interfaz de usuario se puede acercar  
 En WPF, los mapas de bits cambian de tamaño automáticamente por WPF para el nivel de zoom actual de PPP con un algoritmo de bicúbica de alta calidad (valor predeterminado), que funciona bien para las imágenes o capturas de pantalla grande, pero no es apropiado para los iconos de elementos de menú porque introduce percibido tolerancia .  
  
 Recomendaciones:  
  
- Para el logotipo de la imagen y pancartas de material gráfico, el valor predeterminado <xref:System.Windows.Media.BitmapScalingMode> se podría usar el modo de cambio de tamaño.  
  
- Para los elementos de menú y las imágenes de iconografía, el <xref:System.Windows.Media.BitmapScalingMode> debe usarse cuando no hace que otros artefactos distorsión eliminar la tolerancia (en % de 200 y 300%).  
  
- • Para zoom grande niveles no múltiplos de 100% (por ejemplo, 250% o % de 350), escala de imágenes de iconografía con bicúbica resultados en la interfaz de usuario aproximada, decoloración. Primera escala de la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%) y escalado en bicúbica desde allí se obtienen mejores resultados. Consulte el caso especial: prescaling imágenes WPF para PPP grande niveles para obtener más información.  
  
  La clase DpiHelper en el espacio de nombres Microsoft.VisualStudio.PlatformUI proporciona un miembro <xref:System.Windows.Media.BitmapScalingMode> que puede utilizarse para el enlace. Permitirá que el shell de Visual Studio controlar el modo de escalado en todo el producto de manera uniforme, según el factor de escala de PPP de mapa de bits.  
  
  Para usarlo en XAML, agregue:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 El shell de Visual Studio ya establece esta propiedad en los cuadros de diálogo y ventanas de nivel superior. Interfaz de usuario basada en WPF que se ejecuta en Visual Studio ya lo heredará. Si la configuración no se propaga a sus partes específicas de la interfaz de usuario, se puede establecer en el elemento raíz de la interfaz de usuario de WPF y XAML. Lugares donde esto ocurre incluyen los elementos emergentes en los elementos con elementos primarios de Win32, y ventanas del diseñador que se ejecutan fuera de procesan, como Blend.  
  
 Alguna interfaz de usuario puede escalar independientemente del nivel de zoom de PPP de conjunto del sistema, como el editor de texto de Visual Studio y diseñadores de WPF (escritorio de WPF y Windows Store). En estos casos, no debe usarse DpiHelper.BitmapScalingMode. Para corregir este problema en el editor, el equipo del IDE creado una propiedad personalizada denominada RenderOptions.BitmapScalingMode. Establecer ese valor de propiedad en apoyen o NearestNeighbor según el nivel de zoom combinada del sistema y la interfaz de usuario.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: prescaling imágenes WPF para los grandes niveles de PPP  
 Para los niveles de zoom muy grandes que no sean múltiplos de 100% (por ejemplo, 250%, % de 350 etc.), escala de imágenes iconografía con bicúbica resultados en la interfaz de usuario aproximada, decoloración. La impresión de estas imágenes junto con texto claro es casi similar a la de una ilusión óptica. Las imágenes aparecerán a acercarse más al ojo y desenfocadas en relación con el texto. El resultado de escalado en este tamaño ampliada se puede mejorar mediante la primera escala de la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%) y escalado en bicúbica al resto (% de 50 adicional).  
  
 El siguiente es un ejemplo de las diferencias en los resultados, donde se escala la primera imagen con el algoritmo de ajuste de escala doble mejorado -> 100% 200% -> 250% y la segunda se acaba con bicúbica 100% -> 250%.  
  
 ![PPP emite el ejemplo de escalado doble](../extensibility/media/dpi-issues-double-scaling-example.png "PPP emite doble ejemplo de escalado")  
  
 Para habilitar la interfaz de usuario usar este ajuste de escala doble, el marcado XAML para mostrar cada elemento de imagen debe modificarse. Los ejemplos siguientes muestran cómo usar el ajuste de escala doble en WPF en Visual Studio mediante la biblioteca de DpiHelper y Shell.12/14.  
  
 Paso 1: Prescale la imagen a 200%, 300% y así sucesivamente con NearestNeighbor.  
  
 Prescale la imagen mediante cualquier un convertidor que se aplica en un enlace o con una extensión de marcado XAML. Por ejemplo:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Si la imagen también debe ser temáticas (más, si no todos, debería), el marcado puede utilizar un convertidor diferentes que realiza primero los temas de la imagen y, a continuación, el escalado previamente. Puede usar el marcado <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, según el resultado de la conversión deseada.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Paso 2: Asegurarse que el tamaño final es correcto para el valor de PPP actual.  
  
 Dado que WPF escalará la interfaz de usuario para el valor de PPP actual mediante la propiedad BitmapScalingMode establecido en el UIElement, un control de imagen con una imagen prescaled como su origen tendrá un aspecto dos o tres veces mayor que la debería. Los siguientes son un par de formas para contrarrestar este efecto:  
  
-   Si conoce la dimensión de la imagen original al 100%, puede especificar el tamaño exacto del control Image. Estos tamaños refleja que el tamaño de la interfaz de usuario antes de escalar se aplica.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Si no se conoce el tamaño de la imagen original, puede utilizarse una LayoutTransform para reducir verticalmente el objeto de la imagen final. Por ejemplo:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitar la compatibilidad con HDPI para WebOC  
 De forma predeterminada, controles WebOC (por ejemplo, el control WebBrowser en WPF o la interfaz IWebBrowser2) no habilitan la detección de HDPI y soporte técnico. El resultado será un control incrustado con el contenido de visualización es demasiado pequeño en una pantalla de alta resolución. El siguiente describe cómo habilitar la compatibilidad con valores altos de PPP en una instancia de WebOC web específica.  
  
 Implementar la interfaz IDocHostUIHandler (consulte el artículo MSDN sobre el [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interfaz):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Opcionalmente, implementa la interfaz de ICustomDoc (consulte el artículo MSDN sobre el [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interfaz):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Asociar la clase que implementa IDocHostUIHandler con el documento de WebOC. Si implementa la interfaz ICustomDoc anterior, a continuación, tan pronto como propiedad de documento del WebOC es válida, convertirlo en un ICustomDoc y llamar al método SetUIHandler, pasando la clase que implementa IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Si no implementó la interfaz ICustomDoc, a continuación, tan pronto como propiedad de documento del WebOC es válida, deberá convertirlo a IOleObject y llamar al método SetClientSite, pasando la clase que implementa IDocHostUIHandler. Establezca la marca DOCHOSTUIFLAG_DPI_AWARE en el DOCHOSTUIINFO pasada a la llamada de método GetHostInfo:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Debe tratarse de todo lo que necesita para obtener el control WebOC admita HPDI.  
  
## <a name="tips"></a>Sugerencias  
  
1.  Si cambia la propiedad de documento en el control WebOC, es posible que deba volver a asociar el documento con la clase IDocHostUIHandler.  
  
2.  Si lo anterior no funciona, hay un problema conocido con WebOC no recoge el cambio en la marca de PPP. La forma más fiable de corregir esto es activar o desactivar el zoom óptico del WebOC dos llamadas de significado con dos valores diferentes para el porcentaje de zoom. Además, si se requiere esta solución alternativa, podría ser necesario lleve a cabo en cada llamada de navegar.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```

