---
title: Servicio de imágenes y catálogo | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4352575c811d76241721fc8343b6a48c012eddb7
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917411"
---
# <a name="image-service-and-catalog"></a>Catálogo y servicio de imágenes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este manual contiene instrucciones y procedimientos recomendados para adoptar el servicio de imágenes de Visual Studio y el catálogo de imágenes introducidos en Visual Studio 2015.  

 El servicio de imágenes introducido en Visual Studio 2015 permite a los desarrolladores obtener las mejores imágenes para el dispositivo y el tema elegido del usuario para mostrar la imagen, así como corregir los temas para el contexto en el que se muestran. La adopción del servicio de imágenes ayudará a eliminar los principales Pain Points relacionados con el mantenimiento de los recursos, el escalado de HDPI y los aspectos.  

|||  
|-|-|  
|**Problemas hoy**|**Soluciones**|  
|Fusión de color de fondo|Combinación alfa integrada|  
|Imágenes (algunas)|Metadatos de tema|  
|Modo de contraste alto|Recursos de contraste alto alternativos|  
|Necesidad de varios recursos para diferentes modos de PPP|Recursos seleccionables con reserva basada en vectores|  
|Imágenes duplicadas|Un identificador por concepto de imagen|  

 ¿Por qué adoptar el servicio de imágenes?  

- Obtenga siempre la imagen más reciente "píxel-Perfect" de Visual Studio  

- Puede enviar y usar sus propias imágenes.  

- No es necesario probar las imágenes cuando Windows agrega nuevo ajuste de escala de PPP  

- Solucione los obstáculos arquitectónicos anteriores en sus implementaciones  

  La barra de herramientas de Visual Studio Shell antes y después de usar el servicio de imágenes:  

  ![Servicio de imagen antes y después](../extensibility/media/image-service-before-and-after.png "Antes y después del servicio de imágenes")  

## <a name="how-it-works"></a>Cómo funciona  
 El servicio de imágenes puede proporcionar una imagen de mapa de imágenes adecuada para cualquier marco de interfaz de usuario compatible:  

- WPF: BitmapSource  

- WinForms: System. Drawing. Bitmap  

- Win32: HBITMAP  

  Diagrama de flujo del servicio de imágenes  

  ![Diagrama de flujo del servicio de imágenes](../extensibility/media/image-service-flow-diagram.png "Diagrama de flujo del servicio de imágenes")  

  **Monikers de imagen**  

  Un moniker de imagen (o moniker para abreviar) es un par GUID/ID que identifica de forma única un recurso de imagen o de lista de imágenes en la biblioteca de imágenes.  

  **Monikers conocidos**  

  Conjunto de monikers de imagen contenidos en el catálogo de imágenes de Visual Studio y consumible públicamente por cualquier componente o extensión de Visual Studio.  

  **Archivos de manifiesto de imagen**  

  Los archivos de manifiesto de imagen (. imagemanifest) son archivos XML que definen un conjunto de recursos de imagen, los monikers que representan esos recursos y la imagen o imágenes reales que representan cada activo. Los manifiestos de imagen pueden definir imágenes independientes o listas de imágenes para la compatibilidad con la interfaz de usuario heredada. Además, hay atributos que se pueden establecer en el recurso o en las imágenes individuales que hay detrás de cada recurso para cambiar Cuándo y cómo se muestran esos recursos.  

  **Esquema de manifiesto de imagen**  

  Un manifiesto de imagen completo tiene el siguiente aspecto:  

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

 Como ayuda para la lectura y el mantenimiento, el manifiesto de imagen puede usar símbolos para los valores de atributo. Los símbolos se definen de la siguiente manera:  

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
|Importar|Importa los símbolos del archivo de manifiesto especificado para su uso en el manifiesto actual.|  
|GUID|El símbolo representa un GUID y debe coincidir con el formato de GUID|  
|ID.|El símbolo representa un identificador y debe ser un entero no negativo|  
|Cadena|El símbolo representa un valor de cadena arbitrario|  

 Los símbolos distinguen mayúsculas de minúsculas y se hace referencia a ellos mediante la sintaxis $ (nombre de símbolo):  

