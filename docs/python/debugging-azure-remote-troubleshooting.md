---
title: "Solución de problemas de depuración remota de Azure para Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- azure
ms.openlocfilehash: 4d64338d619cbff77333e6518569d5e3b8376e36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="remote-debugging-rroubleshooter-for-python-and-azure"></a>Solucionador de problemas de depuración remota para Python y Azure

Visual Studio no puede conectarse con [Azure App Service para realizar la depuración remota](debugging-azure-remote.md) por alguno de los siguientes motivos:

| Motivo | Resolución |
| --- | --- |
| No tiene instalado Visual Studio 2013 Update 4 o versiones superiores. | Instale una versión adecuada desde [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| El proyecto que está implementado en App Service no coincide con el que está abierto en Visual Studio. | Cargue el proyecto correcto en Visual Studio. |
| El proyecto no se implementó con la configuración de depuración. | Vuelva a implementar la aplicación; para ello, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y seleccione **Publicar**. En la pestaña **Configuración**, asegúrese de que **Depurar** es la configuración seleccionada. |
| App Service no se está ejecutando. | Inícielo desde el Explorador de servidores de Visual Studio o desde el portal de Azure. |
| App Service no está configurado para sockets web. | Vaya al [portal de Azure](https://portal.azure.com), desplácese a su instancia de App Service, abra la hoja **Configuración > Configuración de la aplicación**, establezca **Configuración general > Sockets web** en **Activado** y seleccione **Guardar**. (Tenga en cuenta que las opciones de **depuración** mostradas en esta hoja *no* se aplican a la depuración de Python). |
| `web.debug.config` se ha modificado para deshabilitar el proxy de depuración. | Elimine el archivo y vuelva a publicar el proyecto en App Service; en el transcurso de esta operación, Visual Studio vuelve a crear el archivo. |

Vea también:

- [Depuración remota de Azure para Python](debugging-azure-remote.md)
