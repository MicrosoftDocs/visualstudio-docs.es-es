---
title: Direccionar PPP Issues2 | Microsoft Docs
description: Obtenga información sobre los problemas implicados en la programación de pantallas de alta resolución, como el escalado vertical de contenido, problemas de diseño y el uso de las API de escala de PPP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 455f144a95a41ae482c1f240e1d2f87b888763a5
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598463"
---
# <a name="address-dpi-issues"></a>Problemas de PPP de direcciones
Un número cada vez mayor de dispositivos se envía con pantallas de "alta resolución". Estas pantallas suelen tener más de 200 píxeles por pulgada (PPP). Al trabajar con una aplicación en estos equipos, será necesario que el contenido se escale verticalmente para satisfacer las necesidades de visualización del contenido con una distancia de visualización normal para el dispositivo. A partir de 2014, el destino principal de las pantallas de alta densidad son los dispositivos informáticos móviles (tabletas, portátiles de concha y teléfonos).

Windows 8.1 y versiones posteriores contienen varias características que permiten a estas máquinas trabajar con pantallas y entornos en los que la máquina está conectada a las pantallas de alta densidad y densidad estándar al mismo tiempo.

- Windows puede permitir el escalado de contenido al dispositivo con la opción "hacer que el texto y otros elementos sean mayores o menores" (disponible desde Windows XP).

- Windows 8.1 y versiones posteriores escalarán automáticamente el contenido de la mayoría de las aplicaciones para que sean coherentes cuando se muevan entre las pantallas de densidades de píxeles diferentes. Cuando la pantalla principal es de alta densidad (escala del 200%) y la pantalla secundaria es la densidad estándar (100%), Windows escalará automáticamente el contenido de la ventana de la aplicación hacia abajo en la pantalla secundaria (1 píxel se muestra por cada 4 píxeles representado por la aplicación).

- Windows usará de forma predeterminada el escalado adecuado para la densidad de píxeles y la distancia de visualización de la pantalla (Windows 7 y posterior, configurable por el OEM).

- Windows puede escalar automáticamente el contenido hasta el 250% en dispositivos nuevos que superen los 280 PPP (desde Windows 8.1 S14).

  Windows tiene una forma de tratar con el escalado vertical de la interfaz de usuario para aprovechar el aumento de los recuentos de píxeles. Una aplicación participa en este sistema declarando "reconocimiento de PPP del sistema". El sistema escala verticalmente las aplicaciones que no lo hacen. Esto puede dar lugar a una experiencia de usuario "aproximada" en la que toda la aplicación se ajusta uniformemente. Por ejemplo:

  ![Problemas de PPP borrosos](../extensibility/media/dpi-issues-fuzzy.png "Problemas de PPP borrosos")

  Visual Studio opta por ser compatible con el ajuste de escala de PPP y, por tanto, no está "virtualizado".

  Windows (y Visual Studio) aprovechan varias tecnologías de interfaz de usuario, que tienen diferentes formas de tratar con los factores de escala establecidos por el sistema. Por ejemplo:

- WPF mide los controles de una manera independiente del dispositivo (unidades, no píxeles). La interfaz de usuario de WPF se escala automáticamente para los PPP actuales.

- Todos los tamaños de texto independientemente del marco de interfaz de usuario se expresan en puntos, por lo que el sistema los trata como independientes de PPP. El texto en Win32, WinForms y WPF ya se escala correctamente cuando se dibuja en el dispositivo de pantalla.

- Los cuadros de diálogo de Win32/WinForms y las ventanas tienen medios para habilitar el diseño que cambia de tamaño con texto (por ejemplo, a través de los paneles de diseño de tabla, cuadrícula, flujo y cuadrícula). Permiten evitar ubicaciones de píxeles codificadas de forma rígida que no se escalan cuando se aumentan los tamaños de fuente.

- Los iconos proporcionados por el sistema o los recursos basados en métricas del sistema (por ejemplo, SM_CXICON y SM_CXSMICON) ya se han escalado verticalmente.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Interfaz de usuario de Win32 (GDI, GDI+) anterior y basada en WinForms
Aunque WPF ya tiene un alto reconocimiento de PPP, gran parte de nuestro código basado en Win32/GDI no se escribió originalmente con reconocimiento de PPP. Windows ha proporcionado API de escala de PPP. Las correcciones de problemas de Win32 deberían utilizarlos de forma coherente en todo el producto. Visual Studio proporciona una biblioteca de clases auxiliares para evitar la duplicación de la funcionalidad y garantizar la coherencia en todo el producto.

