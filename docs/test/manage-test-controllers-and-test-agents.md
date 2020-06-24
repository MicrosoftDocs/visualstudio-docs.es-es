---
title: Administrar controladores de pruebas y agentes de pruebas
ms.date: 09/18/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78bd0143ee2584bcabb5e8ed4946818ee2590789
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286705"
---
# <a name="manage-test-controllers-and-test-agents"></a>Administrar controladores de pruebas y agentes de pruebas

Si desea usar Visual Studio para ejecutar pruebas de forma remota, distribuirlas entre varias máquinas, o ejecutar pruebas de carga, debe configurar un controlador de pruebas, agentes de prueba y el archivo de configuración de pruebas. En este tema se describe cómo administrar controladores de pruebas y agentes de prueba después de instalarlos y configurarlos por primera vez.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Si usa Microsoft Test Manager para ejecutar pruebas en entornos de laboratorio, debe administrar los controladores de pruebas y sus agentes con el **Administrador de Test Controller** del **Centro de laboratorio** de Microsoft Test Manager. La información de este tema solo es válida si se usa Visual Studio para ejecutar las pruebas.
::: moniker-end

Para obtener más información sobre cómo instalar y configurar los agentes de prueba y los controladores de pruebas cuando se ejecutan pruebas en Visual Studio, vea [Configurar controladores y agentes de prueba](../test/configure-test-agents-and-controllers-for-load-tests.md).

Para configurar y supervisar el controlador de pruebas y cualquier agente registrado es necesario tener un archivo de configuración de pruebas en el proyecto de prueba que contenga las pruebas que quiera ejecutar. Abra el archivo de configuración de pruebas, elija **Rol** y **Administrar controladores de pruebas** del menú desplegable del campo **Controlador**.

En un proyecto de prueba de carga también puede elegir **Administrar controladores de pruebas** en el menú **Prueba de carga**.

## <a name="add-a-test-agent-to-a-test-controller"></a>Agregar un agente de prueba a un controlador de pruebas

Quizás desee agregar un agente de prueba a un controlador de pruebas diferente o tenga que agregar un agente de prueba a un controlador de pruebas que acaba de instalar.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Para agregar un agente de prueba a un controlador de pruebas

1. Elija **Inicio** > **Herramienta de configuración de Test Agent**.

     Se muestra el cuadro de diálogo **Configurar agentes de prueba**.

    > [!NOTE]
    > Ya debe tener instalado un agente de prueba para agregarlo a un controlador de pruebas. Para obtener más información sobre cómo instalar un agente de prueba, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

