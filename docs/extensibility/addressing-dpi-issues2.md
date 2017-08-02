---
title: "Direccionamiento problemas2 de PPP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Soluci&#243;n de problemas de PPP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Envío un número mayor de dispositivos con pantallas de "alta resolución". Estas pantallas suelen tengan más de 200 píxeles por pulgada \(PPP\). Trabajar con una aplicación en estos equipos requerirá contenido para escalarse para satisfacer las necesidades de ver el contenido a una distancia de visualización normal para el dispositivo. A partir de 2014, el objetivo principal para pantallas de alta densidad es dispositivos \(tabletas, equipos portátiles de ostra y teléfonos\) de informática móvil.  
  
 Windows 8.1 y posterior contiene varias características para permitir que estas máquinas trabajar con pantallas y entornos donde el equipo está conectado a ambos alta densidad y densidad estándar se muestra al mismo tiempo.  
  
-   Windows le permite a ajustar el contenido al dispositivo mediante la "que el texto y otros elementos de mayor o menor" establecer \(disponible desde Windows XP\).  
  
-   Windows 8.1 y posterior se ajusta automáticamente el contenido de la mayoría de las aplicaciones para que sea coherente al moverse entre pantallas de diferentes densidades de píxeles. Cuando la pantalla principal es alta densidad \(ajuste de escala de 200%\) y la pantalla secundaria es densidad estándar \(100%\), Windows ajusta automáticamente el contenido de la ventana de aplicación hacia abajo en la pantalla secundaria \(1 píxel se muestra para cada 4 píxeles representadas por la aplicación\).  
  
-   Windows de forma predeterminada a la derecha de escalado para la densidad de píxeles y ver la distancia de la pantalla \(Windows 7 y versiones posteriores, puede configurar OEM\).  
  
