---
title: "Publicación de una aplicación de Python en Azure App Service desde Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 0163d1279b41ef8fecf9ca774cd3e67f0f47f1b1
ms.lasthandoff: 03/07/2017

---

# <a name="publishing-to-azure-app-service"></a>Publicación en Azure App Service

Puede empezar rápidamente a compilar un sitio web de Python en Visual Studio y publicarlo en Azure App Service mediante los pasos siguientes:

- [Creación de una suscripción de Azure](#create-an-azure-subscription)
- [Creación y prueba del proyecto inicial](#create-and-test-the-initial-project)
- [Publicación en Azure App Service](#publish-to-azure-app-service)

Puede encontrar un breve tutorial de este proceso en el vídeo de youtube.com (3 minutos y 10 segundos) [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (Tutorial de Python en Visual Studio: compilar un sitio web). 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>Creación de una suscripción de Azure

La publicación en Azure requiere una suscripción de Azure, o puede utilizar un sitio temporal.

Para las suscripciones, empiece con una [cuenta completa de Azure gratuita](https://azure.microsoft.com/en-us/free/), que incluye créditos más amplios para servicios de Azure. Considere también la posibilidad de registrarse para [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/), que le ofrece un crédito de&25; USD cada mes durante un año completo.

Para crear un sitio temporal en Azure App Service sin necesidad de una suscripción de Azure:

1. Abra el explorador en [try.azurewebsites.net](https://try.azurewebsites.net).
1. Seleccione **Aplicación web** para el tipo de aplicación, a continuación, seleccione **Siguiente**.
1. Seleccione **Empty Site** (Sitio vacío) para la plantilla y luego seleccione **Crear >**.
1. Inicie sesión con el inicio de sesión social que prefiera y, después de un breve período de tiempo, el sitio estará listo en la dirección URL mostrada.
1. Seleccione **Descargar el perfil de publicación** y guarde el archivo `.publishsettings`, que usará más adelante.

## <a name="create-and-test-the-initial-project"></a>Creación y prueba del proyecto inicial

1. En Visual Studio, seleccione **Archivo > Nuevo > Proyecto**, busque "Bottle", seleccione el **Proyecto web Bottle** y haga clic en **Aceptar**.    

1. Cuando se le solicite que instale paquetes externos, seleccione **Install into a virtual environment** (Instalar en un entorno virtual). Tenga en cuenta el control **Show required packages** (Mostrar paquetes necesarios) que aparece en la parte inferior del cuadro de diálogo, que le mostrará qué paquetes se instalarán:

  ![Instalación de los paquetes necesarios](media/tutorials-common-external-packages.png)

1. Seleccione el intérprete base preferido para el entorno virtual (por ejemplo, **Python 2.7** o **Python 3.4**) y haga clic en **Crear**:

  ![Incorporación de un entorno virtual al crear un proyecto](media/tutorials-common-add-virtual-environment.png)

1. Una vez creado el proyecto, pruébelo localmente seleccionando **Depurar > Iniciar depuración** o presionando F5. De forma predeterminada, la aplicación utiliza un repositorio en memoria que no requiere ninguna configuración. Todos los datos se pierden cuando el servidor web se detiene.

1. Haga clic en la aplicación para ver su funcionamiento.

1. Detenga el depurador cuando haya terminado (**Depurar > Detener depuración** o Mayús-F5).

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y seleccione **Publicar**. 

1. En el cuadro de diálogo **Publicar**, seleccione **Microsoft Azure App Service**:

  ![Publicar en Azure - Paso 1](media/tutorials-common-publish-1.png)

1. Seleccione un destino:

    - Si tiene una suscripción de Azure, seleccione **Microsoft Azure App Service** como el destino de publicación y luego, en el cuadro de diálogo siguiente, seleccione un servicio de aplicación existente o **Nuevo** para crear uno nuevo.
    - Si utiliza un sitio temporal de try.azurewebsites.net, seleccione **Importar** como el destino de publicación y luego busque el archivo `.publishsettings` descargado del sitio y seleccione **Aceptar**.

1. Los detalles de App Service aparecen en la pestaña **Conexión** del cuadro de diálogo **Publicar** que se muestra a continuación.

  ![Publicar en Azure - Paso 2](media/tutorials-common-publish-2.png)

1. Seleccione **siguiente >** según sea necesario para revisar la configuración adicional. Si pretende [depurar de forma remota el código Python en Azure](debugging-azure-remote.md), debe establecer **Configuración** en **Depurar**.
1. Seleccione **Publicar**. Una vez implementada la aplicación en Azure, se abre el explorador predeterminado en ese sitio. 
