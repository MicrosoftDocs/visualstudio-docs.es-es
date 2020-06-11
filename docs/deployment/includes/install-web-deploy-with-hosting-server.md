---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173903"
---
Web Deploy 3.6 para servidores de hospedaje proporciona características de configuración adicionales que permiten la creación del archivo de configuración de publicación de la interfaz de usuario.

1. Si ya tiene Web Deploy 3.6 instalado en Windows Server, desinstálelo utilizando **Panel de Control** > **Programas** > **Desinstalar un programa**.

2. Después, instale Web Deploy 3.6 para servidores de hospedaje en Windows Server.

    Para instalar Web Deploy para servidores de hospedaje, use el Instalador de plataforma web (WebPI). (Para encontrar el vínculo del instalador de plataforma web desde IIS, seleccione **IIS** en el panel izquierdo del Administrador del servidor. En el panel del servidor, haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** . Luego use el vínculo **Obtener nuevos componentes de plataforma web** de la ventana **Acciones**). También puede obtener el instalador de plataforma web (WebPI) de [descargas](https://www.microsoft.com/web/downloads/platform.aspx).

    En el instalador de plataforma web, encontrará **Web Deploy 3.6 para servidores de hospedaje** en la pestaña Aplicaciones.

3. Si aún no ha instalado **Herramientas y scripts de administración de IIS**, hágalo ahora.

    Vaya a **Seleccionar roles de servidor** > **Servidor web (IIS)**  > **Herramientas de administración** y después seleccione el rol **Herramientas y scripts de administración de ISS**, haga clic en **Siguiente** y después instale el rol.

    ![Instalar herramientas y scripts de administración de IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Los scripts y herramientas son necesarios para habilitar la generación del archivo de configuración de publicación.

4. (Opcional) Compruebe que Web Deploy se ejecuta correctamente abriendo **Panel de Control > Sistema y seguridad > Herramientas administrativas > Servicios** y asegúrese de que **Servicio del agente de implementación web** se está ejecutando (el nombre del servicio es diferente en las versiones anteriores).

    Si el servicio del agente no se está ejecutando, inícielo. Si no está presente en absoluto, vaya a **Panel de Control > Programas > Desinstalar un programa** y busque **Microsoft Web Deploy \<version>** . Elija **Cambiar** la instalación y asegúrese de que elige **Se instalará en la unidad de disco duro local** para los componentes de Web Deploy. Complete los pasos de instalación de cambio.