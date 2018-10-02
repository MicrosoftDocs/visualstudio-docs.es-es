---
title: El formato automático en un servicio de lenguaje heredado | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 46e5f30d01a3063a3683aa3cae4ae1da3e0aa141
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579140"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formato automático en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [formato automático en un servicio de lenguaje heredado](https://docs.microsoft.com/visualstudio/extensibility/internals/automatic-formatting-in-a-legacy-language-service).  
  
Con el formato automático, un servicio de lenguaje inserta automáticamente un fragmento de código cuando un usuario empieza a escribir una construcción de código conocidos.  
  
## <a name="automatic-formatting-behavior"></a>Comportamiento de formato automático  
 Por ejemplo, si escribe `if`, el servicio de lenguaje inserta automáticamente las llaves coincidentes, o si presiona la tecla ENTRAR, el servicio de lenguaje fuerza el punto de inserción en la línea nueva para el nivel de sangría adecuado, dependiendo de si la anterior Abre un nuevo ámbito de línea.  
  
 También se puede usar el filtro de comando usado para el resto del servicio de lenguaje para el formato automático. También puede resaltar las llaves coincidentes mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)

