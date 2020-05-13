---
title: Servicio de imágenes y catálogo ? Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710383"
---
# <a name="image-service-and-catalog"></a>Servicio y catálogo de imágenes
Este libro de recetas contiene instrucciones y procedimientos recomendados para adoptar el servicio de imágenes de Visual Studio y el catálogo de imágenes introducidos en Visual Studio 2015.

 El servicio de imágenes introducido en Visual Studio 2015 permite a los desarrolladores obtener las mejores imágenes para el dispositivo y el tema elegido por el usuario para mostrar la imagen, incluido el tema correcto para el contexto en el que se muestran. La adopción del servicio de imágenes ayudará a eliminar los principales puntos débiles relacionados con el mantenimiento de activos, el escalado de HDPI y el tema.

|||
|-|-|
|**Problemas de hoy**|**Soluciones**|
|Mezcla de color de fondo|Mezcla alfa incorporada|
|Imágenes temáticas (algunas)|Metadatos temáticos|
|Modo de contraste alto|Recursos alternativos de alto contraste|
|Necesita varios recursos para diferentes modos de PPP|Recursos seleccionables con reserva basada en vectores|
|Imágenes duplicadas|Un identificador por concepto de imagen|

 ¿Por qué adoptar el servicio de imágenes?

- Obtenga siempre la última imagen "pixel-perfect" de Visual Studio

- Puede enviar y utilizar sus propias imágenes

- No es necesario probar las imágenes cuando Windows agrega nuevo escalado de PPP

- Aborde los antiguos obstáculos arquitectónicos en sus implementaciones

  La barra de herramientas del shell de Visual Studio antes y después de usar el servicio de imágenes:

  ![Antes y después del servicio de imágenes](../extensibility/media/image-service-before-and-after.png "Antes y después del servicio de imágenes")

## <a name="how-it-works"></a>Funcionamiento
 El servicio de imágenes puede proporcionar una imagen de mapa de bits adecuada para cualquier marco de interfaz de usuario compatible:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Diagrama de flujo de servicio de imágenes

  ![Diagrama de flujo del servicio de imágenes](../extensibility/media/image-service-flow-diagram.png "Diagrama de flujo del servicio de imágenes")

  **Monikers de imagen**

  Un moniker de imagen (o moniker para abreviar) es un par GUID/ID que identifica de forma única un recurso de imagen o un recurso de lista de imágenes en la biblioteca de imágenes.

  **Monikers conocidos**

  Conjunto de monikers de imagen contenidos en el catálogo de imágenes de Visual Studio y consumible públicamente por cualquier componente o extensión de Visual Studio.

  **Archivos de manifiesto de imagen**

  Los archivos de manifiesto de imagen (*.imagemanifest*) son archivos XML que definen un conjunto de activos de imagen, los monikers que representan esos activos y la imagen o imágenes reales que representan cada recurso. Los manifiestos de imagen pueden definir imágenes independientes o listas de imágenes para la compatibilidad con la interfaz de usuario heredada. Además, hay atributos que se pueden establecer en el activo o en las imágenes individuales detrás de cada activo para cambiar cuándo y cómo se muestran esos activos.

  **Esquema de manifiesto de imagen**

  Un manifiesto de imagen completo tiene este aspecto:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbols**

 Como ayuda de legibilidad y mantenimiento, el manifiesto de imagen puede utilizar símbolos para los valores de atributo. Los símbolos se definen así:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Subelemento**|**Definición**|
|Importar|Importa los símbolos del archivo de manifiesto dado para su uso en el manifiesto actual|
|Guid|El símbolo representa un GUID y debe coincidir con el formato GUID|
|id|El símbolo representa un identificador y debe ser un entero no negativo|
|String|El símbolo representa un valor de cadena arbitrario|

 Los símbolos distinguen entre mayúsculas y minúsculas y se hace referencia a ellos mediante la sintaxis $(nombre-símbolo):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Algunos símbolos están predefinidos para todos los manifiestos. Se pueden utilizar en el \<atributo Uri \<del elemento Source> o Import> para hacer referencia a rutas de acceso en el equipo local.

