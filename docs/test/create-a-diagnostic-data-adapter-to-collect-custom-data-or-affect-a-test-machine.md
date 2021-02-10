---
title: Creación de un adaptador de datos de diagnóstico para pruebas
description: Aprenda a escribir código para realizar tareas en puntos concretos de la serie de pruebas mediante las API proporcionadas en Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: fe1adfc62e0b8b9045ec87c1a78cdd56412ff320
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964477"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Crear un adaptador de datos de diagnóstico para recopilar datos personalizados o afectar a un equipo de prueba

Es posible que desee crear su propio adaptador de datos de diagnóstico para recopilar información al ejecutar una prueba o quizás desee que el sistema se vea afectado como parte de la prueba. Por ejemplo, quizás desee recopilar los archivos de registro creados por la aplicación en pruebas y adjuntarlos a los resultados de pruebas, o bien ejecutar las pruebas cuando quede poco espacio en el disco del equipo. Con las API proporcionadas en Visual Studio Enterprise, puede escribir código para realizar tareas en puntos concretos de la serie de pruebas. Por ejemplo, puede realizar tareas al inicio de una ejecución de pruebas, antes y después de que se ejecute cada una de las pruebas y una vez que la ejecución de pruebas ha finalizado.

::: moniker range="vs-2017"
Puede usar un archivo de configuración para proporcionar los valores predeterminados al adaptador de datos de diagnóstico personalizado. Por ejemplo, puede proporcionar información acerca de la ubicación del archivo que desea recopilar y adjuntar a los resultados de pruebas, o cuánto espacio en disco desea que quede en el sistema. Esta información se puede establecer para cada configuración de pruebas que cree. Se puede mostrar y modificar con el editor predeterminado que se proporciona en Microsoft Test Manager o puede crear su propio control de usuario para usarlo como un editor. Cualquier cambio que se realice en la configuración del adaptador en el editor se guardará con la configuración de pruebas.
::: moniker-end

::: moniker range=">=vs-2019"
Puede usar un archivo de configuración para proporcionar los valores predeterminados al adaptador de datos de diagnóstico personalizado. Por ejemplo, puede proporcionar información acerca de la ubicación del archivo que desea recopilar y adjuntar a los resultados de pruebas, o cuánto espacio en disco desea que quede en el sistema. Esta información se puede establecer para cada configuración de pruebas que cree. Puede crear un control de usuario propio para usarlo como editor. Cualquier cambio que se realice en la configuración del adaptador en el editor se guardará con la configuración de pruebas.
::: moniker-end

Si ejecuta las pruebas desde Visual Studio, debe establecer que esta configuración de pruebas esté activa. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tareas

Use los temas siguientes como ayuda para crear adaptadores de datos de diagnóstico:

|Tareas|Temas relacionados|
|-|-----------------------|
|**Creación de un adaptador de datos de diagnóstico:** Para crear un adaptador de datos de diagnóstico, se crea una biblioteca de clases y, después, se usan las API del adaptador de datos de diagnóstico para recopilar la información que se quiere o para impactar en un sistema de pruebas que se está usando para ejecutar las pruebas.|-   [Cómo: Crear un adaptador de datos de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Selección de un adaptador de datos de diagnóstico personalizado para usar durante la ejecución de las pruebas:** En la configuración de pruebas, se puede seleccionar el adaptador de datos de diagnóstico que se va a usar durante la ejecución de las pruebas.|-   [Collect diagnostic data while testing (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) [Recopilar datos de diagnóstico durante las pruebas (Azure Test Plans)]<br />-   [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)]|

## <a name="see-also"></a>Vea también

- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)