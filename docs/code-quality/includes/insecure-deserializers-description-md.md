---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147097"
---
Los deserializadores inseguros son vulnerables al deserializar datos que no son de confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados para insertar objetos con efectos secundarios malintencionados. Un ataque contra un deserializador inseguro podría, por ejemplo, ejecutar comandos en el sistema operativo subyacente, comunicarse a través de la red o eliminar archivos.