## <a name="high-resolution-images"></a>Imágenes de alta resolución
Esta sección es principalmente para desarrolladores que amplían Visual Studio 2013. Para Visual Studio 2015, use el servicio de imágenes que está integrado en Visual Studio. También es posible que tenga que admitir y dirigir muchas versiones de Visual Studio y, por tanto, usar el servicio de imágenes en 2015 no es una opción, ya que no existe en versiones anteriores. Esta sección también es para usted.

## <a name="scaling-up-images-that-are-too-small"></a>Escalado vertical de imágenes demasiado pequeñas
Las imágenes que son demasiado pequeñas se pueden escalar verticalmente y representar en GDI y WPF mediante algunos métodos comunes. Las clases auxiliares de PPP administradas están disponibles para los integradores internos y externos de Visual Studio para tratar los iconos de escalado, mapas de bits, imagestrips y ImageList. Las aplicaciones auxiliares nativas de C/C++ y basadas en Win32 están disponibles para escalar HICON, HBITMAP, HIMAGELIST y VsUI:: GdiplusImage. El escalado de un mapa de bits normalmente solo requiere un cambio de una línea después de incluir una referencia a la biblioteca auxiliar. Por ejemplo:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

El escalado de un ImageList depende de si el ImageList está completo en el momento de la carga o se anexa en tiempo de ejecución. Si se completa en tiempo de carga, llame a `LogicalToDeviceUnits()` con el ImageList como lo haría con un mapa de bits. Cuando el código necesite cargar un mapa de bits individual antes de crear el ImageList, asegúrese de escalar el tamaño de la imagen del ImageList:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

En código nativo, las dimensiones se pueden escalar al crear el ImageList de la manera siguiente:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Las funciones de la biblioteca permiten especificar el algoritmo de cambio de tamaño. Al ajustar el tamaño de las imágenes que se van a colocar en ImageList, asegúrese de especificar el color de fondo que se utiliza para la transparencia, o bien use el escalado de NearestNeighbor (lo que provocará distorsiones en 125% y 150%).

Consulte la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentación de en MSDN.

En la tabla siguiente se muestran ejemplos de cómo se deben escalar las imágenes en los factores de escala de PPP correspondientes. Las imágenes que se describen en naranja indican nuestro procedimiento recomendado a partir de Visual Studio 2013 (ajuste de escala del 100%-200% de PPP):

![Escalado de problemas de PPP](../extensibility/media/dpi-issues-scaling.png "Escalado de problemas de PPP")

## <a name="layout-issues"></a>Problemas de diseño
Los problemas de diseño comunes se pueden evitar principalmente si se mantienen los puntos en la interfaz de usuario escalados y se relacionan entre sí, en lugar de usar ubicaciones absolutas (concretamente, en unidades de píxeles). Por ejemplo:

- Las posiciones de diseño/texto deben ajustarse para tener en cuenta las imágenes de escalado vertical.

- Las columnas de las cuadrículas deben ajustarse a los anchos del texto escalado verticalmente.

- También será necesario escalar verticalmente los tamaños o el espacio codificados entre los elementos. Los tamaños basados solo en las dimensiones de texto suelen ser correctos, ya que las fuentes se escalan verticalmente de forma automática.

  Las funciones auxiliares están disponibles en la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> clase para permitir el escalado en el eje X e y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (las funciones permiten el escalado en el eje X/Y)

- int Space = DpiHelper. LogicalToDeviceUnitsX (10);

- int height = VsUI::D piHelper:: LogicalToDeviceUnitsY (5);

  Hay sobrecargas de LogicalToDeviceUnits para permitir el escalado de objetos como Rect, Point y size.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Uso de la biblioteca o la clase DPIHelper para escalar imágenes y diseños
La biblioteca auxiliar de PPP de Visual Studio está disponible en formularios nativos y administrados y se puede usar fuera de Visual Studio Shell por otras aplicaciones.

Para usar la biblioteca, vaya a los [ejemplos de extensibilidad de VSSDK de Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples) y Clone el ejemplo High-DPI_Images_Icons.

