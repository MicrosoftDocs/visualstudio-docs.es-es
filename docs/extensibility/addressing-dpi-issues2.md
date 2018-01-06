---
title: Direccionamiento PPP problemas2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6218e01d061bbf65e0cae051050076e4b8267a2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="addressing-dpi-issues"></a>Solución de problemas de PPP
Un número mayor de dispositivos se entrega con pantallas "alta resolución". Estas pantallas suelen tengan más de 200 píxeles por pulgada (PPP). Trabajar con una aplicación en estos equipos requerirá contenido para escalarse para satisfacer las necesidades de ver el contenido a una distancia de visualización normal para el dispositivo. A partir de 2014, el destino principal para pantallas de alta densidad es informática dispositivos (tabletas, equipos portátiles cocha y teléfonos) móvil.  
  
 Windows 8.1 y posterior contiene varias características para habilitar estas máquinas trabajar con los entornos donde la máquina esté conectada a ambos alta densidad y densidad estándar que se muestra al mismo tiempo y muestra.  
  
-   Windows puede le permiten ajustar el contenido al dispositivo utilizando el "que el texto y otros elementos de mayor o menor" configuración (disponible desde Windows XP).  
  
-   Windows 8.1 y versiones posteriores se ajusta automáticamente contenido para la mayoría de las aplicaciones sea coherente cuando se mueven entre pantallas de las densidades de píxeles que no son iguales. Cuando la pantalla principal es alta densidad (ajuste de escala de 200%) y la pantalla secundaria es densidad estándar (100%), Windows ajusta automáticamente el contenido de la ventana de aplicación hacia abajo en la pantalla secundaria (1 píxel que se muestra para cada 4 píxeles se representa mediante el aplicación).  
  
-   Windows predeterminado para el derecho de escalado para la densidad de píxeles y visualización de distancia para la pantalla (Windows 7 y versiones posteriores, puede configurar OEM).  
  
-   Windows puede escalar automáticamente contenido seguridad a 250% nuevos dispositivos que superan 280 ppi (a partir de Windows 8.1 S14).  
  
 Windows tiene una manera de trabajar con el escalado de interfaz de usuario para aprovechar las ventajas de recuentos de píxel mayor. Una aplicación opts en este sistema declara a sí mismo "PPP en cuenta del sistema." Las aplicaciones que no lo son escalarse por el sistema. Esto puede dar lugar a una experiencia de usuario "aproximada" donde toda la aplicación es estira uniformemente en el píxel. Por ejemplo:  
  
 ![PPP emite aproximada](../extensibility/media/dpi-issues-fuzzy.png "PPP emite aproximada")  
  
 Visual Studio opts en sea compatible con ajuste de escala de PPP y, por tanto, no está "virtualizada."  
  
 Windows (y Visual Studio) aprovechan varias tecnologías de interfaz de usuario, que tienen diferentes formas de tratar establecidos por el sistema de factores de escala. Por ejemplo:  
  
-   WPF mide los controles de una manera independiente del dispositivo (unidades, no píxeles). UI de WPF se escala automáticamente para el valor de PPP actual.  
  
-   Todos los tamaños de texto sin tener en cuenta el marco de interfaz de usuario se expresan en puntos y, por lo que se tratan por el sistema como PPP independiente. Texto de Win32, formularios Windows Forms y WPF ya escale correctamente cuando se dibuja en el dispositivo de pantalla.  
  
-   Ventanas y cuadros de diálogo de Win32/formularios Windows Forms tienen medios para habilitar el diseño que cambian de tamaño con texto: por ejemplo, en la cuadrícula, flujo y paneles de diseño de tabla. Estas instrucciones permiten evitar ubicaciones de píxel codificado de forma rígida que no se escalan cuando se incrementan los tamaños de fuente.  
  
-   Iconos proporcionados por el sistema o recursos basándose en las métricas del sistema (por ejemplo, SM_CXICON y SM_CXSMICON) ya se escalan.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 anteriores (GDI, GDI +) y la interfaz de usuario basada en formularios Windows Forms  
 Aunque WPF ya es alta en cuenta PPP, gran parte de nuestro código basado en Win32/GDI no escribió originalmente con reconocimiento de PPP en mente. Windows ofrece las API de ajuste de escala de PPP. Correcciones para problemas de Win32 deben utilizar forma coherente en todo el producto. Visual Studio ha proporcionado una aplicación auxiliar de biblioteca de clases para evitar la duplicación de funcionalidad y garantizar la coherencia en todo el producto.  
  
