---
title: Icon (elemento) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 475bca35ca1bdc1879301912c7ddd271f369a6ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870013"
---
# <a name="icon-element"></a>Icon (elemento)
El atributo guid de la etiqueta de icono es el guid de un mapa de bits definido. El `id` atributo selecciona la ranura en la Tira de mapa de bits. Este elemento es opcional. Si este elemento no está incluido el valor de **guidOfficeIcon:msotcidNoIcon** se implicarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Obligatorio. El guid de un mapa de bits definido.|  
|id|Obligatorio. Selecciona la ranura en la Tira de mapa de bits.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Buttons (elemento)](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Vea también  
 [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)