|||
|-|-|
|**Símbolo**|**Descripción**|
|CommonProgramFiles|El valor de la variable de entorno %CommonProgramFiles%|
|LocalAppData|El valor de la variable de entorno %LocalAppData%|
|ManifestFolder|La carpeta que contiene el archivo de manifiesto|
|MyDocuments|La ruta de acceso completa de la carpeta Mis documentos del usuario actual|
|ProgramFiles|El valor de la variable de entorno %ProgramFiles%|
|Sistema|La carpeta *Windows-System32*|
|WinDir|El valor de la variable de entorno %WinDir%|

 **Imagen**

 El \<elemento Image> define una imagen a la que puede hacer referencia un moniker. El GUID y el identificador tomados juntos forman el moniker de imagen. El moniker de la imagen debe ser único en toda la biblioteca de imágenes. Si más de una imagen tiene un moniker determinado, la primera encontrada al compilar la biblioteca es la que se conserva.

 Debe contener al menos una fuente. Las fuentes de tamaño neutro darán los mejores resultados en una amplia gama de tamaños, pero no son necesarias. Si se solicita al servicio una imagen de \<un tamaño no definido en el elemento Image> y no hay ningún origen de tamaño neutro, el servicio elegirá el mejor origen específico del tamaño y lo escalará al tamaño solicitado.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Atributo**|**Definición**|
