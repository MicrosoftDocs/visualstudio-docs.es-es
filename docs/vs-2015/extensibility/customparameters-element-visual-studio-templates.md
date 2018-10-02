---
title: Elemento CustomParameters (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b74b32b3134dbbb2fefdf9fc7d1913a36efbdb5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582192"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CustomParameters Element (Visual Studio Templates)](https://docs.microsoft.com/visualstudio/extensibility/customparameters-element-visual-studio-templates).  
  
Agrupa los parámetros personalizados que deben pasarse al Asistente de plantilla cuando el asistente realiza sustituciones de parámetros.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Contiene un nombre de parámetro personalizado y un valor que se usará cuando se crea un proyecto o elemento de la plantilla. Puede haber cero o más elementos `CustomParameter` en un elemento `CustomParameters`.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o elemento de una plantilla con los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` en la plantilla se reemplazarán los archivos con `Red` y `Blue`, respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vea también  
 [CustomParameter (elemento) (plantillas de Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

