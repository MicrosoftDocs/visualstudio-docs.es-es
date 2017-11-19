---
title: Elemento TemplateGroupID (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8f68b3a64fab519e31876d120f223961c10fffc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID (Elemento, Plantillas de Visual Studio)
Especifica en qué tipo de proyecto se mostrará una plantilla de elemento. Este elemento es significativo cuando [ShowByDefault (plantillas de Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) está establecido en `false`. Cuando [ShowByDefault (plantillas de Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) se establece en `true`, una plantilla de elemento estará disponible en todos los tipos de proyecto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
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
  
## <a name="remarks"></a>Comentarios  
 `TemplateGroupID` es un elemento.  
  
 El valor de la `TemplateGroupID` elemento se usa junto con el registro del sistema de proyecto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<número de versión >*\Projects\\) en las plantillas de filtro que aparecen en la **Agregar nuevo elemento** cuadro de diálogo.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)