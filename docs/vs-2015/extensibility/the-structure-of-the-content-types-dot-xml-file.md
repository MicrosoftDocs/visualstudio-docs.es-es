---
title: La estructura de la Content_types] .xml archivo | Microsoft Docs
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
ms.openlocfilehash: 4117e028611c2ff64102a97579d17d72f50407e0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430154"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La estructura de la Content_types] .xml archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene información sobre los tipos de contenido en un paquete VSIX. Visual Studio usa el archivo [Content_Types] .xml para instalar el paquete, pero no instala el propio archivo.  
  
> [!NOTE]
> Aunque en este tema se aplica solo a los archivos .xml [Content_Type] que se usan en paquetes VSIX, el tipo de archivo [Content_Types] .xml forma parte de la *Open Packaging Conventions (OPC)* estándar. Para obtener más información, consulte [OPC: Un nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207) en el sitio Web de MSDN.  
  
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
  
|                           Valor                           |                Descripción                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | La ubicación del esquema de tipos de contenido. |
  
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
|htm o html|text/html|  
|rtf|application/rtf|  
|pdf|Application/pdf|  
|gif|Image/gif|  
|jpg o jpeg|image/jpg|  
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
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Un nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207)
