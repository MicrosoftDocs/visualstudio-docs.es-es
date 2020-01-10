---
title: Estructura del archivo Content_types]. XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3185b70f74478a9a55c4fb918c1535c86d154c76
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846368"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Estructura del archivo [Content_types].xml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene información sobre los tipos de contenido de un paquete VSIX. Visual Studio usa el archivo [Content_Types]. XML para instalar el paquete, pero no instala el propio archivo.  
  
> [!NOTE]
> Aunque este tema se aplica únicamente a los archivos [Content_Type]. XML que se usan en los paquetes VSIX, el tipo de archivo [Content_Types]. XML forma parte del estándar de *convenciones de empaquetado abierto (OPC)* . Para obtener más información, consulte [OPC: un nuevo estándar para empaquetar los datos](https://msdn.microsoft.com/magazine/cc163372.aspx) en el sitio web de MSDN.  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las secciones siguientes se describe el elemento raíz y sus atributos y elementos secundarios.  
  
### <a name="root-element"></a>Elemento Root  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Types`|Contiene elementos secundarios que enumeran los tipos de archivo del paquete VSIX.|  
  
### <a name="attributes"></a>Atributos  
  
|Attribute|Descripción|  
|---------------|-----------------|  
|`Xmlns`|(Obligatorio). La ubicación del esquema utilizado para este archivo [Content_Types]. Xml.|  
  
### <a name="attribute-name-attribute"></a>{Nombre de atributo} Atribui  
  
|                           {2&gt;Value&lt;2}                           |                Descripción                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | La ubicación del esquema de tipos de contenido. |
  
### <a name="child-elements"></a>Elemento secundario  
 El elemento `Types` puede contener cualquier número de elementos `Default`.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Default`|Describe un tipo de contenido en el paquete VSIX. Todos los tipos de archivo del paquete deben tener su propio `Default` elemento.|  
  
### <a name="attributes"></a>Atributos  
  
|Attribute|Descripción|  
|---------------|-----------------|  
|`Extension`|La extensión de nombre de archivo de un archivo en el paquete VSIX.|  
|`ContentType`|Describe el tipo de contenido asociado a la extensión de nombre de archivo.|  
  
### <a name="attribute-name-attribute"></a>{Nombre de atributo} Atribui  
 Visual Studio reconoce los siguientes valores de `ContentType` para los tipos de `Extension` asociados.  
  
|Comprobación de actualización|ContentType|  
|---------------|-----------------|  
|txt|texto/sin formato|  
|archivo pkgdef|texto/sin formato|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o HTML|text/html|  
|rtf|application/rtf|  
|pdf|aplicación/pdf|  
|gif|image/gif|  
|jpg o JPEG|imagen/jpg|  
|tiff|image/tiff|  
|vsix|application/zip|  
|zip|application/zip|  
|dll|application/octet-stream|  
|todos los demás tipos de archivo|application/octet-stream|  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El siguiente archivo [Content_Types]. XML describe un paquete VSIX típico.  
  
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
 [Esquema de extensión VSIX 1,0 referencia](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: un nuevo estándar para empaquetar los datos](https://msdn.microsoft.com/magazine/cc163372.aspx)
