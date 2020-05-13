---
title: Abordar las cuestiones de PPP2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740107"
---
# <a name="address-dpi-issues"></a>Abordar problemas de PPP
Un número cada vez mayor de dispositivos se envían con pantallas de "alta resolución". Estas pantallas suelen tener más de 200 píxeles por pulgada (ppi). Trabajar con una aplicación en estos equipos requerirá que el contenido se escale verticalmente para satisfacer las necesidades de ver el contenido a una distancia de visualización normal para el dispositivo. A partir de 2014, el objetivo principal para las pantallas de alta densidad son los dispositivos informáticos móviles (tabletas, computadoras portátiles y teléfonos).

Windows 8.1 y superior contiene varias características para permitir que estas máquinas funcionen con pantallas y entornos donde la máquina está conectada a pantallas de alta densidad y densidad estándar al mismo tiempo.

- Windows puede permitirle escalar contenido al dispositivo mediante la opción "Hacer texto y otros elementos más grandes o más pequeños" (disponible desde Windows XP).

- Windows 8.1 y versiones posteriores escalarán automáticamente el contenido de la mayoría de las aplicaciones cuando se muevan entre pantallas de densidades de píxeles diferentes. Cuando la pantalla principal es de alta densidad (200% de escala) y la pantalla secundaria es de densidad estándar (100%), Windows reducirá automáticamente el contenido de la ventana de la aplicación en la pantalla secundaria (1 píxel mostrado por cada 4 píxeles representados por la aplicación).

- Windows establecerá de forma predeterminada la escala correcta para la densidad de píxeles y la distancia de visualización de la pantalla (Windows 7 y versiones posteriores, configurables por EL OEM).

- Windows puede escalar automáticamente contenido hasta un 250 % en dispositivos nuevos que superen los 280 ppp (a partir de Windows 8.1 S14).

  Windows tiene una manera de tratar con el escalado vertical de la interfaz de usuario para aprovechar el aumento del recuento de píxeles. Una aplicación opta por este sistema declarándose "consciente del sistema DPI." Las aplicaciones que no lo hacen son escaladas verticalmente por el sistema. Esto puede dar lugar a una experiencia de usuario "difusa" en la que toda la aplicación está uniformemente estirada en píxeles. Por ejemplo:

  ![Problemas de PPP borrosos](../extensibility/media/dpi-issues-fuzzy.png "Problemas de PPP borrosos")

  Visual Studio opta por ser compatible con el escalado de PPP y, por lo tanto, no está "virtualizado".

  Windows (y Visual Studio) aprovechan varias tecnologías de interfaz de usuario, que tienen diferentes formas de tratar con los factores de escalado establecidos por el sistema. Por ejemplo:

- WPFWPF mide los controles de forma independiente del dispositivo (unidades, no píxeles). WPFWPF UI escala automáticamente para el PPP actual.

- Todos los tamaños de texto, independientemente del marco de la interfaz de usuario, se expresan en puntos, por lo que el sistema trata como independiente de PPP. El texto de Win32, WinForms y WPF ya se escala correctamente cuando se dibuja en el dispositivo de visualización.

- Los cuadros de diálogo y ventanas de Win32/WinForms tienen medios para habilitar el diseño que cambia de tamaño con texto (por ejemplo, a través de paneles de cuadrícula, flujo y diseño de tabla). Esto permite evitar ubicaciones de píxeles codificadas de forma rígida que no se escalan cuando se aumentan los tamaños de fuente.

- Los iconos proporcionados por el sistema o los recursos basados en métricas del sistema (por ejemplo, SM_CXICON y SM_CXSMICON) ya se han ampliado.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 más antiguo (GDI, GDI+) y la interfaz de usuario basada en WinForms
Aunque WPFWPF ya es compatible con PPP, gran parte de nuestro código basado en Win32/GDI no se escribió originalmente teniendo en cuenta el conocimiento de PPP. Windows ha proporcionado API de escalado de PPP. Las correcciones para los problemas de Win32 deben usarlos de forma coherente en todo el producto. Visual Studio ha proporcionado una biblioteca de clases auxiliares para evitar duplicar la funcionalidad y garantizar la coherencia en todo el producto.