En archivos de código fuente, incluya *VsUIDpiHelper. h* y llame a las funciones estáticas de la `VsUI::DpiHelper` clase:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> No utilice las funciones auxiliares en las variables estáticas en el nivel de módulo o de clase. La biblioteca también utiliza estáticas para la sincronización de subprocesos y puede que se produzcan problemas de inicialización de orden. Convierta esos valores estáticos en variables miembro no estáticas o ajústelos en una función (para que se construyan en el primer acceso).

Para tener acceso a las funciones auxiliares de PPP desde código administrado que se ejecutará en el entorno de Visual Studio:

- El proyecto de consumo debe hacer referencia a la versión más reciente del shell MPF. Por ejemplo:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Asegúrese de que el proyecto tiene referencias a **System. Windows. Forms**, **PresentationCore** y **PresentationUI**.

- En el código, use el espacio de nombres **Microsoft. VisualStudio. PlatformUI** y llame a las funciones estáticas de la clase DpiHelper. En el caso de los tipos admitidos (puntos, tamaños, rectángulos, etc.), se proporcionan funciones de extensión que devuelven nuevos objetos escalados. Por ejemplo:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Tratar con la aproximación de imagen de WPF en la interfaz de usuario de zoom
En WPF, WPF cambia el tamaño de los mapas de bits automáticamente para el nivel de zoom de PPP actual mediante un algoritmo bicúbico de alta calidad (valor predeterminado), que funciona bien para imágenes o capturas de pantallas grandes, pero no es apropiado para los iconos de elementos de menú porque introduce una aproximación aproximada.

Recomendaciones:

- En el material gráfico de imagen de logotipo y banners, <xref:System.Windows.Media.BitmapScalingMode> se podría usar el modo de cambio de tamaño predeterminado.

- En el caso de los elementos de menú y las imágenes Iconografía, <xref:System.Windows.Media.BitmapScalingMode> debe usarse cuando no provoque que otros artefactos de distorsión eliminen la aproximación (en 200% y 300%).

- En el caso de los niveles de zoom grandes no múltiplos del 100% (por ejemplo, 250% o 350%), el escalado de imágenes de iconografía con resultados bicúbicos en una interfaz de usuario de descoloración aproximada. Para obtener un mejor resultado, escale primero la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%). y el escalado con bicúbico desde allí. Vea caso especial: preescalar imágenes de WPF para niveles de PPP grandes para obtener más información.

  La clase DpiHelper del espacio de nombres Microsoft. VisualStudio. PlatformUI proporciona un miembro <xref:System.Windows.Media.BitmapScalingMode> que se puede usar para el enlace. Permite que el shell de Visual Studio controle el modo de escalado de mapa de bits en el producto uniformemente, en función del factor de escala de PPP.

  Para usarlo en XAML, agregue:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

El shell de Visual Studio ya establece esta propiedad en los cuadros de diálogo y las ventanas de nivel superior. La interfaz de usuario basada en WPF que se ejecuta en Visual Studio ya la hereda. Si el valor no se propaga a las partes concretas de la interfaz de usuario, se puede establecer en el elemento raíz de la interfaz de usuario de XAML o WPF. Entre los lugares en los que esto ocurre se incluyen elementos emergentes, elementos con elementos primarios de Win32 y ventanas del diseñador que se ejecutan fuera de proceso, como Blend.

