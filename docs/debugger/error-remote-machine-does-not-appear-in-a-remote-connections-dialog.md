---
title: 'Error: El equipo remoto no aparece en un cuadro de diálogo conexiones remotas | Documentos de Microsoft'
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
ms.openlocfilehash: c52a2ebd99b052171220fd8a06f1ae7ff5dc258e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Error: la máquina remota no aparece en el cuadro de diálogo Conexiones remotas
Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.  
  
 Si usa el modo de compatibilidad administrada, vea la documentación de Visual Studio 2010: [Solución de problemas de depuración remota - Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causas comunes de este error  
  
-   El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador  
  
-   El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.  
  
-   El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
-   El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)