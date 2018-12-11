---
title: Visor del archivo de imagen | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c0e277a123fe24da9824fae94b13eee686f5663
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778025"
---
# <a name="image-library-viewer"></a>Visor de la biblioteca de imágenes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La herramienta Visor de biblioteca de imágenes de Visual Studio puede cargar y buscar los manifiestos de imagen, que permite al usuario manipularlos en la misma manera Visual Studio. El usuario puede modificar otras opciones, tamaños, PPP, contraste alto y en segundo plano. La herramienta también muestra información de carga para cada manifiesto de imagen y muestra información de origen para cada imagen en el manifiesto de imagen. Esta herramienta es útil para:  
  
1. Diagnóstico de errores  
  
2. Cómo asegurarse de que atributos están correctamente configurados en los manifiestos de la imagen personalizada  
  
3. Buscar imágenes en el catálogo de imagen de Visual Studio para que una extensión de Visual Studio puede utilizar las imágenes que ajustar el estilo de Visual Studio  
  
   ![Imagen prominente del Visor de biblioteca](../../extensibility/internals/media/image-library-viewer-hero.png "imagen prominente del Visor de biblioteca")  
  
   **Moniker de imagen**  
  
   Un moniker de imagen (o moniker para abreviar) es un par de GUID: ID que identifica un recurso de imagen o un activo de la lista de imagen en la biblioteca de imágenes.  
  
   **Archivos de manifiesto de imagen**  
  
   Archivos de imagen de manifiesto (.imagemanifest) son archivos XML que definen un conjunto de activos de imagen, los monikers que representan esos recursos y la imagen real o imágenes que representan cada activo. Manifiestos de la imagen pueden definir imágenes independientes o listas de imágenes para admitir código heredado de la interfaz de usuario. Además, hay atributos que se pueden establecer en el recurso o en las imágenes individuales detrás de cada recurso para cambiar cuándo y cómo se muestran estos activos.  
  
   **Esquema del manifiesto de imagen**  
  
   Un manifiesto de imagen completo tiene este aspecto:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Guid, ID, or String elements -->  
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
  
 **Símbolos**  
  
 Como ayudan a mejorar la legibilidad y el mantenimiento, el manifiesto de imagen puede usar los símbolos para los valores de atributo. Los símbolos se definen de forma similar al siguiente:  
  
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
|GUID|El símbolo representa un GUID y debe coincidir con el formato de GUID.|  
|Id.|El símbolo representa un identificador y debe ser un entero no negativo.|  
|String|El símbolo representa un valor de cadena arbitrario.|  
  
 Los símbolos son distingue mayúsculas de minúsculas y que se hace referencia mediante la sintaxis $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Algunos símbolos están predefinidos para todos los manifiestos. Se pueden usar en el atributo de identificador Uri de la \<origen > o \<importación > elemento para rutas de acceso de referencia en el equipo local.  
  
|||  
|-|-|  
|**Símbolo**|**Descripción**|  
|CommonProgramFiles|El valor de la variable de entorno % CommonProgramFiles %|  
|LocalAppData|El valor de la variable de entorno % LocalAppData %|  
|ManifestFolder|La carpeta que contiene el archivo de manifiesto|  
|Mis documentos|La ruta de acceso completa de la carpeta Mis documentos del usuario actual|  
|ProgramFiles|El valor de la variable de entorno % ProgramFiles %|  
|Sistema|La carpeta Windows\System32|  
|WinDir|El valor de la variable de entorno % WinDir %|  
  
 **Image**  
  
 El \<imagen > elemento define una imagen que se puede hacer referencia mediante un moniker. El GUID y el Id. de juntas forman el moniker de imagen. El moniker de la imagen debe ser único en la biblioteca de imágenes completo. Si más de una imagen tiene un moniker especificado, la primera de ellas al compilar la biblioteca es lo que se conserva.  
  
 Debe contener al menos un origen. Aunque el tamaño neutro orígenes le dará los mejores resultados en una amplia gama de tamaños, no son necesarios. Si el servicio se le pide una imagen de un tamaño no está definido en el \<imagen > elemento y no hay ningún origen independiente del tamaño, el servicio elegir la mejor fuente de tamaño específico y lo escala al tamaño solicitado.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|GUID|[Obligatorio] La parte GUID del moniker de imagen|  
