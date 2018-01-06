---
title: CustomParameter (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords: CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8b2380a585b1c428516e1578587c64b93d5b1d4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter (Elemento, Plantillas de Visual Studio)
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
|`Name`|Requerido. Nombre del parámetro. El formato para los parámetros es $*nombre*$.|  
|`Value`|Requerido. El valor de reemplazo para el parámetro.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa los parámetros personalizados que deben pasarse en el Asistente para plantillas cuando el asistente realice sustituciones de parámetros.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando contiene una plantilla de `CustomParameter` elementos, cada instancia de la `Name` atributo se sustituye por la `Value` atributos en los archivos de proyecto o un elemento creados.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o elemento de una plantilla con los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` en la plantilla de archivos se reemplazarán con `Red` y `Blue`, respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vea también  
 [CustomParameters (elemento) (plantillas de Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)