## <a name="high-resolution-images"></a>Imágenes de alta resolución  
 Esta sección sirve principalmente para los programadores extender Visual Studio 2013. Para Visual Studio 2015, utilizan el servicio de imágenes que está integrado en Visual Studio. También es posible que necesite compatibilidad/muchas versiones de Visual Studio de destino y, por tanto, con el servicio de imágenes en 2015 no es posible porque no existe en versiones anteriores. En esta sección también es para usted, a continuación.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Si se escalan verticalmente las imágenes que son demasiado pequeñas  
 Imágenes que son demasiado pequeñas pueden "ampliar" y se representan en GDI y WPF con algunos métodos comunes. Clases de aplicación auxiliar de PPP administradas están disponibles para los integradores de Visual Studio internos y externos a la dirección de escalado iconos, mapas de bits, imagestrips y imagelists. Basado en Win32 nativo C / C ++ aplicaciones auxiliares están disponibles para el escalado HICON, HBITMAP, HIMAGELIST y VsUI::GdiplusImage. Ajuste de escala de un mapa de bits por lo general, solo requiere un cambio de una línea después de incluir una referencia a la biblioteca auxiliar. Por ejemplo:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Ajuste de escala en una componente imagelist depende de si el componente imagelist está completa en tiempo de carga, o se anexa al tiempo de ejecución. Si completa en tiempo de carga, llame a LogicalToDeviceUnits() con el componente imagelist como lo haría con un mapa de bits. Cuando el código tiene que cargar un mapa de bits individual antes de crear la lista de imágenes, asegúrese de que al escalar el tamaño de la imagen de la lista de imágenes:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 En código nativo, las dimensiones se pueden escalar al crear la lista de imágenes como sigue:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funciones de la biblioteca permiten especificar el algoritmo de ajuste de tamaño. Cuando escala de imágenes que se colocarán en imagelists, asegúrese de especificar el color de fondo que se usa para la transparencia o usar NearestNeighbor escalado (lo que hará que distorsiones en 125% y 150%).  
  
 Consulte la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentación en MSDN.  
  
 En la tabla siguiente se muestra ejemplos de cómo se deben escalar imágenes en PPP correspondiente factores de escala. Las imágenes en color verde denotan nuestro procedimiento recomendado a partir de Visual Studio 2013 (escala de PPP de 100-200%):  
  
 ![Escalado de problemas de PPP](../extensibility/media/dpi-issues-scaling.png "escalado de problemas de PPP")  
  
## <a name="layout-issues"></a>Problemas de diseño  
 Problemas comunes de diseño pueden evitarse principalmente al conservar los puntos en la escala de la interfaz de usuario y relativas entre sí en lugar de utilizar ubicaciones absolutas (específicamente, en unidades de píxeles). Por ejemplo:  
  
-   Posiciones de diseño o texto necesitan para ajustarse a la cuenta para las imágenes de escalado.  
  
-   Columnas de cuadrículas necesitan tener anchos ajustados para el texto escalados.  
  
-   Codificado de forma rígida tamaños o espacio entre los elementos también deberá aumentarse. Los tamaños que se basan únicamente en las dimensiones del texto son suelen funcionar correctamente, porque las fuentes se escalan de forma automática.  
  
 Funciones auxiliares están disponibles en la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> clase para permitir el ajuste de escala en el eje X e Y:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funciones permite escalar en X o eje Y)  
  
-   espacio de int = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   alto de int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Hay sobrecargas LogicalToDeviceUnits para permitir el ajuste de escala en objetos como Rect, el punto y el tamaño.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Uso de la clase/biblioteca de DPIHelper escala de imágenes y diseño  
 La biblioteca de aplicación auxiliar de PPP de Visual Studio está disponible en los formatos nativo y administrados y se puede usar fuera del shell de Visual Studio para otras aplicaciones.  
  
 Para usar la biblioteca, vaya a la [ejemplos de extensibilidad de Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) y clonar el ejemplo de alta DPI_Images_Icons  
  
 En archivos de código fuente, incluir VsUIDpiHelper.h y llame a las funciones estáticas de la clase VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  No use las funciones auxiliares en variables estáticas de nivel de clase o módulo. La biblioteca también usa variables estáticas para la sincronización de subprocesos y que se pueda encontrar problemas de inicialización de pedido. Convertir los datos estáticos a variables de miembro no estáticas, o agruparlos en una función (por lo que crearse en el primer acceso).  
  
 Para obtener acceso a las funciones auxiliares de PPP desde el código administrado que se ejecutará dentro del entorno de Visual Studio:  
  
