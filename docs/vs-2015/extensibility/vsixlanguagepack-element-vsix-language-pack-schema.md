---
title: Elemento del (esquema del paquete de idioma VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd3ed1477d1c4d345e5fc6f6496d12044d4af244
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114237"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento del paquete de idioma de VSIX (esquema del paquete de idioma de VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Necesario. Proporciona el elemento raíz de un paquete de idioma de VSIX. El paquete de idioma de VSIX proporciona información de instalación localizada para un paquete VSIX.  
  
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
|`xmlns`|Espacio de nombres XML en el que se define el esquema del paquete de idioma VSIX.|  
  
## <a name="xmlns-attribute"></a>xmlns (atributo)  
  
|Value|Descripción|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Necesario. Ubicación del archivo que define el esquema para los paquetes de idioma.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Necesario. Nombre localizado de la extensión que se va a instalar.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Necesario. La descripción localizada de la extensión que se va a instalar.|  
|[Elemento MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcional. Vínculo a información localizada sobre la extensión.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|Opcional. La ruta de acceso de una versión localizada del archivo de licencia de la extensión.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|None||  
  
## <a name="element-information"></a>Información de elemento  

:::row:::
    :::column:::
        Espacio de nombres
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Nombre del esquema
    :::column-end:::
    :::column:::
        Esquema del paquete de idioma VSIX
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Archivo de validación
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Puede estar vacío
    :::column-end:::
    :::column:::
        No
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Consulte también  
 [Referencia del esquema del paquete de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md) [localizar paquetes VSIX](../extensibility/localizing-vsix-packages.md) [Referencia del esquema de extensión VSIX 1,0 referencia](/previous-versions/dd393700(v=vs.110))
