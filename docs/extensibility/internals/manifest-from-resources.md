---
title: "Manifiestos de recursos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Manifiestos de recursos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El manifiesto de la herramienta de recursos es una aplicación de consola que toma una lista de recursos de imagen \(archivos .png o .xaml\) y genera un archivo .imagemanifest que permite a las imágenes para su uso con el servicio de imágenes de Visual Studio. Además, esta herramienta puede utilizarse para agregar imágenes a un .imagemanifest existente. Esta herramienta es útil para agregar compatibilidad con configuración elevada de PPP y temas para imágenes a una extensión de Visual Studio. El archivo .imagemanifest generado debe estar incluido en e implementado como parte de una extensión de Visual Studio \(VSIX\).  
  
## Cómo utilizar la herramienta  
 **Sintaxis**  
  
 ManifestFromResources Resources: \< Dir1 \>; \< Img1 \> \/assembly: \< AssemblyName \>\< opcional Args \>  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|Resources|Una lista delimitada por punto y coma de imágenes o directorios. Esta lista debería contener siempre una lista completa de las imágenes que se mostrarán en el manifiesto. Si solo se proporciona una lista parcial, se perderán las entradas no incluidas.<br /><br /> Si un archivo de recursos determinado es una banda de imagen, la herramienta dividirla en imágenes distintas antes de agregar cada subimagen en el manifiesto.<br /><br /> Si la imagen es un archivo .png, se recomienda formatear el nombre de esta manera para que la herramienta puede rellenar los atributos de la imagen derecha: \< nombre \>. \< ancho \>. \< alto \> PNG.|Obligatorio|  
|\/Assembly|El nombre del ensamblado administrado \(sin incluir la extensión\) o la ruta de acceso en tiempo de ejecución del ensamblado nativo que hospeda los recursos \(con respecto a la ubicación de tiempo de ejecución del manifiesto\).|Obligatorio|  
|\/ manifest|El nombre para el archivo .imagemanifest generado. Esto también puede incluir una ruta de acceso absoluta o relativa para crear el archivo en una ubicación diferente. El nombre predeterminado coincide con el nombre del ensamblado.<br /><br /> Valor predeterminado: \< directorio actual \> \\ \< ensamblado \> .imagemanifest|Opcional|  
|\/guidName|El nombre para el símbolo GUID para todas las imágenes en el manifiesto generado.<br /><br /> Valor predeterminado: AssetsGuid|Opcional|  
|\/rootPath|La ruta de acceso raíz que debe eliminarse antes de crear los URI de recurso administrado. \(Esta marca es ayuda a los casos donde la herramienta obtiene mal, por lo que los recursos que no se pudo cargar la ruta de acceso URI relativa\).<br /><br /> Valor predeterminado: \< directorio actual \>|Opcional|  
|\/recursive|Establecer esta marca indica a la herramienta de forma recursiva todos los directorios de búsqueda en el argumento Resources. Si se omite este indicador provocará una búsqueda top\-nivel sólo de directorios.|Opcional|  
|\/isNative|Establecer este indicador cuando el argumento de ensamblado es una ruta de acceso de un ensamblado nativo. Este indicador se omite cuando el argumento de ensamblado es el nombre de un ensamblado administrado. \(Consulte la sección Notas para obtener información adicional acerca de esta marca\).|Opcional|  
|\/newGuids|Establecer esta marca indica a la herramienta para crear un nuevo valor para el símbolo GUID de las imágenes en lugar de combinar el uno del manifiesto existente.|Opcional|  
|\/newIds|Establecer esta marca indica a la herramienta para crear nuevos valores de símbolo de identificador para cada imagen en lugar de combinar valores del manifiesto existente.|Opcional|  
|\/noLogo|Establecer este indicador detiene la información de producto y de copyright de la impresión.|Opcional|  
|\/?|Imprimir la información de ayuda.|Opcional|  
|\/help|Imprimir la información de ayuda.|Opcional|  
  
 **Ejemplos**  
  
-   ManifestFromResources \/resources:D:\\Images \/assembly:My.Assembly.Name \/isNative  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/guidName:MyImages \/newGuids \/newIds  
  
## Notas  
  
-   La herramienta sólo admite archivos .png y XAML. Se omitirá cualquier otro tipo de imagen o un archivo. Se genera una advertencia para todos los tipos no admitidos encontrados durante el análisis de los recursos. Si no hay ninguna imágenes se encuentran cuando finalice la herramienta de análisis de los recursos, se generará un error  
  
-   Siguiendo el formato sugerido para imágenes PNG, la herramienta establecerá el valor de tamaño y dimensión de la .png al tamaño especificado por el formato, incluso si es diferente del tamaño real de la imagen.  
  
-   Se puede omitir el formato de ancho y alto para imágenes PNG, pero la herramienta leerá real ancho y alto de la imagen y utilizarlas para el valor de tamaño y dimensión de la imagen.  
  
-   Ejecutar esta herramienta en la misma franja de imagen varias veces para el mismo .imagemanifest producirá entradas duplicadas de manifiesto, porque la herramienta intenta dividir la franja de imágenes en imágenes independientes y agregarlos al manifiesto existente.  
  
-   Combinar \(omitiendo \/newGuids o \/newIds\) sólo debe hacerse para los manifiestos generados por la herramienta. No se pueden combinar correctamente manifiestos que se hayan adaptado o generados por otros medios.  
  
-   Manifiestos que se generan para ensamblados nativos puede que tenga que editar manualmente después de la generación para hacer que los símbolos ID coincide con los identificadores de archivo .rc de nativo del ensamblado de recursos.  
  
## Resultados del ejemplo  
 **Manifiesto de imagen sencilla**  
  
 Un manifiesto de la imagen será similar a este archivo .xml:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImage" Value="0" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage)"> <Source Uri="$(Resources)/Xaml/MyImage.xaml" /> <Source Uri="$(Resources)/Png/MyImage.16.16.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```  
  
 **Manifiesto de la imagen para una banda de imagen**  
  
 Un manifiesto de la imagen para una banda de imagen debe ser similar a este archivo .xml:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImageStrip_0" Value="1" /> <ID Name="MyImageStrip_1" Value="2" /> <ID Name="MyImageStrip" Value="3" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)"> <Source Uri="$(Resources)/MyImageStrip_0.png"> <Size Value="16" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)"> <Source Uri="$(Resources)/MyImageStrip_1.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists> <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)"> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" /> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" /> </ImageList> </ImageLists> </ImageManifest>  
```  
  
 **Manifiesto de imagen para los recursos de imagen de ensamblado nativo**  
  
 Un manifiesto de la imagen de las imágenes nativas será similar a este archivo .xml:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15198 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" /> <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" /> <ID Name="MyImage1" Value="0" /> <ID Name="MyImage2" Value="1" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage1)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage1)" Type="PNG" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImage2)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage2)" Type="PNG" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```