|Id.|[Obligatorio] La parte del identificador de moniker de la imagen|  
|AllowColorInversion|[Opcional, true de forma predeterminada] Indica si la imagen puede tener sus colores invertidos mediante programación cuando se utiliza en un fondo oscuro.|  
  
 **Origen**  
  
 El \<origen > elemento define un recurso de origen de imagen único (XAML y PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|URI|[Obligatorio] Un URI que define dónde se puede cargar la imagen desde. Puede ser uno de los siguientes:<br /><br /> -A [Pack URI](http://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) mediante la aplicación: / / / entidad<br /><br /> -Una referencia de recurso de componente absoluta<br /><br /> -Una ruta de acceso a un archivo que contiene un recurso nativo|  
|Fondo|[Opcional] Indica qué tipo de fondo que el origen está pensado para usarse.<br /><br /> Puede ser uno de los siguientes:<br /><br /> - *Luz*: el origen se puede usar en un fondo claro.<br /><br /> - *Oscuro*: el origen se puede usar en un fondo oscuro.<br /><br /> - *Contraste alto*: el origen se puede usar en cualquier en segundo plano en modo de contraste alto.<br /><br /> - *HighContrastLight*: el origen se puede usar en un fondo claro en modo de contraste alto.<br /><br /> -*HighContrastDark*: el origen se puede usar en un fondo oscuro en modo de contraste alto.<br /><br /> Si el **en segundo plano** se omite el atributo, el origen se puede usar en cualquier en segundo plano.<br /><br /> Si **en segundo plano** es *luz*, *oscuro*, *HighContrastLight*, o *HighContrastDark*, el nunca se invierten los colores de origen. Si **en segundo plano** se omite o se establece en *contraste alto*, la inversión de colores de origen se controla mediante la imagen **AllowColorInversion** atributo.|  
  
 Un \<origen > elemento puede tener exactamente uno de los siguientes subelementos opcionales:  
  
||||  
|-|-|-|  
|**Element**|**Atributos (todas requeridas)**|**Definición**|  
|\<Tamaño >|Valor|El origen se usará para las imágenes del tamaño especificado (en unidades de dispositivo). La imagen será cuadrada.|  
|\<SizeRange >|MinSize, MaxSize|El origen se usará para las imágenes de MinSize con tamaño máximo (en unidades de dispositivo), ambos inclusive. La imagen será cuadrada.|  
|\<Dimensiones >|Ancho, alto|El origen se usará para las imágenes del ancho y alto (en unidades de dispositivo).|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|El origen se usará para las imágenes desde el ancho y alto mínimo para el máximo ancho/alto (en unidades de dispositivo), ambos inclusive.|  
  
 Un \<origen > elemento también puede tener un elemento opcional \<NativeResource > subelemento, que define un \<origen > que se carga desde un ensamblado nativo en lugar de un ensamblado administrado.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|Tipo|[Obligatorio] El tipo del recurso nativo, XAML o PNG|  
|Id.|[Obligatorio] La parte de identificador entero del recurso nativo|  
  
 **ImageList**  
  
 El \<ImageList > elemento define una colección de imágenes que pueden devolverse en una banda única. La banda se compila a petición, según sea necesario.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|GUID|[Obligatorio] La parte GUID del moniker de imagen|  
|Id.|[Obligatorio] La parte del identificador de moniker de la imagen|  
|Externo|[Opcional, valor predeterminado es false] Indica si el moniker de imagen hace referencia a una imagen en el manifiesto actual.|  
  
 El moniker de la imagen independiente no tiene que hacer referencia a una imagen que se definen en el manifiesto actual. Si no se encuentra la imagen contenida en la biblioteca de imágenes, se utilizará una imagen de marcador de posición en blanco en su lugar.  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 **Validar un manifiesto de imagen personalizada**  
  
 Para crear un manifiesto personalizado, se recomienda que utilice la herramienta ManifestFromResources para generar automáticamente el manifiesto. Para validar el manifiesto personalizado, inicie el Visor del archivo de imagen y seleccione Archivo > rutas de acceso... Para abrir el cuadro de diálogo de directorios de búsqueda. La herramienta usará los directorios de búsqueda para cargar los manifiestos de la imagen, pero, también utilizará para buscar los archivos .dll que contienen las imágenes en un manifiesto, así que asegúrese de incluir el manifiesto y directorios de archivos DLL en este cuadro de diálogo.  
  
 ![Búsqueda del Visor de biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-search.png "búsqueda del Visor de biblioteca de imágenes")  
  
 Haga clic en **agregar...** Para seleccionar nuevos directorios de búsqueda para buscar los manifiestos y sus DLL correspondiente. La herramienta le recordarán estos directorios de búsqueda y se pueden activar o desactivar mediante la activación o desactivación de un directorio.  
  
 De forma predeterminada, la herramienta intentará encontrar el directorio de instalación de Visual Studio y agregue esos directorios a la lista de directorios de búsqueda. Puede agregar manualmente los directorios que no encuentra la herramienta.  
  
 Una vez que se cargan todos los manifiestos, la herramienta puede usarse para activar o desactivar **en segundo plano** colores, **PPP**, **contraste alto**, o **escala** para las imágenes para que un usuario puede inspeccionar visualmente los activos de imagen para comprobar que se están representando correctamente para diferentes configuraciones.  
  
 ![Imagen de fondo del Visor de biblioteca](../../extensibility/internals/media/image-library-viewer-background.png "la imagen de fondo del Visor de biblioteca")  
  
 El color de fondo puede establecerse en un valor personalizado, oscuro o claro. Selección de "Color personalizado" abrirá un cuadro de diálogo de selección de color y agregar ese color personalizado a la parte inferior del cuadro combinado en segundo plano para recuperarlos fácilmente más tarde.  
  
 ![Color personalizado del Visor de biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-custom-color.png "Color personalizado del Visor de biblioteca de imágenes")  
  
 Al seleccionar un moniker de imagen, muestra la información para cada imagen real detrás de ese moniker en el panel de detalles de la imagen de la derecha. El panel también permite a los usuarios copiar un moniker por nombre o por el valor sin formato GUID: Id.  
  
 ![Detalles de la imagen de biblioteca Visor de imágenes](../../extensibility/internals/media/image-library-viewer-image-details.png "biblioteca detalles de la imagen de Visor de imágenes")  
  
 La información mostrada para cada origen de la imagen incluye el tipo de fondo para que se muestre, si se puede aplicar un tema o admite el contraste alto, lo que es válido para los tamaños o si es independiente del tamaño y, si la imagen procede de un ensamblado nativo.  
  
 ![Visor del archivo de imagen puede tema](../../extensibility/internals/media/image-library-viewer-can-theme.png "Visor del archivo de imagen puede tema")  
  
 Al validar un manifiesto de imagen, se recomienda que implemente la imagen DLL en sus ubicaciones del mundo real y el manifiesto. Comprobará que las rutas relativas funciona correctamente y que la biblioteca de imágenes puede buscar y cargar la DLL de la imagen y el manifiesto.  
  
 **Búsqueda de catálogo de imágenes KnownMonikers**  
  
 Para adaptarse mejor al estilo de Visual Studio, una extensión de Visual Studio puede usar imágenes en el catálogo de imágenes de Visual Studio en lugar de crear y usar su propio. Esto tiene la ventaja de no tener que mantener esas imágenes y garantiza que la imagen tendrá una imagen de respaldo de valores altos de PPP, por lo que debe ser correcta en toda la configuración de PPP es compatible con Visual Studio.  
  
 El Visor del archivo de imagen permite un manifiesto que se debe buscar para que un usuario puede encontrar el moniker que representa un recurso de imagen y usar ese moniker en el código. Para buscar imágenes, escriba el término de búsqueda que desee en el cuadro de búsqueda y presione ENTRAR. Mostrará la barra de estado en la parte inferior se encontraron coincidencias cuántos fuera de las imágenes de total en todos los manifiestos.  
  
 ![Filtro del Visor de biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter.png "filtro del Visor de biblioteca de imágenes")  
  
 Cuando se buscan los monikers de la imagen en los manifiestos existentes, se recomienda que buscar y usar solo los monikers de la Visual Studio imágenes del catálogo, otros monikers intencionadamente públicamente accesibles o sus propio monikers personalizados. Si usa los monikers no públicos, se puede interrumpir la interfaz de usuario personalizada o sus imágenes cambiaron inesperados si o cuando se cambia o se actualizan los monikers no públicos e imágenes.  
  
 Además, es posible realizar búsquedas en GUID. Este tipo de búsqueda resulta útil para filtrar la lista a un único manifiesto o subsección único de un manifiesto si ese manifiesto contiene varios GUID.  
  
 ![Biblioteca GUID del filtro del Visor de imágenes](../../extensibility/internals/media/image-library-viewer-filter-guid.png "biblioteca GUID del filtro del Visor de imágenes")  
  
 Por último, buscar por Id. es posible también.  
  
 ![Id. de filtro del Visor de biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-id.png "Id. de filtro del Visor de biblioteca de imágenes")  
  
## <a name="notes"></a>Notas  
  
-   De forma predeterminada, la herramienta se extraerá en varios manifiestos de imagen presentes en el directorio de instalación de Visual Studio. Es el único que tiene los monikers públicamente la **Microsoft.VisualStudio.ImageCatalog** manifiesto. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (hacer **no** reemplazar este GUID en un manifiesto personalizado) tipo: KnownMonikers  
  
-   La herramienta intente cargar todos los manifiestos de imagen que se encuentra, por lo que puede tardar varios segundos para que aparecen en realidad la aplicación al iniciarse. También podría ser lento o no responde al cargar los manifiestos.  
  
## <a name="sample-output"></a>Resultados del ejemplo  
 Esta herramienta no genera ningún resultado.

