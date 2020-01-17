---
title: Recopilar información de diagnóstico con la configuración de pruebas
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bf82ee72d4398095f25de2493c28c5155456b55
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588868"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Recopilar información de diagnóstico con la configuración de pruebas

Puede usar la *configuración de pruebas* de Visual Studio para recopilar datos adicionales al ejecutar las pruebas. Por ejemplo, quizás desee crear una grabación de vídeo al ejecutar la prueba. Hay adaptadores de datos de diagnóstico para:

- Recopilar cada paso de acción de la interfaz de usuario en formato de texto

- Grabar cada acción de la interfaz de usuario para reproducirla

- Recopilar información del sistema

- Recopilar datos de registro de eventos

- Recopilar datos de IntelliTrace para ayudar a aislar errores no reproducibles

Los adaptadores de datos de diagnóstico también pueden usarse para cambiar el comportamiento de una máquina de prueba. Por ejemplo, con una configuración de pruebas en Visual Studio, puede emular diferentes cuellos de botella de la topología de red para evaluar el rendimiento de la aplicación de su equipo.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Usar la configuración de pruebas con Visual Studio

Puede agregar, configurar y seleccionar la configuración de pruebas que se usará para ejecutar pruebas unitarias, de IU codificada, rendimiento web o carga mediante Visual Studio. Para ejecutar las pruebas, recopilar datos o afectar a una máquina de prueba de forma remota, debe especificar el controlador de pruebas que se usará en la configuración de pruebas. El controlador de pruebas tendrá agentes que se pueden usar para cada rol en la configuración de pruebas.

## <a name="diagnostic-data-adapter-details"></a>Detalles de adaptador de datos de diagnóstico

En la tabla siguiente se proporciona información general sobre las diferentes maneras de configurar los adaptadores de datos de diagnóstico para usarlos con roles de máquinas locales o remotas.

