---
title: Depuración publicados Azure servicio en la nube con Visual Studio e IntelliTrace | Microsoft Docs
description: Obtenga información sobre cómo depurar un servicio en la nube con Visual Studio e IntelliTrace
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002946"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Depuración de un servicio en la nube de Azure publicado con Visual Studio e IntelliTrace
Con IntelliTrace, puede registrar información de depuración amplia para una instancia de rol cuando se ejecuta en Azure. Si necesita encontrar la causa de un problema, puede usar los registros de IntelliTrace para recorrer el código de Visual Studio como si se estuviera ejecutando en Azure. De hecho, IntelliTrace graba clave datos de entorno y ejecución de código cuando la aplicación de Azure se ejecuta como un servicio en la nube de Azure y le permite reproducir los datos grabados desde Visual Studio. 

Puede utilizar IntelliTrace si tiene instalado Visual Studio Enterprise y los destinos de la aplicación de Azure .NET Framework 4 o una versión posterior. IntelliTrace recopila información de roles de Azure. Las máquinas virtuales para estos roles siempre ejecutan sistemas operativos de 64 bits.

Como alternativa, puede usar [depuración remota](http://go.microsoft.com/fwlink/p/?LinkId=623041) para conectarse directamente a un servicio en la nube que se ejecuta en Azure.

> [!IMPORTANT]
> IntelliTrace está pensado para escenarios de depuración solo y no debe usarse para una implementación de producción.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Configurar una aplicación de Azure para IntelliTrace
Para habilitar IntelliTrace para una aplicación de Azure, debe crear y publicar la aplicación desde un proyecto de Azure en Visual Studio. Debe configurar IntelliTrace para su aplicación de Azure antes de publicarla en Azure. Si publica la aplicación sin configurar IntelliTrace, deberá volver a publicar el proyecto. Para obtener más información, consulte [una nube de Azure de la publicación de servicios de proyectos con Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Cuando esté listo para implementar la aplicación de Azure, compruebe que los destinos de compilación del proyecto se establecen en **depurar**.

1. En **el Explorador de soluciones**, haga clic en proyecto y, en el menú contextual, seleccione **publicar**.
   
1. En el **publicar aplicación de Azure** cuadro de diálogo, seleccione la suscripción de Azure y seleccione **siguiente**.

1. En el **configuración** página, seleccione el **configuración avanzada** ficha.

1. Activar el **Habilitar IntelliTrace** opción para recopilar registros de IntelliTrace para la aplicación cuando se publica en la nube.
   
1. Para personalizar la configuración de IntelliTrace básica, seleccione **configuración** junto a **Habilitar IntelliTrace**.

    ![Vínculo de configuración de IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. En el **configuración de IntelliTrace** cuadro de diálogo, puede especificar qué eventos de registro, si desea recopilar información de llamadas, qué módulos y procesos para recopilar registros y cuánto espacio asignar a la grabación. Para obtener más información sobre IntelliTrace, vea [depuración con IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![Configuración de IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

El registro de IntelliTrace es un archivo de registro circular del tamaño máximo especificado en la configuración de IntelliTrace (el tamaño predeterminado es 250 MB). Los registros de IntelliTrace se recopilan en un archivo en el sistema de archivos de la máquina virtual. Cuando se solicita los registros, una instantánea se deja en ese momento dado y descargada en el equipo local.

Una vez publicado el servicio de nube de Azure en Azure, puede determinar si se ha habilitado IntelliTrace desde el nodo de Azure en **Explorador de servidores**, tal y como se muestra en la siguiente imagen:

![Explorador de servidores: IntelliTrace habilitado](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Descargar los registros de IntelliTrace para una instancia de rol
Con Visual Studio, puede descargar los registros de IntelliTrace para una instancia de rol siguiendo estos pasos:

1. En **Explorador de servidores**, expanda el **servicios en la nube** nodo y busque la instancia de rol cuyos registros desea descargar. 

1. Haga clic en la instancia de rol y, en el menú contextual, seleccione **ver registros de IntelliTrace**. 

    ![Ver la opción de menú de los registros de IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Los registros de IntelliTrace se descargan en un archivo en un directorio en el equipo local. Cada vez que se solicita el IntelliTrace registra, se crea una nueva instantánea. Mientras se descargan los registros, Visual Studio muestra el progreso de la operación en el **Azure Activity Log** ventana. Como se muestra en la ilustración siguiente, puede expandir el elemento de línea para la operación ver más detalles.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Puede continuar trabajando en Visual Studio mientras se descargan los registros de IntelliTrace. Cuando haya terminado de descargarse el registro, se abre en Visual Studio.

> [!NOTE]
> Los registros de IntelliTrace podrían contener las excepciones que el marco genera y maneja posteriormente. Código del marco interno genera estas excepciones como parte normal de inicio de un rol, por lo que puede omitirlas.
> 
> 

## <a name="next-steps"></a>Pasos siguientes
- [Opciones para depurar los servicios de nube de Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publicación de un servicio de nube de Azure con Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)