---
title: Informe de marcadores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20e9ece55f1e17c874832f473236dfbae7684c54
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833857"
---
# <a name="markers-report"></a>Informe de marcadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El informe de marcadores enumera los marcadores en el período de tiempo mostrado.  El movimiento panorámico, hacer zoom u ocultar carriles puede causar que los marcadores aparezcan o desaparezcan. El informe contiene esta información sobre cada marcador:  
  
- El momento en el que comenzó, con respecto al inicio del seguimiento.  
  
- La duración. La duración es cero para las marcas y mensajes ya que representan un instante.  
  
- El identificador del subproceso que lo generó.  
  
- El proveedor de seguimiento de eventos para Windows (ETW) que lo generó.  
  
- La serie de marcadores desde la que se escribió.  
  
- La categoría de eventos a la que pertenece.  
  
- El nivel de importancia.  
  
- Su tipo (intervalo, marca o mensaje).  
  
- Una descripción exhaustiva de lo que representa  
  
  Elija el botón **Exportar** para guardar el informe de marcadores como un archivo CSV. Puede utilizar los datos del archivo CSV con otras aplicaciones o herramientas.  
  
> [!NOTE]
>  El informe de marcadores puede mostrar 1000 marcadores. Para verlos todos, exporte el informe completo a un archivo CSV.