2. Se presentan dos opciones de ejecución para el agente de pruebas:

   - **Servicio**: si no tiene que ejecutar pruebas automatizadas que interactúen con el escritorio, como pruebas automatizadas de IU o grabaciones de vídeo al ejecutar las pruebas, seleccione **Servicio** en **Ejecutar el agente de prueba como**. El agente de prueba se iniciará como un servicio. Seleccione **Siguiente**.

      Ahora puede escribir los detalles sobre el usuario que se va a usar cuando el agente de prueba se inicie como un servicio.

      1. Escriba el nombre en **Nombre de usuario**.

      2. Escriba la contraseña en **Contraseña**.

        |**Información importante sobre cuentas de usuario**|
        |-|
        |-   No se admiten contraseñas nulas para las cuentas de usuario.|
        |-   Si quiere usar el recopilador de IntelliTrace o la emulación de red, la cuenta de usuario debe ser miembro del grupo Administrators.|
        |-   Si el nombre de usuario del agente no está en el servicio del agente, intentará agregarlo, para lo cual se necesitan permisos en el controlador de pruebas.|
        |-   El usuario que está intentando usar el controlador debe estar en la cuenta Usuarios del controlador de pruebas o no podrá ejecutar las pruebas con el controlador.|

   - **Proceso interactivo**: si quiere ejecutar pruebas automatizadas que deban interactuar con el escritorio, como pruebas automatizadas de IU o grabaciones de vídeo al ejecutar pruebas, seleccione **Proceso interactivo**. El agente de prueba se iniciará como un proceso interactivo y no como un servicio.

      En la siguiente página, escriba los detalles del usuario que se va a usar cuando se inicie el agente de prueba como un proceso, además de otras opciones.

      1. Escriba el nombre en **Nombre de usuario**.

      2. Escriba la contraseña en **Contraseña**.

        > [!NOTE]
        > Si configura el agente de prueba para ejecutarse como un proceso interactivo con un usuario diferente que no es el usuario actualmente activo, debe reiniciar el equipo e iniciar sesión como este usuario diferente para poder iniciar el agente. Además, no se admiten contraseñas nulas para las cuentas de usuario. Si desea utilizar el recopilador de IntelliTrace o la emulación de red, la cuenta de usuario debe ser miembro del grupo Administrators.

      3. Para asegurarse de que un equipo con un agente de prueba puede ejecutar pruebas después de su reinicio, configúrelo de modo que inicie sesión automáticamente como usuario del agente de prueba. Seleccione **Iniciar sesión automáticamente**. De este modo, el nombre de usuario y la contraseña se almacenarán cifrados en el Registro.

      4. Para asegurarse de que el protector de pantalla está deshabilitado, ya que podría interferir con las pruebas automatizadas que deben interactuar con el escritorio, seleccione **Comprobar que el protector de pantalla esté deshabilitado**.

        > [!WARNING]
        > Puede poner en peligro la seguridad si inicia sesión automáticamente o deshabilita el protector de pantalla. Si habilita el inicio de sesión automático, otros usuarios podrán iniciar ese equipo y utilizar la cuenta que se usa para el inicio de sesión automático. Si deshabilita el protector de pantalla, es posible que el equipo no pida al usuario que inicie sesión para desbloquearlo. De este modo, cualquier usuario podrá obtener acceso al equipo si tienen acceso físico a él. Si habilita estas características en un equipo, debe asegurarse de que estos equipos están físicamente protegidos. Por ejemplo, estos equipos se encuentran en un laboratorio físicamente protegido. Si desactiva **Comprobar que el protector de pantalla esté deshabilitado**, no se habilitará el protector de pantalla.

3. Para registrar este agente con un controlador de pruebas diferente, seleccione **Registrar con controlador de pruebas**. Escriba el nombre del controlador de pruebas seguido de un signo de dos puntos ( **:** ) y el número de puerto que use en **Registrar el agente de prueba con el siguiente controlador de pruebas**. Por ejemplo, escriba **agent1:6901**.

    > [!NOTE]
    > El número de puerto predeterminado es 6901.

4. Para guardar los cambios, elija **Aplicar configuración**. Cierre el cuadro de diálogo **Resumen de la configuración** y luego la **Herramienta de configuración de Test Agent**.

> [!WARNING]
> Si el agente está actualmente configurado de modo que se ejecute en otro controlador, quite el agente de prueba de ese controlador.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Quitar un agente de prueba de un controlador de pruebas

Para poder quitar un agente de prueba, es necesario que esté sin conexión.

::: moniker range="vs-2017"
> [!NOTE]
> No puede usar este procedimiento para quitar agentes que estén registrados en un controlador como parte de un entorno de laboratorio. Para quitar dichos agentes de un controlador, debe quitar el entorno mediante Microsoft Test Manager.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> No puede usar este procedimiento para quitar agentes que estén registrados en un controlador como parte de un entorno de laboratorio.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Para quitar un agente de prueba de un controlador de pruebas

::: moniker range=">=vs-2019"
En Visual Studio 2019, no se puede quitar un agente de prueba si el controlador de pruebas está registrado con un proyecto.
::: moniker-end
Si el controlador de pruebas no está registrado con un proyecto, siga estos pasos.

1. En Visual Studio, abra el archivo de configuración de pruebas del proyecto de prueba, elija **Rol** y **Administrar controladores de pruebas** del menú desplegable del campo **Controlador**.

   Se mostrará el cuadro de diálogo **Administrar controlador de prueba**.

