---
title: Manifest from Resources | Microsoft Docs
description: Obtenga información sobre cómo usar la herramienta Manifest from Resources para agregar archivos .png o .xaml a un archivo .imagemanifest para usarlos con Visual Studio Image Service.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f69a46362b3076025a63625adb1ee4a478622259
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903183"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
La herramienta Manifest from Resources es una aplicación de consola que toma una lista de recursos de imagen (archivos .png o .xaml) y genera un archivo .imagemanifest que permite usar esas imágenes con Visual Studio Image Service. Además, esta herramienta se puede usar para agregar imágenes a un archivo .imagemanifest existente. Esta herramienta es útil para agregar compatibilidad con valores altos de PPP y de formato para imágenes a Visual Studio extensión. El archivo .imagemanifest generado debe incluirse e implementarse como parte de una extensión de Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Uso de la herramienta
 **Sintaxis**

 ManifestFromResources /resources: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Argumentos**

|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|
|-|-|-|
|/resources|Lista delimitada por punto y coma de imágenes o directorios. Esta lista siempre debe contener la lista completa de imágenes que estarán en el manifiesto. Si solo se da una lista parcial, se perderán las entradas no incluidas.<br /><br /> Si un archivo de recursos determinado es una franja de imágenes, la herramienta lo dividirá en imágenes independientes antes de agregar cada subimagen al manifiesto.<br /><br /> Si la imagen es un archivo .png, se recomienda dar formato al nombre de este modo para que la herramienta pueda rellenar los atributos correctos de la imagen: \<Name> . \<Width> . \<Height>.png.|Obligatorio|
|/assembly|Nombre del ensamblado administrado (sin incluir la extensión) o la ruta de acceso en tiempo de ejecución del ensamblado nativo que hospeda los recursos (en relación con la ubicación en tiempo de ejecución del manifiesto).|Obligatorio|
|/manifest|Nombre que se debe dar al archivo .imagemanifest generado. Esto también puede incluir una ruta de acceso absoluta o relativa para crear el archivo en una ubicación diferente. El nombre predeterminado coincide con el nombre del ensamblado.<br /><br /> Valor predeterminado: \<Current Directory> \\<ensamblado \> .imagemanifest|Opcionales|
|/guidName|Nombre que se debe dar al símbolo GUID para todas las imágenes del manifiesto generado.<br /><br /> Valor predeterminado: AssetsGuid|Opcionales|
|/rootPath|Ruta de acceso raíz que se debe quitar antes de crear uri de recursos administrados. (Esta marca es para ayudar con los casos en los que la herramienta obtiene la ruta de acceso de URI relativa incorrecta, lo que hace que los recursos no se carguen).<br /><br /> Predeterminado: \<Current Directory>|Opcionales|
|/recursive|Al establecer esta marca, se indica a la herramienta que busque de forma recursiva todos los directorios del argumento /resources. Si se omite esta marca, se realizará una búsqueda de directorios solo de nivel superior.|Opcionales|
|/isNative|Establezca esta marca cuando el argumento de ensamblado sea una ruta de acceso para un ensamblado nativo. Omita esta marca cuando el argumento de ensamblado sea el nombre de un ensamblado administrado. (Consulte la sección Notas para obtener información adicional sobre esta marca).|Opcionales|
|/newGuids|Al establecer esta marca, se indica a la herramienta que cree un nuevo valor para el símbolo GUID de las imágenes en lugar de combinar el del manifiesto existente.|Opcionales|
|/newIds|Al establecer esta marca, se indica a la herramienta que cree nuevos valores de símbolo de identificador para cada imagen en lugar de combinar valores del manifiesto existente.|Opcionales|
|/noLogo|Al establecer esta marca, se impide que se imprima la información del producto y de los derechos de autor.|Opcionales|
|/?|Imprimir información de ayuda.|Opcionales|
|/help|Imprimir información de ayuda.|Opcional|

 **Ejemplos**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Notas

- La herramienta solo admite archivos .png y .xaml. Cualquier otro tipo de imagen o archivo se omitirá. Se genera una advertencia para todos los tipos no admitidos encontrados al analizar los recursos. Si no se encuentra ninguna imagen compatible cuando la herramienta haya terminado de analizar los recursos, se generará un error.

- Al seguir el formato sugerido para las imágenes de .png, la herramienta establecerá el valor de tamaño o dimensión del .png en el tamaño especificado en el formato, incluso si difiere del tamaño real de la imagen.

- El formato de ancho/alto se puede omitir para las imágenes de .png, pero la herramienta leerá el ancho o alto real de la imagen y los usará para el valor de tamaño o dimensión de la imagen.

- La ejecución de esta herramienta en la misma franja de imágenes varias veces para el mismo archivo .imagemanifest dará lugar a entradas de manifiesto duplicadas, ya que la herramienta intenta dividir la franja de imágenes en imágenes independientes y agregar esas entradas al manifiesto existente.

- La combinación (omitiendo /newGuids o /newIds) solo debe realizarse para manifiestos generados por herramientas. Es posible que los manifiestos que se han personalizado o generado a través de otros medios no se combinen correctamente.

- Es posible que los manifiestos generados para ensamblados nativos deban editarse manualmente después de la generación para que los símbolos de identificador coincidan con los identificadores de recurso del archivo .rc del ensamblado nativo.

## <a name="sample-output"></a>Salida de ejemplo
 **Manifiesto de imagen simple**

 Un manifiesto de imagen será similar a este .xml archivo:

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

 Un manifiesto de imagen para una franja de imágenes será similar a este .xml archivo:

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

 **Manifiesto de imagen para recursos de imagen de ensamblado nativo**

 Un manifiesto de imagen para imágenes nativas será similar a este .xml archivo:

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
