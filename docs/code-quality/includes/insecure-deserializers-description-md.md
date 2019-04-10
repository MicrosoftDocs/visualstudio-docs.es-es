---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367273"
---
Deserializadores inseguros son vulnerables al deserializar los datos sin confianza. Un atacante podría modificar los datos serializados para incluir tipos inesperados con efectos secundarios malintencionados. Un ataque contra un deserializador inseguro podría, por ejemplo, ejecutar comandos en el sistema operativo subyacente, se comunican a través de la red o eliminar archivos.