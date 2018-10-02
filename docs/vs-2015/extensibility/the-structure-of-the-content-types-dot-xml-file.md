---
title: La estructura de la Content_types] .xml archivo | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89c5e1bab9f8cbe8cd6e2b980013c6bfdf4bc039
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582553"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La estructura de la Content_types] .xml archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [estructura del archivo [Content_types] .xml](https://docs.microsoft.com/visualstudio/extensibility/the-structure-of-the-content-types-dot-xml-file).  
  
Contiene información sobre los tipos de contenido en un paquete VSIX. Visual Studio usa el archivo [Content_Types] .xml para instalar el paquete, pero no instala el propio archivo.  
  
> [!NOTE]
>  Aunque en este tema se aplica solo a los archivos .xml [Content_Type] que se usan en paquetes VSIX, el tipo de archivo [Content_Types] .xml forma parte de la *Open Packaging Conventions (OPC)* estándar. Para obtener más información, consulte [OPC: nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207) en el sitio Web de MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 Las secciones siguientes describen el elemento raíz y sus atributos y elementos secundarios.  
  
### <a name="root-element"></a>Elemento raíz  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Types`|Contiene los elementos secundarios que enumera los tipos de archivo del paquete VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Xmlns`|(Requerido) La ubicación del esquema usado para el archivo [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo  
  
|Valor|Descripción|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|La ubicación del esquema de tipos de contenido.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 El `Types` elemento puede contener cualquier número de `Default` elementos.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Default`|Describe un tipo de contenido del paquete VSIX. Cada tipo de archivo en el paquete debe tener su propia `Default` elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Extension`|La extensión de nombre de archivo de un archivo en el paquete VSIX.|  
|`ContentType`|Describe el tipo de contenido que está asociado con la extensión de nombre de archivo.|  
  
### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo  
 Visual Studio reconoce los siguientes `ContentType` valores asociado `Extension` tipos.  
  
|Comprobación de actualización|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|texto/html|  
|RTF|aplicación/rtf|  
|PDF|Application/pdf|  
|GIF|Image/gif|  
|jpg o jpeg|imagen jpg|  
|TIFF|imagen tiff|  
|vsix|Application/zip|  
|ZIP|Application/zip|  
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