|Adaptador de datos de diagnóstico usado en la configuración de pruebas|Pruebas manuales en una máquina local|Pruebas automatizadas|Pruebas manuales: recopilación de datos mediante un conjunto de roles y un entorno|Notas|
|-|-|-|-|-|
|**Proxy de cliente ASP.NET para IntelliTrace e Impacto en las pruebas:** Este proxy permite recopilar información sobre las llamadas HTTP de un cliente a un servidor web para los adaptadores de datos de diagnóstico de IntelliTrace y de impacto en las pruebas.|Sí|Sí|Sí|- Úselo solo cuando se seleccionen los adaptadores de datos de diagnóstico de IntelliTrace o Impacto en las pruebas para un rol de cliente.|
|**Generador de perfiles ASP.NET:** puede crear una configuración de pruebas que incluya la generación de perfiles de ASP.NET, que recopila datos de rendimiento en aplicaciones web ASP.NET.|No|Sí (vea las Notas)|No|- Este adaptador de datos de diagnóstico solo se admite cuando se ejecutan pruebas de carga en Visual Studio.|
|**Cobertura de código:** puede crear una configuración de pruebas que incluya la información de cobertura de código que se usa para investigar la cantidad de código que abarcan las pruebas.|No|Sí (vea las Notas)|No|- Solo puede usar la cobertura de código cuando ejecute una prueba automatizada de Visual Studio o *mstest.exe*, y únicamente desde el equipo que ejecuta la prueba. No se admite la recopilación remota.<br />- La recopilación de datos de cobertura de código no funciona si la configuración de pruebas también está configurada para recopilar información de IntelliTrace. **Nota:**  Este adaptador de datos de diagnóstico únicamente es aplicable a las configuraciones de pruebas de Visual Studio. No se usa para la configuración de pruebas en Microsoft Test Manager. Además, este adaptador aporta compatibilidad con los proyectos de prueba de Visual Studio 2010. **Nota:**  Por motivos de compatibilidad, la cobertura de código se aplica cuando las pruebas automatizadas se ejecutan desde Microsoft Test Manager o en un agente de prueba remoto desde Visual Studio con el ejecutor MSTest heredado.|
|**Registro de eventos:** Puede definir una configuración de pruebas para que incluya la recopilación de los registros de eventos, que se incluye en los resultados de las pruebas.|Sí|Sí|Sí||
|**IntelliTrace:** Puede configurar el adaptador de datos de diagnóstico de *IntelliTrace* para que recopile información específica de seguimiento de diagnóstico que ayude a aislar errores que no se reproducen con facilidad. Se crea un archivo de IntelliTrace que contiene esta información. Un archivo de IntelliTrace tiene la extensión *.iTrace*. Cuando una prueba no se ejecuta correctamente, se puede crear un error. El archivo de IntelliTrace que se guarda junto con los resultados de pruebas se vincula automáticamente a este error. Los datos que se recopilan en el archivo de IntelliTrace aumentan la productividad de la depuración porque reducen el tiempo necesario para reproducir y diagnosticar un error en el código. Desde este archivo de IntelliTrace se puede simular la sesión local en otro equipo. Esto reduce el riesgo de que un error no sea reproducible.|Sí|Sí|Sí|- Si habilita la recopilación de datos de IntelliTrace, no funciona la recopilación de datos de cobertura de código.<br />- Si usa IntelliTrace para un rol de cliente web, también debe seleccionar el proxy de cliente ASP.NET para el adaptador de datos de diagnóstico de IntelliTrace e Impacto en las pruebas.<br />-   Solo se admiten las siguientes versiones de IIS: IIS 7.0, IIS 7.5 e IIS 8.0.|
|**Emulación de red:** puede especificar que quiere colocar una carga de red artificial en la prueba mediante una configuración de pruebas. La emulación de la red afecta a la comunicación hacia y desde el equipo, emulando una velocidad de conexión de red determinada, como la conexión de acceso telefónico. |No|Sí (vea las Notas)|No|Puede usar el adaptador de datos de diagnóstico de emulación de red para un rol de cliente o de servidor. No es necesario usar el adaptador en ambos roles que se comunican entre sí. **Nota:**  Este adaptador de datos de diagnóstico únicamente es aplicable a las configuraciones de pruebas de Visual Studio. No se usa para la configuración de pruebas en Microsoft Test Manager. **Nota:**  La emulación de la red no se puede usar para aumentar la velocidad de conexión de la red. **Advertencia:**  Si incluye el adaptador de datos de diagnóstico de emulación de red en la configuración de pruebas y piensa usarlo en la máquina local, debe enlazar también el controlador de emulación de red a uno de los adaptadores de red de su máquina. El controlador de emulación de red es necesario para que el adaptador de datos de diagnóstico de emulación de red funcione. El controlador de emulación de red se instala y enlaza al adaptador de dos maneras: <ul><li>**Controlador de emulación de red instalado con Microsoft Visual Studio Test Agent:** Visual Studio Test Agent se puede usar tanto en equipos remotos como en equipos locales. Cuando se instala Visual Studio Test Agent, el proceso de instalación incluye un paso de configuración que enlaza el controlador de emulación de red a su tarjeta de red. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).</li><li>**Controlador de emulación de red instalado con Microsoft Visual Studio Test Professional:** la primera vez que use la emulación de red, se le pedirá que enlace el controlador de emulación de red a una tarjeta de red.</li></ul> También puede instalar el controlador de emulación de red desde la línea de comandos en la máquina local sin instalar el agente de prueba de Visual Studio usando el siguiente comando: **VSTestConfig NETWORKEMULATION /install** **Advertencia:**  Las pruebas de carga omiten el adaptador Emulación de red. En su lugar, las pruebas de carga usan la configuración especificada en la combinación de redes del escenario de prueba de carga.|
|**Información del sistema:** se puede definir una configuración de pruebas que incluya la información del sistema sobre el equipo donde se ejecuta la prueba.|Sí|Sí|Sí||
|**Impacto en las pruebas:** puede recopilar información sobre los métodos de código de aplicaciones que se usaron al ejecutar un caso de prueba. Dicha información se puede usar junto con los cambios realizados por los desarrolladores en el código de la aplicación para determinar qué pruebas resultaron afectadas por esos cambios de desarrollo.|Sí|Sí|Sí|- Si está recopilando datos de impacto en las pruebas para un rol de cliente web, también debe seleccionar el proxy de cliente ASP.NET para el adaptador de datos de diagnóstico de IntelliTrace e Impacto en las pruebas.<br />-   Solo se admiten las siguientes versiones de IIS: IIS 7.0, IIS 7.5 e IIS 8.0.|
|**Grabadora de vídeo:** puede crear una grabación de vídeo de la sesión de escritorio durante la ejecución de una prueba. El vídeo puede ayudar a otros miembros del equipo a aislar problemas de la aplicación que son difíciles de reproducir.|Sí|Sí (vea las Notas)|Sí|- Si habilita el software del agente de pruebas para que se ejecute como un proceso en lugar de como un servicio, puede crear una grabación de vídeo durante la ejecución de las pruebas automatizadas.|