2. En la lista desplegable **Controlador**, escriba el nombre del equipo donde haya instalado el controlador de pruebas. Si ya ha administrado previamente un controlador concreto, podrá seleccionar su nombre en la lista.

3. En el panel **Agentes**, seleccione el nombre del agente de prueba. Si el agente todavía está en línea, elija **Sin conexión**. Para quitarlo, elija**Quitar**.

   > [!NOTE]
   > Al quitar un agente de prueba, solo queda desasociado del controlador de pruebas. Para desinstalar completamente el agente de prueba, use **Programas y características** en el Panel de control del equipo donde esté instalado el agente de prueba.

::: moniker range="vs-2017"
Si el controlador de pruebas está registrado con un proyecto, quite el agente mediante Microsoft Test Manager.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Cambiar la configuración de un agente de prueba

El agente de prueba puede encontrarse en uno de los siguientes estados:

|Situación|Descripción|
|-|-----------------|
|Ejecutando prueba|Ejecutar pruebas|
|Listo|Disponible para la ejecución de pruebas y para la recopilación de datos y diagnósticos.|
|Sin conexión|No está disponible para la ejecución de pruebas ni para la recopilación de datos y diagnósticos.|
|Desconectado|El agente de prueba no se ha iniciado.|

Para cambiar el estado y otras configuraciones de un agente de prueba, siga los procedimientos que se describen a continuación.

### <a name="to-change-the-settings-of-a-test-agent"></a>Para cambiar la configuración de un agente de prueba

::: moniker range="vs-2017"
> [!NOTE]
> Si el agente de pruebas está registrado con un controlador de pruebas que, a su vez, está registrado con un proyecto, cambie la configuración de Microsoft Test Manager.
::: moniker-end

1. Para configurar y monitorizar los controladores de pruebas y todos los agentes registrados para una prueba de carga, elija el menú **Prueba de carga** en Visual Studio y, luego, elija **Administrar controladores de pruebas**. Para cualquier otra prueba, abra el archivo de configuración de pruebas del proyecto de prueba en Visual Studio, elija **Rol** y **Administrar controladores de pruebas** del menú desplegable del campo **Controlador**.

   Se abre el cuadro de diálogo **Administrar controladores de pruebas**.

1. En la lista de controladores de pruebas, seleccione el nombre del controlador de pruebas cuyos agentes de prueba desee cambiar. Si el controlador de pruebas no aparece en la lista, compruebe si el controlador de prueba se ha registrado correctamente. Para obtener más información, vea el siguiente procedimiento en el que se explica cómo configurar un controlador de pruebas.

1. (Opcional) En el panel **Agentes de prueba**, seleccione el equipo del agente de prueba cuyas propiedades quiera cambiar.

1. Elija **Propiedades**.

1. Cambie las siguientes propiedades de agente de prueba según corresponda:

