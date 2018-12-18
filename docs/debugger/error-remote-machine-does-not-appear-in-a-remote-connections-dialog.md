---
title: 'Error: El equipo remoto no aparece en un cuadro de diálogo conexiones remotas | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f91358597ce19f9dac1341831364dafb1fcabae
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284164"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Error: la máquina remota no aparece en el cuadro de diálogo Conexiones remotas
Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.  
  
 Si está utilizando el modo de compatibilidad administrado, consulte la documentación de Visual Studio 2010: [solución de problemas de depuración remota - Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).  
  
### <a name="common-causes-for-this-error"></a>Causas comunes de este error  
  
-   El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador  
  
-   El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.  
  
-   El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
-   El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)