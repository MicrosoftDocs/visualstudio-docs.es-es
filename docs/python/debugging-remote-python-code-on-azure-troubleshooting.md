---
title: Solución de problemas de depuración remota de Azure para Python
description: Describe cómo solucionar problemas al intentar depurar una aplicación de Python en ejecución en Azure App Service con Visual Studio.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341468"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Solucionador de problemas de depuración remota para Python y Azure

Visual Studio no puede conectarse con [Azure App Service para realizar la depuración remota](debugging-remote-python-code-on-azure.md) por alguno de los siguientes motivos:

| Motivo | Resolución |
| --- | --- |
| No tiene instalado Visual Studio 2013 Update 4 o versiones superiores. | Instale una versión adecuada desde [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). |
| El proyecto que está implementado en App Service no coincide con el que está abierto en Visual Studio. | Cargue el proyecto correcto en Visual Studio. |
| El proyecto no se implementó con la configuración de **depuración**. | Vuelva a implementar la aplicación; para ello, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Publicar**. En la pestaña **Configuración**, asegúrese de que **Depurar** es la configuración seleccionada. |
| App Service no se está ejecutando. | Inícielo desde el **Explorador de servidores** de Visual Studio o desde Azure Portal. |
| App Service no está configurado para sockets web. | Vaya a [Azure Portal](https://portal.azure.com), desplácese a su instancia de App Service, abra **Configuración** > **Configuración de la aplicación**, establezca **Configuración general** > **Sockets web** en **Activado** y haga clic en **Guardar**. (Tenga en cuenta que las opciones de **depuración** mostradas en esta hoja *no* se aplican a la depuración de Python). |
| *web.debug.config* se ha modificado para deshabilitar el proxy de depuración. | Elimine el archivo y vuelva a publicar el proyecto en App Service; en el transcurso de esta operación, Visual Studio vuelve a crear el archivo. |

Vea también:

- [Depuración remota de Azure para Python](debugging-remote-python-code-on-azure.md)