```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  

 Algunos símbolos están predefinidos para todos los manifiestos. Se pueden usar en el atributo URI de la > de \<Source o \<elemento Import > para hacer referencia a las rutas de acceso en el equipo local.  

|||  
|-|-|  
|**Símbolo**|**Descripción**|  
|CommonProgramFiles|El valor de la variable de entorno% CommonProgramFiles%|  
|LocalAppData|El valor de la variable de entorno% LocalAppData%|  
|ManifestFolder|La carpeta que contiene el archivo de manifiesto|  
|MyDocuments|La ruta de acceso completa de la carpeta Mis documentos del usuario actual|  
|ProgramFiles|El valor de la variable de entorno% ProgramFiles%|  
|System|La carpeta Windows\System32|  
|WinDir|El valor de la variable de entorno% WinDir%|  

 **Image**  

 El elemento \<imagen > define una imagen a la que se puede hacer referencia mediante un moniker. El GUID y el identificador se han tomado juntos en el moniker de la imagen. El moniker de la imagen debe ser único en toda la biblioteca de imágenes. Si hay más de una imagen con un moniker determinado, la primera que se encuentre al compilar la biblioteca es la que se conserva.  

 Debe contener al menos un origen. Los orígenes de tamaño neutro proporcionarán los mejores resultados en una amplia gama de tamaños, pero no son necesarios. Si se solicita al servicio una imagen de un tamaño que no está definido en el elemento de \<imagen > y no hay ningún origen independiente del tamaño, el servicio elegirá el mejor origen específico del tamaño y lo escalará al tamaño solicitado.  

```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  

|||  
|-|-|  
|**Attribute**|**Definición**|  
|GUID|Desee Parte del GUID del moniker de la imagen|  
|ID.|Desee La parte de identificador del moniker de imagen|  
|AllowColorInversion|[Opcional, valor predeterminado True] Indica si la imagen puede tener sus colores inversos mediante programación cuando se usa en un fondo oscuro.|  

 **Source**  

 El elemento de > de origen de \<define un recurso de origen de imagen único (XAML y PNG).  

```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  

|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Attribute** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            **Definición**                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      URI      |                                                                                                                                                                                                                                                                                                               Desee URI que define dónde se puede cargar la imagen. Puede tener uno de los valores siguientes:<br /><br /> -Un [pack uri](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) mediante la autoridad Application:///<br />-Una referencia de recurso de componente absoluta<br />-Una ruta de acceso a un archivo que contiene un recurso nativo                                                                                                                                                                                                                                                                                                               |
|  Información previa de   | Opta Indica qué tipo de fondo está previsto usar el origen.<br /><br /> Puede tener uno de los valores siguientes:<br /><br /> *Claro:* El origen se puede usar en un fondo claro.<br /><br /> <em>Oscuro:</em> El origen se puede usar en un fondo oscuro.<br /><br /> *HighContrast:* El origen se puede usar en cualquier fondo del modo contraste alto.<br /><br /> *HighContrastLight:* El origen se puede usar en un fondo claro en modo de contraste alto.<br /><br /> *HighContrastDark:* El origen se puede usar en un fondo oscuro en modo de contraste alto.<br /><br /> Si se omite el atributo Background, el origen puede usarse en cualquier fondo.<br /><br /> Si background es *Light*, *Dark*, *HighContrastLight*o *HighContrastDark*, los colores del origen nunca se invierten. Si se omite Background o se establece en *HighContrast*, el atributo **AllowColorInversion** de la imagen controla la inversión de los colores del origen. |
|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

 Un elemento de origen de \<> puede tener exactamente uno de los siguientes subelementos opcionales:  

||||  
|-|-|-|  
|**Element**|**Atributos (todos obligatorios)**|**Definición**|  
|Tamaño de \<|{2&gt;Value&lt;2}|El origen se usará para las imágenes del tamaño especificado (en unidades de dispositivo). La imagen será cuadrada.|  
|\<SizeRange>|MinSize, MaxSize|El origen se usará para las imágenes de MinSize a MaxSize (en unidades de dispositivo) de un solo uso. La imagen será cuadrada.|  
|\<dimensiones >|Width, Height|El origen se usará para las imágenes con el ancho y alto especificados (en unidades de dispositivo).|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|El origen se usará para las imágenes desde el ancho o el alto mínimo hasta el ancho/alto máximo (en unidades de dispositivo), ambos inclusive.|  

 Un elemento \<Source > también puede tener un subelemento opcional \<NativeResource >, que define un \<de origen > que se carga desde un ensamblado nativo en lugar de un ensamblado administrado.  

```xml  
<NativeResource Type="type" ID="int" />  
```  

|||  
|-|-|  
|**Attribute**|**Definición**|  
|Tipo de|Desee El tipo del recurso nativo, ya sea XAML o PNG|  
|ID.|Desee La parte del identificador entero del recurso nativo|  

 **ImageList**  

 El elemento \<ImageList > define una colección de imágenes que se pueden devolver en una sola banda. La franja se basa en la demanda, según sea necesario.  

```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  

