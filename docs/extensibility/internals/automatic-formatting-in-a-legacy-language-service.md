---
title: El formato automático en un servicio de lenguaje heredado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56910a984fabb3ac4825fd438be17745126692a6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500675"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formato automático en un servicio de lenguaje heredado
Con el formato automático, un servicio de lenguaje inserta automáticamente un fragmento de código cuando un usuario empieza a escribir una construcción de código conocidos.  
  
## <a name="automatic-formatting-behavior"></a>Comportamiento de formato automático  
 Por ejemplo, cuando escriba *si*, el servicio de lenguaje inserta automáticamente las llaves coincidentes, o si presiona la tecla ENTRAR, el servicio de lenguaje fuerza el punto de inserción en la línea nueva para el nivel de sangría adecuado, según Si abre un nuevo ámbito de la línea anterior.  
  
 También se puede usar el filtro de comando usado para el resto del servicio de lenguaje para el formato automático. También puede resaltar las llaves coincidentes mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)