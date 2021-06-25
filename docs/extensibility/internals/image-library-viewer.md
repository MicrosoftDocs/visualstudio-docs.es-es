---
title: Visor de biblioteca de imágenes | Microsoft Docs
description: Obtenga información sobre la Visual Studio Visor de biblioteca de imágenes que carga y busca manifiestos de imagen, lo que le permite ver y manipular atributos de imagen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02e7c5d5ed45b7a6c19c248e949e667ec0a1bdc0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898715"
---
# <a name="image-library-viewer"></a>Visor de la biblioteca de imágenes
La Visual Studio Visor de biblioteca de imágenes puede cargar y buscar manifiestos de imagen, lo que permite al usuario manipularlos de la misma manera Visual Studio hacerlo. El usuario puede modificar el fondo, los tamaños, los VALORES DE PPP, el contraste alto y otras configuraciones. La herramienta también muestra información de carga para cada manifiesto de imagen y muestra información de origen para cada imagen del manifiesto de imagen. Esta herramienta es útil para:

1. Diagnóstico de errores

2. Asegurarse de que los atributos se establecen correctamente en manifiestos de imagen personalizados

3. Buscar imágenes en el catálogo Visual Studio imágenes para que una extensión de Visual Studio pueda usar imágenes que se ajusten al estilo de Visual Studio

   ![Imagen prominente del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-hero.png "Imagen prominente del visor de la biblioteca de imágenes")

   **Moniker de imagen**

   Un moniker de imagen (o moniker en resumen) es un par GUID:ID que identifica de forma única un recurso de imagen o un recurso de lista de imágenes en la biblioteca de imágenes.

   **Archivos de manifiesto de imagen**

   Los archivos de manifiesto de imagen (.imagemanifest) son archivos XML que definen un conjunto de recursos de imagen, los monikers que representan esos recursos y la imagen o imágenes reales que representan cada recurso. Los manifiestos de imagen pueden definir imágenes independientes o listas de imágenes para la compatibilidad con la interfaz de usuario heredada. Además, hay atributos que se pueden establecer en el recurso o en las imágenes individuales detrás de cada recurso para cambiar cuándo y cómo se muestran esos recursos.

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

 Como ayuda de legibilidad y mantenimiento, el manifiesto de imagen puede usar símbolos para los valores de atributo. Los símbolos se definen de esta forma:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Subelemento**|**Definición**|
|-|-|
|Importar|Importa los símbolos del archivo de manifiesto dado para su uso en el manifiesto actual.|
|Guid|El símbolo representa un GUID y debe coincidir con el formato guid.|
|ID|El símbolo representa un identificador y debe ser un entero no negativo.|
|String|El símbolo representa un valor de cadena arbitrario.|

 Los símbolos distinguen mayúsculas de minúsculas y se hace referencia a ellos mediante la sintaxis $(symbol-name):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Algunos símbolos están predefinidos para todos los manifiestos. Se pueden usar en el atributo URI del elemento o para \<Source> \<Import> hacer referencia a rutas de acceso en el equipo local.

|**Símbolo**|**Descripción**|
|-|-|
|CommonProgramFiles|Valor de la variable de entorno %CommonProgramFiles%|
|LocalAppData|Valor de la variable de entorno %LocalAppData%|
|ManifestFolder|Carpeta que contiene el archivo de manifiesto|
|MyDocuments|Ruta de acceso completa de la Mis documentos del usuario actual|
|ProgramFiles|Valor de la variable de entorno %ProgramFiles%|
|Sistema|La carpeta Windows\System32|
|WinDir|Valor de la variable de entorno %WinDir%|

 **Image**

 El \<Image> elemento define una imagen a la que se puede hacer referencia mediante un moniker. El GUID y el identificador tomados juntos forman el moniker de imagen. El moniker de la imagen debe ser único en toda la biblioteca de imágenes. Si más de una imagen tiene un moniker determinado, el primero que se encuentra al compilar la biblioteca es el que se conserva.

 Debe contener al menos un origen. Aunque los orígenes de tamaño neutro darán los mejores resultados en una amplia gama de tamaños, no son necesarios. Si se solicita al servicio una imagen de un tamaño no definido en el elemento y no hay ningún origen neutro de tamaño, el servicio elegirá el mejor origen específico del tamaño y lo escalará al tamaño \<Image> solicitado.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Atributo**|**Definición**|
