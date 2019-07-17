---
title: Icon (elemento) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5ced87596b5e40ae70e3faa06e58493da3d8ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203994"
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
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|GUID|Necesario. El guid de un mapa de bits definido.|  
|id|Necesario. Selecciona la ranura en la Tira de mapa de bits.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
