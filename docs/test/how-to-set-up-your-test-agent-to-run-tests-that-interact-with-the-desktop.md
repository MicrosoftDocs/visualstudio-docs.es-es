---
title: Configuración de un agente de pruebas
ms.date: 09/18/2018
ms.topic: how-to
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 994d5da8af7b00ab8af55681d4a67e9681ebbde6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287537"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Procedimiento Configurar el agente de pruebas para ejecutar pruebas que interactúen con el escritorio

::: moniker range="vs-2017"
Si desea ejecutar pruebas automatizadas que interactúen con el escritorio, debe configurar el agente para que se ejecute como un proceso y no como un servicio. Por ejemplo, si desea ejecutar de forma remota una prueba de IU codificada usando un controlador de pruebas y un agente de prueba o si desea ejecutar una prueba y capturar una grabación de vídeo durante la ejecución, debe configurar el agente para que se ejecute como un proceso. Al asignar agentes a roles en la configuración de pruebas mediante Visual Studio o al asignar agentes a roles en el entorno mediante Microsoft Test Manager, debe cambiar la configuración de los agentes asignados a los roles que tengan que interactuar con el escritorio.
::: moniker-end
::: moniker range=">=vs-2019"
Si desea ejecutar pruebas automatizadas que interactúen con el escritorio, debe configurar el agente para que se ejecute como un proceso y no como un servicio. Por ejemplo, si desea ejecutar de forma remota una prueba de IU codificada usando un controlador de pruebas y un agente de prueba o si desea ejecutar una prueba y capturar una grabación de vídeo durante la ejecución, debe configurar el agente para que se ejecute como un proceso. Al asignar agentes a roles en la configuración de pruebas mediante Visual Studio, debe cambiar la configuración de los agentes asignados a los roles que tengan que interactuar con el escritorio.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Si usa Microsoft Test Manager para configurar un entorno de laboratorio, instala al agente de pruebas. En el **asistente para creación de entornos**, puede especificar que quiere configurar uno de los roles para ejecutar pruebas automatizadas de IU.
:::moniker-end

> [!IMPORTANT]
> El equipo donde se ejecuta un agente en el que desea ejecutar pruebas de IU codificadas no puede estar bloqueado ni puede tener activado un protector de pantalla.

Si ejecuta pruebas de IU codificadas que inician un explorador, se usa la cuenta de servicio del agente de prueba para iniciar ese explorador. Esta cuenta de servicio debe ser igual que la cuenta de usuario que actúa como usuario activo en este equipo. Si no es la misma cuenta de usuario, el explorador no se iniciará.

> [!IMPORTANT]
> Si ejecuta una prueba de IU codificada que inicia un explorador como parte de una definición de compilación, se usa la cuenta del servicio de compilación para iniciar ese explorador. Esta cuenta de servicio debe ser igual que la cuenta de usuario que actúa como usuario activo en este equipo. Si no es la misma cuenta de usuario, el explorador no se iniciará.

Siga el procedimiento que se describe a continuación para configurar los agentes asignados a un rol que realiza una tarea que requiere la interactuación con el escritorio.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Para configurar un agente de modo que se ejecute como un proceso

1. Para configurar el agente de pruebas que tiene instalado para ejecutarlo como proceso, vaya a **Inicio** > **Herramienta de configuración de Test Agent**.

   Se muestra el cuadro de diálogo **Configurar agentes de prueba**.

   ![Configuración de Test Agent para Visual Studio](media/configure-test-agent.png)

2. Seleccione **Proceso interactivo**. El agente de prueba se iniciará como un proceso y no como un servicio. Seleccione **Siguiente**.

