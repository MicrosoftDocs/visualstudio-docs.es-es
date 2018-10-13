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
ms.openlocfilehash: fc4cc8b2594720226a98f3d2664fca30a7ffe22a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269638"
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
  
|||  
|-|-|  
|Espacio de nombres|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Nombre de esquema|Esquema del paquete de idioma VSIX|  
|Archivo de validación|VSIXLanguagePackSchema.xsd|  
|Puede estar vacío|No es aplicable|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema del paquete de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Adaptación de paquetes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

