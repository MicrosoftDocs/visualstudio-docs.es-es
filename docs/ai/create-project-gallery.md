---
title: Crear un proyecto en Visual Studio Tools para IA
description: crear un proyecto con un ejemplo de la galería de azure machine learning
keywords: ia, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 18cf719b100aa7c216de2903c05a24a3abcca244
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916496"
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Crear un proyecto de IA desde la galería de Azure Machine Learning en Visual Studio

Azure Machine Learning se integra con Visual Studio Tools para IA. Se puede usar para enviar trabajos de Machine Learning a destinos de procesamiento remoto como máquinas virtuales de Azure, clústeres de Spark y muchos más. Obtenga más información sobre la [Experimentación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration)

Después de haber [instalado Visual Studio Tools para IA](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

> [!NOTE]
> Debe tener instalado Azure Machine Learning Workbench. Para instalarlo, vea el [inicio rápido de instalación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation)

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Herramientas para IA) y elija **Seleccionar un clúster**

    ![Selector de clúster](media/create-project-gallery/select-cluster.png)

2. Inicie sesión en su suscripción de Azure Machine Learning; para ello, haga clic con el botón derecho en el nodo **Azure Machine Learning** en el Explorador de servidores, seleccione **Iniciar sesión** y siga las instrucciones.

    ![inicio de sesión](media/create-project-gallery/azureml-login.png)

3. Seleccione **AI Tools > Azure Machine Learning Sample Gallery** (Herramientas de IA > Galería de ejemplos de Azure Machine Learning).

    ![Galería de ejemplos](media/create-project-gallery/gallery.png)

4. Para este inicio rápido, seleccione el ejemplo "**MNIST using TensorFlow**" y haga clic en **Instalar**. Proporcione lo siguiente:

   - **Grupo de recursos**: grupo de recursos de Azure donde se almacenarán los metadatos
   - **Cuenta**: cuenta de Experimentación de Azure Machine Learning
   - **Área de trabajo**: área de trabajo de Azure Machine Learning
   - **Tipo de proyecto**: el marco de Machine Learning. En este caso, seleccione **TensorFlow**
   - **Agregar a solución**: determina si se va a agregar a la solución de Visual Studio actual o si se va a crear y abrir una solución nueva
   - **Ruta de acceso del proyecto**: ubicación donde se guarda el código
   - **Nombre de proyecto**: escriba **TensorFlowMNIST**

   ![Proyecto resultante al usar la plantilla Aplicación de Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio crea el archivo de proyecto (un archivo `.pyproj` que se almacena en disco) junto con otros archivos definidos en el ejemplo. Con la plantilla "MNIST", el proyecto contiene varios archivos.

    ![mnist](media/create-project-gallery/azml-mnist.png)

6. Envíe el trabajo a Azure Machine Learning.

    ![mnist](media/create-project-gallery/submit-azml.png)

7. Ejecútelo en un contenedor de Docker o en el equipo local

    ![mnist](media/create-project-gallery/azml-local.png)