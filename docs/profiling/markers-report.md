---
title: Informe de marcadores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b46cb18e1972d22010ce356f1d9208f391f6d79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31580413"
---
# <a name="markers-report"></a>Informe de marcadores
El informe de marcadores enumera los marcadores en el período de tiempo mostrado.  El movimiento panorámico, hacer zoom u ocultar carriles puede causar que los marcadores aparezcan o desaparezcan. El informe contiene esta información sobre cada marcador:  
  
-   El momento en el que comenzó, con respecto al inicio del seguimiento.  
  
-   La duración. La duración es cero para las marcas y mensajes ya que representan un instante.  
  
-   El identificador del subproceso que lo generó.  
  
-   El proveedor de seguimiento de eventos para Windows (ETW) que lo generó.  
  
-   La serie de marcadores desde la que se escribió.  
  
-   La categoría de eventos a la que pertenece.  
  
-   El nivel de importancia.  
  
-   Su tipo (intervalo, marca o mensaje).  
  
-   Una descripción exhaustiva de lo que representa  
  
 Elija el botón **Exportar** para guardar el informe de marcadores como un archivo CSV. Puede utilizar los datos del archivo CSV con otras aplicaciones o herramientas.  
  
> [!NOTE]
>  El informe de marcadores puede mostrar 1000 marcadores. Para verlos todos, exporte el informe completo a un archivo CSV.