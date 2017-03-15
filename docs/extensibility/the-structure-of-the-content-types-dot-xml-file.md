---
title: La estructura del archivo .xml [Content_types] | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La estructura del archivo .xml [Content_types]
Contiene información sobre los tipos de contenido en un paquete VSIX. Visual Studio utiliza el archivo [Content_Types] .xml para instalar el paquete, pero no instala el propio archivo.  
  
> [!NOTE]
>  Aunque este tema solo se aplica a los archivos .xml [Content_Type] que se utilizan en paquetes VSIX, el tipo de archivo .xml [Content_Types] forma parte de la *Open Packaging Conventions (OPC)* estándar. Para obtener más información, consulte [OPC: nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207) en el sitio Web de MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 Las secciones siguientes describen el elemento raíz y sus atributos y elementos secundarios.  
  
### <a name="root-element"></a>Elemento raíz  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Types`|Contiene los elementos secundarios que enumeran los tipos de archivo del paquete VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Xmlns`|(Requerido) La ubicación del esquema usado para el archivo [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo  
  
|Valor|Descripción|  
|-----------|-----------------|  
|http://schemas.OpenFormats.org/Package/2006/Content-Types|La ubicación del esquema de tipos de contenido.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 El `Types` elemento puede contener cualquier número de `Default` elementos.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Default`|Describe un tipo de contenido del paquete VSIX. Cada tipo de archivo del paquete debe tener su propio `Default` elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Extension`|La extensión de nombre de archivo de un archivo del paquete VSIX.|  
|`ContentType`|Describe el tipo de contenido que está asociado con la extensión de nombre de archivo.|  
  
### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo  
 Visual Studio reconoce los siguientes `ContentType` valores asociado `Extension` tipos.  
  
|Extensión|Tipo de contenido|  
|---------------|-----------------|  
|txt|texto sin formato|  
|pkgdef|texto sin formato|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|texto/html|  
|RTF|aplicación/rtf|  
|PDF|Application/pdf|  
|GIF|Image/gif|  
|jpg o jpeg|imagen: jpg|  
|TIFF|imagen tiff|  
|vsix|aplicación o código postal|  
|ZIP|aplicación o código postal|  
|dll|application/octet-stream|  
|todos los demás tipos de archivo|application/octet-stream|  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El siguiente archivo de [Content_Types] .xml describe un paquete VSIX típico.  
  
### <a name="code"></a>Código  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Vea también  
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Un nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207)
