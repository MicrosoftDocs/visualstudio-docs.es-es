---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292072"
---
Web Deploy 3.6 para servidores de hospedaje proporciona características de configuración adicionales que permiten la creación del archivo de configuración de publicación de la interfaz de usuario.

1. Si ya tiene Web Deploy instalado en Windows Server, desinstálelo utilizando **Panel de Control** > **Programas** > **Desinstalar un programa**.

2. Después, instale Web Deploy 3.6 para servidores de hospedaje en Windows Server.

    Para instalar Web Deploy para servidores de hospedaje, use el Instalador de plataforma web (WebPI). (Para encontrar el vínculo del instalador de plataforma web desde IIS, seleccione **IIS** en el panel izquierdo del Administrador del servidor. En el panel del servidor, haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** . Luego use el vínculo **Obtener nuevos componentes de plataforma web** de la ventana **Acciones**). También puede obtener el instalador de plataforma web (WebPI) de [descargas](https://www.microsoft.com/web/downloads/platform.aspx).

    En el instalador de plataforma web, encontrará **Web Deploy 3.6 para servidores de hospedaje** en la pestaña Aplicaciones.

3. Si aún no ha instalado **Herramientas y scripts de administración de IIS**, hágalo ahora.

    Vaya a **Seleccionar roles de servidor** > **Servidor web (IIS)**  > **Herramientas de administración** y después seleccione el rol **Herramientas y scripts de administración de ISS**, haga clic en **Siguiente** y después instale el rol.

    ![Instalar herramientas y scripts de administración de IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Los scripts y herramientas son necesarios para habilitar la generación del archivo de configuración de publicación.

4. (Opcional) Compruebe que Web Deploy se ejecuta correctamente abriendo **Panel de Control > Sistema y seguridad > Herramientas administrativas > Servicios** y asegúrese de que:

    * El **servicio Agente de implementación web** se está ejecutando (el nombre del servicio es diferente en las versiones anteriores).

    * **Servicio de administración web** se está ejecutando.

    Si uno de los servicios del agente no se está ejecutando, reinicie el **servicio Agente de implementación web**.

    Si el servicio Agente de implementación web no está presente en absoluto, vaya a **Panel de Control > Programas > Desinstalar un programa** y busque **Microsoft Web Deploy \<version>** . Elija **Cambiar** la instalación y asegúrese de que elige **Se instalará en la unidad de disco duro local** para los componentes de Web Deploy. Complete los pasos de instalación de cambio.