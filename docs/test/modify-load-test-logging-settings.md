---
title: Configuración de registro de pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24bb1b3af468f35ae333407fc96c42f4f9e669b
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894890"
---
# <a name="modify-load-test-logging-settings"></a>Modificar la configuración de registro de pruebas de carga

El resultado de la prueba de carga completada contiene ejemplos de contadores de rendimiento e información de los errores que se recopilaron periódicamente en un registro de los equipos sometidos a prueba. Se puede recopilar un gran número de muestras de contadores de rendimiento durante la ejecución de pruebas de carga. La cantidad de datos de rendimiento recopilados depende de la duración de la ejecución, del intervalo de muestreo, del número de equipos sometidos a prueba y del número de contadores que se van a recolectar. En el caso de una prueba de carga grande, la cantidad de datos de rendimiento que se recopilan puede ascender fácilmente a varios gigabytes; por tanto, podría considerar la posibilidad de modificar la frecuencia con la que se guardan los datos en el registro. Vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

El *controlador de pruebas* pone en cola todos los datos de ejemplo de la prueba de carga recopilados en un registro de la base de datos mientras la prueba se está ejecutando. Otros datos adicionales, como detalles de tiempo y de errores, se cargan en la base de datos cuando la prueba se completa.

|Tarea|Temas relacionados|
|-|-----------------------|
|**Guardar los registros si se produce un error en una prueba de carga:** puede especificar si quiere guardar el registro de la prueba siempre que se produzca un error en una prueba de carga.|-   [Cómo: Especificar si los errores de las pruebas se guardan en los registros de pruebas](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Establecer el tamaño máximo del archivo de registro:** puede editar el archivo de configuración XML asociado al servicio del controlador de pruebas para especificar el tamaño máximo que quiere usar para el archivo de registro.|[Cómo: Especificar el tamaño máximo del archivo de registro](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)