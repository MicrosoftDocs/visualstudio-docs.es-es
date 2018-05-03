---
title: Solución de problemas de depuración remota de Azure para Python
description: Describe cómo solucionar problemas al intentar depurar una aplicación de Python en ejecución en Azure App Service con Visual Studio.
ms.date: 07/12/2017
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
ms.openlocfilehash: 3d792a411867686abe0734fc67dfe654320d8b38
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Solucionador de problemas de depuración remota para Python y Azure

Visual Studio no puede conectarse con [Azure App Service para realizar la depuración remota](debugging-remote-python-code-on-azure.md) por alguno de los siguientes motivos:

| Motivo | Resolución |
| --- | --- |
| No tiene instalado Visual Studio 2013 Update 4 o versiones superiores. | Instale una versión adecuada desde [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| El proyecto que está implementado en App Service no coincide con el que está abierto en Visual Studio. | Cargue el proyecto correcto en Visual Studio. |
| El proyecto no se implementó con la configuración de depuración. | Vuelva a implementar la aplicación; para ello, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y seleccione **Publicar**. En la pestaña **Configuración**, asegúrese de que **Depurar** es la configuración seleccionada. |
| App Service no se está ejecutando. | Inícielo desde el Explorador de servidores de Visual Studio o desde el portal de Azure. |
| App Service no está configurado para sockets web. | Vaya al [portal de Azure](https://portal.azure.com), desplácese a su instancia de App Service, abra la hoja **Configuración > Configuración de la aplicación**, establezca **Configuración general > Sockets web** en **Activado** y seleccione **Guardar**. (Tenga en cuenta que las opciones de **depuración** mostradas en esta hoja *no* se aplican a la depuración de Python). |
| `web.debug.config` se ha modificado para deshabilitar el proxy de depuración. | Elimine el archivo y vuelva a publicar el proyecto en App Service; en el transcurso de esta operación, Visual Studio vuelve a crear el archivo. |

Vea también:

- [Depuración remota de Azure para Python](debugging-remote-python-code-on-azure.md)
