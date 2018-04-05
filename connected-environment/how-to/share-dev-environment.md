---
title: Cómo compartir un entorno de desarrollo | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 3/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: 9808e1ac3a6d7b3381b807bc0ce209e15f3e97cf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="share-a-development-environment"></a>Compartir un entorno de desarrollo

Con Connected Environment, se puede compartir un entorno de desarrollo con los demás miembros del equipo. Cada programador puede trabajar en su propio espacio sin riesgo de romper el código de los demás. Además, trabajar juntos en un mismo entorno posibilita que se pueda probar código de un extremo a otro sin tener que crear simulaciones de dependencias. Vea la guía [Nociones del desarrollo en equipo](../get-started-nodejs-06.md) para más información.

Para configurar un entorno para varios desarrolladores:
1. [Cree un Connected Environment en Azure](../get-started.md). Deberá tener acceso de propietario o de colaborador a la suscripción de Azure seleccionada.
1. Configure el **grupo de recursos** del entorno para [conceder acceso de colaborador](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure) a cada miembro del equipo. Para comprobar el grupo de recursos de un entorno, ejecute este comando: `vsce env list`.
1. Pida a los miembros del equipo que **seleccionen el entorno** para poder desarrollar en él.
     * **Línea de comandos o VS Code**: Para ver los Connected Environments existentes a los que se tiene acceso: `vsce env list`. Para seleccionar un entorno: `vsce env select`.
     * **IDE de Visual Studio**: abra un proyecto en Visual Studio y seleccione **Connected Environment para AKS** en la lista desplegable de configuración de inicio. En el cuadro de diálogo que se abre, seleccione un entorno de desarrollo existente.

![Lista de configuración de inicio de Visual Studio](../images/LaunchSettings.png)