|||  
|-|-|  
|**Attribute**|**Definición**|  
|GUID|Desee Parte del GUID del moniker de la imagen|  
|ID.|Desee La parte de identificador del moniker de imagen|  
|Externo|[Opcional, valor predeterminado False] Indica si el moniker de imagen hace referencia a una imagen del manifiesto actual.|  

 No es necesario que el moniker de la imagen contenida haga referencia a una imagen definida en el manifiesto actual. Si no se encuentra la imagen contenida en la biblioteca de imágenes, se usará una imagen de marcador de posición en blanco en su lugar.  

## <a name="using-the-image-service"></a>Usar el servicio de imágenes  

### <a name="first-steps-managed"></a>Primeros pasos (administrados)  
 Para usar el servicio de imágenes, debe agregar referencias a algunos o a todos los ensamblados siguientes en el proyecto:  

- **Microsoft.VisualStudio.ImageCatalog.dll**  

  - Obligatorio si usa el catálogo de imágenes integrado KnownMonikers  

- **Microsoft.VisualStudio.Imaging.dll**  

  - Obligatorio si usa **CrispImage** y **ImageThemingUtilities** en la interfaz de usuario de WPF  

- **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  

  - Obligatorio si se usan los tipos **ImageMoniker** y **ImageAttributes**  

  - **EmbedInteropTypes** debe establecerse en true.  

- **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  

  - Obligatorio si se usa el tipo **IVsImageService2**  

  - **EmbedInteropTypes** debe establecerse en true.  

- **Microsoft.VisualStudio.Utilities.dll**  

  - Obligatorio si se usa **BrushToColorConverter** para ImageThemingUtilities. **ImageBackgroundColor** en la interfaz de usuario de WPF  

- **Microsoft.VisualStudio.Shell.\<VSVersion>.0**  

  - Obligatorio si se usa el tipo **IVsUIObject**  

- **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  

  - Obligatorio si usa las aplicaciones auxiliares de interfaz de usuario relacionadas con WinForms  

  - **EmbedInteropTypes** debe establecerse en true.  

### <a name="first-steps-native"></a>Primeros pasos (nativo)  
 Para usar el servicio de imágenes, debe incluir algunos o todos los encabezados siguientes en el proyecto:  

- **KnownImageIds.h**  

  - Obligatorio si se usa el catálogo de imágenes integrado **KnownMonikers**, pero no se puede usar el tipo **ImageMoniker** , como cuando se devuelven valores de llamadas **IVsHierarchy GetGuidProperty** o **GetProperty** .  

- **KnownMonikers.h**  

  - Obligatorio si usa el catálogo de imágenes integrado **KnownMonikers**.  

