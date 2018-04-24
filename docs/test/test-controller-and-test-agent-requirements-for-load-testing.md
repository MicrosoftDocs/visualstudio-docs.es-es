---
title: Requisitos del controlador y el agente de pruebas para pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 1c6ae9d8200d6e8f32b7f8a96b222b4bfb4c75d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Requisitos del agente de prueba y del controlador de pruebas para pruebas de carga

Algunos tipos de pruebas, como las pruebas unitarias, las pruebas de rendimiento web, las pruebas de carga y las pruebas manuales, están integradas en Visual Studio. Visual Studio permite a los usuarios de Visual Studio Application Lifecycle Management ejecutar pruebas en equipos remotos a través de un controlador de pruebas y uno o más agentes. Vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

## <a name="hardware-and-software-requirements"></a>Requisitos de hardware y software

Ambos equipos, el del controlador y el del agente, tienen requisitos de hardware y software concretos. Además, si desea implementar los equipos del agente y del controlador de prueba por varios lenguajes, debe planear cómo admitir esos lenguajes.

### <a name="hardware-requirements"></a>Requisitos de hardware

En la siguiente tabla se muestran los requisitos de hardware recomendados para implementar un agente y un controlador de prueba.

|**Configuración**|**Componente**|**CPU**|**HD**|**Memoria**|
|-----------------------|-------------------|-------------|------------|----------------|
|< 500 usuarios virtuales|Agente de pruebas|2,6 GHz|10 GB|2 GB|
|< 1000 usuarios virtuales|Agente de pruebas|Dos procesadores, 2,6 GHz|10 GB|2 GB|
|N x 1000 usuarios virtuales|Agente de pruebas|Ampliar hasta N agentes, cada uno con dos procesadores a 2,6 Ghz|10 GB|2 GB|
|\< 30 equipos en el entorno de prueba. Incluye los agentes y servidores que se van a probar.|Test Controller|2,6 GHz|||
|N x 30 equipos en el entorno de pruebas. Incluye los agentes y servidores que se van a probar.|Test Controller|N procesadores a 2,6 GHz|||

> [!NOTE]
> El número de usuarios virtuales variará considerablemente según la prueba. Una causa clave de esta varianza es la variación de los *tiempos de reflexión* o los retrasos de usuario. Para obtener más información, vea [Modificar los tiempos de reflexión para simular los retrasos de la interacción humana en un sitio web](../test/edit-think-times-in-load-test-scenarios.md). En una prueba de carga, las pruebas web son normalmente más eficaces y generan más carga que las unitarias. Los números de la tabla anterior son válidos para la ejecución de pruebas web con tiempos de reflexión de 3 a 5 segundos en una aplicación web típica.

Las instrucciones presentadas en esta sección se proporcionan como guía general para el planeamiento del hardware. Los resultados de las pruebas variarán considerablemente en función de la cantidad de datos de prueba y del número de agentes de pruebas. Para los agentes de pruebas, la velocidad de la CPU y la memoria disponible limitarán la carga de las pruebas. Los controladores de pruebas necesitan un número mayor de recursos según el número de agentes de pruebas y la cantidad de datos implicados en las pruebas.

El servidor en el que se ejecuta Visual Studio debe tener una conexión de red de confianza con un ancho de banda mínimo de 1 Mbps y una latencia máxima de 350 ms. No debería haber ningún firewall entre los agentes y el controlador de pruebas. Si los resultados de las pruebas no satisfacen sus expectativas, tenga en cuenta una actualización de la configuración de hardware.

### <a name="additional-hardware-considerations"></a>Consideraciones de hardware adicionales

Los agentes de pruebas generan una cantidad grande de datos en los controladores de prueba, dependiendo de la duración de la prueba y su tamaño. En general, debe prever 10 GB adicionales de almacenamiento en disco duro por cada 24 horas de datos de pruebas.

Además del hardware recomendado, debe pensar en tener hardware adicional para los servidores críticos, como alimentación eléctrica y ventiladores redundantes.

### <a name="language-requirements"></a>Requisitos de lenguaje

Para evitar la confusión y simplificar la operación, se deben configurar los agentes y controladores de pruebas con el mismo idioma que el sistema operativo del equipo y Team Foundation Server. Si el agente y el controlador de pruebas se instalan en equipos diferentes, se deben configurar para que utilicen el mismo idioma. Pero puede instalar una versión en otro idioma de Visual Studio en un sistema operativo en inglés, siempre que ese idioma coincida con el de la implementación de Team Foundation Server.

## <a name="monitor-agent-resources"></a>Supervisar recursos de agentes

Puede supervisar equipos de agente para determinar los recursos que necesitan; para ello, analice los procesos de **QTAgent\*.exe** que se ejecutan y escalan durante las pruebas. El cuello de botella más habitual en los procesos de QTAgent*.exe es el uso de CPU. Si el uso de CPU está con frecuencia en más de noventa, quiere decir que el agente tiene una carga muy elevada. El siguiente cuello de botella más habitual es el uso de memoria. Para pruebas exigentes, supervisar estos recursos puede ayudar a determinar si es necesario aumentar los recursos de los equipos o distribuir las pruebas de forma distinta.

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)