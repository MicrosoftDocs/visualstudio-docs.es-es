---
ms.topic: include
ms.openlocfilehash: 30d3f9da291feb52674937d4b2f1b86f3efd0386
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031302"
---
Hasta el momento hemos ejecutado el código de nuestra aplicación como si fuéramos el único desarrollador que trabaja en la aplicación. En esta sección, veremos cómo Connected Environment simplifica el desarrollo en equipo. Así:
* Posibilita que un equipo de desarrolladores trabaje en el mismo entorno de desarrollo.
* Permite que cada desarrollador itere por su código de manera aislada y sin riesgo de romper el de los demás.
* Permite probar el código de un extremo a otro antes de confirmarlo, sin tener que crear simulaciones de dependencias.

## <a name="challenges-with-developing-microservices"></a>Retos del desarrollo de microservicios
Por el momento, nuestra aplicación de ejemplo no es especialmente compleja, pero en el desarrollo del mundo real, los retos no tardan en aparecer a medida que se van agregando más servicios y el equipo de desarrollo aumenta.

Imagínese trabajar en un servicio que interactúa a su vez con decenas de servicios distintos.

1. Resulta poco realista ejecutar todo localmente al desarrollar. Puede que el equipo donde está desarrollando código no tenga recursos suficientes para ejecutar la aplicación completa. O puede que la aplicación tenga puntos de conexión que deban estar accesibles públicamente (por ejemplo, porque la aplicación responda a un webhook de una aplicación SaaS).
1. Puede probar a ejecutar únicamente los servicios de los que su trabajo dependa, pero para ello debe conocer la clausura completa de las dependencias (por ejemplo, las dependencias de las dependencias). También puede ser una cuestión de no saber del todo cómo compilar y ejecutar dependencias porque no ha trabajado en ellas.
1. Algunos desarrolladores recurren a simular muchas de las dependencias de servicio. Esto puede ser útil a veces, si bien administrar dichas simulaciones pronto requerirá su correspondiente esfuerzo de desarrollo, aparte de que con esto el entorno de desarrollo que se obtiene es muy distinto al de producción, y pueden surgir errores imperceptibles.
1. De todo esto se desprende que realizar cualquier tipo de pruebas de un extremo a otro va a ser tarea complicada. Las pruebas de integración solo tienen sentido después de la confirmación, lo que significa que veremos problemas más adelante en el ciclo de desarrollo.

![](../media/microservices-challenges.png)


## <a name="work-in-a-shared-development-environment"></a>Trabajar en un entorno de desarrollo compartido
Con Connected Environment, se puede configurar un entorno de desarrollo *compartido* en Azure. Así, cada programador se puede centrar exclusivamente en su parte de la aplicación y desarrollar de forma iterativa *código previo a la confirmación* en un entorno que ya contenga todos los demás servicios y recursos en la nube de los que sus escenarios dependen. Las dependencias siempre estarán actualizadas y los desarrolladores trabajarán de una manera que se asemeja bastante a un entorno de producción.

## <a name="work-in-your-own-space"></a>Trabajar en un espacio propio
A medida que desarrolla el código del servicio, a menudo ese código no estará en un estado adecuado cuando esté listo para confirmarlo. El desarrollador seguirá dándole forma de modo iterativo, probándolo y experimentando con las soluciones. En Connected Environment existe el concepto de **espacio**, que permite trabajar de manera aislada y sin riesgo de romper el código de los miembros del equipo.

> [!Note]
> Antes de continuar, cierre todas las ventanas de VS Code de ambos servicios y ejecute `vsce up -d` en las carpetas raíz de cada uno de los servicios. (Esta es una limitación de la versión preliminar).

Veamos más detenidamente dónde se ejecutan los servicios. Ejecute el comando `vsce list` y verá un resultado similar al siguiente:

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------------------
mywebapi     mainline  mywebapi-0.1.0     80/TCP  2m ago     <not attached>
webfrontend  mainline  webfrontend-0.1.0  80/TCP  1m ago     https://webfrontend-contosodev.vsce.io
```

La columna Space muestra que ambos servicios se ejecutan en un espacio llamado `mainline`. Cualquiera que abra la dirección URL pública y se desplace a la aplicación web invocará la ruta de acceso de código que hemos escrito antes, que se ejecuta a través de ambos servicios. Ahora, imaginemos que queremos seguir desarrollando `mywebapi`. ¿Cómo podríamos hacerlo sin interrumpir el trabajo de otros desarrolladores que usan el entorno de desarrollo? Lo haremos configurando nuestro propio espacio.

## <a name="create-a-space"></a>Crear un espacio
Para ejecutar nuestra propia versión de `mywebapi` en un espacio distinto de `mainline`, vamos a crear nuestro propio espacio:
``` 
vsce space create --name scott
```

En el ejemplo anterior usé mi nombre en el nuevo espacio para que mis compañeros supieran identificar el espacio en el que estoy trabajando, pero se le puede llamar del modo que se quiera y ser flexible sobre lo que significa, como "sprint4" o "demo". 

Ejecute el comando `vsce space list` para ver una lista de todos los espacios en el entorno de desarrollo. Verá un asterisco (*) junto al espacio seleccionado actualmente. En nuestro caso, el espacio denominado "scott" se seleccionó automáticamente cuando se creó. Puede seleccionar otro espacio en cualquier momento con el comando `vsce space select`.