- **ImageParameters140.h**  

  - Obligatorio si se usan los tipos **ImageMoniker** y **ImageAttributes** .  

- **VSShell140.h**  

  - Obligatorio si se usa el tipo **IVsImageService2** .  

- **ImageThemingUtilities.h**  

  - Es necesario si no puede permitir que el servicio de imágenes Controle automáticamente sus requisitos.  

  - No use este encabezado si el servicio de imágenes puede controlar la imagen de los mismos.  

- **VSUIDPIHelper.h**  

  - Obligatorio si se usan las aplicaciones auxiliares de PPP para obtener el PPP actual.  

## <a name="how-do-i-write-new-wpf-ui"></a>Cómo escribir una nueva interfaz de usuario de WPF  

1. Comience agregando las referencias de ensamblado requeridas en la sección anterior de los primeros pasos del proyecto. No es necesario agregar todos ellos, por lo que debe agregar solo las referencias que necesite. (Nota: Si usa o tiene acceso a los **colores** en lugar de a los **pinceles**, puede omitir la referencia a las **utilidades**, ya que no necesitará el convertidor).  

2. Seleccione la imagen deseada y obtenga su moniker. Use un **KnownMoniker**, o bien use el suyo propio si tiene sus propias imágenes y monikers personalizados.  

3. Agregue **CrispImages** a su XAML. (Vea el ejemplo siguiente).  

4. Establezca la propiedad **ImageThemingUtilities. ImageBackgroundColor** en la jerarquía de la interfaz de usuario. (Debe establecerse en la ubicación donde se conoce el color de fondo, no necesariamente en el **CrispImage**). (Vea el ejemplo siguiente).  

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

 **¿Cómo actualizar la interfaz de usuario de WPF existente?**  

 Actualizar la interfaz de usuario de WPF existente es un proceso relativamente sencillo que consta de tres pasos básicos:  

1. Reemplazar todos los elementos de la imagen \<> en la interfaz de usuario con \<elementos > CrispImage  

2. Cambiar todos los atributos de origen a atributos de moniker  

    - Si la imagen nunca cambia y usa **KnownMonikers**, enlace estáticamente esa propiedad a **KnownMoniker**. (Vea el ejemplo anterior).  

    - Si la imagen nunca cambia y usa su propia imagen personalizada, enlace de forma estática a su propio moniker.  

    - Si la imagen puede cambiar, enlace el atributo moniker a una propiedad de código que notifique los cambios de propiedad.  

3. En algún lugar de la jerarquía de la interfaz de usuario, establezca **ImageThemingUtilities. ImageBackgroundColor** para asegurarse de que la inversión de color funciona correctamente.  

    - Esto podría requerir el uso de la clase **BrushToColorConverter** . (Vea el ejemplo anterior).  

## <a name="how-do-i-update-win32-ui"></a>Cómo actualizar la interfaz de usuario de Win32  
 Agregue lo siguiente al código siempre que sea adecuado para reemplazar la carga sin procesar de las imágenes. Cambie los valores para devolver HBITMAPs frente a HICONs frente a HIMAGELIST según sea necesario.  

 **Obtención del servicio de imágenes**  

```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  

 **Solicitud de la imagen**  

```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  

CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  

```  

## <a name="how-do-i-update-winforms-ui"></a>¿Cómo actualizar la interfaz de usuario de WinForms?  
 Agregue lo siguiente al código siempre que sea adecuado para reemplazar la carga sin procesar de las imágenes. Cambie los valores para devolver mapas de bits frente a iconos según sea necesario.  

 **Instrucciones Using útiles**  

```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  

 **Obtención del servicio de imágenes**  

```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  

```  

 **Solicitud de la imagen**  

