---
title: Visor de la biblioteca de imágenes (Image Library Viewer) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707747"
---
# <a name="image-library-viewer"></a>Visor de la biblioteca de imágenes
La herramienta Visor de biblioteca de imágenes de Visual Studio puede cargar y buscar manifiestos de imagen, lo que permite al usuario manipularlos de la misma manera que Visual Studio. El usuario puede modificar el fondo, los tamaños, los PPP, el alto contraste y otros ajustes. La herramienta también muestra información de carga para cada manifiesto de imagen y muestra información de origen para cada imagen en el manifiesto de imagen. Esta herramienta es útil para:

1. Diagnóstico de errores

2. Asegurarse de que los atributos se establecen correctamente en manifiestos de imagen personalizados

3. Búsqueda de imágenes en el catálogo de imágenes de Visual Studio para que una extensión de Visual Studio pueda usar imágenes que se ajusten al estilo de Visual Studio

   ![Imagen prominente del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-hero.png "Imagen prominente del visor de la biblioteca de imágenes")

   **Apodo de imagen**

   Un moniker de imagen (o moniker para abreviar) es un par GUID:ID que identifica de forma única un recurso de imagen o un recurso de lista de imágenes en la biblioteca de imágenes.

   **Archivos de manifiesto de imagen**

   Los archivos de manifiesto de imagen (.imagemanifest) son archivos XML que definen un conjunto de activos de imagen, los monikers que representan esos activos y la imagen o imágenes reales que representan cada recurso. Los manifiestos de imagen pueden definir imágenes independientes o listas de imágenes para la compatibilidad con la interfaz de usuario heredada. Además, hay atributos que se pueden establecer en el activo o en las imágenes individuales detrás de cada activo para cambiar cuándo y cómo se muestran esos activos.

   **Esquema de manifiesto de imagen**

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
|Importar|Importa los símbolos del archivo de manifiesto dado para su uso en el manifiesto actual.|
|Guid|El símbolo representa un GUID y debe coincidir con el formato GUID.|
|id|El símbolo representa un identificador y debe ser un entero no negativo.|
|String|El símbolo representa un valor de cadena arbitrario.|

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
|Sistema|La carpeta Windows-System32|
|WinDir|El valor de la variable de entorno %WinDir%|

 **Imagen**

 El \<elemento Image> define una imagen a la que puede hacer referencia un moniker. El GUID y el identificador tomados juntos forman el moniker de imagen. El moniker de la imagen debe ser único en toda la biblioteca de imágenes. Si más de una imagen tiene un moniker determinado, la primera encontrada al compilar la biblioteca es la que se conserva.

 Debe contener al menos una fuente. Aunque las fuentes de tamaño neutro darán los mejores resultados en una amplia gama de tamaños, no son necesarias. Si se solicita al servicio una imagen de \<un tamaño no definido en el elemento Image> y no hay ningún origen de tamaño neutro, el servicio elegirá el mejor origen específico del tamaño y lo escalará al tamaño solicitado.

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
|Identificador URI|[Requerido] URI que define desde dónde se puede cargar la imagen. Puede tener uno de los valores siguientes:<br /><br /> - Un [URI de paquete](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) con la autoridad application:///<br /><br /> - Una referencia de recursos de componentes absoluta<br /><br /> - Una ruta de acceso a un archivo que contiene un recurso nativo|
|Información previa|[Opcional] Indica qué tipo de fondo está destinado a utilizar se va a utilizar el origen.<br /><br /> Puede tener uno de los valores siguientes:<br /><br /> - *Luz*: La fuente se puede utilizar sobre un fondo claro.<br /><br /> - *Oscuro*: La fuente se puede utilizar sobre un fondo oscuro.<br /><br /> - *HighContrast*: La fuente se puede utilizar en cualquier fondo en el modo de contraste alto.<br /><br /> - *HighContrastLight*: La fuente se puede utilizar en un fondo claro en el modo de contraste alto.<br /><br /> -*HighContrastDark*: La fuente se puede utilizar en un fondo oscuro en el modo de contraste alto.<br /><br /> Si se omite el atributo **Background,** el origen se puede utilizar en cualquier fondo.<br /><br /> Si **Background** es *Light*, *Dark*, *HighContrastLight*o *HighContrastDark*, los colores del origen nunca se invierten. Si **Background** se omite o se establece en *HighContrast*, la inversión de los colores del origen se controla mediante el atributo **AllowColorInversion** de la imagen.|

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

