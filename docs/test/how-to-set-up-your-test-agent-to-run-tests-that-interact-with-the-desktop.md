---
title: Configuración de un agente de pruebas de Visual Studio para ejecutar pruebas que interactúen con el escritorio
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d1b6655dd493a2ac62ba333f3858b299ee398f8d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974811"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Cómo: Configurar el agente de pruebas para ejecutar pruebas que interactúen con el escritorio

Si desea ejecutar pruebas automatizadas que interactúen con el escritorio, debe configurar el agente para que se ejecute como un proceso y no como un servicio. Por ejemplo, si desea ejecutar de forma remota una prueba de IU codificada usando un controlador de pruebas y un agente de prueba o si desea ejecutar una prueba y capturar una grabación de vídeo durante la ejecución, debe configurar el agente para que se ejecute como un proceso. Al asignar agentes a roles en la configuración de pruebas mediante Visual Studio o al asignar agentes a roles en el entorno mediante Microsoft Test Manager, debe cambiar la configuración de los agentes asignados a los roles que tengan que interactuar con el escritorio.

> [!WARNING]
> Si usa Microsoft Test Manager para configurar un entorno de laboratorio, instala al agente de pruebas. En el asistente para creación de entornos, puede especificar que desea configurar uno de los roles para ejecutar pruebas de IU codificada.

> [!IMPORTANT]
> El equipo donde se ejecuta un agente en el que desea ejecutar pruebas de IU codificadas no puede estar bloqueado ni puede tener activado un protector de pantalla.

Si ejecuta pruebas de IU codificadas que inician un explorador, se usa la cuenta de servicio del agente de prueba para iniciar ese explorador. Esta cuenta de servicio debe ser igual que la cuenta de usuario que actúa como usuario activo en este equipo. Si no es la misma cuenta de usuario, el explorador no se iniciará.

> [!IMPORTANT]
> Si ejecuta una prueba de IU codificada que inicia un explorador como parte de una definición de compilación, se usa la cuenta del servicio de compilación para iniciar ese explorador. Esta cuenta de servicio debe ser igual que la cuenta de usuario que actúa como usuario activo en este equipo. Si no es la misma cuenta de usuario, el explorador no se iniciará.

 Siga el procedimiento que se describe a continuación para configurar los agentes asignados a un rol que realiza una tarea que requiere la interactuación con el escritorio.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Para configurar un agente de modo que se ejecute como un proceso

1.  Para configurar el agente de pruebas que ha instalado para ejecutarse como un proceso, vaya a **Inicio**, **Todos los programas**, **Microsoft Visual Studio**, **Herramienta de configuración de Microsoft Visual Studio Test Agent**.

     Se muestra el cuadro de diálogo **Configurar agentes de prueba**.

2.  Para ver la página que permite especificar que el agente se ha de ejecutar como proceso, elija **Opciones de ejecución**.

     Se mostrará la página que permite especificar que el agente se ejecute como un proceso o un servicio.

3.  Seleccione **Proceso interactivo**. El agente de prueba se iniciará como un proceso y no como un servicio. Seleccione **Siguiente**.

     Ahora, puede escribir los detalles del usuario que se va a usar cuando se inicie el agente de prueba como un proceso, además de otras opciones.

    > [!NOTE]
    > El usuario que se agrega para iniciar el proceso también debe agregarse como un miembro del grupo TeamTestAgentService en el equipo donde está instalado el controlador de pruebas para este agente. Si este usuario es el usuario actual, al agregarlo al equipo donde está instalado el controlador de pruebas, se debe cerrar la sesión o reiniciar este equipo.

4.  Escriba el nombre en **Nombre de usuario**.

5.  Escriba la contraseña en **Contraseña**.

     **Información importante sobre cuentas de usuario:**

    -   No se admiten contraseñas nulas para las cuentas de usuario.

    -   Si desea usar IntelliTrace o el adaptador de diagnóstico y datos de emulación de red, la cuenta de usuario debe ser miembro del grupo Administrators. Si el equipo que está ejecutando el agente de pruebas usa un SO que tenga Cuenta de usuario con privilegios mínimos, también tiene que ejecutarlo como administrador (elevado). Si el nombre de usuario del agente no está en el servicio del agente, intentará agregarlo, para lo cual se necesitan permisos en el controlador de pruebas.

    -   El usuario que va a usar el controlador de pruebas debe estar en la cuenta Usuarios del controlador o no podrá ejecutar las pruebas.

6.  Para asegurarse de que un equipo con un agente de prueba puede ejecutar pruebas después de su reinicio, podrá configurarlo de modo que inicie sesión automáticamente como usuario del agente de prueba. Seleccione **Iniciar sesión automáticamente**. De este modo, el nombre de usuario y la contraseña se almacenarán cifrados en el Registro.

    > [!NOTE]
    > Si está conectado al entorno de laboratorio mediante el escritorio remoto o usa una conexión de invitado, podría experimentar desconexiones inesperadas con frecuencia. Una posible causa de la pérdida de conexión es que la máquina esté configurada para iniciar sesión automáticamente en la red.

7.  Para asegurarse de que el protector de pantalla está deshabilitado, ya que podría interferir con las pruebas automatizadas que deben interactuar con el escritorio, seleccione **Comprobar que el protector de pantalla esté deshabilitado**.

    > [!WARNING]
    > Puede poner en peligro la seguridad si inicia sesión automáticamente o deshabilita el protector de pantalla. Si habilita el inicio de sesión automático, otros usuarios podrán iniciar ese equipo y utilizar la cuenta que se usa para el inicio de sesión automático. Si deshabilita el protector de pantalla, es posible que el equipo no pida al usuario que inicie sesión para desbloquearlo. De este modo, cualquier usuario podrá obtener acceso al equipo si tienen acceso físico a dicho equipo. Si habilita estas características en un equipo, debe asegurarse de que estos equipos están físicamente protegidos. Por ejemplo, estos equipos se encuentran en un laboratorio físicamente protegido. Si desactiva **Comprobar que el protector de pantalla esté deshabilitado**, no se habilita el protector de pantalla.

     Para volver a cambiar el agente de modo que se ejecute como un servicio, puede usar esta herramienta y seleccionar **Servicio**.

8.  Para aplicar los cambios, elija **Aplicar configuración**.

     Se abre el cuadro de diálogo **Resumen de la configuración**, en el que se muestra el estado de cada uno de los pasos necesarios para configurar el agente de pruebas.

9. Para cerrar el cuadro de diálogo **Resumen de la configuración**, elija **Cerrar**. Después, elija **Cerrar** de nuevo para cerrar la Herramienta de configuración de Test Agent.

    > [!NOTE]
    > Hay un icono de área de notificación que se ejecuta en el equipo para un agente de prueba que se ejecuta como un proceso. Este icono muestra el estado del agente de prueba. Con esta herramienta se puede iniciar, detener o reiniciar el agente si se está ejecutando como un proceso. Para iniciar el agente de pruebas como proceso si no se está ejecutando, elija **Inicio**, **Todos los programas**, **Microsoft Visual Studio**, **Microsoft Visual Studio Test Agent**.

     Si el controlador de este agente de pruebas se registra con Team Foundation Server, el estado de un agente que se está ejecutando como un proceso interactivo se muestra en la vista **Controladores** del **Centro de laboratorio** de Microsoft Test Manager. Se muestra precedido de un símbolo de asterisco para denotar que se ejecuta como un proceso interactivo. Para reiniciar este agente de pruebas, debe usar la herramienta que se ejecuta en el equipo del agente de pruebas y no la vista **Controladores**.

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)