```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  

// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  

```  

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>¿Cómo usar monikers de imagen en una nueva ventana de herramientas?  
 La plantilla de proyecto de paquete VSIX se actualizó para Visual Studio 2015. Para crear una nueva ventana de herramientas, haga clic con el botón derecho en el Proyecto VSIX y seleccione "Agregar nuevo elemento...". (Ctrl + Mayús + A). En el nodo extensibilidad del lenguaje del proyecto, seleccione "ventana de herramientas personalizada", asigne un nombre a la ventana de herramientas y haga clic en el botón "agregar".  

 Estos son los lugares principales para usar monikers en una ventana de herramientas. Siga las instrucciones para cada una:  

1. La pestaña de la ventana de herramientas cuando las pestañas son lo suficientemente pequeñas (también se usan en el modificador de la ventana Ctrl + Tab).  

    Agregue esta línea al constructor de la clase que se deriva del tipo **ToolWindowPane** :  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  

2. El comando para abrir la ventana de herramientas.  

    En el archivo. Vsct del paquete, edite el botón de comando de la ventana de herramientas:  

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

   **¿Cómo usar monikers de imagen en una ventana de herramientas existente?**  

   Actualizar una ventana de herramientas existente para usar monikers de imagen es similar a los pasos para crear una nueva ventana de herramientas.  

   Estos son los lugares principales para usar monikers en una ventana de herramientas. Siga las instrucciones para cada una:  

3. La pestaña de la ventana de herramientas cuando las pestañas son lo suficientemente pequeñas (también se usan en el modificador de la ventana Ctrl + Tab).  

   1. Quite estas líneas (si existen) en el constructor de la clase que deriva del tipo **ToolWindowPane** :  

       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  

   2. Vea el paso #1 de la sección "¿Cómo uso de monikers de imagen en una nueva ventana de herramientas?". sección anterior.  

4. El comando para abrir la ventana de herramientas.  

   - Vea el paso #2 de la sección "¿Cómo uso de monikers de imagen en una nueva ventana de herramientas?". sección anterior.  

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Cómo usar monikers de imagen en un archivo. Vsct?  
 Actualice el archivo. Vsct como se indica en las líneas comentadas a continuación:  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
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

 **¿Qué ocurre si el archivo. Vsct también necesita ser leído por versiones anteriores de Visual Studio?**  

 Las versiones anteriores de Visual Studio no reconocen la marca de comando **IconIsMoniker** . Puede usar imágenes del servicio de imágenes en las versiones de Visual Studio que lo admiten, pero seguir usando imágenes de estilo antiguo en versiones anteriores de Visual Studio. Para ello, debe dejar el archivo. Vsct sin modificar (y, por lo tanto, compatible con versiones anteriores de Visual Studio) y crear un archivo CSV (valores separados por comas) que se asigne a los pares GUID/identificador definidos en un archivo. Vsct \<mapas de > bits de los pares GUID/ID de los moniker de imagen.  

 El formato del archivo CSV de asignación es:  

```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  

 El archivo CSV se implementa con el paquete y su ubicación se especifica mediante la propiedad **IconMappingFilename** del atributo de paquete **ProvideMenuResource** :  

```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  

 **IconMappingFilename** es una ruta de acceso relativa cuya raíz es implícita en $PackageFolder $ (como en el ejemplo anterior) o una ruta de acceso absoluta con raíz explícita en un directorio definido por una variable de entorno, como @ "%userprofile%\dir1\dir2\MyMappingFile.csv".  

## <a name="how-do-i-port-a-project-system"></a>¿Cómo puerto un sistema de proyectos?  
 **Cómo proporcionar ImageMonikers para un proyecto**  

1. Implemente **VSHPROPID_SupportsIconMonikers** en el **IVsHierarchy**del proyecto y devuelva true.  

2. Implemente **VSHPROPID_IconMonikerImageList** (si el proyecto original usaba **VSHPROPID_IconImgList**) o **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId** **VSHPROPID_OpenFolderIconMonikerGuid** **, VSHPROPID_OpenFolderIconMonikerId (si** el proyecto original usaba **VSHPROPID_IconHandle** y **VSHPROPID_OpenFolderIconHandle**).  