## <a name="high-resolution-images"></a>Imágenes de alta resolución
Esta sección es principalmente para los desarrolladores que extienden Visual Studio 2013. Para Visual Studio 2015, use el servicio de imágenes integrado en Visual Studio. También puede encontrar que necesita admitir o apuntar a muchas versiones de Visual Studio y, por lo tanto, el uso del servicio de imágenes en 2015 no es una opción, ya que no existe en versiones anteriores. Esta sección también es para ti entonces.

## <a name="scaling-up-images-that-are-too-small"></a>Escalar imágenes demasiado pequeñas
Las imágenes que son demasiado pequeñas se pueden escalar verticalmente y representarse en GDI y WPF mediante algunos métodos comunes. Las clases auxiliares de PPP administrados están disponibles para los integradores internos y externos de Visual Studio para abordar iconos de escalado, mapas de bits, imágenes e listas de imágenes. Los c/C++helpernativos nativos basados en Win32 están disponibles para escalar HICON, HBITMAP, HIMAGELIST y VsUI::GdiplusImage. El escalado de un mapa de bits normalmente solo requiere un cambio de una línea después de incluir una referencia a la biblioteca auxiliar. Por ejemplo:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

El escalado de una lista de imágenes depende de si la lista de imágenes se ha completado en tiempo de carga o se anexa en tiempo de ejecución. Si se completa en `LogicalToDeviceUnits()` tiempo de carga, llame con la lista de imágenes como lo haría con un mapa de bits. Cuando el código necesite cargar un mapa de bits individual antes de componer la lista de imágenes, asegúrese de escalar el tamaño de imagen de la lista de imágenes:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

En el código nativo, las dimensiones se pueden escalar al crear la lista de imágenes de la siguiente manera:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Las funciones de la biblioteca permiten especificar el algoritmo de cambio de tamaño. Al escalar las imágenes que se van a colocar en las listas de imágenes, asegúrese de especificar el color de fondo que se utiliza para la transparencia, o utilice la escala NearestNeighbor (que provocará distorsiones al 125% y 150%).

Consulte <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> la documentación en MSDN.

En la tabla siguiente se muestran ejemplos de cómo se deben escalar las imágenes en los factores de escala de PPP correspondientes. Las imágenes descritas en naranja denotan nuestra práctica recomendada a partir de Visual Studio 2013 (escalado de 100%-200% PPP):

![Escalado de problemas de PPP](../extensibility/media/dpi-issues-scaling.png "Escalado de problemas de PPP")

## <a name="layout-issues"></a>Problemas de diseño
Los problemas de diseño comunes se pueden evitar principalmente manteniendo los puntos en la interfaz de usuario escalados y relativos entre sí en lugar de mediante el uso de ubicaciones absolutas (específicamente, en unidades de píxeles). Por ejemplo:

- Las posiciones de diseño/texto deben ajustarse para tener en cuenta las imágenes escaladas.

- Las columnas de las cuadrículas deben tener anchos ajustados para el texto escalado vertical.

- Los tamaños codificados de forma rígida o el espacio entre los elementos también tendrán que ampliarse. Los tamaños que se basan solo en dimensiones de texto suelen estar bien, ya que las fuentes se escalan automáticamente.

  Las funciones auxiliares están disponibles en la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> clase para permitir el escalado en los ejes X e Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (las funciones permiten escalar en el eje X/Y)

- espacio int á DpiHelper.LogicalToDeviceUnitsX (10);

- int height á VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Hay sobrecargas LogicalToDeviceUnits para permitir el escalado de objetos como Rect, Point y Size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Uso de la biblioteca/clase DPIHelper para escalar imágenes y diseño
La biblioteca auxiliar de PPP de Visual Studio está disponible en formularios nativos y administrados y otras aplicaciones pueden usarla fuera del shell de Visual Studio.

Para usar la biblioteca, vaya a los ejemplos de [extensibilidad de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) de Visual Studio y clone el ejemplo de alta DPI_Images_Icons.