Algunas interfaces de usuario se pueden escalar independientemente del nivel de zoom de PPP establecido en el sistema, como el editor de texto de Visual Studio y los diseñadores basados en WPF (WPF Desktop y la tienda Windows). En estos casos, no se debe usar DpiHelper. BitmapScalingMode. Para corregir este problema en el editor, el equipo del IDE creó una propiedad personalizada titulada RenderOptions. BitmapScalingMode. Establezca el valor de la propiedad en HighQuality o NearestNeighbor según el nivel de zoom combinado del sistema y la interfaz de usuario.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: escalar imágenes de WPF para niveles de PPP grandes
En el caso de niveles de zoom muy grandes que no son múltiplos del 100% (por ejemplo, 250%, 350%, etc.), el escalado de imágenes de iconografía con resultados bicúbicos en una interfaz de usuario de decoloración aproximada. La impresión de estas imágenes junto con el texto nítido es prácticamente similar a la de una ilusión óptica. Las imágenes parecen estar más cerca del ojo y de centrarse en relación con el texto. El resultado de la escala con este tamaño ampliado se puede mejorar escalando primero la imagen con NearestNeighbor al múltiplo más grande del 100% (por ejemplo, 200% o 300%). y el escalado con bicúbico al resto (un 50% adicional.

A continuación se presenta un ejemplo de las diferencias en los resultados, donde la primera imagen se escala con el algoritmo de doble escala 100%->200%->250%, y el segundo solo con bicúbico 100%->250%.

![Ejemplo de doble escala de problemas de PPP](../extensibility/media/dpi-issues-double-scaling-example.png "Ejemplo de doble escala de problemas de PPP")

Para habilitar la interfaz de usuario para que use este escalado doble, es necesario modificar el marcado XAML para mostrar cada elemento de imagen. En los siguientes ejemplos se muestra cómo usar el escalado doble en WPF en Visual Studio con la biblioteca DpiHelper y el shell. 12/14.

Paso 1: ajustar el tamaño de la imagen a 200%, 300% y así sucesivamente con NearestNeighbor.

Ajuste el tamaño de la imagen mediante un convertidor aplicado en un enlace o con una extensión de marcado XAML. Por ejemplo:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Si también es necesario que la imagen tenga el mismo nombre (la mayoría, si no todos, deberían), el marcado puede utilizar un convertidor diferente que primero realiza la imagen y, a continuación, el escalado previo. El marcado puede utilizar <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> , dependiendo de la salida de conversión deseada.

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

Paso 2: asegurarse de que el tamaño final es correcto para el PPP actual.

Dado que WPF escalará la interfaz de usuario para los PPP actuales mediante el conjunto de propiedades BitmapScalingMode en el UIElement, un control de imagen que use una imagen preajustada como su origen tendrá una apariencia de dos o tres veces mayor de lo que debería. A continuación se muestran un par de formas de contrarrestar este efecto:

- Si conoce la dimensión de la imagen original en 100%, puede especificar el tamaño exacto del control de imagen. Estos tamaños reflejarán el tamaño de la interfaz de usuario antes de aplicar el escalado.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Si no se conoce el tamaño de la imagen original, se puede usar una LayoutTransform para reducir verticalmente el objeto de imagen final. Por ejemplo:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitación de la compatibilidad con HDPI con WebOC
De forma predeterminada, los controles WebOC (como el control WebBrowser en WPF o la interfaz IWebBrowser2) no habilitan la detección y compatibilidad con HDPI. El resultado será un control incrustado con contenido para mostrar que es demasiado pequeño en una pantalla de alta resolución. A continuación se describe cómo habilitar la compatibilidad con PPP alta en una instancia específica de WebOC Web.

Implemente la interfaz IDocHostUIHandler (vea el artículo de MSDN en [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Opcionalmente, implemente la interfaz ICustomDoc (vea el artículo de MSDN en [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Asocie la clase que implementa IDocHostUIHandler con el documento de WebOC. Si ha implementado la interfaz ICustomDoc anterior, tan pronto como la propiedad del documento de WebOC es válida, conviértala en un ICustomDoc y llame al método SetUIHandler, pasando la clase que implementa IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Si no implementó la interfaz ICustomDoc, tan pronto como la propiedad del documento de WebOC sea válida, deberá convertirla en un IOleObject y llamar al `SetClientSite` método, pasando la clase que implementa IDocHostUIHandler. Establezca la marca de DOCHOSTUIFLAG_DPI_AWARE en el DOCHOSTUIINFO que se pasa a la `GetHostInfo` llamada al método:

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

Esto debería ser todo lo que necesita para obtener el control WebOC para admitir HPDI.

## <a name="tips"></a>Sugerencias

1. Si cambia la propiedad de documento en el control WebOC, puede que tenga que volver a asociar el documento con la clase IDocHostUIHandler.

2. Si el anterior no funciona, existe un problema conocido con el WebOC que no recoge el cambio en la marca de PPP. La forma más confiable de corregirlo es alternar el zoom óptico del WebOC, lo que significa dos llamadas con dos valores diferentes para el porcentaje de zoom. Además, si se requiere esta solución alternativa, podría ser necesario realizarla en cada llamada de navegación.

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
