---
title: Visual Studio con un codespace (versión preliminar)
description: Aprenda a usar el IDE de Visual Studio con GitHub Codespaces para el desarrollo en Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c3a2e14236c2d24bc9650fab81150cc295826844
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006259"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Uso de Visual Studio con un codespace (versión preliminar)

Visual Studio ofrece una gran compatibilidad con el desarrollo en GitHub Codespaces. Puede crear un codespace y conectarse a él y tener toda la eficacia de Visual Studio para trabajar en sus proyectos en un entorno remoto hospedado. Aunque el código fuente y las herramientas se encuentran en un codespace y la compilación y la depuración se realicen en la nube, su experiencia de desarrollo resultará tan rápida y exenta de fricciones como si trabajara localmente. Puede trabajar con un codespace desde Visual Studio 2019 Preview ([registrarse para la versión beta pública limitada](https://github.com/features/codespaces/signup-vs)).

> [!NOTE]
> En este artículo se describe específicamente el uso de Visual Studio para conectarse a GitHub Codespaces. Puede ver cómo conectarse a un codespace con otros clientes en la documentación de [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) o [la documentación](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) de GitHub.

> [!NOTE]
> Si aún no tiene [Visual Studio 2019 Preview](https://aka.ms/vspreview) instalado, puede descargarlo de [visualstudio.microsoft.com](https://aka.ms/vspreview).

## <a name="enable-connect-to-github-codespaces"></a>Habilitación de Conectarse a GitHub Codespaces

La conexión a GitHub Codespaces con Visual Studio 2019 Preview no está habilitada de forma predeterminada, por lo que primero debe habilitar la opción Características en versión preliminar.

1. En Visual Studio 2019 Preview, use el elemento de menú **Herramientas** > **Opciones** para abrir el cuadro de diálogo Opciones.

2. En **Entorno**, seleccione **Características en versión preliminar** y active la característica en versión preliminar **Conectarse a GitHub Codespaces**.

   ![Activación de la característica en versión preliminar Conectarse a GitHub Codespaces](media/connect-to-github-codespaces-preview-feature.png)

3. Tendrá que reiniciar Visual Studio para que la característica esté disponible.

## <a name="create-a-codespace"></a>Creación de un codespace

Si aún no tiene un codespace, puede crear uno desde Visual Studio.

1. Al iniciar Visual Studio, la ventana Inicio mostrará un botón **Connect to a codespace** (Conectarse a un codespace) en "introducción".

   ![Ventana de inicio de Visual Studio con la opción Connect to a codespace (Conectarse a un codespace)](media/visual-studio-start-window.png)

2. Seleccione **Conectarse a un codespace** (Conectarse a un codespace) y se le pedirá que inicie sesión en GitHub. También puede crear una cuenta de GitHub si aún no tiene una.

   ![Inicio de sesión en GitHub en Visual Studio](media/visual-studio-sign-in-to-github.png)

   Una vez que seleccione **Iniciar sesión en GitHub**, siga el flujo de trabajo de inicio de sesión de GitHub en línea.

3. Si nunca ha creado un codespace, se le pedirá que cree uno.

   En "Codespace details" (Detalles de Codespace), debe proporcionar una **dirección URL de repositorio**. GitHub Codespaces clonará el repositorio especificado en el codespace cuando se cree.

   También puede modificar el tiempo de espera de **Tipo de instancia** y **Suspender tras** a través de sus listas desplegables. Una vez que haya establecido los detalles de codespace, seleccione el botón **Create and Connect** (Crear y conectar).

   ![Detalles de Visual Studio codespace](media/visual-studio-codespace-details.png)

   GitHub Codespaces comenzará a preparar el codespace y abrirá Visual Studio cuando el codespace esté listo.

   El nombre de codespace aparecerá en el indicador remoto en la barra de menús.

   ![Visual Studio conectado al codespace del repositorio de eShopOnWeb](media/visual-studio-eshoponweb-codespace.png)

4. Comience a usar Visual Studio de la misma manera que trabajaría de forma local. Pruebe lo siguiente:

   * Examinar código fuente
   * Seleccione un archivo de solución y compile la solución (**Ctrl+Mayús+B**).
   * Establezca un punto de interrupción en un archivo de código fuente y presione **F5** para iniciar la aplicación en el depurador.
   * Realice los cambios y confírmelos en el repositorio.   

> [!NOTE]
> En este momento, no puede crear instancias de GitHub Codespaces para Visual Studio a través del portal [GitHub Codespaces](https://github.com/codespaces). Solo se pueden crear con Visual Studio.

## <a name="connect-to-a-codespace"></a>Conexión a un codespace

Después de crear el codespace, puede abrirlo directamente desde Visual Studio.

1. Al iniciar Visual Studio, la ventana Inicio mostrará un botón **Connect to a Codespace** (Conectarse a un codespace) en "introducción".

   ![Ventana de inicio de Visual Studio con la opción Connect to a codespace (Conectarse a un codespace)](media/visual-studio-start-window.png)

   Si ya se encuentra en Visual Studio, puede usar el elemento de menú **Archivo** > **Connect to a Codespace** (Conectarse a un codespace).

   ![Elemento de menú Archivo > Connect to a codespace (Conectarse a un codespace) de Visual Studio](media/visual-studio-file-connect-to-codespace.png)

2. Seleccione **Connect to a codespace** (Conectarse a un codespace). Si aún no lo ha hecho, se le pedirá que inicie sesión en GitHub.

3. Después verá todas las instancias de GitHub Codespaces, con sus detalles, en el panel derecho.

   ![Visual Studio muestra las instancias de GitHub Codespaces disponibles con sus detalles](media/visual-studio-connect-codespace.png)

   Los codespaces que clonen un repositorio de Azure DevOps solo estarán visibles aquí en Visual Studio y no en la página Codespaces de GitHub.

4. Elija un codespace y seleccione el botón **Conectar**. Si el codespace se ha suspendido, se reiniciará y Visual Studio se abrirá conectado a ese codespace.

   El nombre de codespace aparecerá en el indicador remoto en la barra de menús.

   ![Visual Studio conectado al codespace del repositorio de eShopOnWeb](media/visual-studio-eshoponweb-codespace.png)

5. Comience a usar Visual Studio de la misma manera que trabajaría de forma local. Pruebe lo siguiente:

   * Examinar código fuente
   * Seleccione un archivo de solución y compile la solución (**Ctrl+Mayús+B**).
   * Establezca un punto de interrupción en un archivo de código fuente y presione **F5** para iniciar la aplicación en el depurador.
   * Realice los cambios y confírmelos en el repositorio.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Consulte también

* [¿Qué es GitHub Codespaces?](codespaces-overview.md)
* [Personalización de un codespace](customize-codespaces.md)
* [Características de Visual Studio compatibles](supported-features-codespaces.md)