-   El proyecto debe hacer referencia a la versión más reciente de MPF de Shell. Por ejemplo:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Asegúrese de que el proyecto tiene referencias a **System.Windows.Forms**, **PresentationCore**, y **PresentationUI**.  
  
-   En el código, utilice la **Microsoft.VisualStudio.PlatformUI** funciones estáticas de espacio de nombres y llame al método de clase DpiHelper. Para los tipos compatibles (puntos, tamaños, rectángulos etc.), hay siempre las funciones de extensión que devuelven nuevos objetos de escala. Por ejemplo:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Trabajar con tolerancia de imagen WPF en la interfaz de usuario puede acercar  
 En WPF, los mapas de bits cambian de tamaño automáticamente por WPF para el nivel de zoom actual de PPP con un algoritmo de alta calidad bicúbica (valor predeterminado), que funciona bien para imágenes o capturas de pantalla de gran tamaño, pero no es apropiado para los iconos de elementos de menú porque introduce desenfocan percibido .  
  
 Recomendaciones:  
  
-   Para las ilustraciones de imagen y los banners de logotipo, el valor predeterminado <xref:System.Windows.Media.BitmapScalingMode> podría utilizar el modo de cambio de tamaño.  
  
-   Para elementos de menú y las imágenes de iconography, la <xref:System.Windows.Media.BitmapScalingMode> debe usarse cuando no hacen que otros artefactos de distorsión eliminar desenfocan (en 200% y un 300%).  
  
-   Para un nivel de zoom grande no múltiplos de 100% (por ejemplo, 250% o % de 350), ajuste de escala de imágenes de iconography con Bicúbica produce aproximada, decoloración de interfaz de usuario. Escala de la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%) y ajuste de escala con bicúbica desde allí se obtienen mejores resultados. Vea caso especial: prescaling imágenes WPF para PPP grande niveles para obtener más información.  
  
 La clase DpiHelper en el espacio de nombres Microsoft.VisualStudio.PlatformUI proporciona un miembro <xref:System.Windows.Media.BitmapScalingMode> que se puede utilizar para el enlace. Permitirá el shell de Visual Studio controlar el modo de escalado en todo el producto uniformemente, según el factor de escala de PPP de mapa de bits.  
  
 Para usarlo en XAML, agregue:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 El shell de Visual Studio ya establece esta propiedad en los cuadros de diálogo y ventanas de nivel superior. Interfaz de usuario basada en WPF ejecuta en Visual Studio ya la heredará. Si la configuración no se propaga a sus partes específicas de la interfaz de usuario, se puede establecer en el elemento raíz de la interfaz de usuario de WPF en XAML. Lugares donde esto sucede incluyen elementos emergentes, en los elementos con elementos primarios de Win32, y ventanas del diseñador que se ejecutan fuera de procesan, como Blend.  
  
 Alguna interfaz de usuario puede escalar independientemente el nivel de zoom de PPP de conjunto del sistema, como el editor de texto de Visual Studio y los diseñadores de WPF (tienda Windows y escritorio de WPF). En estos casos, no debe usarse DpiHelper.BitmapScalingMode. Para corregir este problema en el editor, el equipo IDE creado una propiedad personalizada denominada RenderOptions.BitmapScalingMode. Establecer ese valor de propiedad apoyen o NearestNeighbor según el nivel de zoom combinado del sistema y la interfaz de usuario.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: prescaling imágenes WPF para grandes niveles de PPP  
 Para los niveles de zoom muy grandes que no sean múltiplos de 100% (por ejemplo, 250%, % de 350 etc.), ajuste de escala en imágenes iconography con resultados bicúbica en aproximada, decoloración de interfaz de usuario. La impresión de estas imágenes junto con texto nítido casi es similar al de un efecto óptico. Las imágenes parecen ser más cercano para el ojo y desenfocadas en relación con el texto. Amplía la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o % de 300) y ajuste de escala con bicúbica al resto (un 50%), se puede mejorar el resultado de escala en este tamaño ampliada.  
  
 El siguiente es un ejemplo de las diferencias en los resultados, donde se escala la primera imagen con el algoritmo de ajuste de escala de doble mejorado -> 100% 200% -> 250% y la segunda se acaba con bicúbica 100% -> % de 250.  
  
 ![PPP emite doble ejemplo escalado](../extensibility/media/dpi-issues-double-scaling-example.png "doble ejemplo escalado de problemas de PPP")  
  
 Para habilitar la interfaz de usuario a usar este ajuste de escala de doble, el marcado XAML para mostrar cada elemento de imagen deberá modificarse. Los ejemplos siguientes muestran cómo utilizar la escala doble en WPF en Visual Studio mediante la biblioteca de DpiHelper y Shell.12/14.  
  
 Paso 1: Prescale la imagen a 200%, 300% y así sucesivamente con NearestNeighbor.  
  
 Prescale la imagen utilizando un convertidor de cualquier aplicado en un enlace, o con una extensión de marcado XAML. Por ejemplo:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Si la imagen también debe aplicarles un tema (más, si no todos, debe), el marcado puede utilizar un convertidor diferentes que realiza primero los temas de la imagen y, a continuación, previa ajuste de escala. Puede utilizar el marcado <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, según el resultado de la conversión deseada.  
  
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
  
 Porque WPF ajusta a la interfaz de usuario para el valor de PPP actual mediante la propiedad BitmapScalingMode activada UIElement, un control de imagen con una imagen prescaled como su origen tendrá un aspecto dos o tres veces mayor que se debe. Éstos son un par de formas para contrarrestar este efecto:  
  
