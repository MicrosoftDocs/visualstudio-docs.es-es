---
title: 'Error: La máquina remota no aparece en un cuadro de diálogo conexiones remotas | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd194bc26574e8004894a72ce29d753cabf66a21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850804"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Error: La máquina remota no aparece en el cuadro de diálogo Conexiones remotas
Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.

 Si está utilizando el modo de compatibilidad administrado, consulte la documentación de Visual Studio 2010: [Solución de problemas de depuración remota - Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Causas comunes de este error

- El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador

- El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.

- El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).

- El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)