---
title: "Elemento License (esquema del paquete de idioma VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento License (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Opcional. La ruta de acceso de una versión localizada del archivo de licencia para la extensión.  
  
## Sintaxis  
  
```  
<License>FilePath\license.txt</License>  
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
 La ruta de acceso relativa del archivo de licencia traducido que se mostrará.  
  
## Comentarios  
 Si el `License` se define el elemento, a continuación, se muestra el texto del archivo de licencia designado durante la instalación y el usuario debe aceptar la licencia para poder continuar.  
  
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