---
title: TemplateID (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a52b360994c53eef69ceafa45828ec1020be16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186422"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica un identificador para una plantilla de elemento que se clasifica en un grupo de plantillas de elementos mediante el elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<TemplateID> ... </TemplateID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 `string`Que representa un identificador de una plantilla de elemento que se clasifica en un grupo de plantillas de elementos por el `TemplateGroupID` elemento.  
  
## <a name="remarks"></a>Observaciones  
 `TemplateID` es un elemento opcional.  
  
 Si un archivo. vstemplate omite el `TemplateID` elemento, se usa el elemento [Name](../extensibility/name-element-visual-studio-templates.md) como identificador de la plantilla.  
  
 El valor del `TemplateID` elemento se utiliza junto con el registro del sistema del proyecto (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\11.0\Projects \\ ) para filtrar las plantillas que aparecen en el cuadro de diálogo **Agregar nuevo elemento** .  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
