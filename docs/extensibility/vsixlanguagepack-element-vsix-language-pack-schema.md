---
title: "Elemento VSIXLanguagePack (esquema del paquete de idioma VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Elemento VSIXLanguagePack (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obligatorio. Proporciona el elemento raíz para un paquete de idioma VSIX. El paquete de idioma VSIX proporciona información de instalación adaptada para un paquete VSIX.  
  
## Sintaxis  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`xmlns`|El espacio de nombres XML en el que se define el esquema del paquete de idioma VSIX.|  
  
## Atributo xmlns  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obligatorio. La ubicación del archivo que define el esquema para los paquetes de idioma.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obligatorio. El nombre traducido de la extensión para instalarse.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obligatorio. La descripción adaptada de la extensión que se va a instalar.|  
|[Elemento URL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcional. Un vínculo a información localizada sobre la extensión.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|Opcional. La ruta de acceso de una versión localizada del archivo de licencia para la extensión.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Ninguno||  
  
## Información de elemento  
  
|||  
|-|-|  
|Espacio de nombres|http:\/\/schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Nombre de esquema|Esquema del paquete de idioma VSIX|  
|Archivo de validación|VSIXLanguagePackSchema.xsd|  
|Puede estar vacío|No|  
  
## Vea también  
 [Referencia del esquema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)