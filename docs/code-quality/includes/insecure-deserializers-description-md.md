---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65840912"
---
Deserializadores inseguros son vulnerables al deserializar los datos sin confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. Un ataque contra un deserializador inseguro podría, por ejemplo, ejecutar comandos en el sistema operativo subyacente, se comunican a través de la red o eliminar archivos.