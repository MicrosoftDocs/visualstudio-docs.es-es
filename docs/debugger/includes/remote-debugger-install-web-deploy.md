---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2d82fc0eb60b2680be9ed2bdb7de13313593da0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
1. Si piensa implementar aplicaciones con Web Deploy en Visual Studio, instale la versión más reciente de Web Deploy en el servidor.

    Para instalar Web Deploy, use la [instalador de plataforma Web (WPI)](https://www.microsoft.com/web/downloads/platform.aspx) u obtenga un instalador directamente desde el [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). Buscar Web Deploy en la pestaña aplicaciones. 

2. Compruebe que Web Deploy se ejecuta correctamente, abra **el Panel de Control > sistema y seguridad > Herramientas administrativas > servicios** y asegúrese de que **servicio Web Deployment Agent** se ejecuta (el nombre del servicio es diferente en versiones anteriores).

    Si el servicio del agente no se está ejecutando, inícielo. Si no está presente en absoluto, vaya a **el Panel de Control > Programas > desinstalar un programa**, buscar **Microsoft Web Deploy <version>** . Elegir **cambio** la instalación y asegúrese de que elige **se instalará en la unidad de disco duro local** para los componentes Web Deploy. Complete los pasos de instalación de cambio.