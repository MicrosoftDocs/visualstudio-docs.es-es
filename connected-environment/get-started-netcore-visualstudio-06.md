---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube con Visual Studio - Paso 6: Nociones del desarrollo en equipo | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: b4bc1f44e63614346f4e2d149e76becabdcb8c71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introducción a Connected Environment con .NET Core y Visual Studio

Paso anterior: [Llamar a otro contenedor](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>Nociones del desarrollo en equipo

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

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>Trabajar en un entorno de desarrollo compartido
Con Connected Environment, se puede configurar un entorno de desarrollo *compartido* en Azure. Así, cada programador se puede centrar exclusivamente en su parte de la aplicación y desarrollar de forma iterativa *código previo a la confirmación* en un entorno que ya contenga todos los demás servicios y recursos en la nube de los que sus escenarios dependen. Las dependencias siempre estarán actualizadas y los desarrolladores trabajarán de una manera que se asemeja bastante a un entorno de producción.

## <a name="work-in-your-own-space"></a>Trabajar en un espacio propio
A medida que desarrolla el código del servicio, a menudo ese código no estará en un estado adecuado cuando esté listo para confirmarlo. El desarrollador seguirá dándole forma de modo iterativo, probándolo y experimentando con las soluciones. En Connected Environment existe el concepto de **espacio**, que permite trabajar de manera aislada y sin riesgo de romper el código de los miembros del equipo.

Haga lo siguiente para asegurarse de que los servicios `webfrontend` y `mywebapi` se están ejecutando en nuestro entorno de desarrollo **y en el espacio `mainline`**.
1. Cierre las sesiones de depuración/F5 de ambos servicios, pero deje los proyectos abiertos en la ventana de Visual Studio.
2. Cambie a la ventana de Visual Studio con el proyecto `mywebapi` y presione Ctrl+F5 para ejecutar el servicio sin el depurador asociado.
3. Cambie a la ventana de Visual Studio con el proyecto `webfrontend` y presione Ctrl+F5 para ejecutarlo también.

> [!Note]
A veces hay que actualizar el explorador si la página web se muestra inicialmente tras presionar Ctrl+F5.

Cualquiera que abra la dirección URL pública y se desplace a la aplicación web invocará la ruta de acceso de código que hemos escrito, que se ejecuta a través de ambos servicios con el espacio predeterminado `mainline`. Ahora, imaginemos que queremos seguir desarrollando `mywebapi`. ¿Cómo podríamos hacerlo sin interrumpir el trabajo de otros desarrolladores que usan el entorno de desarrollo? Lo haremos configurando nuestro propio espacio.

### <a name="create-a-new-space"></a>Crear un espacio
En Visual Studio, se pueden crear más espacios que se usarán cuando se presione F5 o Ctrl+F5 en el servicio. Puede denominar un espacio como quiera y ser flexible sobre lo que significa (p. ej., `sprint4` o `demo`).

Haga lo siguiente para crear un espacio:
1. Cambie a la ventana de Visual Studio con el proyecto `mywebapi`.
2. Haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Propiedades**.
3. Seleccione la pestaña **Depurar** de la izquierda para mostrar la configuración de Connected Environment.
4. Desde ahí, puede cambiar o crear el Connected Environment o el espacio que se usará cuando se presione F5 o Ctrl+F5. *Asegúrese de seleccionar el Connected Environment que creó anteriormente*.
5. En la lista desplegable **Space** (Espacio), seleccione **<Create New Space...>** (Crear espacio).

    ![](images/Settings.png)

6. En el cuadro de diálogo **Add Space** (Agregar espacio), escriba un nombre para el espacio y haga clic en **Aceptar**. He usado mi nombre ("scott") en el nuevo espacio para que mis compañeros sepan identificar el espacio en el que estoy trabajando.

    ![](images/AddSpace.png)

7. Ahora deberíamos ver nuestro entorno de desarrollo y el nuevo espacio seleccionado en la página de propiedades del proyecto.

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>Actualizar el código de *mywebapi*

1. En el proyecto `mywebapi`, realice la siguiente modificación de código en el método `string Get(int id)` del archivo `ValuesController.cs`:
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. Establezca un punto de interrupción en este bloque de código actualizado (puede que ya tenga uno establecido con anterioridad).
3. Presione F5 para iniciar el servicio `mywebapi`. Esto hará que el servicio se inicie en el entorno de desarrollo usando el espacio seleccionado, que en nuestro caso es `scott`.

Este es un diagrama que le ayudará a comprender cómo funcionan los diferentes espacios. La ruta azul señala una solicitud realizada a través del espacio `mainline`, que es la ruta predeterminada que se usa si no se ha antepuesto ningún espacio a la dirección URL. La ruta verde señala una solicitud realizada a través del espacio `scott`.

![](media/Space-Routing.png)

Esta capacidad integrada de Connected Environment permite probar código de un extremo a otro en un entorno compartido, y todo ello sin que los demás desarrolladores tengan que volver a crear la pila de servicios completa en sus correspondientes espacios. Cabe mencionar que estas rutas requieren que se reenvíen encabezados de propagación al código de la aplicación, como se ha explicado en el paso anterior de esta guía.

## <a name="test-code-running-in-the-scott-space"></a>Probar el código que se ejecuta en el espacio `scott`
Para probar nuestra nueva versión de `mywebapi` junto con `webfrontend`, abra el explorador en la dirección URL de punto de acceso público de `webfrontend` (p. ej., https://webfrontend-teamenv.vsce.io) y vaya a la página About. Debería ver el mensaje original "Hello from webfrontend and Hello from mywebapi".

Ahora, agregue el fragmento "scott-" a la dirección URL para que se muestre algo parecido a https://scott-webfrontend-teamenv.vsce.io y actualice el explorador. Se debería seleccionar el punto de interrupción que establecimos en el proyecto `mywebapi`. Haga clic en F5 para continuar y, ahora, debería ver en el explorador el nuevo mensaje, "Hello from webfrontend and mywebapi now says something new". Esto se debe a que la ruta de acceso al código actualizado en `mywebapi` se ejecuta en el espacio `scott`.

> [!div class="nextstepaction"]
> [Resumen](get-started-netcore-visualstudio-07.md)