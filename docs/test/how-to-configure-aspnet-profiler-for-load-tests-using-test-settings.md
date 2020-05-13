---
title: Configuración del generador de perfiles ASP.NET para pruebas de carga
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 07df32104394dffcd61d1561309b77e61593f6e6
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880239"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Procedimiento para configurar el generador de perfiles ASP.NET para pruebas de carga mediante la configuración de pruebas en Visual Studio

Puede usar el adaptador de datos de diagnóstico del generador de perfiles ASP.NET para recopilar información del generador de perfiles ASP.NET. Este adaptador de datos de diagnóstico recopila datos de rendimiento de las aplicaciones ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Este adaptador de datos de diagnóstico no se puede usar en las pruebas que se ejecutan con Microsoft Test Manager (en desuso en Visual Studio 2017). Puede usar el adaptador de datos de diagnóstico del generador de perfiles ASP.NET con pruebas de carga que solo usan sitios web, para lo que se requiere Visual Studio Enterprise.

El adaptador de datos de diagnóstico del generador de perfiles ASP.NET permite recopilar datos del generador de perfiles ASP.NET de la capa de aplicación mientras se ejecuta una prueba de carga. No debe ejecutar el generador de perfiles en pruebas de carga largas, por ejemplo, las que se ejecutan durante más de una hora. Esto es porque el archivo de generador de perfiles aumenta su tamaño, quizá hasta centenares de megabytes. En su lugar, ejecute pruebas de carga más cortas con el generador de perfiles ASP.NET, que le ofrecen un diagnóstico profundo de los problemas de rendimiento.

> [!NOTE]
> El adaptador de datos de diagnóstico del generador de perfiles ASP.NET perfila el proceso de Internet Information Services (IIS). Por tanto, no funcionará en un servidor web de desarrollo. Para generar perfiles del sitio web en su prueba de carga, tiene que instalar un agente de prueba en la máquina en la que se ejecuta IIS. El agente de prueba no generará carga, sino que será un agente de recopilación únicamente. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

Para obtener más información, vea [Cómo: Crear una configuración de pruebas para una prueba de carga distribuida](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Ajustes del generador de perfiles ASP.NET para la configuración de pruebas

Antes de seguir los pasos de este procedimiento, debe abrir la configuración de pruebas en Visual Studio y seleccionar la página **Datos y diagnósticos**.

1. Seleccione el rol que se va a usar para recopilar los datos del generador de perfiles ASP.NET.

    > [!WARNING]
    > Este rol debe ser un servidor web.

2. Seleccione **Generador de perfiles ASP.NET** para habilitar la recopilación de datos de generación de perfiles ASP.NET y, luego, elija **Configurar**.

     Se muestra el cuadro de diálogo para configurar la recopilación de datos de generación de perfiles ASP.NET.

3. En **Intervalo de muestreo**, escriba un valor que indique cuántos ciclos de reloj de CPU no detenidos se debe esperar entre cada muestra de generación de perfiles ASP.NET.

4. Para habilitar la generación de perfiles de interacción de capa, seleccione **Habilitar generación de perfiles de interacción de capa**.

     La generación de perfiles de interacción de capas cuenta el número de solicitudes que se envían al servidor web para cada artefacto (por ejemplo, *MyPage.aspx* o *CompanyLogo.gif*) y el tiempo necesario para atender cada solicitud. Además, la generación de perfiles de interacción de capas recopila las conexiones de ADO.NET que se usaron como parte de la solicitud de página, y cuántas consultas y llamadas a procedimientos almacenados se ejecutaron como parte de la atención de esa solicitud.

     Se recopilan dos conjuntos diferentes de información de tiempos:

    - La información de tiempos (mínimo, máximo, promedio y total) para atender cada solicitud web.

    - La información de tiempos (mínimo, máximo, promedio y total) para ejecutar cada consulta.

Con el adaptador de datos de diagnóstico del generador de perfiles ASP.NET configurado en la configuración de pruebas, puede recopilar datos de generación de perfiles ASP.NET en la aplicación web ASP.NET.

## <a name="see-also"></a>Vea también

- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Cómo: Crear una configuración de pruebas para una prueba de carga distribuida](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)