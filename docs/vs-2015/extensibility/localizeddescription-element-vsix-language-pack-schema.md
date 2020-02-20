---
title: Elemento LocalizedDescription (esquema del paquete de idioma VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 49bf12f3056eb7ddb0e0afb8333a1f1893c7b954
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477019"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>Elemento LocalizedDescription (esquema del paquete de idioma VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Necesario. Proporciona una descripción localizada de la extensión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
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
 Necesario. Una descripción de texto de la extensión en el lenguaje de destino.  
  
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
