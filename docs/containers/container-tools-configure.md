---
title: Configuración de las herramientas de contenedor de Visual Studio
description: Configure las herramientas disponibles en Visual Studio para trabajar con contenedores de Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188779"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Cómo configurar las herramientas de contenedor de Visual Studio

Mediante la configuración de Visual Studio, puede controlar algunos aspectos del funcionamiento de Visual Studio con los contenedores de Docker, incluida la configuración que afecta al rendimiento y al uso de recursos cuando trabaja con contenedores de Docker.

## <a name="container-tools-settings"></a>Configuración de las herramientas de contenedor

En el menú principal, elija **Herramientas > Opciones** y expanda **Herramientas de contenedor > Configuración**. Aparecerá la configuración de las herramientas de contenedor.

::: moniker range="vs-2017"

![Opciones de herramientas de contenedor en Visual Studio, que muestran: Extraer automáticamente las imágenes de Docker necesarias al cargar el proyecto, Iniciar automáticamente los contenedores en segundo plano, Terminar automáticamente los contenedores al cerrar la solución y No pedir confirmación para confiar en el certificado SSL de localhost.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Configuración **general** de las herramientas de contenedor:

![Opciones de herramientas de contenedor en Visual Studio, que muestran: Instale Docker Desktop si es necesario y confíe en el certificado SSL de ASP.NET Core.](./media/configure-container-tools/tools-options-1.png)

Configuración de un **proyecto único** y **Docker Compose** de las herramientas de contenedor:

![Opciones de herramientas de contenedor en Visual Studio, que muestran: Terminar contenedores al cerrar el proyecto, extraer las imágenes necesarias de Docker al abrir el proyecto y ejecutar contenedores al abrir el proyecto.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

La tabla siguiente puede ayudarle a decidir cómo configurar estas opciones.

::: moniker range="vs-2017"
| Name | Configuración predeterminada | Se aplica a | DESCRIPCIÓN |
| -----|:---------------:|:----------:| ----------- |
| Extraer automáticamente las imágenes de Docker necesarias al cargar el proyecto | Activado | Docker Compose | Para aumentar el rendimiento al cargar proyectos, Visual Studio iniciará una operación docker pull en segundo plano para que cuando se esté listo para ejecutar el código, la imagen ya esté descargada o en proceso de descarga. Si simplemente carga proyectos y explora código, puede desactivar esta opción para evitar la descarga de imágenes de contenedor que no son necesarias. |
| Iniciar automáticamente los contenedores en segundo plano | Activado | Docker Compose | Una vez más, para aumentar el rendimiento, Visual Studio crea un contenedor con montajes de volumen listos para cuando se compile y ejecute el contenedor. Si desea controlar cuándo se crea el contenedor, desactive esta opción. |
| Terminar automáticamente los contenedores al cerrar la solución | Activado | Docker Compose | Desactive esta opción si quiere que los contenedores de la solución sigan ejecutándose después de cerrar la solución o de cerrar Visual Studio. |
| No pedir confirmación para confiar en el certificado SSL de localhost | Desactivado | Proyectos de ASP.NET Core 2.1 | Si el certificado SSL de localhost no es de confianza, Visual Studio le pedirá confirmación cada vez que ejecute el proyecto, a menos que se active esta casilla. |
::: moniker-end

::: moniker range=">=vs-2019"

En la siguiente tabla se describe la configuración **general**:

| Name | Configuración predeterminada | Se aplica a | DESCRIPCIÓN |
| -----|:---------------:|:----------:| ----------- |
| Instalar Docker Desktop si es necesario | Preguntarme | Proyecto único, Docker Compose | Elija si desea que se le pregunte si Docker Desktop no está instalado. |
| Confiar en el certificado SSL de ASP.NET Core | Preguntarme | Proyectos de ASP.NET Core 2.x | Cuando se establece en **Preguntarme**, si el certificado SSL de localhost no es de confianza, Visual Studio le pedirá confirmación cada vez que ejecute el proyecto. |

En la siguiente tabla se describe la configuración de **Proyecto único** y **Docker Compose**:

| Name | Configuración predeterminada | Se aplica a | DESCRIPCIÓN |
| -----|:---------------:|:----------:| ----------- |
| Extraer las imágenes de Docker necesarias al abrir el proyecto | True | Proyecto único, Docker Compose | Para aumentar el rendimiento al cargar proyectos, Visual Studio iniciará una operación docker pull en segundo plano para que cuando se esté listo para ejecutar el código, la imagen ya esté descargada o en proceso de descarga. Si simplemente carga proyectos y explora código, puede establecer esta opción en **False** para evitar la descarga de imágenes de contenedor que no son necesarias. |
| Ejecutar contenedores al abrir el proyecto | True | Proyecto único, Docker Compose | Una vez más, para aumentar el rendimiento, Visual Studio crea un contenedor de antemano listo para cuando se compile y ejecute el contenedor. Si desea controlar cuándo se crea el contenedor, establezca esta opción en **False**. |
| Detener los contenedores al cerrar el proyecto | True | Proyecto único y Docker Compose | Establezca en **False** si quiere que los contenedores de la solución sigan ejecutándose después de cerrar la solución o de cerrar Visual Studio. |

::: moniker-end
> [!WARNING]
> Si el certificado SSL de localhost no es de confianza y se activa la casilla de supresión de la confirmación, las solicitudes HTTPS web pueden producir un error en tiempo de ejecución en la aplicación o el servicio. En ese caso, desmarque la casilla **Do not prompt** (No pedir confirmación), ejecute el proyecto e indique que confía en la solicitud.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo trabajar con contenedores en Visual Studio, consulte la [introducción](overview.md).