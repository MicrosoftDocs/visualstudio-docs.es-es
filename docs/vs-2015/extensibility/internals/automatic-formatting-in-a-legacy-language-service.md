---
title: El formato automático en un servicio de lenguaje heredado | Microsoft Docs
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
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19c36f5a31c6d3ed7284922bc830ea4925da5833
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246732"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formato automático en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Con el formato automático, un servicio de lenguaje inserta automáticamente un fragmento de código cuando un usuario empieza a escribir una construcción de código conocidos.  
  
## <a name="automatic-formatting-behavior"></a>Comportamiento de formato automático  
 Por ejemplo, si escribe `if`, el servicio de lenguaje inserta automáticamente las llaves coincidentes, o si presiona la tecla ENTRAR, el servicio de lenguaje fuerza el punto de inserción en la línea nueva para el nivel de sangría adecuado, dependiendo de si la anterior Abre un nuevo ámbito de línea.  
  
 También se puede usar el filtro de comando usado para el resto del servicio de lenguaje para el formato automático. También puede resaltar las llaves coincidentes mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)

