---
title: Servicios conectados
description: Obtenga información sobre cómo agregar almacenamiento de datos de Azure, autenticación y notificaciones de inserción desde Visual Studio para Mac en una aplicación multiplataforma.
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.topic: how-to
ms.openlocfilehash: 69ad6007283b3c56a8d0e5902cc2b9bdc445f220
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847087"
---
# <a name="connected-services-walkthrough"></a>Tutorial de Servicios conectados

El flujo de trabajo de Servicios conectados integra el flujo de trabajo de Azure Portal en Visual Studio para Mac, por lo que no tiene que salir de su proyecto para agregar servicios.

En este tutorial se muestra cómo agregar un servicio back-end de Azure, que ofrece almacenamiento de datos en la nube, autenticación y notificaciones de inserción a una aplicación multiplataforma de biblioteca de clases portables (PCL) de Xamarin.Forms.

1. Para comenzar, haga doble clic en el nodo **Servicios conectados** de la solución, lo que abre la **Galería de servicios**.
  Se trata de una lista de todos los servicios disponibles para el tipo de aplicación. Haga clic en un servicio (como **Back-end móvil con Azure App Service**) para seleccionarlo.

    [![Nodo Servicios conectados en Visual Studio para Mac](media/connected-services-image001-sml.png "Nodo Servicios conectados en Visual Studio para Mac")](media/connected-services-image001.png#lightbox)

2. En la página Detalles de servicio se incluye una descripción del servicio y las dependencias que deben instalarse.
  Haga clic en el botón **Agregar** para agregar las dependencias a la aplicación:

    [![Back-end móvil con Azure](media/connected-services-image002-sml.png "Back-end móvil con Azure")](media/connected-services-image002.png#lightbox)

3. Para que funcionen, las dependencias deben agregarse a PCL y a los proyectos específicos de la plataforma.
  Seleccione las casillas para agregar el servicio a todos los proyectos que harán referencia a él (directa o indirectamente):

    [![Marcar todos los proyectos que deben hacer referencia al servicio](media/connected-services-image003-sml.png "Activación de todos los proyectos que deben hacer referencia al servicio")](media/connected-services-image003.png#lightbox)

4. Elija **Aceptar** en los cuadros de diálogo **Aceptación de licencia** de los paquetes de NuGet.
  Puede haber dos cuadros de diálogo para aceptar, uno de MobileClient y las dependencias y otro de SQLiteStore, lo cual es necesario para la sincronización de datos sin conexión:

    [![Aceptación de los acuerdos de licencia](media/connected-services-image004-sml.png "Administración de los contratos de licencia")](media/connected-services-image004.png#lightbox)

    ![Ventana de aceptación de licencia](media/connected-services-image005.png "Ventana Aceptación de licencia")

5. Una vez agregadas las dependencias, se le pedirá que inicie sesión con la cuenta que quiere utilizar para comunicarse con Azure.
  Si ya ha iniciado sesión con un identificador de Microsoft, Visual Studio para Mac intentará capturar las suscripciones de Azure y los servicios de aplicación asociados a ellas. Si no tiene ninguna suscripción, puede agregar una; para ello, debe registrar una evaluación gratuita o comprar un plan de suscripción en Azure Portal.

6. Seleccione un servicio de aplicaciones de la lista. Esto rellenará el código de plantilla para el objeto `MobileServiceClient` con la dirección URL correspondiente del servicio de aplicaciones en Azure:

    [![Selección de un servicio de aplicaciones de la lista](media/connected-services-image006-sml.png "Selección de un servicio de aplicaciones de la lista")](media/connected-services-image006.png#lightbox)

    Si no aparece ningún servicio, haga clic en el botón **Nuevo** (consulte el paso 9).

7. Copie el código de plantilla para `MobileServiceClient` en la PCL. La ubicación del archivo no es importante, siempre y cuando solo haya una instancia del mismo.
  El enfoque recomendado es crear una clase `AzureService` que controle todas las interacciones de Azure y utilice `MobileServiceClient`:

    ![Copia del código de configuración en la aplicación](media/connected-services-image007.png "Copia del código de configuración en la aplicación")

8. Siga la documentación de **Pasos siguientes** para agregar datos, sincronización sin conexión, autenticación y notificaciones de inserción a la aplicación:

    [![Revisión de las instrucciones de pasos siguientes](media/connected-services-image008-sml.png "Revisión de las instrucciones de pasos siguientes")](media/connected-services-image008.png#lightbox)

9. Si no tiene ningún servicio de aplicaciones existente, puede crear servicios nuevos desde Visual Studio para Mac.
  Haga clic en el botón **Nuevo** en la parte inferior izquierda de la lista de servicios para abrir el cuadro de diálogo **Nuevo servicio de aplicaciones**:

    [![Creación de un servicio de aplicaciones en Visual Studio para Mac](media/connected-services-image009-sml.png "Creación de un servicio de aplicaciones en Visual Studio para Mac")](media/connected-services-image009.png#lightbox)

Un servicio nuevo necesita los parámetros siguientes:

- **Nombre del servicio de aplicaciones**: nombre o identificador único del plan
- **Suscripción**: la suscripción que le gustaría utilizar para pagar el servicio
- **Grupo de recursos**: forma de organizar todos los recursos de Azure de un proyecto. Hay la opción de usar uno existente o crear uno nuevo. Si se trata de su primer servicio de Azure, cree uno nuevo.
- **Plan del servicio**: determina la ubicación y el coste de todos los recursos que lo utilizan. Hay la opción de usar uno existente o crear uno nuevo. Si se trata de su primer servicio de Azure, utilice el predeterminado o cree uno nuevo en el nivel libre (F1).

Visite la [documentación de las aplicaciones móviles](/azure/app-service-mobile/) para obtener más información.

## <a name="see-also"></a>Consulte también

- [Servicios conectados (Visual Studio en Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)