|-|-|
|Guid|[Obligatorio] La parte GUID del moniker de imagen|
|ID|[Obligatorio] Parte del identificador del moniker de imagen|
|AllowColorInversion|[Opcional, valor predeterminado true] Indica si la imagen puede tener sus colores invertidos mediante programación cuando se usa en un fondo oscuro.|

 **Origen**

 El \<Source> elemento define un único recurso de origen de imagen (XAML y PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Atributo**|**Definición**|
|-|-|
|Identificador URI|[Obligatorio] URI que define desde dónde se puede cargar la imagen. Puede tener uno de los valores siguientes:<br /><br /> - Un [URI de paquete](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) mediante la application:/// de paquetes<br /><br /> - Referencia de recursos de componentes absolutos<br /><br /> - Ruta de acceso a un archivo que contiene un recurso nativo|
|Información previa|[Opcional] Indica qué tipo de fondo está pensado para usar el origen.<br /><br /> Puede tener uno de los valores siguientes:<br /><br /> - *Light:* el origen se puede usar en un fondo claro.<br /><br /> - *Oscuro:* el origen se puede usar en un fondo oscuro.<br /><br /> - *HighContrast:* el origen se puede usar en cualquier fondo en contraste alto modo.<br /><br /> - *HighContrastLight:* el origen se puede usar en un fondo claro en contraste alto modo.<br /><br /> -*HighContrastDark:* el origen se puede usar en un fondo oscuro en contraste alto modo.<br /><br /> Si se **omite** el atributo Background, el origen se puede usar en cualquier fondo.<br /><br /> Si **Background** es *Light*, *Dark*, *HighContrastLight* o *HighContrastDark*, los colores del origen nunca se invierten. Si **Background** se omite o se establece en *HighContrast*, la inversión de los colores del origen se controla mediante el atributo **AllowColorInversion** de la imagen.|

 Un \<Source> elemento puede tener exactamente uno de los siguientes subelementos opcionales:

|**Element**|**Atributos (todos obligatorios)**|**Definición**|
|-|-|-|
|\<Size>|Valor|El origen se usará para las imágenes del tamaño especificado (en unidades de dispositivo). La imagen será cuadrada.|
|\<SizeRange>|MinSize, MaxSize|El origen se usará para las imágenes de MinSize a MaxSize (en unidades de dispositivo) de forma inclusiva. La imagen será cuadrada.|
|\<Dimensions>|Ancho, alto|El origen se usará para las imágenes del ancho y alto dados (en unidades de dispositivo).|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|El origen se usará para las imágenes desde el ancho y alto mínimos hasta el ancho o alto máximos (en unidades de dispositivo) de forma inclusiva.|

 Un \<Source> elemento también puede tener un subelemento opcional, que define un que se carga desde un ensamblado nativo en lugar \<NativeResource> de un ensamblado \<Source> administrado.

```xml
<NativeResource Type="type" ID="int" />
```

|**Atributo**|**Definición**|
|-|-|
|Tipo|[Obligatorio] El tipo del recurso nativo, ya sea XAML o PNG|
|ID|[Obligatorio] Parte del identificador entero del recurso nativo|

 **ImageList**

 El \<ImageList> elemento define una colección de imágenes que se pueden devolver en una sola franja. La franja se basa a petición, según sea necesario.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Atributo**|**Definición**|
|-|-|
|Guid|[Obligatorio] La parte GUID del moniker de imagen|
|ID|[Obligatorio] Parte del identificador del moniker de imagen|
|Externo|[Opcional, valor predeterminado false] Indica si el moniker de imagen hace referencia a una imagen en el manifiesto actual.|

 El moniker de la imagen independiente no tiene que hacer referencia a una imagen definida en el manifiesto actual. Si la imagen contenida no se encuentra en la biblioteca de imágenes, se usará una imagen de marcador de posición en blanco en su lugar.

## <a name="how-to-use-the-tool"></a>Uso de la herramienta
 **Validación de un manifiesto de imagen personalizado**

 Para crear un manifiesto personalizado, se recomienda usar la herramienta ManifestFromResources para generar automáticamente el manifiesto. Para validar el manifiesto personalizado, inicie el Visor de biblioteca de imágenes y seleccione Archivo > establecer rutas de acceso... para abrir el cuadro de diálogo Directorios de búsqueda. La herramienta usará los directorios de búsqueda para cargar manifiestos de imagen, pero también los usará para buscar los archivos .dll que contienen las imágenes de un manifiesto, así que asegúrese de incluir los directorios de manifiesto y DLL en este cuadro de diálogo.

 ![Búsqueda del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-search.png "Búsqueda del visor de la biblioteca de imágenes")

 Haga **clic en Agregar...** para seleccionar nuevos directorios de búsqueda para buscar manifiestos y sus archivos DLL correspondientes. La herramienta recordará estos directorios de búsqueda y se pueden activar o desactivar si se comprueba o desactiva un directorio.

 De forma predeterminada, la herramienta intentará encontrar el directorio Visual Studio instalar y agregar esos directorios a la lista de directorios de búsqueda. Puede agregar manualmente directorios que la herramienta no encuentre.

 Una vez **cargados** todos los manifiestos,  la herramienta se puede usar para alternar los colores de fondo, **PPP,** contraste alto o escala de grises de las imágenes para que un usuario pueda inspeccionar visualmente los recursos de imagen para comprobar que se representan correctamente para diversas configuraciones.

 ![Fondo del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-background.png "Fondo del visor de la biblioteca de imágenes")

 El color de fondo se puede establecer en Claro, Oscuro o un valor personalizado. Al seleccionar "Color personalizado", se abrirá un cuadro de diálogo de selección de color y se agregará ese color personalizado a la parte inferior del cuadro combinado de fondo para facilitar la recuperación más adelante.

 ![Color personalizado para el visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-custom-color.png "Color personalizado para el visor de la biblioteca de imágenes")

 Al seleccionar un moniker de imagen, se muestra la información de cada imagen real detrás de ese moniker en el panel Detalles de la imagen de la derecha. El panel también permite a los usuarios copiar un moniker por nombre o por valor GUID:ID sin formato.

 ![Detalles de la imagen del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-image-details.png "Detalles de la imagen del visor de la biblioteca de imágenes")

 La información que se muestra para cada origen de imagen incluye el tipo de fondo en el que se va a mostrar, si se puede mostrar como un elemento de tipo themed o admite contraste alto, para qué tamaños es válido o si el tamaño es neutro y si la imagen procede de un ensamblado nativo.

 ![Tema del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-can-theme.png "Tema del visor de la biblioteca de imágenes")

 Al validar un manifiesto de imagen, se recomienda implementar el manifiesto y el archivo DLL de imagen en sus ubicaciones reales. Esto comprobará que las rutas de acceso relativas funcionan correctamente y que la biblioteca de imágenes puede encontrar y cargar el manifiesto y el archivo DLL de imagen.

 **Búsqueda de knownMonikers del catálogo de imágenes**

 Para que coincida mejor Visual Studio estilo, una extensión Visual Studio puede usar imágenes en el catálogo de imágenes de Visual Studio en lugar de crear y usar las suyas propias. Esto tiene la ventaja de no tener que mantener esas imágenes y garantiza que la imagen tendrá una imagen de respaldo de valores altos de PPP, por lo que debería tener un aspecto correcto en todas las configuraciones de PPP que Visual Studio admite.

 El visor de biblioteca de imágenes permite buscar un manifiesto para que un usuario pueda encontrar el moniker que representa un recurso de imagen y usar ese moniker en el código. Para buscar imágenes, escriba el término de búsqueda deseado en el cuadro de búsqueda y presione Entrar. La barra de estado de la parte inferior mostrará cuántas coincidencias se encontraron del total de imágenes en todos los manifiestos.

 ![Filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro del visor de la biblioteca de imágenes")

 Al buscar monikers de imagen en manifiestos existentes, se recomienda buscar y usar solo los monikers de Visual Studio Image Catalog, otros monikers accesibles intencionadamente o sus propios monikers personalizados. Si usa monikers no públicos, la interfaz de usuario personalizada podría estar rota o cambiar sus imágenes de maneras inesperadas si esos monikers e imágenes no públicos se cambian o actualizan.

 Además, es posible buscar por GUID. Este tipo de búsqueda es útil para filtrar la lista a un único manifiesto o a una sola subsección de un manifiesto si ese manifiesto contiene varios GUID.

 ![GUID del filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID del filtro del visor de la biblioteca de imágenes")

 Por último, también es posible buscar por identificador.

 ![Id. del filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-id.png "Id. del filtro del visor de la biblioteca de imágenes")

## <a name="notes"></a>Notas

- De forma predeterminada, la herramienta extraerá varios manifiestos de imagen presentes en el Visual Studio instalar. El único que tiene monikers que se pueden consumir públicamente es el **manifiesto Microsoft.VisualStudio.ImageCatalog.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369  (no invalidar este GUID en un manifiesto personalizado) Tipo: KnownMonikers

- La herramienta intenta al iniciarse cargar todos los manifiestos de imagen que encuentra, por lo que la aplicación puede tardar varios segundos en aparecer realmente. También puede ser lento o no responde al cargar los manifiestos.

## <a name="sample-output"></a>Salida de ejemplo
 Esta herramienta no genera ninguna salida.
