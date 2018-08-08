---
title: Configuración de la emulación de red mediante la configuración de pruebas en Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a4639e59b8c8847a4368a0f3841fa271a302e7ca
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380849"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Cómo: Configurar la emulación de red mediante la configuración de pruebas en Visual Studio

Puede configurar el adaptador de datos de diagnóstico para probar la aplicación en varios entornos de red desde Visual Studio. También puede configurarlo para probar una carga de red artificial, o cuello de botella, durante la ejecución de las pruebas.

> [!WARNING]
> Si ejecuta las pruebas en una red real que es más lenta que la red objeto de la emulación, la prueba se ejecutará a la velocidad de la red más lenta. La emulación solo puede reducir y no aumentar la velocidad del entorno de red.

 En el siguiente procedimiento se describe cómo configurar la emulación de red en el editor de configuración. Estos pasos se aplican al editor de configuración de Microsoft Test Manager y Visual Studio.

> [!NOTE]
> El adaptador de datos de diagnóstico de emulación de red solo se aplica a la configuración de pruebas de Visual Studio. No se usa para la configuración de pruebas en Microsoft Test Manager.

Para la emulación de red, debe usarse una cuenta que tiene privilegios de administrador. Si ha seleccionado la emulación de red para un rol local que ejecuta pruebas manuales, debe iniciar Microsoft Test Manager con privilegios de administrador. Si ha seleccionado la emulación de red para cualquier otro rol, debe comprobar que el agente de prueba de la máquina de ese rol usa una cuenta de usuario que es miembro del grupo de administradores. Para obtener más información sobre cómo configurar la cuenta del agente de pruebas, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> La cuenta Network Service, que es la cuenta predeterminada del agente de prueba, no es miembro del grupo de administradores.

 **Emulación de red verdadera**

 Visual Studio usa la emulación de red auténtica basada en software para todos los tipos de prueba. Esto incluye las pruebas de carga. La emulación de red verdadera simula las condiciones de la red por manipulación directa de los paquetes de red. El emulador de red verdadera puede emular el comportamiento de las redes cableadas e inalámbricas utilizando un vínculo físico confiable, como Ethernet. En la emulación de red verdadera se incorporan los siguientes atributos de red:

-   Tiempo de ida y vuelta por la red (latencia)

-   Cantidad de ancho de banda disponible

-   Comportamiento de puesta en cola

-   Pérdida de paquetes

-   Reordenación de paquetes

-   Propagaciones de errores.

 La emulación de red verdadera también proporciona flexibilidad en el filtrado de paquetes de red en función de las direcciones IP o de protocolos como TCP, UDP e ICMP.

 Los desarrolladores y evaluadores basados en red pueden utilizar la emulación de red verdadera para emular un entorno de pruebas deseado, evaluar el rendimiento, predecir el efecto de un cambio o tomar decisiones sobre la optimización de la tecnología. Cuando se compara con las bases de prueba de hardware, la emulación de red verdadera es una solución mucho más barata y flexible.

## <a name="configure-network-emulation-for-your-test-settings"></a>Configurar la emulación de red para la configuración de pruebas
 Antes de seguir los pasos de este procedimiento, debe abrir la configuración de pruebas en Visual Studio y seleccionar la página **Datos y diagnósticos**.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Para configurar la emulación de red para la configuración de pruebas

1.  Seleccione el rol que se va a usar para emular una red concreta.

    > [!NOTE]
    > Solo tiene que configurar el adaptador de Emulación de red en el rol del cliente o el rol de servidor. No tiene que utilizar el adaptador en ambos roles. El adaptador emula ruido de la red que afecta a la comunicación entre ambos roles, para que no tenga que utilizarlo en ambos. A menos que sea necesario, debería elegir un rol de cliente para que el adaptador de Emulación de red evite la sobrecarga adicional en el rol de servidor.

2.  Seleccione **Emulación de red** y, luego, elija **Configurar**.

     Se abrirá el cuadro de diálogo para configurar la emulación de red.

3.  Elija la flecha situada junto a **Seleccione el perfil de red que desea usar** y seleccione el tipo de red que quiere emular durante la ejecución de una prueba (por ejemplo, **Cable-DSL de 768 Kbps**).

    > [!WARNING]
    > Si ejecuta las pruebas en una red real que es más lenta que la red objeto de la emulación, la prueba se ejecutará a la velocidad de la red más lenta. La emulación solo puede reducir y no aumentar la velocidad del entorno de red.

4.  Si incluye el adaptador de datos de diagnóstico de emulación de red en la configuración de pruebas y piensa usarlo en la máquina local, debe enlazar también el controlador de emulación de red a uno de los adaptadores de red de su máquina. El controlador de emulación de red es necesario para que el adaptador de datos de diagnóstico de emulación de red funcione. El controlador de emulación de red se instala y enlaza al adaptador de dos maneras:

    -   **Controlador de emulación de red instalado con Microsoft Visual Studio Test Agent:** Microsoft Visual Studio Test Agent se puede usar tanto en equipos remotos como en el equipo local. Cuando se instala Visual Studio Test Agent, el proceso de instalación incluye un paso de configuración que enlaza el controlador de emulación de red a su tarjeta de red. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

    -   **Controlador de emulación de red instalado con Microsoft Visual Studio Test Professional:** la primera vez que se usa la emulación de red, se le pide que enlace el controlador de emulación de red a una tarjeta de red.

    > [!TIP]
    > También puede instalar el controlador de emulación de red desde la línea de comandos en el equipo local sin instalar Visual Studio Test Agent con el siguiente comando: **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Vea también

- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Ejecutar pruebas manuales (VSTS)](/vsts/manual-test/getting-started/run-manual-tests)