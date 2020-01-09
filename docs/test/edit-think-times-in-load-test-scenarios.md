---
title: Tiempos de reflexión para pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 887d2af9e60be914bd74141041ecc375cfea4f00
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590038"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Modificación de los tiempos de reflexión de usuario para simular los retrasos de la interacción humana en un sitio web en escenarios de pruebas de carga

Los tiempos de reflexión de usuario se usan para simular el comportamiento humano que hace que las personas esperen entre interacciones con un sitio web. Los tiempos de reflexión de usuario aparecen entre solicitudes en una prueba de rendimiento web y entre iteraciones de prueba en un escenario de prueba de carga. El uso de tiempos de reflexión en una prueba de carga puede ser útil para crear simulaciones de carga más precisas. Puede cambiar la posibilidad de uso de tiempos de reflexión, o su aplicación en pruebas de carga. La opción de uso de tiempos de reflexión de usuario en las pruebas de carga se cambia en el **Editor de pruebas de carga**.

El *perfil de reflexión* es un valor que se aplica a un escenario en una prueba de carga. Este valor determina si los tiempos de reflexión de usuario que se guardan en las pruebas de rendimiento web individuales se utilizan durante la prueba de carga. Si desea utilizar tiempos de reflexión de usuario en alguna prueba de rendimiento web pero no en otras, debe colocarlos en escenarios diferentes. Para más información sobre los escenarios, consulte [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md).

Inicialmente, se establece si se van a utilizar tiempos de reflexión de usuario en las pruebas de carga cuando se crea la prueba de carga mediante el **Asistente para prueba de carga nueva**. Para más información, consulte [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md).

Las opciones de **Perfil de reflexión de usuario** se describen en la lista siguiente:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Off**

Los tiempos de reflexión se omiten. Utilice esta configuración cuando desee generar carga máxima para cargar su servidor web de forma considerable. No la utilice cuando trate de crear interacciones de usuario con un servidor web más realistas.

**On**

Los tiempos de reflexión de usuario se utilizan exactamente como se grabaron en la prueba de rendimiento web. Simula que varios usuarios ejecutan las pruebas de rendimiento web exactamente como se han grabado. Dado que una prueba de carga simula varios usuarios, el uso del mismo tiempo de reflexión podría crear un modelo de carga de usuarios virtuales sincronizados que resultaría poco natural.

**Distribución normal**

Se utilizan los tiempos de reflexión, pero modificados según una curva normal. Proporciona una simulación más realista de usuarios virtuales variando ligeramente el tiempo de reflexión entre las solicitudes.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, vea [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Cambio del perfil de reflexión de usuario

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Para cambiar un perfil de reflexión en un escenario de prueba de carga

1. En el proyecto de prueba de carga y de rendimiento web, abra una prueba de carga.

2. En el **Editor de pruebas de carga**, elija el nodo del escenario cuyo **Perfil de reflexión** quiere cambiar. El **Perfil de reflexión de usuario** se muestra en la ventana **Propiedades**. Presione **F4** para abrir la ventana **Propiedades**.

3. Cambie la propiedad **Perfil de reflexión de usuario** en la ventana **Propiedades**.

4. Cuando haya terminado de cambiar las propiedades, elija **Guardar** en el menú **Archivo**. Entonces podrá ejecutar la prueba de carga con el nuevo perfil de reflexión.

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
