---
title: RequiredFrameworkVersion (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1583f5a0fab15c65d70819eb1b6e76cac5660ea5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion (Elemento, Plantillas de Visual Studio)
Especifica la versión mínima de .NET Framework que requiere la plantilla. Jerarquía del esquema.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<RequiredFrameworkVersion >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestran en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser el número de versión mínima de .NET Framework que se requiere para la plantilla.  
  
## <a name="remarks"></a>Comentarios  
 `RequiredFrameworkVersion` es un elemento opcional. Utilice este elemento si la plantilla solo es compatible con una versión mínima específica y versiones posteriores, si la hubiera, de .NET Framework.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)