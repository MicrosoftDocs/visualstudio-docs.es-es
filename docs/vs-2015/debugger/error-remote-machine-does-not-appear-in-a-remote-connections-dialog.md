---
title: 'Error: El equipo remoto no aparece en un cuadro de diálogo conexiones remotas | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 552be1e38cdb7401af36b287b23091d754c35980
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581648"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Error: la máquina remota no aparece en el cuadro de diálogo Conexiones remotas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: la máquina remota no aparece en un cuadro de diálogo conexiones remotas](https://docs.microsoft.com/visualstudio/debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog).  
  
Si el equipo remoto no aparece en el cuadro de diálogo Conexiones remotas, compruebe las siguientes causas comunes.  
  
 Si está utilizando el modo de compatibilidad administrado, consulte la documentación de Visual Studio 2010: [solución de problemas de depuración remota - Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causas comunes de este error  
  
-   El equipo remoto se está ejecutando en una máquina que se encuentra en una subred diferente. Para solucionar este problema, escriba manualmente la dirección IP o el nombre del equipo en el cuadro de diálogo Calificador  
  
-   El depurador remoto no se está ejecutando en la máquina remota. Para solucionar este problema, inicie al depurador remoto.  
  
-   El firewall está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el firewall para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
-   El software antivirus está bloqueando la comunicación entre Visual Studio y la máquina remota. Para solucionar este problema, configure el software antivirus para permitir la comunicación entre Visual Studio y el depurador remoto (msvsmon).  
  
## <a name="see-also"></a>Vea también  
 [Configurar las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



