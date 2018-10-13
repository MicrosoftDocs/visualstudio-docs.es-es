---
title: CustomParameter (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9540b42497b15eace2ed7a54ef9c26f76c0576a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198853"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene un nombre de parámetro personalizado y un valor que se usará cuando se crea un proyecto o elemento de la plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. Nombre del parámetro. El formato de los parámetros es $*nombre*$.|  
|`Value`|Requerido. El valor de reemplazo para el parámetro.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa los parámetros personalizados que deben pasarse al Asistente de plantilla cuando el asistente realiza sustituciones de parámetros.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando una plantilla contiene `CustomParameter` elementos, cada instancia de la `Name` atributo se sustituye por el `Value` atributo en los archivos de proyecto o elemento creados.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o elemento de una plantilla con los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` en la plantilla se reemplazarán los archivos con `Red` y `Blue`, respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elemento CustomParameters (plantillas de Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

