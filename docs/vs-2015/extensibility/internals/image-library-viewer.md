---
title: Visor de la biblioteca de imágenes | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6423c569fd1909539de9460ab3dcde0bcf753c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532033"
---
# <a name="image-library-viewer"></a>Visor de la biblioteca de imágenes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La herramienta Visor de la biblioteca de imágenes de Visual Studio puede cargar y buscar manifiestos de imagen, lo que permite al usuario manipularlos de la misma forma que lo haría Visual Studio. El usuario puede modificar el fondo, los tamaños, los PPP, el contraste alto y otros valores de configuración. La herramienta también muestra la información de carga de cada manifiesto de imagen y muestra información de origen de cada imagen en el manifiesto de imagen. Esta herramienta es útil para:  
  
1. Diagnóstico de errores  
  
2. Asegurarse de que los atributos se establecen correctamente en los manifiestos de imagen personalizados  
  
3. Buscar imágenes en el catálogo de imágenes de Visual Studio para que una extensión de Visual Studio pueda usar imágenes que se ajusten al estilo de Visual Studio  
  
   ![Imagen prominente del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-hero.png "Imagen prominente del visor de la biblioteca de imágenes")  
  
   **Moniker de imagen**  
  
   Un moniker de imagen (o moniker para abreviar) es un par GUID: ID que identifica de forma única un recurso de imagen o un recurso de lista de imágenes en la biblioteca de imágenes.  
  
   **Archivos de manifiesto de imagen**  
  
   Los archivos de manifiesto de imagen (. imagemanifest) son archivos XML que definen un conjunto de recursos de imagen, los monikers que representan esos recursos y la imagen o imágenes reales que representan cada activo. Los manifiestos de imagen pueden definir imágenes independientes o listas de imágenes para la compatibilidad con la interfaz de usuario heredada. Además, hay atributos que se pueden establecer en el recurso o en las imágenes individuales que hay detrás de cada recurso para cambiar Cuándo y cómo se muestran esos recursos.  
  
   **Esquema de manifiesto de imagen**  
  
   Un manifiesto de imagen completo tiene el siguiente aspecto:  
  
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
  
 Como ayuda para la lectura y el mantenimiento, el manifiesto de imagen puede usar símbolos para los valores de atributo. Los símbolos se definen de la siguiente manera:  
  
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
|Importar|Importa los símbolos del archivo de manifiesto especificado para su uso en el manifiesto actual.|  
|GUID|El símbolo representa un GUID y debe coincidir con el formato de GUID.|  
|ID|El símbolo representa un identificador y debe ser un entero no negativo.|  
|String|El símbolo representa un valor de cadena arbitrario.|  
  
 Los símbolos distinguen mayúsculas de minúsculas y se hace referencia a ellos mediante la sintaxis $ (nombre de símbolo):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Algunos símbolos están predefinidos para todos los manifiestos. Se pueden usar en el atributo URI del \<Source> \<Import> elemento o para hacer referencia a las rutas de acceso en el equipo local.  
  
|**Símbolo**|**Descripción**|  
|-|-|  
|CommonProgramFiles|El valor de la variable de entorno% CommonProgramFiles%|  
|LocalAppData|El valor de la variable de entorno% LocalAppData%|  
|ManifestFolder|La carpeta que contiene el archivo de manifiesto|  
|MyDocuments|La ruta de acceso completa de la carpeta Mis documentos del usuario actual|  
|ProgramFiles|El valor de la variable de entorno% ProgramFiles%|  
|Sistema|La carpeta Windows\System32|  
|DirWin|El valor de la variable de entorno% WinDir%|  
  
 **Imagen**  
  
 El \<Image> elemento define una imagen a la que se puede hacer referencia mediante un moniker. El GUID y el identificador se han tomado juntos en el moniker de la imagen. El moniker de la imagen debe ser único en toda la biblioteca de imágenes. Si hay más de una imagen con un moniker determinado, la primera que se encuentre al compilar la biblioteca es la que se conserva.  
  
 Debe contener al menos un origen. Aunque los orígenes de tamaño neutro proporcionarán los mejores resultados en una amplia gama de tamaños, no son necesarios. Si se solicita al servicio una imagen de un tamaño no definido en el \<Image> elemento y no hay ningún origen independiente del tamaño, el servicio elegirá el mejor origen específico del tamaño y lo escalará al tamaño solicitado.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
    
