---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube con Visual Studio - Paso 1: Instalar las herramientas | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: b2edc476ffd4648f9ddb0e3d076f8eb400458242
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884959"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introducción a Connected Environment con .NET Core y Visual Studio

En esta guía aprenderá a:

1. Crear en Azure un entorno basado en Kubernetes optimizado para el desarrollo.
1. Desarrollar código de forma iterativa en contenedores usando Visual Studio.
1. Desarrollar dos servicios independientes y usar la detección de servicios DNS de Kubernetes para llamar a otro servicio.
1. Desarrollar y probar el código de manera productiva en un entorno de equipo.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Instalar la CLI de Connected Environment
Connected Environment requiere una configuración mínima del equipo local. La mayor parte de la configuración del entorno de desarrollo se almacena en la nube y se puede compartir con otros usuarios.

1. Descargue y ejecute el [instalador de la CLI de Connected Environment](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Obtener las herramientas de depuración de Kubernetes
Aunque la CLI de Connected Environment se puede usar como una herramienta independiente, los desarrolladores de .NET Core que usen **VS Code** o **Visual Studio** tienen a su disposición algunas características sofisticadas, como la **depuración de Kubernetes**.

### <a name="visual-studio-debugging"></a>Depuración de Visual Studio 
1. Instale la versión más reciente de [Visual Studio 2017](https://www.visualstudio.com/vs/)
1. Asegúrese de que la siguiente carga de trabajo está seleccionada en el instalador de Visual Studio:
    * Desarrollo web y ASP.NET
1. Instale la [extensión de Visual Studio para Connected Environment](https://aka.ms/get-vsce-visualstudio).

Ya estamos preparados para crear una aplicación web ASP.NET con Visual Studio.

> [!div class="nextstepaction"]
> [Crear una aplicación web ASP.NET](get-started-netcore-visualstudio-02.md)