-   Windows puede escalar automáticamente contenido de 250% en los nuevos dispositivos que superan 280 ppi \(a partir de Windows 8.1 S14\).  
  
 Windows tiene una manera de trabajar con el escalado de interfaz de usuario para aprovechar los recuentos de píxel mayor. Una aplicación activa la participación en este sistema declarando propio "system cuenta DPI". Las aplicaciones que no se escalan verticalmente por el sistema. Esto puede provocar una experiencia de usuario "parciales" donde toda la aplicación es estira uniformemente en el píxel. Por ejemplo:  
  
 ![Problemas de PPP borrosos](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Para ser compatible con ajuste de escala de PPP se inscribe en Visual Studio y, por tanto, no está "virtualizada."  
  
 Windows \(y Visual Studio\) aprovechan varias tecnologías de interfaz de usuario que tienen diferentes formas de trabajar con el sistema de factores de escala. Por ejemplo:  
  
-   WPF mide los controles de una manera independiente del dispositivo \(unidades, no píxeles\). UI de WPF se escala automáticamente para la resolución actual.  
  
-   Todos los tamaños de texto independientemente de marco de interfaz de usuario se expresan en puntos y, por lo que se tratan por el sistema como independiente de los PPP. Texto de Win32, formularios Windows Forms y WPF ya escale correctamente cuando se dibuja en el dispositivo de pantalla.  
  
-   Ventanas y cuadros de diálogo de Win32\/formularios Windows Forms tienen medios para habilitar diseño que cambia de tamaño con texto: por ejemplo, a través de la cuadrícula, el flujo y paneles de diseño de tabla. Esto permite evitar ubicaciones de píxel codificado de forma rígida que no se escalan cuando aumentan los tamaños de fuente.  
  
-   Iconos proporcionados por el sistema o recursos basándose en las métricas del sistema \(por ejemplo, SM\_CXICON y SM\_CXSMICON\) ya se escalan verticalmente.  
  
## Win32 anteriores \(GDI, GDI \+\) y la interfaz de usuario basada en formularios Windows Forms  
 Aunque WPF ya es alta con reconocimiento de PPP, gran parte de nuestro código basado en Win32\/GDI no se escribió originalmente con reconocimiento de PPP en mente. Windows ofrece las API de ajuste de PPP. Correcciones para problemas de Win32 deben utilizar coherente en todo el producto. Visual Studio ha proporcionado una aplicación auxiliar de biblioteca de clases para evitar duplicar la funcionalidad y garantizar la coherencia del producto.  
  
## Imágenes de alta resolución  
 Esta sección es principalmente para los desarrolladores extender Visual Studio 2013. Para Visual Studio 2015, use el servicio de imágenes que está integrado en Visual Studio. También es posible que necesite compatibilidad\/destino muchas versiones de Visual Studio y lo que el uso del servicio de imágenes en 2015 no es una opción porque no existe en versiones anteriores. Esta sección es también a continuación.  
  
## El escalado de las imágenes que son demasiado pequeñas  
 Imágenes que son demasiado pequeñas pueden "escaladas" y se procesa en GDI y WPF con algunos métodos comunes. Clases de aplicación auxiliar PPP administradas están disponibles para integradores de Visual Studio internos y externos a escala iconos, mapas de bits, imagestrips y imagelists de dirección. Basadas en Win32 nativo C \/ C \+\+ aplicaciones auxiliares están disponibles para el escalado HICON, HBITMAP, HIMAGELIST y VsUI::GdiplusImage. Normalmente el escalado de un mapa de bits, sólo requiere un cambio de una línea después de incluir una referencia a la biblioteca auxiliar. Por ejemplo:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Escalado imagelist depende de si se completa en tiempo de carga imagelist, o se agrega en tiempo de ejecución. Si completa en tiempo de carga, llame a LogicalToDeviceUnits\(\) con el componente imagelist como lo haría con un mapa de bits. Cuando el código se debe cargar un mapa de bits individual antes de crear la lista de imágenes, asegúrese de escalar el tamaño de la imagen de la lista de imágenes:  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 En código nativo, las dimensiones se pueden escalar al crear imagelist como sigue:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funciones de la biblioteca permiten especificar el algoritmo de ajuste de tamaño. Cuando escala imágenes se coloquen en imagelists, asegúrese de especificar el color de fondo que se usa para la transparencia o use NearestNeighbor escalado \(lo que hará que las distorsiones en 125% y 150%\).  
  
 Consulte la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentación en MSDN.  
  
 En la tabla siguiente se muestra ejemplos de cómo se deben escalar imágenes a PPP correspondiente factores de escala. Las imágenes en verde indican nuestra recomendación a partir de Visual Studio 2013 \(ajuste de PPP de 100 a 200%\):  
  
 ![Escalado de problemas de PPP](~/extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## Problemas de diseño  
 Problemas comunes de diseño pueden evitarse principalmente manteniendo puntos en la escala de la interfaz de usuario y relativos a otro, en lugar de mediante ubicaciones absolutas \(específicamente, en unidades de píxeles\). Por ejemplo:  
  
-   Posiciones de diseño o texto que necesite ajustar a cuenta para las imágenes de escala real.  
  
-   Columnas de cuadrículas deben tener anchos ajustados para el texto de la escala real.  
  
-   Codificado de forma rígida tamaños o espacio entre los elementos también necesitará aumentarse. Los tamaños que solo se basan en las dimensiones del texto son suelen funcionar correctamente, ya que las fuentes se escalan de forma automática.  
  
 Funciones auxiliares están disponibles en la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> clase para permitir el ajuste de escala de los ejes X e Y:  
  
-   LogicalToDeviceUnitsX\/LogicalToDeviceUnitsY \(funciones permite escalar en X y el eje Y\)  
  
-   espacio de int \= DpiHelper.LogicalToDeviceUnitsX \(10\);  
  
-   alto de int \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\);  
  
 Hay sobrecargas LogicalToDeviceUnits para permitir el escalado de objetos como Rect, punto y tamaño.  
  
## Mediante la clase\/biblioteca de DPIHelper a escalar imágenes y diseño  
 La biblioteca auxiliar de PPP de Visual Studio está disponible en formatos nativos y administrados y se puede usar fuera del shell de Visual Studio por otras aplicaciones.  
  
 Para usar la biblioteca, vaya a la [ejemplos de extensibilidad de Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) y clonar en el ejemplo de alta DPI\_Images\_Icons  
  
 En archivos de origen, incluya VsUIDpiHelper.h y llamar a las funciones estáticas de la clase VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  No utilice las funciones auxiliares en variables estáticas de nivel de clase o módulo. La biblioteca también utiliza variables estáticas para la sincronización de subprocesos y se puede encontrar problemas de inicialización de la orden. Convertir los datos estáticos a variables de miembro no estáticas, o incluirlos en una función \(de manera que crearse en el primer acceso\).  
  
 Para obtener acceso a las funciones auxiliares de PPP desde código administrado que se ejecutará dentro del entorno de Visual Studio:  
  
-   El proyecto debe hacer referencia a la versión más reciente de MPF de Shell. Por ejemplo:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Asegúrese de que el proyecto contiene referencias a **System.Windows.Forms**, **PresentationCore**, y **PresentationUI**.  
  
-   En el código, utilice la **Microsoft.VisualStudio.PlatformUI** espacio de nombres y llamar a funciones estáticas de la clase DpiHelper. Para los tipos compatibles \(puntos, tamaños, rectángulos y así sucesivamente\), hay siempre la escalan de las funciones de extensión que devuelven nuevos objetos. Por ejemplo:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## Tratar con tolerancia de imagen WPF en la interfaz de usuario de zoom  
 En WPF, los mapas de bits cambian de tamaño automáticamente por WPF para el nivel de zoom actual de PPP con un algoritmo de bicúbica de alta calidad \(valor predeterminado\), que funciona bien para imágenes o capturas de pantalla grande, pero que es inapropiado para los iconos de elemento de menú porque introduce tolerancia percibido.  
  
 Recomendaciones:  
  
-   Para las ilustraciones de imagen y titulares de logotipo, el valor predeterminado <xref:System.Windows.Media.BitmapScalingMode> se podría utilizar el modo de cambio de tamaño.  
  
-   Para los elementos de menú y las imágenes iconografía, la <xref:System.Windows.Media.BitmapScalingMode> debe usarse cuando no genera otros artefactos de distorsión eliminar la tolerancia \(en 200 y 300%\).  
  
-   •	Para los niveles de zoom grande no múltiplos de 100% \(por ejemplo, 250% o % de 350\), escalar imágenes iconografía con Bicúbica produce aproximada, decoloración de interfaz de usuario. Se obtiene un resultado mejor escala de la imagen con NearestNeighbor al múltiplo más grande del 100% \(por ejemplo, 200% o 300%\) y escalar con bicúbica desde allí. Consulte el caso especial: prescaling imágenes WPF PPP grandes niveles para obtener más información.  
  
 La clase DpiHelper en el espacio de nombres Microsoft.VisualStudio.PlatformUI proporciona un miembro <xref:System.Windows.Media.BitmapScalingMode> que se puede utilizar para el enlace. Permitirá que el shell de Visual Studio controlar el modo de escalado en todo el producto de manera uniforme, según el factor de escala de PPP de mapa de bits.  
  
 Para usarla en XAML, agregue:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 El shell de Visual Studio ya establece esta propiedad en los cuadros de diálogo y ventanas de nivel superior. Interfaz de usuario basada en WPF ejecuta en Visual Studio ya heredará. Si la configuración no se propaga a sus partes específicas de la interfaz de usuario, se puede establecer en el elemento raíz de la interfaz de usuario de WPF en XAML. Lugares donde esto pasa incluyen elementos emergentes, en los elementos primarios de Win32, y ventanas de diseñador que se ejecutan fuera de procesan, como Blend.  
  
 Alguna IU puede escalar independientemente del nivel de zoom de PPP de conjunto del sistema, como el editor de texto de Visual Studio y los diseñadores de WPF \(escritorio de WPF y tienda Windows\). En estos casos, no debería utilizarse DpiHelper.BitmapScalingMode. Para corregir este problema en el editor, el equipo del IDE creado una propiedad personalizada denominada RenderOptions.BitmapScalingMode. Establecer valor de la propiedad apoyen o NearestNeighbor según el nivel de zoom combinado del sistema y la interfaz de usuario.  
  
## Caso especial: prescaling imágenes WPF para los grandes niveles de PPP  
 Para los niveles de zoom muy grandes que no son múltiplos de 100% \(por ejemplo, 250%, % 350 etc.\), escalar imágenes iconografía con resultados bicúbica en aproximada, decoloración de interfaz de usuario. La impresión de estas imágenes junto con texto nítido casi es similar de una ilusión óptica. Las imágenes parecen estar más cerca al ojo y desenfocadas en relación con el texto. Escala de la imagen con NearestNeighbor al múltiplo más grande del 100% \(por ejemplo, 200% o 300%\) y escalar con bicúbica al resto \(% de 50 adicional\) puede mejorar el resultado escalado en este tamaño ampliada.  
  
 El siguiente es un ejemplo de las diferencias en los resultados, donde se escala la primera imagen con el algoritmo de ajuste de escala de doble mejorado \-\> 100% 200% \-\> 250% y el segundo sólo con bicúbica 100% \-\> 250%.  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 Para habilitar la interfaz de usuario deben usar esta escala doble, el marcado XAML para mostrar cada elemento de imagen deberá modificarse. Los ejemplos siguientes muestran cómo utilizar escalado doble en WPF en Visual Studio mediante la biblioteca de DpiHelper y Shell.12\/14.  
  
 Paso 1: Prescale la imagen a 200%, 300% y así sucesivamente con NearestNeighbor.  
  
 Prescale la imagen utilizando un convertidor de cualquier aplicado en un enlace o con una extensión de marcado XAML. Por ejemplo:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Si la imagen también se debe aplicar un tema \(más, si no todos, debería\), el marcado puede utilizar un convertidor diferentes que realiza primero los temas de la imagen y previamente, a continuación, la escala. Puede utilizar el marcado <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, dependiendo del resultado de la conversión deseada.  
  
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
  
 Paso 2: Asegurar que el tamaño final es correcto para la resolución actual.  
  
 Dado que WPF escalará la interfaz de usuario para el valor de PPP actual mediante la propiedad BitmapScalingMode establecido en el UIElement, un control de imagen con una imagen prescaled como su origen será dos o tres veces mayor debería. Éstas son un par de formas para contrarrestar este efecto:  
  
-   Si conoce la dimensión de la imagen original al 100%, puede especificar el tamaño exacto del control Image. Estos tamaños reflejan que el tamaño de la interfaz de usuario antes de la escala se aplica.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Si no se conoce el tamaño de la imagen original, LayoutTransform puede utilizarse para reducir el tamaño del objeto de la imagen final. Por ejemplo:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## Habilitar la compatibilidad con HDPI para WebOC  
 De forma predeterminada, WebOC controles \(por ejemplo, el control WebBrowser en WPF o la interfaz IWebBrowser2\) no habilitan la detección de HDPI y soporte técnico. El resultado será un control incrustado con contenido de visualización es demasiado pequeño en una pantalla de alta resolución. El siguiente describe cómo habilitar la compatibilidad con configuración elevada de PPP en una instancia de WebOC web específica.  
  
 Implementar la interfaz IDocHostUIHandler \(consulte el artículo MSDN sobre la [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interfaz\):  
  
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
  
 Opcionalmente, implementar la interfaz ICustomDoc \(consulte el artículo MSDN sobre la [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interfaz\):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Asociar la clase que implementa IDocHostUIHandler con documento de WebOC. Si implementa la interfaz ICustomDoc anterior, a continuación, tan pronto como propiedad de documento de WebOC es válida, convertirlo en un ICustomDoc y llamar al método SetUIHandler, pasando la clase que implementa IDocHostUIHandler.  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Si no se implementa la interfaz ICustomDoc, a continuación, tan pronto como propiedad de documento de WebOC es válida, debe convertirlo a un IOleObject y llame al método SetClientSite, pasando la clase que implementa IDocHostUIHandler. Establecer el indicador DOCHOSTUIFLAG\_DPI\_AWARE en el DOCHOSTUIINFO pasado a la llamada al método GetHostInfo:  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Esto debería ser todo lo que necesita para obtener el control WebOC admita HPDI.  
  
## Sugerencias  
  
1.  Si cambia la propiedad de documento en el control de WebOC, debe asociar el documento con la clase IDocHostUIHandler.  
  
2.  Si lo anterior no funciona, hay un problema conocido con WebOC no recoge el cambio de la marca de PPP. La forma más fiable de arreglar esto es alternar el zoom óptico de WebOC, dos llamadas de significado con dos valores diferentes para el porcentaje de zoom. Además, si se requiere esta solución alternativa, pueden ser necesario para realizar en cada llamada de navegar.  
  
    ```c#  
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