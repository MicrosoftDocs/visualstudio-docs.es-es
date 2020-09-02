---
title: TemplateGroupID (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53d1f6628ff9df48879a34417b7d89223d848dd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186437"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica en qué tipo de proyecto se mostrará una plantilla de elemento. Este elemento es importante cuando [ShowByDefault (plantillas de Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) está establecido en `false` . Cuando [ShowByDefault (plantillas de Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) está establecido en `true` , una plantilla de elemento está disponible en todos los tipos de proyecto.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateGroupID>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto especifica un identificador para una categoría de plantillas de elementos.  
  
## <a name="remarks"></a>Observaciones  
 `TemplateGroupID` es un elemento.  
  
 El valor del `TemplateGroupID` elemento se utiliza junto con el registro del sistema del proyecto (HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio \\ *\<version number>* \projects \\ ) para filtrar plantillas que aparecen en el cuadro de diálogo **Agregar nuevo elemento** .  
  
|Valor de Visual C++|Significado|  
|------------------------|-------------|  
|VC-Native|Se usa en objetos nativos. También el valor predeterminado si no se puede determinar un tipo de proyecto.|  
|VC-Managed|Utilizado para proyectos (/ clr) administrados|  
|VC-Windows|Utilizado para todos los proyectos destinados a la plataforma de Windows (nativo/administrado/almacén)|  
|WinRT-Native-UAP|Utilizado para proyectos de la Tienda Windows 10|  
|CodeSharing-Native|Utilizado para proyectos de elementos compartidos|  
|WinRT-Native-6.3|Utilizado para proyectos de la Tienda Windows 8.1|  
|WinRT-Native-Phone-6.3|Utilizado para proyectos de Windows Phone 8.1|  
|WinRT-Native|Utilizado para proyectos de la Tienda Windows 8.0|  
|VC-Android|Utilizado para proyectos Android|  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
