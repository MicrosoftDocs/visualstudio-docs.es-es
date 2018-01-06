---
title: Manifiestos de recursos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bbf234d18c48ed501987f160bd2b98ec9f768b6e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="manifest-from-resources"></a>Manifiestos de recursos
El manifiesto de la herramienta de recursos es una aplicación de consola que toma una lista de recursos de imagen (archivos .png o .xaml) y genera un archivo .imagemanifest que permite que esas imágenes para su uso con el servicio de imágenes de Visual Studio. Además, esta herramienta puede usarse para agregar imágenes a un .imagemanifest existente. Esta herramienta es útil para agregar compatibilidad con valores altos de PPP y temas para imágenes a una extensión de Visual Studio. El archivo .imagemanifest generado debe estar incluido en y se ha implementado como parte de una extensión de Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 **Sintaxis**  
  
 Resources ManifestFromResources:\<Dir1 >;\< Img1 > /assembly:\<AssemblyName > \<Args opcional >  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|Resources|Una lista delimitada por punto y coma de imágenes o directorios. Esta lista debería contener siempre la lista completa de las imágenes que se incluirán en el manifiesto. Si solo se proporciona una lista parcial, se perderán las entradas no incluidas.<br /><br /> Si un archivo de recursos determinado es una franja de imagen, la herramienta dividirá lo imágenes independientes antes de agregar cada subimagen al manifiesto.<br /><br /> Si la imagen es un archivo .png, le recomendamos que dar formato al nombre similar al siguiente para que la herramienta puede rellenar los atributos derecho de la imagen: \<nombre >.\< Ancho >. \<Alto >. png.|Obligatorio|  
|/Assembly|El nombre del ensamblado administrado (sin incluir la extensión) o la ruta de acceso en tiempo de ejecución del ensamblado nativo que hospeda los recursos (con respecto a la ubicación de tiempo de ejecución del manifiesto).|Obligatorio|  
|/ manifest|El nombre que asigne al archivo .imagemanifest generado. Esto también puede incluir una ruta de acceso absoluta o relativa para crear el archivo en una ubicación diferente. El nombre predeterminado coincide con el nombre del ensamblado.<br /><br /> Valor predeterminado: \<directorio actual >\\< ensamblado\>.imagemanifest|Optional|  
|/guidName|El nombre que asigne al símbolo GUID para todas las imágenes en el manifiesto generado.<br /><br /> Valor predeterminado: AssetsGuid|Optional|  
|/rootPath|La ruta de acceso raíz que debe eliminarse antes de crear los URI de recurso administrado. (Esta marca es ayudar a los casos donde la herramienta obtiene incorrecto, por lo que los recursos que no se pudo cargar la ruta de acceso URI relativa).<br /><br /> Valor predeterminado: \<directorio actual >|Optional|  
|/recursive|Si establece esta marca indica a la herramienta de forma recursiva los directorios de búsqueda en el argumento Resources. Si se omite esta marca se producirá una búsqueda top-nivel solo de directorios.|Optional|  
|/isNative|Establezca esta marca cuando el argumento de ensamblado es una ruta de acceso para un ensamblado nativo. Omitir esta marca cuando el argumento de ensamblado es el nombre de un ensamblado administrado. (Vea la sección Notas para obtener información adicional acerca de esta marca).|Optional|  
|/newGuids|Si establece esta marca indica a la herramienta para crear un nuevo valor para el símbolo GUID de las imágenes en lugar de combinar el empezando por el manifiesto existente.|Optional|  
|/newIds|Si establece esta marca indica a la herramienta para crear nuevos valores de símbolo de Id. de cada imagen en lugar de combinar los valores del manifiesto del existente.|Optional|  
|/noLogo|Al establecer este indicador detiene la información de producto y de copyright de impresión.|Optional|  
|/?|Imprimir la información de ayuda.|Optional|  
|/help|Imprimir la información de ayuda.|Optional|  
  
 **Ejemplos**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Notas  
  
-   La herramienta solo admite archivos .png y XAML. Se omitirá cualquier otro tipo de imagen o un archivo. Se genera una advertencia para todos los tipos no compatibles que se encuentra durante el análisis de los recursos. Si no se admite imágenes se encuentran cuando finalice la herramienta de análisis de los recursos, se generará un error  
  
-   Siguiendo el formato sugerido para las imágenes PNG, la herramienta establecerá el valor de tamaño y dimensión para el .png al tamaño especificado por el formato, incluso si difiere del tamaño real de la imagen.  
  
-   Se puede omitir el formato de ancho/alto para imágenes PNG, pero la herramienta leerá real ancho/alto de la imagen y úselos para el valor de tamaño y dimensión de la imagen.  
  
-   Cuando se ejecute esta herramienta en la misma franja de imagen varias veces para el mismo .imagemanifest generará entradas duplicadas de manifiesto, porque la herramienta intenta dividir la franja de imágenes en imágenes independientes y agregarlas al manifiesto existente.  
  
-   Solo se debe realizar la combinación (omitiendo los /newGuids o /newIds) para los manifiestos generados por la herramienta. Manifiestos que se han personalizado o generados por otros medios no se pueden combinar correctamente.  
  
-   Manifiestos que se generan para ensamblados nativos podrían sea necesario editar manualmente después de la generación para hacer que los símbolos de identificador coincide con el recurso de identificadores de archivo .rc del ensamblado nativo.  
  
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
  
 **Manifiesto de imagen en una banda de imagen**  
  
 Un manifiesto de imagen en una banda de imagen será similar a este archivo .xml:  
  
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