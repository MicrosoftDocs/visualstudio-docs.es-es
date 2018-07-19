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
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811926"
---
1. Si piensa implementar sus aplicaciones con Web Deploy en Visual Studio, instale la versión más reciente de Web Deploy en el servidor.

    Para instalar Web Deploy, use el [instalador de plataforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para encontrar el vínculo del instalador de plataforma Web de IIS, seleccione **IIS** en el panel izquierdo del administrador del servidor. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

    En el instalador de plataforma Web, encontrará Web Deploy en la pestaña aplicaciones. También puede obtener un instalador directamente desde el [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Compruebe que Web Deploy se ejecuta correctamente abriendo **Panel de Control > sistema y seguridad > Herramientas administrativas > servicios** y asegúrese de que **servicio del agente de implementación Web** se está ejecutando (la nombre del servicio es diferente en las versiones anteriores).

    Si no se está ejecutando el servicio del agente, inícielo. Si no está presente en absoluto, vaya a **Panel de Control > Programas > desinstalar un programa**, encontrar **Microsoft Web Deploy <version>** . Elegir **cambio** la instalación y asegúrese de que elige **se instalará en la unidad de disco dura local** para los componentes Web Deploy. Complete los pasos de instalación de cambio.