|Propiedad del agente de prueba|Descripción|
|-|-----------------|
|**Peso**|Sirve para distribuir la carga cuando se utilizan agentes de prueba con diferentes niveles de rendimiento. Por ejemplo, un agente de prueba con un peso de 100 recibe dos veces la carga de un agente de prueba con un peso de 50.|
|**Conmutación de IP**|Sirve para configurar la conmutación de IP. La conmutación de IP permite que un agente de prueba envíe solicitudes a un servidor utilizando un intervalo de direcciones IP. De esta forma se simulan llamadas procedentes de diferentes equipos cliente.<br /><br /> La conmutación de IP es importante si la prueba de carga accede a una granja de servidores web. La mayoría de los equilibradores de carga establecen una afinidad entre un cliente y un servidor web determinado mediante la dirección IP del cliente. Si aparentemente todas las solicitudes proceden del mismo cliente, el equilibrador de carga no equilibrará la carga. Para obtener un buen equilibrio de carga en la granja de servidores web, asegúrese de que las solicitudes procedan de un intervalo de direcciones IP. **Nota:**  Puede especificar un adaptador de red o usar **(Todas sin asignar)** para seleccionar de forma automática una dirección que no esté en uso. <br /><br /> Para poder usar la característica de conmutación de IP, es preciso que el servicio Visual Studio Test Agent se ejecute como usuario del grupo Administradores de ese equipo de agente. Este usuario se selecciona durante la instalación del agente, pero se puede cambiar modificando las propiedades del servicio y reiniciándolo.<br /><br /> Para comprobar que la conmutación de IP funciona correctamente, habilite el registro de IIS en el servidor web y utilice la funcionalidad de registro de IIS para comprobar que las solicitudes proceden de las direcciones IP configuradas.|
|**Atributos**|Conjunto de pares nombre-valor que se pueden utilizar en la selección del agente de prueba. Por ejemplo, una prueba puede requerir un sistema operativo determinado. Puede agregar atributos en la pestaña **Roles** del archivo de configuración de pruebas y se pueden usar para seleccionar un agente que tenga atributos coincidentes. Si quiere ejecutar una prueba en varias máquinas, cree un atributo en el rol de la configuración de pruebas que se configura para ejecutar las pruebas y, después, configure un atributo coincidente en cada agente de prueba que quiera usar en ese rol. **Nota:**  Esta configuración solo está disponible para los agentes de pruebas registrados en un controlador de pruebas que no está registrado en un proyecto, ya que estos atributos se usan únicamente en las configuraciones de pruebas de Visual Studio.|

Los cambios en el peso y los atributos de un agente de prueba entran inmediatamente en vigor, pero no afectan a las pruebas que se están ejecutando. El intervalo de direcciones IP entra en vigor después de reiniciar el controlador de pruebas.

(Opcional) Para cambiar el estado de un agente de prueba, seleccione el agente en la lista y, a continuación, seleccione una acción entre las opciones disponibles en función del estado actual del agente.

> [!NOTE]
> Si el agente de prueba se ejecuta como un proceso, se administra su estado con el icono del área de notificación que se ejecuta en el equipo donde está instalado el agente de prueba. Este icono muestra el estado del agente de prueba. Con esta herramienta se puede iniciar, detener o reiniciar el agente si se está ejecutando como un proceso.

## <a name="configure-a-test-controller"></a>Configurar un controlador de pruebas

Para configurar un controlador de pruebas, use la **Herramienta de configuración de Team Test Controller**. Cuando se configura un controlador de pruebas, se puede registrar con otra colección de proyectos o anular su registro en una colección de proyectos.

Si quiere registrar el controlador de pruebas con la colección de proyectos de Team Foundation Server, la cuenta que use para el servicio del controlador de pruebas debe ser miembro del grupo Test Service Accounts de la colección de proyectos, o bien la cuenta que use para ejecutar la herramienta de configuración del controlador de pruebas debe ser un administrador de la colección de proyectos.

> [!NOTE]
> Si anula el registro de un controlador de pruebas de una colección de proyectos que tiene entornos existentes, los entornos se conservarán si esa colección de proyectos de equipo se mueve y el controlador de pruebas vuelve a registrarse en la colección de proyectos que se ha movido.

### <a name="to-configure-a-test-controller"></a>Para configurar un controlador de pruebas

1. Para ejecutar la herramienta de reconfiguración del controlador de pruebas en cualquier momento, elija **Inicio** > **Herramienta de configuración de Test Controller**.

     Se muestra el cuadro de diálogo **Configurar controlador de pruebas**.

2. Seleccione el usuario que desee usar como cuenta de inicio de sesión para el servicio de controlador de pruebas.

    > [!NOTE]
    > No se admiten contraseñas nulas para las cuentas de usuario.

4. (Opcional) Si no quiere usar el controlador de pruebas con un entorno de laboratorio, sino solamente para ejecutar pruebas desde Visual Studio, desactive **Registrar el controlador de pruebas con colección de proyectos de equipo**.

5. (Opcional) Si quiere configurar el controlador de pruebas para pruebas de carga, seleccione **Configurar el controlador de pruebas para pruebas de carga**. Escriba la instancia de SQL Server en **Crear base de datos de resultados de pruebas de carga en esta instancia de SQL Server**.

