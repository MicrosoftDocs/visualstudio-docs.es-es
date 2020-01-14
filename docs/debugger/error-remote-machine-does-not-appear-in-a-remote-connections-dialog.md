---
title: 'Error: el equipo remoto no aparece en un cuadro de diálogo de conexiones remotas | Microsoft Docs'
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
ms.openlocfilehash: dd46d2164ccb3cd26831160235b992d699229e2c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916189"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Error: la máquina remota no aparece en el cuadro de diálogo Conexiones remotas
Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.

 Si usa el modo de compatibilidad administrada, vea la documentación de Visual Studio 2010: [Solución de problemas de depuración remota - Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Causas comunes de este error

- El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador

- El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.

- El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).

- El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)