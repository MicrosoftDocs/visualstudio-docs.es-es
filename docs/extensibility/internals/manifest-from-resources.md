---
title: Manifiesto de recursos de recursos Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707275"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
La herramienta Manifiesto desde recursos es una aplicación de consola que toma una lista de recursos de imagen (archivos .png o .xaml) y genera un archivo .imagemanifest que permite usar esas imágenes con Visual Studio Image Service. Además, esta herramienta se puede utilizar para agregar imágenes a un .imagemanifest existente. Esta herramienta es útil para agregar alto PPP y compatibilidad con temas para imágenes a una extensión de Visual Studio. El archivo .imagemanifest generado debe incluirse e implementarse como parte de una extensión de Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Cómo utilizar la herramienta
 **Sintaxis**

 ManifestFromResources /resources:\<Dir1>; \<Img1> /assembly:\< \<AssemblyName>> de args opcionales

 **Argumentos**

||||
|-|-|-|
|**Cambiar nombre**|**Notas**|**Requerido u Opcional**|
|/recursos|Una lista delimitada por punto y coma de imágenes o directorios. Esta lista siempre debe contener la lista completa de imágenes que estarán en el manifiesto. Si solo se proporciona una lista parcial, se perderán las entradas no incluidas.<br /><br /> Si un archivo de recursos determinado es una tira de imagen, la herramienta lo dividirá en imágenes independientes antes de agregar cada subimagen al manifiesto.<br /><br /> Si la imagen es un archivo .png, le recomendamos que formatee el nombre \<de esta manera para que la herramienta pueda rellenar los atributos correctos para la imagen: Nombre>. \<Ancho>. \<Altura>.png.|Obligatorio|
|/ensamblaje|El nombre del ensamblado administrado (sin incluir la extensión) o la ruta de acceso en tiempo de ejecución del ensamblado nativo que hospeda los recursos (en relación con la ubicación en tiempo de ejecución del manifiesto).|Obligatorio|
|/manifest|El nombre que se va a asignar al archivo .imagemanifest generado. Esto también puede incluir una ruta de acceso absoluta o relativa para crear el archivo en una ubicación diferente. El nombre predeterminado coincide con el nombre del ensamblado.<br /><br /> Predeterminado: \<Directorio \\ actual\>><Assembly .imagemanifest|Opcional|
|/guidName|El nombre que se va a asignar al símbolo GUID de todas las imágenes del manifiesto generado.<br /><br /> Predeterminado: AssetsGuid|Opcional|
|/rootPath|La ruta de acceso raíz que debe quitarse antes de crear URI de recursos administrados. (Esta marca es para ayudar con los casos en los que la herramienta obtiene la ruta de ACCESO URI relativa incorrecta, lo que hace que los recursos no se carguen.)<br /><br /> Predeterminado: \<directorio actual>|Opcional|
|/recursivo|Al establecer esta marca, la herramienta busca recursivamente cualquier directorio en el argumento /resources. Si se omite esta marca, se realizará una búsqueda de directorios de solo nivel superior.|Opcional|
|/isNative|Establezca esta marca cuando el argumento de ensamblado sea una ruta de acceso para un ensamblado nativo. Omita esta marca cuando el argumento de ensamblado sea el nombre de un ensamblado administrado. (Consulte la sección Notas para obtener información adicional sobre esta marca.)|Opcional|
|/newGuids|Al establecer esta marca, se indica a la herramienta que cree un nuevo valor para el símbolo GUID de las imágenes en lugar de combinar el del manifiesto existente.|Opcional|
|/newIds|Al establecer esta marca, se indica a la herramienta que cree nuevos valores de símbolo de identificador para cada imagen en lugar de combinar valores del manifiesto existente.|Opcional|
|/noLogo|Al establecer esta marca, se detiene la impresión de la información del producto y de los derechos de autor.|Opcional|
|/?|Imprima la información de ayuda.|Opcional|
|/help|Imprima la información de ayuda.|Opcional|

 **Ejemplos**

- ManifestFromResources /resources:D:-Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:-Imágenes-Image1.png;D:-Imágenes-Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:-Imágenes-Image1.png;D:-Imágenes-Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Notas

- La herramienta solo admite archivos .png y .xaml. Cualquier otro tipo de imagen o archivo se ignorará. Se genera una advertencia para todos los tipos no admitidos encontrados al analizar los recursos. Si no se encuentra ninguna imagen compatible cuando la herramienta haya terminado de analizar los recursos, se generará un error

- Siguiendo el formato sugerido para las imágenes .png, la herramienta establecerá el valor de tamaño/dimensión para el .png en el tamaño especificado por el formato, incluso si difiere del tamaño real de la imagen.

- El formato de anchura/altura se puede omitir para las imágenes .png, pero la herramienta leerá el ancho/alto real de la imagen y los usará para el valor de tamaño/dimensión de la imagen.

- Al ejecutar esta herramienta en la misma tira de imagen varias veces para el mismo .imagemanifest, se producirán entradas de manifiesto duplicadas, ya que la herramienta intenta dividir la tira de imagen en imágenes independientes y agregarlas al manifiesto existente.

- La combinación (omitiendo /newGuids o /newIds) solo debe realizarse para los manifiestos generados por la herramienta. Es posible que los manifiestos que se han personalizado o generado a través de otros medios no se combinen correctamente.

- Es posible que los manifiestos que se generan para ensamblados nativos deban editarse a mano después de la generación para que los símbolos de identificador coincidan con los identificadores de recursos del archivo .rc del ensamblado nativo.

## <a name="sample-output"></a>Salida de ejemplo
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

 **Manifiesto de imagen para una tira de imagen**

 Un manifiesto de imagen para una tira de imagen será similar a este archivo .xml:

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

 Un manifiesto de imagen para imágenes nativas será similar a este archivo .xml:

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
