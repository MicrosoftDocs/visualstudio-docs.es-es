---
title: Elemento MoreInfoURL (esquema del paquete de idioma VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 3f07b67b-95c5-4ae8-8b7e-d643cbbb0348
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c583d67e1920080f11158a4001e191e93e234006
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476840"
---
# <a name="moreinfourl-element-vsix-language-pack-schema"></a>Elemento MoreInfoURL (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcional. Vínculo a información localizada sobre la extensión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<MoreInfoURL>URL</MoreInfoURL>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Necesario. Proporciona el elemento raíz de un paquete de idioma de VSIX.|  
  
## <a name="text-value"></a>Valor de texto  
 Opcional. Un vínculo a un sitio Web. El vínculo es una cadena de texto.  
  
## <a name="element-information"></a>Información de elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Espacio de nombres    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nombre del esquema   |                 Esquema del paquete de idioma VSIX                 |
| Archivo de validación |                VSIXLanguagePackSchema.xsd                 |
|  Puede estar vacío   |                      No aplicable                       |
  
## <a name="see-also"></a>Consulte también  
 [Referencia del esquema del paquete de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referencia del esquema de extensión VSIX 1,0](/previous-versions/dd393700(v=vs.110))
