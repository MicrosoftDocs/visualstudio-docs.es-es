---
title: La estructura del archivo [Content_types] .xml | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38e65f484411abcfb2acd78b124b77ff3f2c49cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144572"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La estructura del archivo [Content_types] .xml
Contiene información sobre los tipos de contenido en un paquete VSIX. Visual Studio usa el archivo [Content_Types] .xml para instalar el paquete, pero no instala el propio archivo.  
  
> [!NOTE]
>  Aunque en este tema se aplica solo a los archivos .xml [Content_Type] que se utilizan en paquetes VSIX, el tipo de archivo [Content_Types] .xml forma parte de la *Open Packaging Conventions (OPC)* estándar. Para obtener más información, consulte [OPC: nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207) en el sitio Web de MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 Las secciones siguientes describen el elemento raíz y sus atributos y elementos secundarios.  
  
### <a name="root-element"></a>Elemento raíz  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Types`|Contiene los elementos secundarios que enumeran los tipos de archivo del paquete VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Xmlns`|(Requerido) La ubicación del esquema usado para este archivo de [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo  
  
|Valor|Descripción|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|La ubicación del esquema de tipos de contenido.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 El `Types` elemento puede contener cualquier número de `Default` elementos.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Default`|Describe un tipo de contenido del paquete VSIX. Cada tipo de archivo en el paquete debe tener su propio `Default` elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Extension`|La extensión de nombre de archivo de un archivo en el paquete VSIX.|  
|`ContentType`|Describe el tipo de contenido que está asociado con la extensión de nombre de archivo.|  
  
### <a name="attribute-name-attribute"></a>{Nombre del atributo} Atributo  
 Visual Studio reconoce los siguientes `ContentType` valores para la asociada `Extension` tipos.  
  
|Comprobación de actualización|Tipo de contenido|  
|---------------|-----------------|  
|txt|texto/sin formato|  
|pkgdef del|texto/sin formato|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|texto/html|  
|RTF|aplicación/rtf|  
|PDF|Application/pdf|  
|GIF|Image/gif|  
|jpg o jpeg|imagen: jpg|  
|TIFF|imagen: tiff|  
|vsix|aplicación/código postal|  
|Código postal|aplicación/código postal|  
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