---
title: CustomParameter ((elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59bfec972750a4f893d1cb8b7cf08710bcca761a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555978"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contiene un nombre y valor de parámetro personalizado que se usará cuando se cree un proyecto o elemento a partir de la plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Necesario. El nombre del parámetro. El formato de los parámetros es $*Name*$.|  
|`Value`|Necesario. Valor de reemplazo para el parámetro.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa los parámetros personalizados que se van a pasar al Asistente para plantillas cuando el asistente realiza reemplazos de parámetros.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando una plantilla contiene `CustomParameter` elementos, cada instancia `Name` se reemplaza por el `Value` atributo en los archivos de proyecto o elemento creados.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o un elemento a partir de una plantilla con los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` de los archivos de plantilla se reemplazarán por `Red` y `Blue` , respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Consulte también  
 [CustomParameters ((elemento, plantillas de Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
