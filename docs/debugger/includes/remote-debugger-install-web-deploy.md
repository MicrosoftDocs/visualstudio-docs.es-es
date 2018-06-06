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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794221"
---
1. Si piensa implementar aplicaciones con Web Deploy en Visual Studio, instale la versión más reciente de Web Deploy en el servidor.

    Para instalar Web Deploy, use la [instalador de plataforma Web (WPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para buscar el vínculo del instalador de plataforma Web de IIS, seleccione **IIS** en el panel izquierdo del administrador del servidor. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

    En el instalador de plataforma Web, encontrará Web Deploy en la pestaña aplicaciones. También puede obtener un instalador directamente desde el [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Compruebe que Web Deploy se ejecuta correctamente, abra **el Panel de Control > sistema y seguridad > Herramientas administrativas > servicios** y asegúrese de que **servicio Web Deployment Agent** se ejecuta (el nombre del servicio es diferente en versiones anteriores).

    Si el servicio del agente no se está ejecutando, inícielo. Si no está presente en absoluto, vaya a **el Panel de Control > Programas > desinstalar un programa**, buscar **Microsoft Web Deploy <version>** . Elegir **cambio** la instalación y asegúrese de que elige **se instalará en la unidad de disco duro local** para los componentes Web Deploy. Complete los pasos de instalación de cambio.