En los archivos de origen, incluya *VsUIDpiHelper.h* y llame a las funciones estáticas de `VsUI::DpiHelper` la clase:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> No utilice las funciones auxiliares en variables estáticas de nivel de módulo o de clase. La biblioteca también utiliza estáticas para la sincronización de subprocesos y es posible que se encuentre con problemas de inicialización de pedidos. Convierta esas estáticas en variables miembro no estáticas o envuélvalas en una función (para que se construyan en el primer acceso).

Para tener acceso a las funciones auxiliares de PPP desde código administrado que se ejecutará dentro del entorno de Visual Studio:

- El proyecto de consumo debe hacer referencia a la versión más reciente de Shell MPF. Por ejemplo:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Asegúrese de que el proyecto tiene referencias a **System.Windows.Forms**, **PresentationCore**y **PresentationUI**.

- En el código, use el **Microsoft.VisualStudio.PlatformUI** espacio de nombres y llame a las funciones estáticas de DpiHelper clase. Para los tipos admitidos (puntos, tamaños, rectángulos, etc.), se proporcionan funciones de extensión que devuelven nuevos objetos escalados. Por ejemplo:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Tratar con el difuso de imágenes de WPF en la interfaz de usuario ampliable
En WPFWPF, WPFWPF cambia el tamaño automáticamente de los mapas de bits para el nivel de zoom de PPP actual mediante un algoritmo bicúbico de alta calidad (predeterminado), que funciona bien para imágenes o capturas de pantalla grandes, pero es inapropiado para los iconos de elementos de menú porque introduce el difusor percibido.

Recomendaciones:

- Para la ilustración de <xref:System.Windows.Media.BitmapScalingMode> imágenes de logotipos y banners, se podría utilizar el modo de cambio de tamaño predeterminado.

- Para los elementos de menú <xref:System.Windows.Media.BitmapScalingMode> y las imágenes de iconografía, se debe utilizar cuando no causa que otros artefactos de distorsión eliminen el mareo (al 200% y al 300%).

- Para niveles de zoom grandes no múltiplos del 100% (por ejemplo, 250% o 350%), escalado de imágenes de iconografía con resultados bicúbicos en una interfaz de usuario difusa y lavada. Un mejor resultado se obtiene escalando primero la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%) y escalando con bicúbico desde allí. Consulte Caso especial: preescalado de imágenes de WPF para grandes niveles de PPP para obtener más información.

  El DpiHelper clase en el Microsoft.VisualStudio.PlatformUI espacio de nombres proporciona un miembro <xref:System.Windows.Media.BitmapScalingMode> que se puede usar para el enlace. Permitirá que el shell de Visual Studio controle el modo de escalado de mapa de bits en todo el producto de forma uniforme, en función del factor de escalado de PPP.

  Para usarlo en XAML, agrega:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

El shell de Visual Studio ya establece esta propiedad en ventanas y cuadros de diálogo de nivel superior. La interfaz de usuario basada en WPF que se ejecuta en Visual Studio ya la heredará. Si la configuración no se propaga a los elementos concretos de la interfaz de usuario, se puede establecer en el elemento raíz de la interfaz de usuario XAML/WPF. Los lugares donde esto sucede incluyen ventanas emergentes, en elementos con padres de Win32 y ventanas de diseño que se ejecutan fuera de proceso, como Blend.

Algunas interfazes de usuario pueden escalar independientemente del nivel de zoom de PPP del conjunto de sistemas, como el editor de texto de Visual Studio y los diseñadores basados en WPF (WPF Desktop y Windows Store). En estos casos, DpiHelper.BitmapScalingMode no debe utilizarse. Para corregir este problema en el editor, el equipo IDE creó una propiedad personalizada denominada RenderOptions.BitmapScalingMode. Establezca ese valor de propiedad en HighQuality o NearestNeighbor en función del nivel de zoom combinado del sistema y la interfaz de usuario.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: preescalado de imágenes WPF para grandes niveles de PPP
Para niveles de zoom muy grandes que no son múltiplos del 100% (por ejemplo, 250%, 350%, etc.), escalar imágenes de iconografía con resultados bicúbicos en una interfaz de usuario difusa y lavada. La impresión de estas imágenes junto con texto nítido es casi como la de una ilusión óptica. Las imágenes parecen estar más cerca del ojo y desenfocadas en relación con el texto. El resultado de la escala en este tamaño aumentado se puede mejorar primero escalando la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%) y escalando con bicúbico al resto (un 50% adicional).