3. Escriba el nombre de usuario y la contraseña del usuario que ejecutará el proceso del agente de prueba.

   > [!NOTE]
   > - El usuario que se agrega para iniciar el proceso también debe agregarse como un miembro del grupo TeamTestAgentService en el equipo donde está instalado el controlador de pruebas para este agente. Si este usuario es el usuario actual, al agregarlo al equipo donde está instalado el controlador de pruebas, se debe cerrar la sesión o reiniciar el equipo.
   > - No se admiten contraseñas nulas para las cuentas de usuario.
   > - Si desea usar IntelliTrace o el adaptador de diagnóstico y datos de emulación de red, la cuenta de usuario debe ser miembro del grupo Administrators. Si el equipo que está ejecutando el agente de pruebas usa un SO que tenga Cuenta de usuario con privilegios mínimos, también tiene que ejecutarlo como administrador (elevado). Si el nombre de usuario del agente no está en el servicio del agente, intentará agregarlo, para lo cual se necesitan permisos en el controlador de pruebas.
   > - El usuario que va a usar el controlador de pruebas debe estar en la cuenta Usuarios del controlador o no podrá ejecutar las pruebas.

4. Para asegurarse de que un equipo con un agente de pruebas puede ejecutar pruebas después de su reinicio, podrá configurarlo de modo que inicie sesión automáticamente como usuario del agente de prueba. Seleccione **Iniciar sesión automáticamente**. De este modo, el nombre de usuario y la contraseña se almacenarán cifrados en el Registro.

   > [!NOTE]
   > Si está conectado al entorno de laboratorio mediante el escritorio remoto o usa una conexión de invitado, podría experimentar desconexiones inesperadas con frecuencia. Una posible causa de la pérdida de conexión es que la máquina esté configurada para iniciar sesión automáticamente en la red.

5. Para asegurarse de que el protector de pantalla está deshabilitado, ya que podría interferir con las pruebas automatizadas que deben interactuar con el escritorio, seleccione **Comprobar que el protector de pantalla esté deshabilitado**.

   > [!WARNING]
   > Puede poner en peligro la seguridad si inicia sesión automáticamente o deshabilita el protector de pantalla. Si habilita el inicio de sesión automático, otros usuarios podrán iniciar ese equipo y utilizar la cuenta que se usa para el inicio de sesión automático. Si deshabilita el protector de pantalla, es posible que el equipo no pida al usuario que inicie sesión para desbloquearlo. De este modo, cualquier usuario podrá obtener acceso al equipo si tienen acceso físico a dicho equipo. Si habilita estas características en un equipo, debe asegurarse de que estos equipos están físicamente protegidos. Por ejemplo, estos equipos se encuentran en un laboratorio físicamente protegido. Si desactiva **Comprobar que el protector de pantalla esté deshabilitado**, no se habilita el protector de pantalla.

   Para volver a cambiar el agente de modo que se ejecute como un servicio, puede usar esta herramienta y seleccionar **Servicio**.

6. Para aplicar los cambios, elija **Aplicar configuración**.

   Se abre el cuadro de diálogo **Resumen de la configuración**, en el que se muestra el estado de cada uno de los pasos necesarios para configurar el agente de pruebas.

7. Para cerrar el cuadro de diálogo **Resumen de la configuración**, elija **Cerrar**. Después, elija **Cerrar** de nuevo para cerrar la **Herramienta de configuración de Test Agent**.

   > [!NOTE]
   > Hay un icono de área de notificación que se ejecuta en el equipo para un agente de prueba que se ejecuta como un proceso. Este icono muestra el estado del agente de prueba. Con esta herramienta se puede iniciar, detener o reiniciar el agente si se está ejecutando como un proceso. Para iniciar el agente de pruebas como proceso si no está en ejecución, elija **Inicio** > **Visual Studio** > **Microsoft Visual Studio Test Agent**.

   ::: moniker range="vs-2017"
   Si el controlador de este agente de pruebas se registra con Team Foundation Server, el estado de un agente que se está ejecutando como un proceso interactivo se muestra en la vista **Controladores** del **Centro de laboratorio** de Microsoft Test Manager. Se muestra precedido de un símbolo de asterisco para denotar que se ejecuta como un proceso interactivo. Para reiniciar este agente de pruebas, debe usar la herramienta que se ejecuta en el equipo del agente de pruebas y no la vista **Controladores**.
   ::: moniker-end

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
