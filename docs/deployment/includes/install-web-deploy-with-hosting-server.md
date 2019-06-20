---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67256611"
---
Web Deploy 3.6 para servidores de hospedaje proporciona características de configuración adicionales que permiten la creación del archivo de configuración de publicación de la interfaz de usuario.

1. Si ya tiene Web Deploy 3.6 instalado en Windows Server, desinstálelo utilizando **Panel de Control** > **Programas** > **Desinstalar un programa**.

2. Después, instale Web Deploy 3.6 para servidores de hospedaje en Windows Server.

    Para instalar Web Deploy para servidores de hospedaje, use el [Instalador de plataforma web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para encontrar el vínculo del instalador de plataforma web desde IIS, seleccione **IIS** en el panel izquierdo del Administrador del servidor. Haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** .)

    En el instalador de plataforma web, encontrará **Web Deploy para servidores de hospedaje** en la pestaña Aplicaciones.

3. Si aún no ha instalado **Herramientas y scripts de administración de IIS**, hágalo ahora.

    Vaya a **Seleccionar roles de servidor** > **Servidor web (IIS)**  > **Herramientas de administración** y después seleccione el rol **Herramientas y scripts de administración de ISS**, haga clic en **Siguiente** y después instale el rol.

    ![Instalar herramientas y scripts de administración de IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Los scripts y herramientas son necesarios para habilitar la generación del archivo de configuración de publicación.

4. (Opcional) Compruebe que Web Deploy se ejecuta correctamente abriendo **Panel de Control > Sistema y seguridad > Herramientas administrativas > Servicios** y asegúrese de que **Servicio del agente de implementación web** se está ejecutando (el nombre del servicio es diferente en las versiones anteriores).

    Si el servicio del agente no se está ejecutando, inícielo. Si no está presente en absoluto, vaya a **Panel de Control > Programas > Desinstalar un programa** y busque **Microsoft Web Deploy \<versión>** . Elija **Cambiar** la instalación y asegúrese de que elige **Se instalará en la unidad de disco duro local** para los componentes de Web Deploy. Complete los pasos de instalación de cambio.