---
title: Icon (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31a6e0cf18422118c184f290fc8200d9c9263356
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186684"
---
# <a name="icon-element"></a>Icon (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El atributo guid de la etiqueta de icono es el guid de un mapa de bits definido.  El atributo id, selecciona la ranura en la Tira de mapa de bits. Este elemento es opcional.  Si este elemento se omite el valor de **guidOfficeIcon:msotcidNoIcon** se implicarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Requerido. El guid de un mapa de bits definido.|  
|id|Requerido. Selecciona la ranura en la Tira de mapa de bits.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

