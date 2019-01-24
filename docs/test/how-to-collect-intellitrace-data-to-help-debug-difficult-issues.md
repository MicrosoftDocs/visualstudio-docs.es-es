---
title: Datos de IntelliTrace
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: d9023f094ca662a270d7a28609e09f012d8f445c
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154368"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Procedimiento para recopilar datos de IntelliTrace para ayudar a depurar problemas difíciles

Puede configurar el adaptador de datos de diagnóstico de IntelliTrace de modo que recopile información específica de seguimiento de diagnóstico en Visual Studio. Las pruebas pueden usar este adaptador, la prueba puede obtener los eventos de diagnóstico significativos de la aplicación de forma que un desarrollador pueda usarlos después para seguir paso a paso el código y detectar la causa de un error. El adaptador de datos de diagnóstico de IntelliTrace se puede utilizar para pruebas manuales o automatizadas.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace funciona únicamente en una aplicación escrita con código administrado. Al realizar pruebas de una aplicación web que use un explorador como cliente, no se debe habilitar IntelliTrace para el cliente en la configuración de pruebas porque no hay código administrado. En este caso, se podrá configurar un entorno y recopilar los datos de IntelliTrace de forma remota en el servidor web.

Los datos de IntelliTrace se almacenan en un archivo con la extensión *.iTrace*. Si la ejecución de uno de los pasos de la prueba es incorrecta, puede crear un error. El archivo de IntelliTrace que contiene la información de diagnóstico se adjunta automáticamente a este error.

> [!NOTE]
> El adaptador de datos de diagnóstico de IntelliTrace no crea un archivo de IntelliTrace cuando un paso de la prueba es correcto. Solo se guarda un archivo si un caso de prueba no es correcto o si se envía un error.

Los datos que se recopilan en el archivo de IntelliTrace aumentan la productividad de la depuración porque reducen el tiempo necesario para reproducir y diagnosticar un error en el código. Además, como se puede compartir el archivo de IntelliTrace con otro usuario que puede replicar la sesión local en su propio equipo, se reduce la probabilidad de que un error no sea reproducible.

> [!NOTE]
> Si habilita IntelliTrace en la configuración de pruebas, no funcionará la recopilación de los datos de cobertura de código.

> [!WARNING]
> El adaptador de datos de diagnóstico de IntelliTrace funciona mediante la instrumentación de un proceso administrado, que debe realizarse después de que se hayan cargado las pruebas para la ejecución. Si el proceso que desea supervisar ya se ha iniciado, no se recopilará ningún archivo de IntelliTrace porque el proceso ya se está ejecutando. Para sortearlo, debe asegurarse de que se detiene el proceso antes de que se carguen las pruebas. Después inicie el proceso una vez cargadas las pruebas o una vez iniciada la primera prueba.

En el siguiente procedimiento, se describe cómo configurar los datos de IntelliTrace que se van a recopilar. Estos pasos son válidos para el editor de configuración de Microsoft Test Manager y el cuadro de diálogo de configuración de pruebas de Visual Studio.

> [!NOTE]
> La cuenta de usuario del agente de prueba que se utiliza para recolectar los datos de IntelliTrace debe ser un miembro del grupo de administradores. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Configurar los datos que se van a recopilar con el adaptador de datos de diagnóstico de IntelliTrace

Antes de seguir los pasos que se describen en este procedimiento, debe abrir la configuración de pruebas en Microsoft Test Manager o en Visual Studio y seleccionar la página **Datos y diagnósticos**.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Para configurar los datos que se van a recopilar con el adaptador de datos de diagnóstico de IntelliTrace, siga estos pasos:

1.  Seleccione el rol que se usará para recopilar los datos de IntelliTrace.

2.  Seleccione **IntelliTrace**.

3.  Si va a agregar IntelliTrace para un rol de cliente web o para una aplicación web ASP.NET, también deberá seleccionar **ASP.NET Client Proxy for IntelliTrace and Test Impact** (ASP.NET Client Proxy for IntelliTrace and Test Impacto en las pruebas).

     Este proxy permite recopilar información sobre las llamadas HTTP de un cliente a un servidor web para los adaptadores de datos de diagnóstico de IntelliTrace y de impacto en las pruebas.

    > [!WARNING]
    > Si decide usar una cuenta personalizada para la identidad usada para el grupo de aplicaciones en el servidor de Internet Information Server (IIS) donde quiera recopilar los datos de IntelliTrace, necesita crear el perfil de usuario local en el equipo de IIS para la cuenta personalizada que se use. Puede crear el perfil local para la cuenta personalizada iniciando sesión localmente en el equipo de IIS una vez o ejecutando la siguiente línea de comandos con las credenciales de la cuenta personalizada:
    >
    > **runas /user:domain\name /profile cmd.exe**

