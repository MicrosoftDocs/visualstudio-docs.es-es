---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube con Visual Studio - Paso 3: Crear un entorno de desarrollo de Kubernetes | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: 01451ca57cbd4bac5c6bf08d040905b9463b15a3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introducción a Connected Environment con .NET Core y Visual Studio

Paso anterior: [Crear una aplicación web ASP.NET](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Crear un entorno de desarrollo en Azure
Con Connected Environment, puede crear entornos de desarrollo basados en Kubernetes totalmente administrables con Azure y optimizados para el desarrollo. Teniendo abierto el proyecto que acabamos de crear, seleccione **Connected Environment para AKS** en la lista desplegable de configuración de inicio, como se indica aquí.

![](images/LaunchSettings.png)

En el cuadro de diálogo que se abre, asegúrese de haber iniciado sesión con la cuenta adecuada y, luego, seleccione un entorno de desarrollo existente o **<Crear nuevo Connected Environment para AKS...>** para crear uno desde cero.

![](images/ConnectedEnvDialog.png)

Puede dejar los valores predeterminados proporcionados o ajustarlos a sus preferencias. Haga clic en **Aceptar** cuando haya definido los valores de forma adecuada.

![](images/NewEnvDialog.png)

En el cuadro de diálogo anterior, dejemos por ahora la lista desplegable **Espacio** establecida en `mainline` de forma predeterminada. Nos detendremos en esto más adelante. Active la casilla **Accesible públicamente** para que la aplicación web sea accesible a través de un punto de conexión público. Esto no es obligatorio, pero nos será útil para explicar algunos conceptos más adelante en este tutorial. En cualquier caso, no se preocupe: podrá depurar el sitio web con Visual Studio.

![](images/ConnectedEnvDialog2.png)

Haga clic en **Aceptar** para seleccionar o crear el entorno de desarrollo. Se iniciará una tarea en segundo plano para llevar esto a cabo que tardará unos minutos en completarse. Para comprobar si todavía está en curso, desplace el cursor por el icono **Tareas en segundo plano** en la esquina inferior izquierda de la barra de estado (ver abajo).

![](images/BackgroundTasks.png)

> [!Note]
No podrá depurar la aplicación hasta que el entorno de desarrollo se haya creado correctamente.

## <a name="look-at-the-files-added-to-project"></a>Ver los archivos agregados al proyecto
Mientras esperamos a que el entorno de desarrollo se cree, echemos un vistazo a los archivos que se agregaron al proyecto cuando decidimos usar un entorno de desarrollo.

En primer lugar, veremos que se ha agregado una carpeta denominada `charts` y que, dentro de ella, se ha creado un [gráfico de Helm](https://docs.helm.sh) para la aplicación usando scaffolding. Estos archivos se usan para implementar la aplicación en el entorno de desarrollo.

Veremos que se ha agregado un archivo denominado `Dockerfile`. Este archivo contiene la información necesaria para empaquetar la aplicación en formato de Docker estándar. También se ha creado un archivo `HeaderPropagation.cs`; nos detendremos en este archivo más adelante en el tutorial. 

Por último, veremos un archivo denominado `vsce.yaml` que contiene la información de configuración necesaria para el entorno de desarrollo, por ejemplo, si la aplicación debe ser accesible a través de un punto de conexión público.

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Depurar un contenedor en Kubernetes](get-started-netcore-visualstudio-04.md)