|**Attribute**|**Definición**|  
|-|-|
|GUID|Desee Parte del GUID del moniker de la imagen|  
|ID|Desee La parte de identificador del moniker de imagen|  
|AllowColorInversion|[Opcional, valor predeterminado True] Indica si la imagen puede tener sus colores inversos mediante programación cuando se usa en un fondo oscuro.|  
  
 **Origen**  
  
 El \<Source> elemento define un único recurso de origen de imagen (XAML y PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|**Attribute**|**Definición**|  
|-|-|  
|Identificador URI|Desee URI que define dónde se puede cargar la imagen. Puede tener uno de los valores siguientes:<br /><br /> -Un [pack uri](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) mediante la autoridad Application:///<br /><br /> -Una referencia de recurso de componente absoluta<br /><br /> -Una ruta de acceso a un archivo que contiene un recurso nativo|  
|Fondo|Opta Indica qué tipo de fondo está previsto usar el origen.<br /><br /> Puede tener uno de los valores siguientes:<br /><br /> - *Light*: el origen se puede usar en un fondo claro.<br /><br /> - *Dark*: el origen se puede usar en un fondo oscuro.<br /><br /> - *HighContrast*: el origen puede usarse en cualquier fondo del modo contraste alto.<br /><br /> - *HighContrastLight*: el origen se puede usar en un fondo claro en modo de contraste alto.<br /><br /> -*HighContrastDark*: el origen se puede usar en un fondo oscuro en modo de contraste alto.<br /><br /> Si se omite el atributo **background** , el origen puede usarse en cualquier fondo.<br /><br /> Si **background** es *Light*, *Dark*, *HighContrastLight*o *HighContrastDark*, los colores del origen nunca se invierten. Si se omite **background** o se establece en *HighContrast*, el atributo **AllowColorInversion** de la imagen controla la inversión de los colores del origen.|  
  
 Un \<Source> elemento puede tener exactamente uno de los siguientes subelementos opcionales:  
  
|**Element**|**Atributos (todos obligatorios)**|**Definición**|  
|-|-|-|  
|\<Size>|Valor|El origen se usará para las imágenes del tamaño especificado (en unidades de dispositivo). La imagen será cuadrada.|  
|\<SizeRange>|MinSize, MaxSize|El origen se usará para las imágenes de MinSize a MaxSize (en unidades de dispositivo) de un solo uso. La imagen será cuadrada.|  
|\<Dimensions>|Ancho, alto|El origen se usará para las imágenes con el ancho y alto especificados (en unidades de dispositivo).|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|El origen se usará para las imágenes desde el ancho o el alto mínimo hasta el ancho/alto máximo (en unidades de dispositivo), ambos inclusive.|  
  
 Un \<Source> elemento también puede tener un \<NativeResource> subelemento opcional, que define un \<Source> que se carga desde un ensamblado nativo en lugar de un ensamblado administrado.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|**Attribute**|**Definición**|  
|-|-|  
|Tipo|Desee El tipo del recurso nativo, ya sea XAML o PNG|  
|ID|Desee La parte del identificador entero del recurso nativo|  
  
 **ImageList**  
  
 El \<ImageList> elemento define una colección de imágenes que se pueden devolver en una sola banda. La franja se basa en la demanda, según sea necesario.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|**Attribute**|**Definición**|  
|-|-|  
|GUID|Desee Parte del GUID del moniker de la imagen|  
|ID|Desee La parte de identificador del moniker de imagen|  
|Externo|[Opcional, valor predeterminado False] Indica si el moniker de imagen hace referencia a una imagen del manifiesto actual.|  
  
 No es necesario que el moniker de la imagen contenida haga referencia a una imagen definida en el manifiesto actual. Si no se encuentra la imagen contenida en la biblioteca de imágenes, se usará una imagen de marcador de posición en blanco en su lugar.  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 **Validar un manifiesto de imagen personalizado**  
  
 Para crear un manifiesto personalizado, se recomienda usar la herramienta ManifestFromResources para generar automáticamente el manifiesto. Para validar el manifiesto personalizado, inicie el visor de la biblioteca de imágenes y seleccione Archivo > establecer rutas de acceso... para abrir el cuadro de diálogo Buscar directorios. La herramienta utilizará los directorios de búsqueda para cargar los manifiestos de imagen, pero también los usará para buscar los archivos. dll que contienen las imágenes en un manifiesto, por lo que debe asegurarse de incluir los directorios de manifiesto y DLL en este cuadro de diálogo.  
  
 ![Búsqueda del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-search.png "Búsqueda del visor de la biblioteca de imágenes")  
  
 Haga clic en **Agregar...** para seleccionar nuevos directorios de búsqueda para buscar manifiestos y sus archivos dll correspondientes. La herramienta recordará estos directorios de búsqueda y se pueden activar o desactivar mediante la comprobación o desactivación de un directorio.  
  
 De forma predeterminada, la herramienta intentará buscar el directorio de instalación de Visual Studio y agregar esos directorios a la lista de directorios de búsqueda. Puede Agregar manualmente los directorios que la herramienta no encuentra.  
  
 Una vez que se cargan todos los manifiestos, la herramienta se puede usar para alternar los colores de **fondo** , el valor de **PPP**, el **contraste alto**o **grayscaling** para las imágenes, de modo que un usuario pueda inspeccionar visualmente los recursos de imagen para comprobar que se representan correctamente para varias configuraciones.  
  
 ![Fondo del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-background.png "Fondo del visor de la biblioteca de imágenes")  
  
 El color de fondo se puede establecer en claro, oscuro o en un valor personalizado. Al seleccionar "color personalizado", se abrirá un cuadro de diálogo de selección de color y se agregará ese color personalizado a la parte inferior del cuadro combinado de fondo para facilitar la recuperación posterior.  
  
 ![Color personalizado para el visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-custom-color.png "Color personalizado para el visor de la biblioteca de imágenes")  
  
 Al seleccionar un moniker de imagen, se muestra la información de cada imagen real detrás de ese moniker en el panel de detalles de la imagen de la derecha. El panel también permite a los usuarios copiar un moniker por nombre o por GUID sin formato: ID.  
  
 ![Detalles de la imagen del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-image-details.png "Detalles de la imagen del visor de la biblioteca de imágenes")  
  
 La información mostrada para cada origen de imagen incluye el tipo de fondo en el que se va a mostrar, si puede ser compatible o descontraste alto, en qué tamaños es válido o si es independiente del tamaño, y si la imagen procede de un ensamblado nativo.  
  
 ![Tema del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-can-theme.png "Tema del visor de la biblioteca de imágenes")  
  
 Al validar un manifiesto de imagen, se recomienda implementar el manifiesto y el archivo DLL de imagen en sus ubicaciones reales. Esto comprobará que las rutas de acceso relativas funcionan correctamente y que la biblioteca de imágenes puede buscar y cargar el archivo DLL de manifiesto y de imagen.  
  
 **Buscando catálogo de imágenes KnownMonikers**  
  
 Para hacer coincidir mejor el estilo de Visual Studio, una extensión de Visual Studio puede usar imágenes en el catálogo de imágenes de Visual Studio en lugar de crear y usar el suyo propio. Esto tiene la ventaja de no tener que mantener esas imágenes y garantiza que la imagen tendrá una imagen de copia de seguridad de PPP alta, por lo que debe ser correcta en todos los valores de PPP que admite Visual Studio.  
  
 El visor de la biblioteca de imágenes permite buscar un manifiesto para que un usuario pueda encontrar el moniker que representa un recurso de imagen y utilizar ese moniker en el código. Para buscar imágenes, escriba el término de búsqueda deseado en el cuadro de búsqueda y presione Entrar. En la barra de estado de la parte inferior se mostrará el número de coincidencias encontradas en el total de imágenes de todos los manifiestos.  
  
 ![Filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter.png "Filtro del visor de la biblioteca de imágenes")  
  
 Al buscar monikers de imagen en manifiestos existentes, se recomienda buscar y usar solo los monikers del catálogo de imágenes de Visual Studio, otros monikers accesibles de forma intencionada o sus propios monikers personalizados. Si usa monikers no públicos, es posible que la interfaz de usuario personalizada se interrumpa o que sus imágenes cambien de maneras inesperadas si se cambian o se actualizan los monikers y las imágenes no públicos.  
  
 Además, es posible realizar búsquedas por GUID. Este tipo de búsqueda es útil para filtrar la lista por un único manifiesto o una única subsección de un manifiesto si dicho manifiesto contiene varios GUID.  
  
 ![GUID del filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID del filtro del visor de la biblioteca de imágenes")  
  
 Por último, también es posible buscar por identificador.  
  
 ![Id. del filtro del visor de la biblioteca de imágenes](../../extensibility/internals/media/image-library-viewer-filter-id.png "Id. del filtro del visor de la biblioteca de imágenes")  
  
## <a name="notes"></a>Notas  
  
- De forma predeterminada, la herramienta incorporará varios manifiestos de imagen presentes en el directorio de instalación de Visual Studio. El único que tiene monikers que se va a consumir públicamente es el manifiesto **Microsoft. VisualStudio. ImageCatalog** . GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 **(no invalide** este GUID en un manifiesto personalizado) tipo: KnownMonikers  
  
- La herramienta intenta iniciarse para cargar todos los manifiestos de imagen que encuentra, por lo que la aplicación puede tardar varios segundos en aparecer realmente. También puede ser lento o no responde mientras se cargan los manifiestos.  
  
## <a name="sample-output"></a>Salida de ejemplo  
 Esta herramienta no genera ningún resultado.
