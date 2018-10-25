---
title: Elemento LocalizedName (esquema del paquete de idioma VSIX) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d17ce9db334d3b2cc8b6c892784b10d42eba07ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832425"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Elemento LocalizedName (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Requerido. El nombre localizado de la extensión para instalarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Ninguna||  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguna||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Requerido. Proporciona el elemento raíz para un paquete de idioma VSIX.|  
  
## <a name="text-value"></a>Valor de texto  
 Requerido. El nombre del paquete de idioma en el idioma de destino.  
  
## <a name="element-information"></a>Información de elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Espacio de nombres    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nombre de esquema   |                 Esquema del paquete de idioma VSIX                 |
| Archivo de validación |                VSIXLanguagePackSchema.xsd                 |
|  Puede estar vacío   |                      No es aplicable                       |
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema del paquete de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