-   Si conoce la dimensión de la imagen original al 100%, puede especificar el tamaño exacto del control Image. Estos tamaños refleja que el tamaño de la interfaz de usuario antes de escalar se aplica.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Si no se conoce el tamaño de la imagen original, LayoutTransform puede utilizarse para reducir verticalmente el objeto de la imagen final. Por ejemplo:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitación de la compatibilidad con HDPI contiene Web OC  
 De forma predeterminada, WebOC controles (por ejemplo, el control WebBrowser en WPF, o la interfaz IWebBrowser2) no habilitan la detección de HDPI y soporte técnico. El resultado será un control incrustado con el contenido de pantalla es demasiado pequeño en una pantalla de alta resolución. A continuación describe cómo habilitar la compatibilidad con valores altos de PPP en una instancia de WebOC web específico.  
  
 Implemente la interfaz IDocHostUIHandler (vea el artículo MSDN sobre el [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interfaz):  
  
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
  
 Si lo desea, implemente la interfaz de ICustomDoc (vea el artículo MSDN sobre el [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interfaz):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Asocie la clase que implementa IDocHostUIHandler con documentos de WebOC. Si implementa la interfaz ICustomDoc anterior, a continuación, tan pronto como propiedad de documento del contiene Web OC es válida, convertirlo en un ICustomDoc y llame al método SetUIHandler, pasando la clase que implementa IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Si no implementa la interfaz de ICustomDoc, a continuación, tan pronto como propiedad de documento del contiene Web OC es válida, debe convertirlo a un IOleObject y llamar al método SetClientSite, pasando de la clase que implementa IDocHostUIHandler. Establezca la marca DOCHOSTUIFLAG_DPI_AWARE en el DOCHOSTUIINFO pasado a la llamada al método de GetHostInfo:  
  
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
  
 Debe ser todo lo que necesita obtener el control de WebOC para admitir HPDI.  
  
## <a name="tips"></a>Sugerencias  
  
1.  Si cambia la propiedad de documento en el control de WebOC, tendrá que volver a asociar el documento con la clase IDocHostUIHandler.  
  
2.  Si lo anterior no funciona, hay un problema conocido con contiene Web OC no recoge el cambio en la marca de PPP. La forma más fiable de corrección de esto es activar o desactivar el zoom óptico de contiene Web OC, dos llamadas de significado con dos valores diferentes para el porcentaje de zoom. Además, si se requiere esta solución alternativa, pueden ser necesario para realizar en cada llamada de navegar.  
  
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