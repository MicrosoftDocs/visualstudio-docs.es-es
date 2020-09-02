---
title: Manifest from Resources | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4827402b63eadf517f031b04b7c7cf2fe8a4f56b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537103"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La herramienta Manifest from Resources es una aplicación de consola que toma una lista de recursos de imagen (archivos. png o. xaml) y genera un archivo. imagemanifest que permite usar esas imágenes con el servicio de imágenes de Visual Studio. Además, esta herramienta se puede usar para agregar imágenes a un imagemanifest existente. Esta herramienta es útil para agregar la compatibilidad con las imágenes y los elementos de gran nivel en una extensión de Visual Studio. El archivo. imagemanifest generado debe incluirse en e implementarse como parte de una extensión de Visual Studio (. vsix).  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 **Sintaxis**  
  
 ManifestFromResources/Resources: \<Dir1> ; \<Img1> /Assembly: \<AssemblyName>\<Optional Args>  
  
 **Argumentos**  
  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|-|-|-|  
|/resources|Una lista delimitada por signos de punto y coma de imágenes o directorios. Esta lista siempre debe contener la lista completa de imágenes que se incluirán en el manifiesto. Si solo se proporciona una lista parcial, se perderán las entradas que no se incluyan.<br /><br /> Si un archivo de recursos determinado es una franja de imágenes, la herramienta lo dividirá en imágenes independientes antes de agregar cada subimagen al manifiesto.<br /><br /> Si la imagen es un archivo. png, se recomienda dar formato al nombre de este modo para que la herramienta pueda rellenar los atributos adecuados para la imagen: \<Name> . \<Width> . \<Height> . dicho.|Obligatorio|  
|/Assembly|Nombre del ensamblado administrado (sin incluir la extensión) o la ruta de acceso en tiempo de ejecución del ensamblado nativo que hospeda los recursos (en relación con la ubicación en tiempo de ejecución del manifiesto).|Obligatorio|  
|/manifest|Nombre que se va a asignar al archivo. imagemanifest generado. También puede incluir una ruta de acceso absoluta o relativa para crear el archivo en una ubicación diferente. El nombre predeterminado coincide con el nombre del ensamblado.<br /><br /> Valor predeterminado: \<Current Directory> \\ ensamblado de<\> . imagemanifest|Opcional|  
|/guidName|Nombre que se va a asignar al símbolo GUID para todas las imágenes del manifiesto generado.<br /><br /> Valor predeterminado: AssetsGuid|Opcional|  
|/rootPath|La ruta de acceso raíz que debe quitarse antes de crear los URI de recursos administrados. (Esta marca es para ayudar en los casos en los que la herramienta obtiene la ruta de acceso del URI relativa equivocada, lo que provoca un error en la carga de los recursos).<br /><br /> Valor predeterminado: \<Current Directory>|Opcional|  
|/Recursive|Al establecer esta marca, se indica a la herramienta que busque de forma recursiva en los directorios del argumento/Resources. Si se omite este marcador, se producirá una búsqueda de directorios de nivel superior.|Opcional|  
|/isNative|Establezca esta marca cuando el argumento de ensamblado sea una ruta de acceso para un ensamblado nativo. Omita esta marca cuando el argumento de ensamblado sea el nombre de un ensamblado administrado. (Consulte la sección Notas para obtener más información acerca de esta marca).|Opcional|  
|/newGuids|Al establecer esta marca, se indica a la herramienta que cree un nuevo valor para el símbolo GUID de las imágenes en lugar de combinar el del manifiesto existente.|Opcional|  
|/newIds|Al establecer esta marca, se indica a la herramienta que cree nuevos valores de símbolo de identificador para cada imagen en lugar de combinar los valores del manifiesto existente.|Opcional|  
|/noLogo|Al establecer esta marca se detiene la impresión del producto y la información de copyright.|Opcional|  
|/?|Imprime la información de ayuda.|Opcional|  
|/help|Imprime la información de ayuda.|Opcional|  
  
 **Ejemplos**  
  
- ManifestFromResources/Resources: D:\Images/Assembly: My. Assembly. Name/isNative  
  
- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly: My. Assembly. Name/manifest: MyImageManifest. imagemanifest  
  
- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/Assembly: My. Assembly. Name/guidName: maimages/newGuids/newIds  
  
## <a name="notes"></a>Notas  
  
- La herramienta solo admite archivos. png y. Xaml. Cualquier otro tipo de imagen o archivo se omitirá. Se genera una advertencia para todos los tipos no compatibles encontrados durante el análisis de los recursos. Si no se encuentra ninguna imagen compatible cuando la herramienta termine de analizar los recursos, se generará un error.  
  
- Al seguir el formato sugerido para las imágenes. png, la herramienta establecerá el tamaño o el valor de dimensión para el. png en el tamaño especificado en el formato, aunque sea distinto del tamaño real de la imagen.  
  
- El formato de ancho y alto se puede omitir para las imágenes. png, pero la herramienta leerá el ancho o el alto real de la imagen y los usará para el valor de dimensión/tamaño de la imagen.  
  
- Ejecutar esta herramienta en la misma franja de imágenes varias veces para el mismo. imagemanifest producirá entradas de manifiesto duplicadas, porque la herramienta intenta dividir la banda de imagen en imágenes independientes y agregarlas al manifiesto existente.  
  
- La combinación (omitiendo/newGuids o/newIds) solo debe realizarse para los manifiestos generados por la herramienta. Los manifiestos que se han personalizado o generado a través de otros medios no se pueden combinar correctamente.  
  
- Es posible que los manifiestos generados para los ensamblados nativos deban editarse manualmente después de la generación para que los símbolos de identificador coincidan con los identificadores de recursos del archivo. rc del ensamblado nativo.  
  
## <a name="sample-output"></a>Salida de ejemplo  
 **Manifiesto de imagen simple**  
  
 Un manifiesto de imagen será similar a este archivo. xml:  
  
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
  
 **Manifiesto de imagen para una franja de imágenes**  
  
 Un manifiesto de imagen para una franja de imágenes será similar a este archivo. xml:  
  
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
  
 Un manifiesto de imagen para imágenes nativas será similar a este archivo. xml:  
  
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
