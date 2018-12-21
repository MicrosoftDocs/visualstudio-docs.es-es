---
title: Especificación del porcentaje de usuarios virtuales que usan datos de caché web para pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 2195b99658d05e9e73a86cf723fcb8e9d4f36bd4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060244"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Procedimiento para especificar el porcentaje de usuarios virtuales que usan datos de caché web

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba. Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La propiedad **Porcentaje de nuevos usuarios** se establece en la ventana **Propiedades**. Para modificar las propiedades del escenario de prueba de carga se usa el **Editor de pruebas de carga**.

La propiedad **Porcentaje de nuevos usuarios** afecta a la manera en la que la prueba de carga simula el almacenamiento en caché que debería realizar un explorador web. De forma predeterminada, la propiedad **Porcentaje de nuevos usuarios** está establecida en 0 %. Si el valor de la propiedad **Porcentaje de nuevos usuarios** se establece en 100 %, cada ejecución de pruebas de rendimiento web en una prueba de carga se trata como si fuese la primera vez que el usuario visita el sitio web y, por lo tanto, no tiene contenido alguno del sitio web en la memoria caché del explorador de visitas previas. Por tanto, se descargan todas las solicitudes de la prueba web, incluidas todas las solicitudes dependientes, como las imágenes.

> [!NOTE]
> Cuando el mismo recurso almacenable en caché se solicita más de una vez en una prueba web, no se descargan las solicitudes.

Si realiza una prueba de carga de un sitio web que cuenta con muchos usuarios de retorno, que probablemente tengan imágenes y otro tipo de contenido que se almacena localmente en la memoria caché, un valor de 100 % para la propiedad **Porcentaje de nuevos usuarios** genera más solicitudes de descarga que las que habría si se tratase del uso real. En este caso, debería calcular el porcentaje de visitas al sitio web de los usuarios que lo hacen por primera vez y establecer la propiedad **Porcentaje de nuevos usuarios** en consecuencia.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>Para especificar el porcentaje de nuevos usuarios para un escenario

1. Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2. En la carpeta **Escenarios** de árboles de la prueba de carga, elija el nodo de escenario cuyo valor de porcentaje de nuevos usuarios quiere cambiar.

3. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

4. Establezca el valor de la propiedad **Porcentaje de nuevos usuarios** escribiendo un número para el porcentaje de nuevos usuarios.

5. Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga con el nuevo valor de **Porcentaje de nuevos usuarios**.

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Tutorial: Creación y ejecución de una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)
- [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md)