## <a name="how-to-use-the-tool"></a>Cómo utilizar la herramienta
 **Validación de un manifiesto de imagen personalizado**

 Para crear un manifiesto personalizado, se recomienda usar la herramienta ManifestFromResources para generar automáticamente el manifiesto. Para validar el manifiesto personalizado, inicie el Visor de biblioteca de imágenes y seleccione > de archivos Establecer rutas... para abrir el cuadro de diálogo Directorios de búsqueda. La herramienta usará los directorios de búsqueda para cargar manifiestos de imagen, pero también los usará para buscar los archivos .dll que contienen las imágenes en un manifiesto, así que asegúrese de incluir los directorios de manifiesto y DLL en este cuadro de diálogo.

 ![Búsqueda del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-search.png "Búsqueda del visor de la biblioteca de imágenes")

 Haga clic en **Agregar...** para seleccionar nuevos directorios de búsqueda para buscar manifiestos y sus archivos DLL correspondientes. La herramienta recordará estos directorios de búsqueda, y se pueden activar o desactivar marcando o desmarcando un directorio.

 De forma predeterminada, la herramienta intentará encontrar el directorio de instalación de Visual Studio y agregar esos directorios a la lista de directorios de búsqueda. Puede agregar manualmente directorios que la herramienta no encuentre.

 Una vez cargados todos los manifiestos, la herramienta se puede utilizar para alternar los colores de **fondo,** **DPI,** **alto contraste**o escala de **grises** para las imágenes para que un usuario pueda inspeccionar visualmente los activos de imagen para comprobar que se representan correctamente para varios ajustes.

 ![Fondo del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-background.png "Fondo del visor de la biblioteca de imágenes")

 El color de fondo se puede establecer en Luz, Oscuro o un valor personalizado. Al seleccionar "Color personalizado" se abrirá un cuadro de diálogo de selección de color y se agregará ese color personalizado a la parte inferior del cuadro combinado de fondo para una fácil recuperación más adelante.

 ![Color personalizado para el visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-custom-color.png "Color personalizado para el visor de la biblioteca de imágenes")

 Al seleccionar un moniker de imagen, se muestra la información de cada imagen real detrás de ese moniker en el panel Detalles de imagen de la derecha. El panel también permite a los usuarios copiar un moniker por nombre o por valor GUID:ID sin formato.

 ![Detalles de la imagen del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-image-details.png "Detalles de la imagen del visor de la biblioteca de imágenes")

 La información que se muestra para cada origen de imagen incluye en qué tipo de fondo se muestra, si se puede crear temas o admite contraste alto, para qué tamaños es válido o si es de tamaño neutro y si la imagen procede de un ensamblado nativo.

 ![Tema del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-can-theme.png "Tema del visor de la biblioteca de imágenes")

 Al validar un manifiesto de imagen, se recomienda implementar el archivo DLL de manifiesto e imagen en sus ubicaciones del mundo real. Esto comprobará que las rutas de acceso relativas funcionan correctamente y que la biblioteca de imágenes puede encontrar y cargar el archivo DLL de manifiesto e imagen.

 **Búsqueda del catálogo de imágenes KnownMonikers**

 Para que coincida mejor con el estilo de Visual Studio, una extensión de Visual Studio puede usar imágenes en el catálogo de imágenes de Visual Studio en lugar de crear y usar su propio. Esto tiene la ventaja de no tener que mantener esas imágenes y garantiza que la imagen tendrá una imagen de respaldo de PPP alto, por lo que debe verse correcta en todos los valores de PPP que admite Visual Studio.

 El visor de la biblioteca de imágenes permite buscar un manifiesto para que un usuario pueda encontrar el moniker que representa un recurso de imagen y usar ese moniker en el código. Para buscar imágenes, introduzca el término de búsqueda deseado en el cuadro de búsqueda y pulse Intro. La barra de estado en la parte inferior mostrará cuántas coincidencias se encontraron del total de imágenes en todos los manifiestos.

 ![Filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro del visor de la biblioteca de imágenes")

 Al buscar monikers de imagen en manifiestos existentes, se recomienda buscar y usar solo los monikers del catálogo de imágenes de Visual Studio, otros monikers de acceso público intencionalmente o sus propios monikers personalizados. Si usa monikers no públicos, la interfaz de usuario personalizada podría romperse o cambiar sus imágenes de maneras inesperadas si o cuando esos monikers e imágenes no públicos se cambian o actualizan.

 Además, es posible buscar por GUID. Este tipo de búsqueda es útil para filtrar la lista a un único manifiesto o una sola subsección de un manifiesto si ese manifiesto contiene varios GUID.

 ![GUID del filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID del filtro del visor de la biblioteca de imágenes")

 Por último, la búsqueda por ID también es posible.

 ![Id. del filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-id.png "Id. del filtro del visor de la biblioteca de imágenes")

## <a name="notes"></a>Notas

- De forma predeterminada, la herramienta extraerá varios manifiestos de imagen presentes en el directorio de instalación de Visual Studio. El único que tiene monikers públicamente consumibles es el **Microsoft.VisualStudio.ImageCatalog** manifiesto. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 **(no** invalide este GUID en un manifiesto personalizado) Tipo: KnownMonikers

- La herramienta intenta al iniciar se cargan todos los manifiestos de imagen que encuentra, por lo que la aplicación puede tardar varios segundos en aparecer realmente. También puede ser lento o no responde al cargar los manifiestos.

## <a name="sample-output"></a>Salida de ejemplo
 Esta herramienta no genera ninguna salida.
