---
title: Configurar agentes y controladores de pruebas para pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 388be0aa6b1d9bad7ec90620bd025530b3d0e00d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="configure-test-agents-and-test-controllers-for-running-load-tests"></a>Configurar agentes y controladores de pruebas para ejecutar pruebas de carga

Visual Studio puede generar cargas simuladas para una aplicación mediante máquinas virtuales o físicas. Dichas máquinas deben configurarse como un único controlador de pruebas y uno o varios agentes de prueba. Puede usar el controlador de pruebas y los agentes de prueba para generar más carga de la que un único equipo puede generar por sí solo.

> [!NOTE]
> También puede usar pruebas de carga basadas en la nube para proporcionar máquinas virtuales que generen la carga de muchos usuarios que acceden al sitio web al mismo tiempo. Obtenga más información sobre las pruebas de carga basadas en la nube en [Run load tests using VSTS](/vsts/load-test/get-started-simple-cloud-load-test) (Ejecutar pruebas de carga mediante VSTS).

## <a name="load-simulation-architecture"></a>Arquitectura de simulación de carga

La arquitectura de simulación de carga está compuesta por un cliente de Visual Studio, un controlador de pruebas y agentes de prueba.

-   El cliente se utiliza para desarrollar pruebas, ejecutarlas y ver los resultados.

-   El controlador de pruebas se utiliza para administrar los agentes de prueba y recopilar los resultados de pruebas.

-   Los agentes de prueba se utilizan para ejecutar las pruebas y recopilar datos, que incluyen información del sistema y datos de generación de perfiles de ASP.NET definidos en la configuración de pruebas.

Esta arquitectura proporciona las siguientes ventajas:

-   La capacidad de ampliar la generación de carga agregando agentes de prueba adicionales a un controlador de pruebas.

-   Flexibilidad para instalar el software del cliente, del controlador de pruebas y de los agentes de prueba en el mismo equipo o en equipos distintos. Por ejemplo:

     **Configuración local:**

    -   Máquina1: Visual Studio, controlador, agente.

     ![Equipo local que usa controlador y agente](./media/load-test-configa.png)

     **Configuración remota típica:**

    -   Máquina1 y 2: Visual Studio (varios evaluadores pueden utilizar el mismo controlador).

    -   Máquina3: controlador (puede tener también agentes instalados).

    -   Máquina4-n: agente o agentes asociados al controlador en Máquina3.

     ![Equipo remoto que usa controlador y agentes](./media/load-test-configb.png)

Aunque un controlador de pruebas normalmente administra varios agentes de prueba, un agente solo puede estar asociado a un único controlador. Un equipo de desarrolladores puede compartir cada uno de los agentes de prueba. Esta arquitectura permite aumentar el número de agentes de prueba con facilidad, lo que permite generar cargas mayores.

## <a name="test-agent-and-test-controller-interaction"></a>Interacción entre el agente de prueba y el controlador de pruebas

El controlador de pruebas administra un conjunto de agentes de prueba para ejecutar las pruebas. El controlador se comunica con los agentes para iniciar las pruebas, detenerlas, realizar un seguimiento del estado de los agentes y recopilar los resultados de pruebas.

### <a name="test-controller"></a>Test Controller

El controlador de pruebas proporciona una arquitectura general para ejecutar las pruebas e incluye características especiales para ejecutar las pruebas de carga. Envía la prueba de carga a todos los agentes de prueba y espera a que todos ellos hayan inicializado la prueba. Cuando todos los agentes de prueba están listos, el controlador de pruebas envía un mensaje a los agentes para iniciar la prueba.

### <a name="test-agent"></a>Test Agent

El agente de prueba se ejecuta como un servicio que realiza escuchas de solicitudes del controlador de pruebas para iniciar una nueva prueba. Cuando el agente de prueba recibe una solicitud, el servicio del agente de prueba inicia un proceso en el que se ejecutan las pruebas. Todos los agentes de prueba ejecutan la misma prueba de carga.

 El administrador asigna un peso a los agentes de prueba y la carga se distribuye según el peso de cada uno de ellos. Por ejemplo, si el agente de prueba 1 tiene un peso de 30, el agente de prueba 2 tiene un peso de 70 y la carga se establece en 1000 usuarios, entonces el agente 1 simulará 300 usuarios virtuales, mientras que el agente 2 simulará 700 usuarios virtuales. Vea [Administrar controladores de pruebas y agentes de pruebas con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

 El agente de prueba toma como entrada un conjunto de pruebas y un conjunto de parámetros de simulación. Un concepto clave es que las pruebas son independientes del equipo donde se ejecutan.

## <a name="test-controller-and-test-agent-connection-points"></a>Puntos de conexión del controlador y el agente de prueba

La siguiente ilustración muestra los puntos de conexión entre el controlador de prueba, el agente de prueba y el cliente. Describe qué puertos se usan para las conexiones entrantes y salientes, así como las restricciones de seguridad empleadas en estos puertos.

 ![Puertos de controlador de pruebas y agente de prueba y seguridad](./media/test-controller-agent-firewall.png)

 Para obtener más información, vea [Configurar los puertos para los controladores de prueba y los agentes de prueba](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Información de instalación del controlador y el agente de pruebas

Para obtener información importante sobre los requisitos de hardware y software de los controladores y los agentes de pruebas, los procedimientos para instalarlos y la configuración del entorno para lograr un rendimiento óptimo, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

## <a name="using-the-test-controller-and-test-agent-with-unit-tests"></a>Uso de controladores y agentes de prueba con pruebas unitarias

Después de instalar un controlador de pruebas y uno o más agentes, puede especificar si desea utilizar una ejecución remota con el controlador en la configuración para las pruebas de carga. Además, puede especificar los datos y adaptadores de diagnóstico para utilizar con el rol asociado a los agentes en la configuración de pruebas.

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)