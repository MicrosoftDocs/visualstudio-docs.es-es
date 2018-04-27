---
ms.topic: include
ms.openlocfilehash: 9da28d29dc431f2f6ec92a01c397244147042f12
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
2. Presione F5 (o escriba `vsce up` en la ventana de terminal) para ejecutar el servicio. Al hacerlo, se ejecutará automáticamente en nuestro nuevo espacio seleccionado, `scott`. 
1. Podemos confirmar esto si ejecutamos `vsce list` de nuevo. En primer lugar, verá que ahora hay una instancia de `mywebapi` ejecutándose en el espacio `scott` (la versión que se ejecuta en `mainline` sigue ejecutándose, pero no aparece). En segundo lugar, la dirección URL de punto de acceso de `webfrontend` tiene como prefijo el texto "scott-". Esta dirección URL es única en el espacio `scott` y significa que las solicitudes enviadas a la "dirección URL de scott" probarán primero a enrutar a los servicios en el espacio `scott` y volverán a los servicios en el espacio `mainline`.

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Esta capacidad integrada de Connected Environment permite probar código de un extremo a otro en un entorno compartido, y todo ello sin que los demás desarrolladores tengan que volver a crear la pila de servicios completa en sus correspondientes espacios. Cabe mencionar que estas rutas requieren que se reenvíen encabezados de propagación al código de la aplicación, como se ha explicado en el paso anterior de esta guía.

## <a name="test-code-in-a-space"></a>Probar el código en un espacio
Para probar nuestra nueva versión de `mywebapi` junto con `webfrontend`, abra el explorador en la dirección URL de punto de acceso público de webfrontend y vaya a la página About. El nuevo mensaje debería aparecer.

Ahora, vamos a quitar el fragmento "scott-" de la dirección URL y a actualizar el explorador. Debería producirse el comportamiento anterior (el que muestra la versión de `mywebapi` que se ejecuta en `mainline`).