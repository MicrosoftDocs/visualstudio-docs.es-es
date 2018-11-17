---
title: Elemento VSIXLanguagePack (esquema del paquete de idioma VSIX) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 556b701f0a1dbc348fef53273379586f7a0dba2c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744181"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento VSIXLanguagePack (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Requerido. Proporciona el elemento raíz para un paquete de idioma VSIX. El paquete de idioma VSIX proporciona información de instalación localizada para un paquete VSIX.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`xmlns`|El espacio de nombres XML en el que se define el esquema del paquete de idioma de VSIX.|  
  
## <a name="xmlns-attribute"></a>Atributo xmlns  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Requerido. La ubicación del archivo que define el esquema de los paquetes de idioma.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Requerido. El nombre localizado de la extensión para instalarse.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Requerido. La descripción adaptada de la extensión para instalarse.|  
|[Elemento MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcional. Un vínculo a información localizada sobre la extensión.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|Opcional. La ruta de acceso de una versión localizada del archivo de licencia para la extensión.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguna||  
  
## <a name="element-information"></a>Información de elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Espacio de nombres    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nombre de esquema   |                 Esquema del paquete de idioma VSIX                 |
| Archivo de validación |                VSIXLanguagePackSchema.xsd                 |
|  Puede estar vacío   |                            No                             |
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema del paquete de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