|Guid|[Requerido] La parte GUID del moniker de imagen|
|id|[Requerido] La parte id del moniker de imagen|
|AllowColorInversion|[Opcional, predeterminado true] Indica si la imagen puede tener sus colores invertidos mediante programación cuando se usa en un fondo oscuro.|

 **Origen**

 El \<elemento Source> define un único recurso de origen de imagen (XAML y PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Atributo**|**Definición**|
|Identificador URI|[Requerido] URI que define desde dónde se puede cargar la imagen. Puede tener uno de los valores siguientes:<br /><br /> - Un [URI de paquete](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) con la autoridad application:///<br />- Una referencia de recursos de componentes absoluta<br />- Una ruta de acceso a un archivo que contiene un recurso nativo|
|Información previa|[Opcional] Indica qué tipo de fondo está destinado a utilizar se va a utilizar el origen.<br /><br /> Puede tener uno de los valores siguientes:<br /><br /> *Luz:* La fuente se puede utilizar en un fondo claro.<br /><br /> *Oscuro:* La fuente se puede utilizar sobre un fondo oscuro.<br /><br /> *HighContrast:* La fuente se puede utilizar en cualquier fondo en el modo de contraste alto.<br /><br /> *HighContrastLight:* La fuente se puede utilizar en un fondo claro en el modo de contraste alto.<br /><br /> *HighContrastDark:* La fuente se puede utilizar en un fondo oscuro en el modo de contraste alto.<br /><br /> Si se omite el atributo Background, el origen se puede utilizar en cualquier fondo.<br /><br /> Si Background es *Light*, *Dark*, *HighContrastLight*o *HighContrastDark*, los colores del origen nunca se invierten. Si Background se omite o se establece en *HighContrast*, la inversión de los colores del origen se controla mediante el atributo **AllowColorInversion** de la imagen.|

Un \<elemento Source> puede tener exactamente uno de los siguientes subelementos opcionales:

||||
|-|-|-|
|**Elemento**|**Atributos (todos requeridos)**|**Definición**|
|\<Tamaño>|Value|La fuente se utilizará para imágenes del tamaño dado (en unidades de dispositivo). La imagen será cuadrada.|
|\<> sizeRange|MinSize, MaxSize|El origen se utilizará para las imágenes de MinSize a MaxSize (en unidades de dispositivo) de forma inclusiva. La imagen será cuadrada.|
|\<Dimensiones>|Ancho, alto|La fuente se utilizará para imágenes de la anchura y altura dadas (en unidades de dispositivo).|
|\<> De DimensionRange|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|La fuente se utilizará para imágenes desde la anchura/altura mínima hasta la anchura/altura máxima (en unidades de dispositivo) inclusive.|

 Un \<elemento source> también \<puede tener un subelemento \<nativoopcional>, que define un> de origen que se carga desde un ensamblado nativo en lugar de un ensamblado administrado.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Atributo**|**Definición**|
|Tipo|[Requerido] El tipo del recurso nativo, XAML o PNG|
|id|[Requerido] La parte de ID entero del recurso nativo|

 **Imagelist**

 El \<Elemento de> ImageList define una colección de imágenes que se pueden devolver en una sola tira. La tira se construye bajo demanda, según sea necesario.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Atributo**|**Definición**|
|Guid|[Requerido] La parte GUID del moniker de imagen|
|id|[Requerido] La parte id del moniker de imagen|
|Externo|[Opcional, predeterminado false] Indica si el moniker de imagen hace referencia a una imagen en el manifiesto actual.|

 El moniker de la imagen contenida no tiene que hacer referencia a una imagen definida en el manifiesto actual. Si la imagen contenida no se encuentra en la biblioteca de imágenes, se utilizará una imagen de marcador de posición en blanco en su lugar.

## <a name="using-the-image-service"></a>Uso del servicio de imágenes

### <a name="first-steps-managed"></a>Primeros pasos (administrados)
 Para usar el servicio de imágenes, debe agregar referencias a algunos o todos los ensamblados siguientes al proyecto:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Necesario si utiliza el catálogo de imágenes integrado **KnownMonikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Necesario si usa **CrispImage** e **ImageThemingUtilities** en la interfaz de usuario de WPF.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Necesario si utiliza los tipos **ImageMoniker** y **ImageAttributes.**

  - **EmbedInteropTypes** debe establecerse en true.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Necesario si usa el **IVsImageService2** tipo.

  - **EmbedInteropTypes** debe establecerse en true.

- *Microsoft.VisualStudio.Utilities.dll*

  - Necesario si usa **el BrushToColorConverter** para el **ImageThemingUtilities.ImageBackgroundColor** en la interfaz de usuario de WPF.

- *Microsoft.VisualStudio.Shell. \<VSVersion>.0*

  - Necesario si utiliza el **Tipo IVsUIObject.**

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Necesario si utiliza las aplicaciones auxiliares de interfaz de usuario relacionadas con WinForms.

  - **EmbedInteropTypes** debe establecerse en true

### <a name="first-steps-native"></a>Primeros pasos (nativo)
 Para utilizar el servicio de imágenes, debe incluir algunos o todos los encabezados siguientes en el proyecto:

- **KnownImageIds.h**

  - Necesario si usa el catálogo de imágenes integrado **KnownMonikers**, pero no puede usar el tipo **ImageMoniker,** como al devolver valores de **IVsHierarchy GetGuidProperty** o **GetProperty** llamadas.

- **KnownMonikers.h**

  - Necesario si utiliza el catálogo de imágenes integrado **KnownMonikers**.

- **ImageParameters140.h**

  - Necesario si utiliza los tipos **ImageMoniker** y **ImageAttributes.**

- **VSShell140.h**

  - Necesario si usa el **IVsImageService2** tipo.

- **ImageThemingUtilities.h**

  - Necesario si no puede permitir que el servicio de imágenes se encargue de la segmentación por usted.

  - No utilice este encabezado si el servicio de imágenes puede controlar el tema de la imagen.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Necesario si utiliza las aplicaciones auxiliares de PPP para obtener el PPP actual.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Necesario si utiliza las aplicaciones auxiliares de reconocimiento de PPP para obtener el PPP actual.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>¿Cómo escribo una nueva interfaz de usuario de WPF?

1. Comience agregando las referencias de ensamblado necesarias en la sección de los primeros pasos anteriores al proyecto. No es necesario agregarlos todos, así que agregue solo las referencias que necesita. (Nota: si está utilizando o tiene acceso a **Colores** en lugar de **Pinceles**, entonces puede omitir la referencia a **Utilidades,** ya que no necesitará el convertidor.)

2. Seleccione la imagen deseada y obtenga su apodo. Utilice un **KnownMoniker**o utilice el suyo propio si tiene sus propias imágenes y monikers personalizados.

3. Agrega **CrispImages** a tu XAML. (Véase el siguiente ejemplo.)

4. Establezca la propiedad **ImageThemingUtilities.ImageBackgroundColor** en la jerarquía de la interfaz de usuario. (Esto debe establecerse en la ubicación donde se conoce el color de fondo, no necesariamente en el **CrispImage**.) (Véase el siguiente ejemplo.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **¿Cómo actualizo la interfaz de usuario de WPF existente?**

 La actualización de la interfaz de usuario de WPF existente es un proceso relativamente sencillo que consta de tres pasos básicos:

1. Reemplace \<todos los elementos \<Image> de la interfaz de usuario por elementos de> CrispImage.

2. Cambie todos los atributos Source a Moniker attributes.

    - Si la imagen nunca cambia y está utilizando **KnownMonikers**, vincule estáticamente esa propiedad al **KnownMoniker**. (Véase el ejemplo anterior.)

    - Si la imagen nunca cambia y está utilizando su propia imagen personalizada, entonces enlace estáticamente a su propio apodo.

    - Si la imagen puede cambiar, enlace el Moniker atributo a una propiedad de código que notifica los cambios de propiedad.

3. En algún lugar de la jerarquía de la interfaz de usuario, establezca **ImageThemingUtilities.ImageBackgroundColor** para asegurarse de que la inversión de color funciona correctamente.

    - Esto puede requerir el uso de la **BrushToColorConverter** clase. (Véase el ejemplo anterior.)

## <a name="how-do-i-update-win32-ui"></a>¿Cómo actualizo la interfaz de usuario de Win32?
 Agregue lo siguiente al código cuando corresponda para reemplazar la carga sin procesar de imágenes. Cambiar valores para devolver HBITMAPs frente a HICONs frente a HIMAGELIST según sea necesario.

 **Obtenga el servicio de imágenes**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Solicitar la imagen**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>¿Cómo actualizo la interfaz de usuario de WinForms?
 Agregue lo siguiente al código cuando corresponda para reemplazar la carga sin procesar de imágenes. Cambie los valores para devolver mapas de bits frente a iconos según sea necesario.

 **Útil uso de la declaración**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Obtenga el servicio de imágenes**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Solicitar la imagen**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>¿Cómo utilizo monikers de imagen en una nueva ventana de herramientas?
 La plantilla de proyecto de paquete VSIX se actualizó para Visual Studio 2015. Para crear una nueva ventana de herramientas, haga clic con el botón derecho en el proyecto VSIX y seleccione **Agregar** > **nuevo elemento** (**Ctrl**+**Shift**+**A**). En el nodo Extensibilidad para el idioma del proyecto, seleccione Ventana de **herramientas personalizadas**, asigne un nombre a la ventana de herramientas y pulse el botón **Agregar.**

 Estos son los lugares clave para usar monikers en una ventana de herramientas. Siga las instrucciones para cada uno:

1. La pestaña de la ventana de herramientas cuando las pestañas se vuelven lo suficientemente pequeñas (también se utiliza en el modificador de ventana **Ctrl**+**Tab).**

    Agregue esta línea al constructor de la clase que deriva del tipo **ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. El comando para abrir la ventana de herramientas.

    En el archivo *.vsct* del paquete, edite el botón de comando de la ventana de herramientas:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **¿Cómo utilizo monikers de imagen en una ventana de herramientas existente?**

   La actualización de una ventana de herramientas existente para utilizar monikers de imagen es similar a los pasos para crear una nueva ventana de herramientas.

   Estos son los lugares clave para usar monikers en una ventana de herramientas. Siga las instrucciones para cada uno:

3. La pestaña de la ventana de herramientas cuando las pestañas se vuelven lo suficientemente pequeñas (también se utiliza en el modificador de ventana **Ctrl**+**Tab).**

   1. Quite estas líneas (si existen) en el constructor de la clase que deriva del tipo **ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Consulte el paso #1 de la "¿Cómo uso los monikers de imagen en una nueva ventana de herramientas?" sección anterior.

4. El comando para abrir la ventana de herramientas.

   - Vea el paso #2 de la "¿Cómo uso los monikers de imagen en una nueva ventana de herramientas?" sección anterior.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>¿Cómo uso los monikers de imagen en un archivo .vsct?
 Actualice su archivo *.vsct* como se indica en las líneas comentadas a continuación:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **¿Qué sucede si mi archivo .vsct también necesita ser leído por versiones anteriores de Visual Studio?**

 Las versiones anteriores de Visual Studio no reconocen la marca de comando **IconIsMoniker.** Puede usar imágenes del servicio de imágenes en versiones de Visual Studio que lo admiten, pero seguir usando imágenes de estilo antiguo en versiones anteriores de Visual Studio. Para ello, dejaría el archivo *.vsct* sin cambios (y, por lo tanto, compatible con versiones anteriores de Visual Studio) y crearía \<un archivo CSV (valores separados por comas) que se asigna a partir de pares GUID/ID definidos en el elemento de> Bitmaps de un archivo *.vsct* a los pares GUID/ID de moniker de imagen.

 El formato del archivo CSV de asignación es:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 El archivo CSV se implementa con el paquete y su ubicación se especifica mediante la propiedad **IconMappingFilename** del atributo de paquete **ProvideMenuResource:**

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 El **IconMappingFilename** es una ruta de acceso relativa implícitamente arraigada en $PackageFolder$ (como en el ejemplo anterior) o una ruta de acceso absoluta explícitamente arraigada en un directorio definido por una variable de entorno, como *por ejemplo, "%UserProfile%-dir1-dir2-MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>¿Cómo puedo portar un sistema de proyecto?
 **Cómo suministrar ImageMonikers para un proyecto**

1. Implemente **VSHPROPID_SupportsIconMonikers** en **IVsHierarchy**del proyecto y devuelva true.

2. Implemente **VSHPROPID_IconMonikerImageList** (si el proyecto original utiliza **VSHPROPID_IconImgList)** o **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (si el proyecto original usó **VSHPROPID_IconHandle** y **VSHPROPID_OpenFolderIconHandle).**

3. Cambie la implementación de los VSHPROPID originales para los iconos para crear versiones "heredadas" de los iconos si los puntos de extensión los solicitan. **IVsImageService2** proporciona la funcionalidad necesaria para obtener esos iconos

   **Requisitos adicionales para los sabores del proyecto VB/C**

   Implemente **solo VSHPROPID_SupportsIconMonikers** si detecta que su proyecto es el **sabor más externo.** De lo contrario, el sabor más externo real puede no admitir monikers de imagen en realidad, y su sabor base podría efectivamente "ocultar" imágenes personalizadas.

   **¿Cómo utilizo monikers de imagen en CPS?**

   La configuración de imágenes personalizadas en CPS (Common Project System) se puede realizar manualmente o a través de una plantilla de elemento que viene con el SDK de extensibilidad del sistema de proyectos.

   **Uso del SDK de extensibilidad del sistema de proyectos**

   Siga las instrucciones de [Proporcionar iconos personalizados para el tipo de proyecto/tipo](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) de elemento para personalizar las imágenes de CPS. Puede encontrar más información sobre CPS en la documentación de [extensibilidad](https://github.com/Microsoft/VSProjectSystem) de Visual Studio Project System

   **Utilizar manualmente ImageMonikers**

4. Implemente y exporte la interfaz **IProjectTreeModifier** en el sistema de proyectos.

5. Determine qué **conocidoMoniker** o moniker de imagen personalizado desea utilizar.

6. En el método **ApplyModifications,** realice lo siguiente en algún lugar del método antes de devolver el nuevo árbol, de forma similar al ejemplo siguiente:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Si va a crear un nuevo árbol, puede establecer las imágenes personalizadas pasando los monikers deseados en el método NewTree, de forma similar al ejemplo siguiente:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>¿Cómo puedo convertir de una tira de imagen real a una tira de imagen basada en moniker?
 **Necesito apoyar a HIMAGELISTs**

 Si ya hay una tira de imágenes existente para el código que desea actualizar para usar el servicio de imágenes, pero está limitado por las API que requieren pasar listas de imágenes, todavía puede obtener las ventajas del servicio de imágenes. Para crear una tira de imagen basada en moniker, siga los pasos que se indican a continuación para crear un manifiesto a partir de monikers existentes.

1. Ejecute la herramienta **ManifestFromResources** y pasándole la tira de imagen. Esto generará un manifiesto para la tira.

   - Recomendado: proporcione un nombre no predeterminado para que el manifiesto se adapte a su uso.

2. Si solo utiliza **KnownMonikers**, haga lo siguiente:

   - Reemplace \<la sección Imágenes \<> del manifiesto por Imágenes/>.

   - Elimine todos los ID de subimagen (cualquier cosa con \<el nombre de la tira de imágenes>_).

   - Recomendado: cambie el nombre del símbolo AssetsGuid y del símbolo de la tira de imagen para que se adapte a su uso.

   - Reemplace cada GUID de **ContainedImage**por $(ImageCatalogGuid), reemplace cada ID\<de **ContainedImage**por $( moniker>) y agregue el atributo External-"true" a cada **ContainedImage**

       - \<> de apodos deben reemplazarse con el **ConocidoMoniker** que coincida con la imagen pero con el "ConocidoMonikers". del nombre.

   - Agregue <Manifiesto de importación\\ "$(ManifestFolder)\><Ruta de acceso de dir de\* instalación relativa a \<* .Microsoft.VisualStudio.ImageCatalog.imagemanifest" /> en la parte superior de la> sección Símbolos.

       - La ruta de acceso relativa viene determinada por la ubicación de implementación definida en la creación de la configuración para el manifiesto.

3. Ejecute la herramienta **ManifestToCode** para generar contenedores de modo que el código existente tenga un moniker que pueda usar para consultar el servicio de imágenes para la tira de imágenes.

   - Recomendado: proporcione nombres no predeterminados para los contenedores y espacios de nombres para adaptarse a su uso.

4. Realice todos los complementos, la creación/implementación de la configuración y otros cambios de código para trabajar con el servicio de imágenes y los nuevos archivos.

   Manifiesto de ejemplo que incluye imágenes internas y externas para ver cómo debería ser:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **No necesito apoyar a HIMAGELISTs**

1. Determine el conjunto de **KnownMonikers** que coincidan con las imágenes de la tira de imágenes o cree sus propios monikers para las imágenes de la tira de imágenes.

2. Actualice cualquier asignación que haya utilizado para obtener la imagen en el índice requerido en la tira de imagen para usar los monikers en su lugar.

3. Actualice el código para usar el servicio de imágenes para solicitar monikers a través de la asignación actualizada. (Esto podría significar actualizar a **CrispImages** para código administrado, o solicitar HBITMAPs o HICONs del servicio de imágenes y pasarlos para código nativo.)

## <a name="testing-your-images"></a>Prueba de tus imágenes
 Puede utilizar la herramienta Visor de biblioteca de imágenes para probar los manifiestos de imagen para asegurarse de que todo está creado correctamente. Puede encontrar la herramienta en el SDK de [Visual Studio 2015](visual-studio-sdk.md). La documentación de esta herramienta y otras se pueden encontrar [aquí](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Recursos adicionales

### <a name="samples"></a>Ejemplos
 Varios de los ejemplos de Visual Studio en GitHub se han actualizado para mostrar cómo usar el servicio de imágenes como parte de varios puntos de extensibilidad de Visual Studio.

 Compruebe [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) las muestras más recientes.

### <a name="tooling"></a>Tooling
 Se creó un conjunto de herramientas de soporte técnico para el servicio de imágenes para ayudar a crear o actualizar la interfaz de usuario que funciona con el servicio de imágenes. Para obtener más información acerca de cada herramienta, consulte la documentación que viene con las herramientas. Las herramientas se incluyen como parte del SDK de [Visual Studio 2015.](visual-studio-sdk.md)

 **ManifestFromResources**

 La herramienta Manifiesto de recursos toma una lista de recursos de imagen (PNG o XAML) y genera un archivo de manifiesto de imagen para usar esas imágenes con el servicio de imágenes.

 **ManifestToCode**

 La herramienta Manifiesto en código toma un archivo de manifiesto de imagen y genera un archivo contenedor para hacer referencia a los valores de manifiesto en código (c++ , C o VB) o archivos *.vsct.*

 **ImageLibraryViewer**

 La herramienta Visor de biblioteca de imágenes puede cargar manifiestos de imagen y permite al usuario manipularlos de la misma manera que Visual Studio para asegurarse de que el manifiesto se crea correctamente. El usuario puede modificar el fondo, los tamaños, la configuración de PPP, el contraste alto y otros ajustes. También muestra información de carga para buscar errores en los manifiestos y muestra información de origen para cada imagen del manifiesto.

## <a name="faq"></a>Preguntas más frecuentes

- ¿Hay alguna dependencia que debe \<incluir al cargar Reference Include"Microsoft.VisualStudio.*. Interop.14.0.DesignTime" />?

  - Establezca EmbedInteropTypes"true" en todos los archivos DLL de interoperabilidad.

- ¿Cómo implemento un manifiesto de imagen con mi extensión?

  - Agregue el archivo *.imagemanifest* al proyecto.

  - Establezca "Incluir en VSIX" en True.

- Estoy actualizando mi sistema de proyectos CPS. ¿Qué pasó con **ImageName** y **StockIconService?**

  - Estos se eliminaron cuando CPS se actualizó para usar monikers. Ya no es necesario llamar a **StockIconService**, simplemente pasar el **KnownMoniker** deseado al método o propiedad mediante el método de extensión **ToProjectSystemType()** en las utilidades cpS. Puede encontrar una asignación de **ImageName** a **KnownMonikers** a continuación:

    |||
    |-|-|
    |**ImageName**|**KnownMoniker**|
    |ImageName.OfflineWebApp|KnownImageIds.Web|
    |ImageName.WebReferencesFolder|KnownImageIds.Web|
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName.ReferenceFolder|KnownImageIds.Reference|
    |ImageName.Reference|KnownImageIds.Reference|
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName.Folder|KnownImageIds.FolderClosed|
    |ImageName.OpenFolder|KnownImageIds.FolderOpened|
    |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName.ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName.DependentFile|KnownImageIds.GenerateFile|
    |ImageName.MissingFile|KnownImageIds.DocumentWarning|
    |ImageName.WindowsForm|KnownImageIds.WindowsForm|
    |ImageName.WindowsUserControl|KnownImageIds.UserControl|
    |ImageName.WindowsComponent|KnownImageIds.ComponentFile|
    |ImageName.XmlSchema|KnownImageIds.XMLSchema|
    |ImageName.XmlFile|KnownImageIds.XMLFile|
    |ImageName.WebForm|KnownImageIds.Web|
    |ImageName.WebService|KnownImageIds.WebService|
    |ImageName.WebUserControl|KnownImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName.AspPage|KnownImageIds.ASPFile|
    |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName.StyleSheet|KnownImageIds.StyleSheet|
    |ImageName.ScriptFile|KnownImageIds.JSScript|
    |ImageName.TextFile|KnownImageIds.Document|
    |ImageName.SettingsFile|KnownImageIds.Settings|
    |ImageName.Resources|KnownImageIds.DocumentGroup|
    |ImageName.Bitmap|KnownImageIds.Image|
    |ImageName.Icon|KnownImageIds.IconFile|
    |ImageName.Image|KnownImageIds.Image|
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|
    |ImageName.XWorld|KnownImageIds.XWorldFile|
    |ImageName.Audio|KnownImageIds.Sound|
    |ImageName.Video|KnownImageIds.Media|
    |ImageName.Cab|KnownImageIds.CABProject|
    |ImageName.Jar|KnownImageIds.JARFile|
    |ImageName.DataEnvironment|KnownImageIds.DataTable|
    |ImageName.PreviewFile|KnownImageIds.Report|
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName.XsltFile|KnownImageIds.XSLTransform|
    |ImageName.Cursor|KnownImageIds.CursorFile|
    |ImageName.AppDesignerFolder|KnownImageIds.Property|
    |ImageName.Data|KnownImageIds.Database|
    |ImageName.Application|KnownImageIds.Application|
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|
    |ImageName.Pfx|KnownImageIds.Certificate|
    |ImageName.Snk|KnownImageIds.Rule|
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName.CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName.Empty|KnownImageIds.Blank|
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Estoy actualizando mi proveedor de lista de finalización. ¿Qué **KnownMonikers** coinciden con los antiguos **estándarStandardGlyphGroup** y **StandardGlyph** valores?

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegadoPúblico|
    |GlyphGroupDelegate|GlyphItemInternal|DelegadoInterno|
    |GlyphGroupDelegate|GlyphItemFriend|DelegadoInterno|
    |GlyphGroupDelegate|GlyphItemProtected|DelegadoProtegido|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtegido|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|
    |GlyphGroupOperator|GlyphItemProtected|OperadorProtegido|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|EstructuraPúblico|
    |GlyphGroupStruct|GlyphItemInternal|EstructuraInterno|
    |GlyphGroupStruct|GlyphItemFriend|EstructuraInterno|
    |GlyphGroupStruct|GlyphItemProtected|EstructuraProtegido|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|EstructuraAcceso atravesado|
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||Referencia|
    |GlyphLibrary||Biblioteca|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Diálogo|
    |GlyphOpenFolder||CarpetaAbierta|
    |GlyphClosedFolder||CarpetaCerrada|
    |GlyphArrow||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Fragmento de código|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation||StatusInformation|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||Recursividad|
    |GlyphXmlItem||Etiqueta|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||Documento|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||Llamada|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||Llamada|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
