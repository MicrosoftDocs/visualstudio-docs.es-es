---
title: Manifiesto desde recursos | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f1affa200527e770dc87c51c4bb6f7b8a088fcc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959382"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
El manifiesto de la herramienta de recursos es una aplicación de consola que toma una lista de recursos de imagen (.png o .xaml archivos) y genera un archivo .imagemanifest que permite que esas imágenes para su uso con el servicio de imágenes de Visual Studio. Además, esta herramienta puede usarse para agregar imágenes a un .imagemanifest existente. Esta herramienta es útil para agregar compatibilidad con valores altos de PPP y temas para las imágenes a una extensión de Visual Studio. El archivo generado .imagemanifest debe incluido en e implementarse como parte de una extensión de Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 **Sintaxis**  
  
 ManifestFromResources Resources:\<Dir1 >;\< Img1 > /assembly:\<AssemblyName > \<Args opcional >  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|Resources|Una lista delimitada por punto y coma de las imágenes o directorios. Esta lista debería contener siempre la lista completa de las imágenes que se incluirán en el manifiesto. Si solo se proporciona una lista parcial, se perderán las entradas no incluidas.<br /><br /> Si un archivo de recursos determinado es una tira de imagen, la herramienta dividirla en imágenes independientes antes de agregar cada subimagen en el manifiesto.<br /><br /> Si la imagen es un archivo .png, se recomienda que formatear el nombre de esta manera para que la herramienta puede rellenar los atributos de la imagen adecuados: \<Nombre >. \<Ancho >. \<Alto >. png.|Obligatorio|  
|/Assembly|El nombre del ensamblado administrado (sin incluir la extensión) o la ruta de acceso en tiempo de ejecución del ensamblado nativo que hospeda los recursos (con respecto a la ubicación de tiempo de ejecución del manifiesto).|Obligatorio|  
|/ manifest|El nombre que asigne al archivo .imagemanifest generado. Esto también puede incluir una ruta de acceso absoluta o relativa para crear el archivo en una ubicación diferente. El nombre predeterminado coincide con el nombre del ensamblado.<br /><br /> Predeterminado: \<Directorio actual >\\< ensamblado\>.imagemanifest|Optional|  
|/guidName|El nombre para el símbolo GUID para todas las imágenes en el manifiesto generado.<br /><br /> Predeterminado: AssetsGuid|Optional|  
|/rootPath|La ruta de acceso raíz que debe eliminarse antes de crear los URI de recurso administrado. (Esta marca es ayudar con los casos donde la herramienta obtiene la ruta de acceso relativa de URI incorrecto, por lo que los recursos no pueda cargarse).<br /><br /> Predeterminado: \<Directorio actual >|Optional|  
|/recursive|Al establecer esta marca indica a la herramienta de forma recursiva todos los directorios de búsqueda en el argumento Resources. Si se omite esta marca dará como resultado una búsqueda top-multinivel sólo de directorios.|Optional|  
|/isNative|Establezca esta marca cuando el argumento de ensamblado es una ruta de acceso para un ensamblado nativo. Esta marca se omite cuando el argumento de ensamblado es el nombre de un ensamblado administrado. (Consulte la sección Notas para obtener más información acerca de esta marca).|Optional|  
|/newGuids|Al establecer esta marca indica a la herramienta para crear un nuevo valor para el símbolo GUID de las imágenes en lugar de combinar el uno del manifiesto existente.|Optional|  
|/newIds|Al establecer esta marca indica a la herramienta para crear nuevos valores de símbolo de identificador para cada imagen en lugar de combinar los valores del manifiesto existente.|Optional|  
|/noLogo|Al establecer esta marca detiene la información de producto y copyright de impresión.|Optional|  
|/?|Imprimir información de ayuda.|Optional|  
|/help|Imprimir información de ayuda.|Optional|  
  
 **Ejemplos**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Notas  
  
-   La herramienta solo admite archivos .png y XAML. Se omitirá cualquier otro tipo de imagen o un archivo. Se genera una advertencia para todos los tipos no compatibles que encuentra durante el análisis de los recursos. Si no se admite las imágenes se encuentran cuando finalice la herramienta de análisis de los recursos, se generará un error  
  
-   Siguiendo el formato sugerido para imágenes PNG, la herramienta establecerá el valor de tamaño y la dimensión para el .png al tamaño especificado de formato, incluso si es diferente del tamaño real de la imagen.  
  
-   Se puede omitir el formato de ancho y alto para las imágenes PNG, pero la herramienta leerá real ancho/alto de la imagen y úselos para el valor de tamaño y la dimensión de la imagen.  
  
-   Ejecutar esta herramienta en la franja de imágenes mismo varias veces para el mismo .imagemanifest producirá las entradas duplicadas del manifiesto, porque la herramienta intenta dividir la franja de imágenes en imágenes independientes y agregarlos al manifiesto existente.  
  
-   Combinar (omitiendo /newGuids o /newIds) solo debe realizarse para los manifiestos generados por la herramienta. Los manifiestos que se hayan adaptado o generados por otros medios no se pueden combinar correctamente.  
  
-   Los manifiestos que se generan para los ensamblados nativos puede que tenga que editar manualmente después de la generación para que los símbolos de Id. coincida con los identificadores de archivo .rc del ensamblado nativo de recursos.  
  
## <a name="sample-output"></a>Resultados del ejemplo  
 **Manifiesto de imagen simple**  
  
 Un manifiesto de imagen será similar a este archivo .xml:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImage" Value="0" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">  
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />  
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```  
  
 **Manifiesto de imagen para una banda de imagen**  
  
 Un manifiesto de imagen para una banda de imagen será similar a este archivo .xml:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImageStrip_0" Value="1" />  
    <ID Name="MyImageStrip_1" Value="2" />  
    <ID Name="MyImageStrip" Value="3" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">  
      <Source Uri="$(Resources)/MyImageStrip_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">  
      <Source Uri="$(Resources)/MyImageStrip_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists>  
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />  
    </ImageList>  
  </ImageLists>  
</ImageManifest>  
```  
  
 **Manifiesto de imagen para los recursos de imagen de ensamblado nativo**  
  
 Un manifiesto de imagen de las imágenes nativas será similar a este archivo .xml:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15198 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />  
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />  
    <ID Name="MyImage1" Value="0" />  
    <ID Name="MyImage2" Value="1" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage1)" Type="PNG" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage2)" Type="PNG" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```