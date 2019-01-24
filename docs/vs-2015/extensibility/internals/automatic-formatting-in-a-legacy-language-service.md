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
ms.openlocfilehash: c1e9be96038334edeb9163c15d16a98999bd0c2e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795497"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formato automático en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Con el formato automático, un servicio de lenguaje inserta automáticamente un fragmento de código cuando un usuario empieza a escribir una construcción de código conocidos.  
  
## <a name="automatic-formatting-behavior"></a>Comportamiento de formato automático  
 Por ejemplo, si escribe `if`, el servicio de lenguaje inserta automáticamente las llaves coincidentes, o si presiona la tecla ENTRAR, el servicio de lenguaje fuerza el punto de inserción en la línea nueva para el nivel de sangría adecuado, dependiendo de si la anterior Abre un nuevo ámbito de línea.  
  
 También se puede usar el filtro de comando usado para el resto del servicio de lenguaje para el formato automático. También puede resaltar las llaves coincidentes mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)

