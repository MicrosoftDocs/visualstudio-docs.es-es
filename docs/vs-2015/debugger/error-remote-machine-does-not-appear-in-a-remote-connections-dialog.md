---
title: 'Error: La máquina remota no aparece en el cuadro de diálogo Conexiones remotas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a97211c1fa86123a2a7a65f2ff86b0cecac957dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697323"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Error: La máquina remota no aparece en el cuadro de diálogo Conexiones remotas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.  
  
 Si usa el modo de compatibilidad administrada, vea la documentación de Visual Studio 2010: [Solución de problemas de depuración remota - Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causas comunes de este error  
  
- El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador  
  
- El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.  
  
- El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
- El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
## <a name="see-also"></a>Consulte también  
 [Configurar las herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
