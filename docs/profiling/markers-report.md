---
title: Informe de marcadores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 765fd6db153f30ad312ea873919a20e5f885b158
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613887"
---
# <a name="markers-report"></a>Informe de marcadores
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