3. Cambie la implementación del VSHPROPIDs original para iconos para crear versiones "heredadas" de los iconos si los puntos de extensión los solicitan. **IVsImageService2** proporciona la funcionalidad necesaria para obtener esos iconos.  

   **Requisitos adicionales para VB/C# tipos de proyecto**  

   Solo implemente **VSHPROPID_SupportsIconMonikers** si detecta que el proyecto es el **tipo más externo**. De lo contrario, es posible que el tipo más externo real no admita los monikers de la imagen en realidad y que el tipo base pueda "ocultar" imágenes personalizadas.  

   **¿Cómo usar monikers de imagen en CPS?**  

   La configuración de imágenes personalizadas en CPS (sistema común de proyectos) puede realizarse manualmente o a través de una plantilla de elementos que se incluye con el SDK de extensibilidad del sistema de proyectos.  

   **Usar el SDK de extensibilidad del sistema del proyecto**  

   Siga las instrucciones de [proporcionar iconos personalizados para el tipo de proyecto/tipo de elemento](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) para personalizar las imágenes de CPS. Puede encontrar más información sobre CPS en la [documentación de extensibilidad del sistema de proyectos de Visual Studio](https://github.com/Microsoft/VSProjectSystem)  

   **Uso manual de ImageMonikers**  

4. Implemente y exporte la interfaz **IProjectTreeModifier** en el sistema del proyecto.  

5. Determine qué **moKnownMoniker** o moniker de imagen personalizado desea usar.  

6. En el método **ApplyModifications** , realice lo siguiente en alguna parte del método antes de devolver el nuevo árbol, similar al ejemplo siguiente:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
   ```  

7. Si va a crear un nuevo árbol, puede establecer las imágenes personalizadas pasando los monikers deseados al método NewTree, de forma similar al ejemplo siguiente:  

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Cómo convertir una franja de imágenes real en una franja de imágenes basada en moniker?  
 **Necesito admitir HIMAGELISTs**  

 Si ya existe una franja de imágenes para el código que desea actualizar para usar el servicio de imágenes, pero está restringida por las API que requieren pasar por las listas de imágenes, puede seguir aprovechando las ventajas del servicio de imágenes. Para crear una franja de imágenes basada en moniker, siga los pasos que se indican a continuación para crear un manifiesto a partir de monikers existentes.  

1. Ejecute la herramienta **ManifestFromResources** y pásele la franja de imagen. Se generará un manifiesto para la franja.  

   - Recomendado: proporcione un nombre no predeterminado para que el manifiesto se ajuste a su uso.  

2. Si solo usa **KnownMonikers**, haga lo siguiente:  

   - Reemplace la \<imágenes > sección del manifiesto con \<imágenes/>.  

   - Quite todos los identificadores de subimagen (cualquier elemento con \<nombre imagestrip > _ # #).  

   - Recomendado: cambie el nombre del símbolo AssetsGuid y el símbolo de la franja de imagen para que se ajuste a su uso.  

   - Reemplace el GUID de cada **ContainedImage**por $ (ImageCatalogGuid), reemplace el identificador de cada **ContainedImage**por $ (\<moniker >) y agregue el atributo external = "true" a cada **ContainedImage**  

       - \<moniker > debe reemplazarse por el **KnownMoniker** que coincide con la imagen, pero con "KnownMonikers". se ha quitado del nombre.  

   - Agregue < Import manifest = "$ (ManifestFolder)\\< ruta de acceso del directorio de instalación relativa a\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest"/\> en la parte superior de la \<de símbolos > sección.  

       - La ruta de acceso relativa viene determinada por la ubicación de implementación definida en la creación del programa de instalación para el manifiesto.  

3. Ejecute la herramienta **ManifestToCode** para generar contenedores para que el código existente tenga un moniker que pueda usar para consultar el servicio de imágenes para la franja de imagen.  

   - Recomendado: proporcione nombres no predeterminados para los contenedores y espacios de nombres que se adapten a su uso.  

4. Realice todas las adiciones, la implementación o la creación de la configuración y otros cambios de código para trabajar con el servicio de imágenes y los nuevos archivos.  

   Manifiesto de ejemplo que incluye imágenes internas y externas para ver su aspecto:  

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

 **No es necesario admitir HIMAGELISTs**  

1. Determine el conjunto de **KnownMonikers** que coinciden con las imágenes de la franja de imágenes o cree sus propios monikers para las imágenes de la franja de imágenes.  

2. Actualice la asignación que usó para obtener la imagen en el índice requerido de la franja de imágenes para usar los monikers en su lugar.  

3. Actualice el código para usar el servicio de imágenes para solicitar monikers a través de la asignación actualizada. (Esto podría significar actualizar a **CrispImages** para código administrado o solicitar HBITMAPs o HICONs desde el servicio de imágenes y pasarlos para código nativo).  

## <a name="testing-your-images"></a>Prueba de las imágenes  
 Puede usar la herramienta Visor de la biblioteca de imágenes para probar los manifiestos de imagen con el fin de asegurarse de que todo se ha creado correctamente. Puede encontrar la herramienta en el [SDK de Visual Studio 2015](visual-studio-sdk.md). La documentación de esta herramienta y otras se pueden encontrar [aquí](internals/vssdk-utilities.md).  

## <a name="additional-resources"></a>Recursos adicionales  

### <a name="samples"></a>Los ejemplos de  
 Algunos de los ejemplos de Visual Studio en GitHub se han actualizado para mostrar cómo usar el servicio de imágenes como parte de varios puntos de extensibilidad de Visual Studio.  

 Consulte [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) para obtener los ejemplos más recientes.  

### <a name="tooling"></a>Tooling  
 Se creó un conjunto de herramientas de soporte para el servicio de imágenes que ayudarán a crear o actualizar la interfaz de usuario que funciona con el servicio de imágenes. Para obtener más información acerca de cada herramienta, consulte la documentación que se incluye con las herramientas. Las herramientas se incluyen como parte del [SDK de Visual Studio 2015.](https://msdn.microsoft.com/library/bb166441.aspx)  

 **ManifestFromResources**  

 La herramienta Manifest from Resources toma una lista de recursos de imagen (PNG o XAML) y genera un archivo de manifiesto de imagen para usar esas imágenes con el servicio de imágenes.  

 **ManifestToCode**  

 La herramienta manifest to Code toma un archivo de manifiesto de imagen y genera un archivo contenedor para hacer referencia a los valoresC++del C#manifiesto en los archivos de código (, o VB) o. Vsct.  

 **ImageLibraryViewer**  

 La herramienta Visor de la biblioteca de imágenes puede cargar manifiestos de imagen y permite al usuario manipularlos de la misma manera que en Visual Studio se debe asegurar de que el manifiesto se crea correctamente. El usuario puede modificar el fondo, los tamaños, la configuración de PPP, contraste alto y otros valores de configuración. También muestra la información de carga para buscar errores en los manifiestos y muestra información de origen de cada imagen en el manifiesto.  

## <a name="faq"></a>Preguntas más frecuentes  

- Existen dependencias que se deben incluir al cargar \<referencia include = "Microsoft. VisualStudio. *. Interop. 14.0. DesignTime "/>?  

  - Establezca EmbedInteropTypes = "true" en todos los archivos dll de interoperabilidad.  

- Cómo implementar un manifiesto de imagen con mi extensión  

  - Agregue el archivo. imagemanifest al proyecto.  

  - Establezca "incluir en VSIX" en true.  

- Estoy actualizando el sistema del proyecto de CPS. ¿Qué ha ocurrido con **ImageName** y **StockIconService**?  

  - Se quitaron cuando se actualizó CPS para usar monikers. Ya no necesita llamar a **StockIconService**, simplemente pase el **KnownMoniker** deseado al método o propiedad mediante el método de extensión **ToProjectSystemType ()** en las utilidades de CPS. Puede encontrar una asignación de **ImageName** a **KnownMonikers** a continuación:  

    |||  
    |-|-|  
    |**ImageName**|**KnownMoniker**|  
    |ImageName.OfflineWebApp|KnownImageIds.Web|  
    |ImageName.WebReferencesFolder|KnownImageIds.Web|  
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
    |ImageName. ReferenceFolder|KnownImageIds.Reference|  
    |ImageName. Reference|KnownImageIds.Reference|  
    |ImageName. SdlWebReference|KnownImageIds.WebReferenceFolder|  
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
    |ImageName. XmlFile|KnownImageIds.XMLFile|  
    |ImageName.WebForm|KnownImageIds.Web|  
    |ImageName.WebService|KnownImageIds.WebService|  
    |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
    |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
    |ImageName.AspPage|KnownImageIds.ASPFile|  
    |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
    |ImageName. StyleSheet|KnownImageIds. StyleSheet|  
    |ImageName.ScriptFile|KnownImageIds.JSScript|  
    |ImageName.TextFile|KnownImageIds.Document|  
    |ImageName.SettingsFile|KnownImageIds. Settings|  
    |ImageName. Resources|KnownImageIds.DocumentGroup|  
    |ImageName.Bitmap|KnownImageIds.Image|  
    |ImageName.Icon|KnownImageIds.IconFile|  
    |ImageName.Image|KnownImageIds.Image|  
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
    |ImageName. XWorld|KnownImageIds.XWorldFile|  
    |ImageName. audio|KnownImageIds.Sound|  
    |ImageName.Video|KnownImageIds.Media|  
    |ImageName.Cab|KnownImageIds.CABProject|  
    |ImageName.Jar|KnownImageIds.JARFile|  
    |ImageName. Environment|KnownImageIds.DataTable|  
    |ImageName.PreviewFile|KnownImageIds.Report|  
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
    |ImageName.XsltFile|KnownImageIds.XSLTransform|  
    |ImageName.Cursor|KnownImageIds.CursorFile|  
    |ImageName.AppDesignerFolder|KnownImageIds.Property|  
    |ImageName. Data|KnownImageIds. Database|  
    |ImageName.Application|KnownImageIds.Application|  
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
    |ImageName.Pfx|KnownImageIds.Certificate|  
    |ImageName.Snk|KnownImageIds.Rule|  
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
    |ImageName. CSharpProject|KnownImageIds.CSProjectNode|  
    |ImageName. Empty|KnownImageIds. Blank|  
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
    |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  

  - Actualizo mi proveedor de lista de finalización. ¿Qué **KnownMonikers** coinciden con los valores antiguos de **StandardGlyphGroup** y **StandardGlyph** ?  

    ||||  
    |-|-|-|  
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
    |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
    |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
    |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
    |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
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
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
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
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
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
    |GlyphOpenFolder||FolderOpened|  
    |GlyphClosedFolder||FolderClosed|  
    |GlyphArrow||GoToNext|  
    |GlyphCSharpFile||CSFileNode|  
    |GlyphCSharpExpansion||Fragmento de código|  
    |GlyphKeyword||IntellisenseKeyword|  
    |GlyphInformation||StatusInformation|  
    |GlyphReference||ClassMethodReference|  
    |GlyphRecursion||Recursión|  
    |GlyphXmlItem||Etiqueta|  
    |GlyphJSharpProject||DocumentCollection|  
    |GlyphJSharpDocument||Documento|  
    |GlyphForwardType||GoToNext|  
    |GlyphCallersGraph||Llamar a|  
    |GlyphCallGraph||CallFrom|  
    |GlyphWarning||StatusWarning|  
    |GlyphMaybeReference||QuestionMark|  
    |GlyphMaybeCaller||Llamar a|  
    |GlyphMaybeCall||CallFrom|  
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
