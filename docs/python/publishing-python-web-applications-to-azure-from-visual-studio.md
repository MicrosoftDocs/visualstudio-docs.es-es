---
title: Publicación de una aplicación de Python en Azure App Service
description: Las opciones para publicar una aplicación de Python en Azure App Service, incluida la implementación en Git y contenedores para Linux, y la implementación en IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: c3c8d6c16f2f7e432b6b5e988bf63521f3dfc8c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784120"
---
# <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

Actualmente, Python es compatible con Azure App Service para Linux y se pueden publicar aplicaciones con la [implementación de Git](#publish-to-app-service-on-linux-using-git-deploy) y los [contenedores](#publish-to-app-service-on-linux-using-containers), tal como se describe en este artículo.

> [!Note]
> La compatibilidad de Python con Azure App Service para Windows oficialmente entró en desuso. Como resultado, el comando **Publish** de Visual Studio solo se admite oficialmente para un [destino de IIS](#publish-to-iis) y la depuración remota de Azure App Service ya no se admite de manera oficial.
>
> Sin embargo, las características de [publicación en App Service en Windows](publish-to-app-service-windows.md) sigue funcionando por el momento, porque las extensiones de Python para App Service en Windows siguen disponibles, pero no se actualizarán ni atenderán.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publicación en App Service en Linux mediante la implementación de Git

La implementación de Git conecta una instancia de App Service en Linux con una rama específica de un repositorio Git. La confirmación de código en esa rama se implementa de manera automática en la instancia de App Service y App Service instala automáticamente cualquier dependencia que aparece en *requirements.txt*. En este caso, App Service en Linux ejecuta el código en una imagen de contenedor configurada previamente que usa el servidor web Gunicorn. Actualmente, este servicio está en versión preliminar y no es compatible con su uso en producción.

Para más información, consulte los artículos siguientes en la documentación de Azure:

- [Inicio rápido: Creación de una aplicación web de Python en Azure App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) brinda un breve tutorial del proceso de implementación de Git mediante una aplicación Flask sencilla e implementación desde un repositorio Git local.
- El artículo sobre [cómo configurar Python](/azure/app-service/containers/how-to-configure-python) describe las características del contenedor de App Service en Linux y cómo personalizar el comando de inicio de Gunicorn para la aplicación.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publicación en App Service en Linux mediante los contenedores

En lugar de confiar en el contenedor creado previamente con App Service en Linux, puede proporcionar su propio contenedor. Esta opción permite elegir qué servidores web se usarán y personalizar el comportamiento del contenedor.

Existen dos opciones para crear, administrar e insertar contenedores:

- Use Visual Studio Code y las extensiones de Docker, tal como se describe en el artículo sobre la [implementación de Python con contenedores de Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Incluso si no usa Visual Studio Code, en el artículo se proporcionan detalles útiles sobre cómo compilar imágenes de contenedor para aplicaciones de Flask o Django con los servidores web uwsgi y nginx preparados para el entorno de producción. Luego puede implementar esos mismos contenedores con la CLI de Azure.

- Use la línea de comandos y la CLI de Azure, tal como se describe en este artículo sobre el [uso de una imagen personalizada de Docker](/azure/app-service/containers/tutorial-custom-docker-image) de la documentación de Azure. Esta guía es genérica, pero no específica para Python.

## <a name="publish-to-iis"></a>Publicación en IIS

Desde Visual Studio, puede publicar en una máquina virtual Windows u otro equipo compatible con IIS con el comando **Publish**. Cuando use IIS, asegúrese de crear o modificar un archivo *web.config* en la aplicación que indique a IIS dónde encontrar el intérprete de Python. Para más información, consulte el artículo sobre cómo [configurar aplicaciones web para IIS](configure-web-apps-for-iis-windows.md).