4.  Elija **Configurar** para **IntelliTrace** a fin de modificar los valores predeterminados de IntelliTrace.

     Se mostrará el cuadro de diálogo para configurar los datos que se van a recopilar.

    > [!WARNING]
    > Si habilita la recopilación de los datos de IntelliTrace, no funcionará la recopilación de los datos de cobertura de código.

5.  Elija la pestaña **General**. Seleccione **Solo eventos de IntelliTrace** para que se registren los eventos de diagnóstico significativos con un impacto mínimo en el rendimiento durante las pruebas.

     o bien

     Seleccione **Información de llamadas y eventos de IntelliTrace** para registrar los eventos de diagnóstico y la traza de los métodos con información de las llamadas. Este nivel de traza podría afectar al rendimiento durante la ejecución de las pruebas.

6.  Si quiere recopilar datos de una aplicación ASP.NET que se ejecuta en Internet Information Services, seleccione **Recopilar datos de aplicaciones ASP.NET que se ejecutan en Internet Information Services**. Establezca y configure el agente de prueba en el rol de servidor web. Vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).

7.  Elija la pestaña **Módulos**. Seleccione **Recopilar datos de todos los módulos excepto los siguientes** y use **Agregar** para agregarlos a la lista de módulos, o bien haga clic en **Quitar** para quitar un módulo. Esta opción permite incluir todos los módulos que se ejecutan en el sistema excepto los módulos especificados.

     o bien

     Seleccione **Recopilar datos solo de los siguientes módulos** y haga clic en **Agregar** para agregarlos a la lista de módulos, o bien haga clic en **Quitar** para quitar un módulo. Esta opción permite especificar exactamente los módulos deseados.

    > [!NOTE]
    > Si es posible, seleccione los procesos concretos que desea supervisar. Esto se recomienda para un rendimiento óptimo.

8.  Elija la pestaña **Procesos**. Seleccione **Recopilar datos de todos los procesos excepto los siguientes** y haga clic en **Agregar** para agregarlos a la lista de procesos, o bien haga clic en el botón **Quitar** para quitar un proceso. Esta opción permite incluir todos los procesos que se ejecutan en el sistema excepto los procesos especificados.

     o bien

     Seleccione **Recopilar datos solo de los procesos especificados** y haga clic en **Agregar** para agregarlos a la lista de procesos, o bien haga clic en **Quitar** para quitar un proceso. Esta opción permite especificar exactamente los procesos deseados.

9. (Opcional) Elija la pestaña **Eventos de IntelliTrace**. Active o desactive cada una de las categorías de evento de IntelliTrace que desee incluir o excluir al recopilar los eventos de diagnóstico.

10. (Opcional) Expanda cada categoría de evento de IntelliTrace y active o desactive cada uno de los eventos que desee incluir o excluir de los eventos de IntelliTrace.

11. (Opcional) Elija la pestaña **Opciones avanzadas**. Luego, elija la flecha situada junto a **Cantidad máxima de espacio en disco para el registro** y seleccione el tamaño máximo que quiera habilitar para el archivo de IntelliTrace.

    > [!NOTE]
    > Si aumenta el tamaño de la grabación, se puede producir un problema de tiempo de espera al guardar esta grabación junto con los resultados de pruebas.

12. Si usa Microsoft Test Manager, seleccione **Guardar**. Si usa Visual Studio, elija **Aceptar**. Ya está configurado IntelliTrace y su configuración se ha guardado para la configuración de pruebas.

    > [!NOTE]
    > Para restablecer la configuración de este adaptador de datos de diagnóstico, elija **Restablecer la configuración predeterminada** para Visual Studio o **Restablecer valores predeterminados** para Microsoft Test Manager.

## <a name="see-also"></a>Vea también

- [Collect diagnostic data while testing (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) [Recopilar datos de diagnóstico durante las pruebas (Azure Test Plans)]
- [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)]
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Recopilar datos de IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)