> [!NOTE]
> Para obtener más información sobre cómo solucionar problemas de controladores de pruebas, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Administrar los agentes durante la ejecución de las pruebas con un controlador de pruebas

En el momento de agregar roles para la aplicación a la configuración de pruebas de Visual Studio, podrá agregar propiedades de agente para cada uno de los roles. Esto determina qué agentes de prueba están disponibles para este rol. Cuando se ejecutan las pruebas mediante esta configuración de pruebas, el controlador de pruebas seleccionado para la configuración de pruebas determina la disponibilidad de los agentes necesarios. A continuación se describen los casos que se pueden dar cuando se determina la disponibilidad de los agentes:

- No hay ningún agente disponible para el rol que debe ejecutar las pruebas. No se pueden ejecutar las pruebas. Podrá realizar una de las siguientes acciones y, a continuación, ejecutar de nuevo las pruebas:

  - Podrá esperar a que haya un agente disponible para este rol a fin de ejecutar las pruebas.

  - Si hay algún agente sin conexión que se pueda utilizar para este rol, podrá reiniciar el agente de modo que esté disponible.

  - Podrá agregar al controlador de pruebas otro agente con las propiedades correctas para ese rol.

  - Podrá cambiar las propiedades de agente para este rol en la configuración de pruebas para habilitar otros agentes que desee utilizar.

- No hay ningún agente disponible para uno o varios roles que ejecutan los adaptadores de datos de diagnóstico. Se pueden ejecutar las pruebas, pero no se puede ejecutar el adaptador de datos de diagnóstico. Podrá ejecutar las pruebas sin adaptador de datos de diagnóstico o podrá realizar una de las siguientes acciones y ejecutar de nuevo las pruebas:

  - Podrá esperar a que haya un agente disponible para estos roles.

  - Si hay algún agente sin conexión que se pueda usar para este rol, deberá cambiar su estado a En línea desde **Administrar controlador de pruebas** en el menú **Prueba**. Además, es posible que tenga que reiniciar el agente si ha estado desconectado del controlador.

  - Compruebe que los agentes que necesite para esta ejecución de pruebas no estén ejecutando pruebas. Podrá comprobar el estado de cualquier agente desde **Administrar controlador de pruebas** en el menú **Prueba**.

  - Podrá agregar al controlador de pruebas otro agente con las propiedades correctas para el rol.

  - Podrá cambiar las propiedades de agente para el rol en la configuración de pruebas para habilitar otros agentes que desee utilizar.

## <a name="load-tests-from-delay-signed-assemblies"></a>Cargar pruebas de ensamblados con firma retardada

El controlador de pruebas y los agentes de prueba solo pueden cargar ensamblados de prueba con firma segura o sin firma. Algunos ensamblados de prueba tienen firma retrasada porque deben tener acceso a los ensamblados de producción de la aplicación. Sin embargo, estos ensamblados no tienen firma segura porque son solo ensamblados de prueba y no se distribuyen. Estos ensamblados no se pueden cargar porque tienen firma retrasada, de modo que debe deshabilitar la comprobación de nombre seguro para esos ensamblados en todas las máquinas en las que se va a cargar el ensamblado, incluso en la máquina del controlador de pruebas. Para deshabilitar la comprobación de la firma retardada, use *sn.exe*. También puede que deba incluir el token de clave pública del ensamblado con firma retrasada para el que se pide que se omita la comprobación de nombre seguro.

Use *Sn.exe* (herramienta de nombre seguro) para deshabilitar la comprobación de la firma retardada.

De esta manera se deshabilita la comprobación del nombre seguro, sólo para el ensamblado especificado, en el equipo en el que se ejecuta el comando. Este procedimiento sólo es posible si posee los permisos necesarios.

Una vez que se haya completado la serie de pruebas, vuelva a habilitar la comprobación de la firma retardada con el comando *SN.exe*.

Un método recomendado para deshabilitar y volver a habilitar la comprobación de la firma es usar el comando *SN.exe* en los scripts. Puede deshabilitar la comprobación en un script de instalación y volver a habilitarla en un script de limpieza.

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
