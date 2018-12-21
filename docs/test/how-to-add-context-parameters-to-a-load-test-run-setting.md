---
title: Adición de parámetros de contexto a los parámetros de ejecución de una prueba de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cefa93a6f65b4b84b4ece5a4eb428d909dd0596d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048501"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Procedimiento para agregar parámetros de contexto a los parámetros de ejecución de una prueba de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Para obtener una lista completa de las propiedades de los parámetros de ejecución y sus descripciones, consulte [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

Puede crear parámetros de contexto que se van a usar en los parámetros de ejecución de una prueba de carga mediante el Editor de prueba de carga. Los parámetros de contexto le permiten parametrizar una cadena.

Suponga que su prueba de carga contiene una prueba de rendimiento web que ya usa una dirección URL parametrizada de un servidor web mediante un parámetro de contexto. Puede agregar un parámetro de contexto a un parámetro de ejecución de una prueba de carga que use el mismo valor de nombre que el empleado en la prueba de rendimiento web. Esto asignará la prueba de rendimiento web a un servidor diferente cuando ejecute la prueba de carga. Por ejemplo, si la prueba de carga incluye una prueba de rendimiento web que usa un parámetro de contexto denominado WebServer1 para el nombre del servidor web en la dirección URL. Si a continuación especifica un parámetro de contexto en el parámetro de ejecución de la prueba de carga que también se denomine WebServer1, la prueba de carga usará el parámetro de contexto que asignó en el parámetro de ejecución de la prueba de carga. Para mayor claridad, si la prueba de rendimiento web de la prueba de carga usa el mismo nombre de parámetro de contexto que un parámetro de contexto de la prueba de carga, el parámetro de contexto de la prueba de carga invalidará el parámetro de contexto que se emplea en la prueba de rendimiento web.

> [!WARNING]
> Tenga cuidado para no invalidar involuntariamente el parámetro de contexto de una prueba de rendimiento web al usar parámetros de contexto en un parámetro de ejecución. Evite usar los mismos nombres de parámetro de contexto a menos que lo haga intencionadamente.

Si asigna el valor del parámetro de contexto Webserver1 a `http://CorporateStagingWebServer`, puede usar `WebServer1` en toda la prueba de carga y, de esta forma, cambiar fácilmente el valor a un servidor web diferente en cualquier momento.

Además, si asigna valores diferentes a un parámetro de contexto usando el mismo nombre en parámetros de ejecución de pruebas de carga diferentes, puede ejecutar la prueba de carga usando entornos diferentes:

- Parámetro de ejecución Servidor web de ensayo corporativo: El parámetro de contexto que se denomina `WebServer1=http://CorporateStagingWebServer`

- Parámetro de ejecución Servidor web de producción corporativo: El parámetro de contexto que se denomina `WebServer1=http://CorporateProductionWebServer`

  **Cambiar el parámetro de ejecución desde la línea de comandos**

  Si desea usar parámetros de ejecución diferentes desde la línea de comandos para aprovechar la estrategia de parámetros de contexto, use los siguientes comandos:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  - y -

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Para agregar un parámetro de contexto a un parámetro de ejecución

1.  Abra una prueba de carga.

2.  Expanda la carpeta **Parámetros de ejecución** en el árbol de pruebas de carga del Editor de pruebas de carga.

3.  Haga clic con el botón derecho en el parámetro de ejecución concreto al que desee agregar un parámetro de contexto y, a continuación, elija **Agregar parámetro de contexto**.

     Se agregará un nuevo parámetro de contexto a la carpeta **Parámetros de contexto** de la carpeta **Parámetros de ejecución** del árbol de pruebas de carga.

     O bien

     Si el parámetro de ejecución ya contiene una carpeta **Parámetros de contexto**, puede hacer clic en ella con el botón derecho y, a continuación, elegir **Agregar parámetro de contexto**.

4.  En la ventana **Propiedades**, cambie el valor de **Nombre** según corresponda (por ejemplo, WebServer1). En la ventana **Propiedades**, cambie **Valor** por el parámetro que quiera usar (por ejemplo, `http://CorporateStagingWebServer`).

5.  (Opcional) Repita los pasos del 3 al 5 y use otra cadena para la propiedad **Valor** (por ejemplo, `http://CorporateProductionWebServer`).

6.  Elija los parámetros de ejecución que quiera activar. Abra el menú contextual en los parámetros de ejecución y seleccione **Establecer como activa**.

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)