A continuación se muestra un ejemplo de las diferencias en los resultados, donde la primera imagen se escala con el algoritmo de doble escala mejorado 100%->200%->250%, y la segunda solo con bicúbico 100%->250%.

![Ejemplo de doble escalado de problemas de PPP](../extensibility/media/dpi-issues-double-scaling-example.png "Ejemplo de doble escalado de problemas de PPP")

Para permitir que la interfaz de usuario use este doble escalado, el marcado XAML para mostrar cada Image elemento tendrá que modificarse. En los ejemplos siguientes se muestra cómo usar el doble escalado en WPFWPF en Visual Studio mediante la biblioteca DpiHelper y Shell.12/14.

Paso 1: Preescale la imagen al 200%, 300%, y así sucesivamente usando NearestNeighbor.

Preajuste la escala de la imagen mediante un convertidor aplicado en un enlace o con una extensión de marcado XAML. Por ejemplo:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Si la imagen también necesita ser temática (la mayoría, si no todos, debería), el marcado puede usar un convertidor diferente que primero realiza el tema de la imagen y, a continuación, el escalado previo. El marcado puede <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>usar o , dependiendo de la salida de conversión deseada.

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

Paso 2: Asegúrese de que el tamaño final es correcto para el DPI actual.

Dado que WPFWPF escalará la interfaz de usuario para el PPP actual mediante el BitmapScalingMode propiedad establecida en el UIElement, un Image control con una imagen preescalado como su origen se verá dos o tres veces mayor de lo que debería. Las siguientes son un par de maneras de contrarrestar este efecto:

- Si conoce la dimensión de la imagen original al 100%, puede especificar el tamaño exacto del control Image. Estos tamaños reflejarán el tamaño de la interfaz de usuario antes de aplicar el escalado.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Si no se conoce el tamaño de la imagen original, un LayoutTransform se puede utilizar para reducir la escala del objeto Image final. Por ejemplo:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitación de la compatibilidad con HDPI en el WebOC
De forma predeterminada, los controles WebOC (como el control WebBrowser en WPFWPF o la interfaz IWebBrowser2) no habilitan la detección y compatibilidad con HDPI. El resultado será un control incrustado con contenido de pantalla que es demasiado pequeño en una pantalla de alta resolución. A continuación se describe cómo habilitar la compatibilidad con PPP altos en una instancia WebOC específica.

Implemente la interfaz IDocHostUIHandler (consulte el artículo de MSDN en [el IDocHostUIHandler:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))

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

Opcionalmente, implemente la interfaz ICustomDoc (consulte el artículo de MSDN en [el ICustomDoc:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Asocie la clase que implementa IDocHostUIHandler con el documento de WebOC. Si ha implementado la interfaz ICustomDoc anterior, tan pronto como la propiedad de documento de WebOC sea válida, conviéstela en un ICustomDoc y llame al método SetUIHandler, pasando la clase que implementa IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Si NO implementó la interfaz ICustomDoc, tan pronto como la propiedad de documento de WebOC sea válida, `SetClientSite` deberá convertirla en un IOleObject y llamar al método, pasando la clase que implementa IDocHostUIHandler. Establezca el indicador DOCHOSTUIFLAG_DPI_AWARE en el DOCHOSTUIINFO pasado a la `GetHostInfo` llamada al método:

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

Esto debe ser todo lo que necesita para obtener el control WebOC para admitir HPDI.

## <a name="tips"></a>Sugerencias

1. Si cambia la propiedad document del control WebOC, es posible que deba volver a asociar el documento con la clase IDocHostUIHandler.

2. Si lo anterior no funciona, hay un problema conocido con el WebOC no recoger el cambio al indicador DPI. La forma más confiable de arreglar esto es alternar el zoom óptico del WebOC, lo que significa dos llamadas con dos valores diferentes para el porcentaje de zoom. Además, si se requiere esta solución alternativa, puede ser necesario realizarla en cada llamada de navegación.

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
