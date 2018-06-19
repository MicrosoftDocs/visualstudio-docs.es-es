---
title: Hace referencia a elemento (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e758bb0bc493086d9e8090c14eaca744129c277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136502"
---
# <a name="references-element-visual-studio-templates"></a>References (Elemento, Plantillas de Visual Studio)
Agrupa las referencias de ensamblado que la plantilla se agrega a los proyectos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Referencias >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Referencia](../extensibility/reference-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica la referencia de ensamblado para agregar cuando el elemento se agrega a un proyecto. Debe haber uno o varios `Reference` elementos en un `References` elemento.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|  
  
## <a name="remarks"></a>Comentarios  
 `References` es un elemento secundario opcional de `TemplateContent`.  
  
 El `Reference` y `References` elementos solo se pueden utilizar en archivos .vstemplate que tienen un `Type` valor del atributo `Item`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el `TemplateContent` elemento de una plantilla de elementos. Este código XML agrega referencias a los ensamblados System.dll y System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)