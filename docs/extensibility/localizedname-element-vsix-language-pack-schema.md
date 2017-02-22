---
title: "Elemento LocalizedName (esquema del paquete de idioma VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento LocalizedName (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obligatorio. El nombre traducido de la extensión para instalarse.  
  
## Sintaxis  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|Ninguna||  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Ninguna||  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento del paquete de idioma VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obligatorio. Proporciona el elemento raíz para un paquete de idioma VSIX.|  
  
## Valor de texto  
 Obligatorio. El nombre del paquete de idioma en el idioma de destino.  
  
## Información de elemento  
  
|||  
|-|-|  
|Espacio de nombres|http:\/\/schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Nombre de esquema|Esquema del paquete de idioma VSIX|  
|Archivo de validación|VSIXLanguagePackSchema.xsd|  
|Puede estar vacío|No es aplicable|  
  
## Vea también  
 [Referencia del esquema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)