---
title: Elemento PreviewImage (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 56cef17add36ae1310b94421bfcf8a31951e00be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage (Elemento, Plantillas de Visual Studio)
Especifica la imagen de vista previa, como un nombre de archivo para la imagen de vista previa que aparece en el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<PreviewImage >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<PreviewImage>"filename"</PreviewImage>  
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
  
 El texto debe ser una cadena que representa un nombre de archivo.  
  
## <a name="remarks"></a>Comentarios  
 `PreviewImage` es un elemento opcional.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)