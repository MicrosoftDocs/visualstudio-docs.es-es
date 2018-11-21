---
title: Servicios conectados
description: Agregar almacenamiento de datos de Azure, autenticación y notificaciones de inserción a aplicaciones móviles desde Visual Studio para Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: conceptdev
ms.author: crdun
ms.date: 11/06/2018
ms.openlocfilehash: ada47aa3d0cb0d9917404efc2775b843223c6e86
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948951"
---
# <a name="connected-services-walkthrough"></a>Tutorial de Servicios conectados

El flujo de trabajo de Servicios conectados integra el flujo de trabajo de Azure Portal en Visual Studio para Mac, por lo que no tiene que salir de su proyecto para agregar servicios.

En este tutorial se muestra cómo agregar un servicio back-end de Azure, que ofrece almacenamiento de datos en la nube, autenticación y notificaciones de inserción a una aplicación multiplataforma de biblioteca de clases portables (PCL) de Xamarin.Forms.

1. Para comenzar, haga doble clic en el nodo **Servicios conectados** de la solución, lo que abre la **Galería de servicios**.
  Se trata de una lista de todos los servicios disponibles para el tipo de aplicación. Haga clic en un servicio (como **Back-end móvil con Azure App Service**) para seleccionarlo.

    [![Nodo de Servicios conectados de Visual Studio para Mac](media/connected-services-image001-sml.png "Nodo de Servicios conectados de Visual Studio para Mac")](media/connected-services-image001.png#lightbox)

2. En la página Detalles de servicio se incluye una descripción del servicio y las dependencias que deben instalarse.
  Haga clic en el botón **Agregar** para agregar las dependencias a la aplicación:

    [![Back-end móvil con Azure](media/connected-services-image002-sml.png "Back-end móvil con Azure")](media/connected-services-image002.png#lightbox)

3. Para que funcionen, las dependencias deben agregarse a PCL y a los proyectos específicos de la plataforma.
  Seleccione las casillas para agregar el servicio a todos los proyectos que harán referencia a él (directa o indirectamente):

    [![Marque todos los proyectos que deben hacer referencia al servicio](media/connected-services-image003-sml.png "Marque todos los proyectos que deben hacer referencia al servicio")](media/connected-services-image003.png#lightbox)

4. Elija **Aceptar** en los cuadros de diálogo **Aceptación de licencia** de los paquetes de NuGet.
  Puede haber dos cuadros de diálogo para aceptar, uno de MobileClient y las dependencias y otro de SQLiteStore, lo cual es necesario para la sincronización de datos sin conexión:

    [![Aceptar los contratos de licencia](media/connected-services-image004-sml.png "Aceptar los contratos de licencia")](media/connected-services-image004.png#lightbox)

    ![Ventana Aceptación de licencia](media/connected-services-image005.png "Ventana Aceptación de licencia")

5. Una vez agregadas las dependencias, se le pedirá que inicie sesión con la cuenta que quiere utilizar para comunicarse con Azure.
  Si ya ha iniciado sesión con un identificador de Microsoft, Visual Studio para Mac intentará capturar las suscripciones de Azure y los servicios de aplicación asociados a ellas. Si no tiene ninguna suscripción, puede agregar una; para ello, debe registrar una evaluación gratuita o comprar un plan de suscripción en Azure Portal.

6. Seleccione un servicio de aplicaciones de la lista. Esto rellenará el código de plantilla para el objeto `MobileServiceClient` con la dirección URL correspondiente del servicio de aplicaciones en Azure:

    [![Seleccione el servicio de aplicaciones en la lista](media/connected-services-image006-sml.png "Seleccione el servicio de aplicaciones en la lista")](media/connected-services-image006.png#lightbox)

    Si no aparece ningún servicio, haga clic en el botón **Nuevo** (consulte el paso 9).

7. Copie el código de plantilla para `MobileServiceClient` en la PCL. La ubicación del archivo no es importante, siempre y cuando solo haya una instancia del mismo.
  El enfoque recomendado es crear una clase `AzureService` que controle todas las interacciones de Azure y utilice `MobileServiceClient`:

    ![Copiar el código de configuración en la aplicación](media/connected-services-image007.png "Copiar el código de configuración en la aplicación")

8. Siga la documentación de **Pasos siguientes** para agregar datos, sincronización sin conexión, autenticación y notificaciones de inserción a la aplicación:

    [![Revisar las instrucciones de Pasos siguientes](media/connected-services-image008-sml.png "Revisar las instrucciones de Pasos siguientes")](media/connected-services-image008.png#lightbox)

9. Si no tiene ningún servicio de aplicaciones existente, puede crear servicios nuevos desde Visual Studio para Mac.
  Haga clic en el botón **Nuevo** en la parte inferior izquierda de la lista de servicios para abrir el cuadro de diálogo **Nuevo servicio de aplicaciones**:

    [![Crear un nuevo servicio de aplicaciones en Visual Studio para Mac](media/connected-services-image009-sml.png "Crear un nuevo servicio de aplicaciones en Visual Studio para Mac")](media/connected-services-image009.png#lightbox)

Un servicio nuevo necesita los parámetros siguientes:

-   **Nombre del servicio de aplicaciones**: nombre o identificador único del plan
-   **Suscripción**: la suscripción que le gustaría utilizar para pagar el servicio
-   **Grupo de recursos**: forma de organizar todos los recursos de Azure de un proyecto. Hay la opción de usar uno existente o crear uno nuevo. Si se trata de su primer servicio de Azure, cree uno nuevo.
-   **Plan del servicio**: determina la ubicación y el coste de todos los recursos que lo utilizan. Hay la opción de usar uno existente o crear uno nuevo. Si se trata de su primer servicio de Azure, utilice el predeterminado o cree uno nuevo en el nivel libre (F1).

Visite la [documentación de las aplicaciones móviles](/azure/app-service-mobile/) para obtener más información.

## <a name="see-also"></a>Vea también

- [Servicios conectados (Visual Studio en Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)