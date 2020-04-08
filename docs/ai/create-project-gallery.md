---
title: Crear un proyecto
description: crear un proyecto con un ejemplo de la galería de azure machine learning
keywords: ia, visual studio, azure machine learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: fb1158015f1a7065514511b8d62810c937382b7f
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638683"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Crear un proyecto de IA desde la galería de Azure Machine Learning en Visual Studio

Azure Machine Learning se integra con Visual Studio Tools para IA. Se puede usar para enviar trabajos de Machine Learning a destinos de procesamiento remoto como máquinas virtuales de Azure, clústeres de Spark y muchos más. 

Después de haber [instalado Visual Studio Tools para AI](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

> [!NOTE]
> Debe tener instalado Azure Machine Learning Workbench. Para instalarlo, vea el [inicio rápido de instalación de Azure Machine Learning](/azure/machine-learning/preview/quickstart-installation)

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Tools para AI) y elija **Seleccionar un clúster**.

    ![Selector de clúster](media/create-project-gallery/select-cluster.png)

2. Inicie sesión en su suscripción de Azure Machine Learning; para ello, haga clic con el botón derecho en el nodo **Azure Machine Learning** en el Explorador de servidores, seleccione **Iniciar sesión** y siga las instrucciones.

    ![inicio de sesión](media/create-project-gallery/azureml-login.png)

3. Seleccione **AI Tools > Azure Machine Learning Sample Gallery** (Herramientas de IA > Galería de ejemplos de Azure Machine Learning).

    ![Galería de ejemplos](media/create-project-gallery/gallery.png)

4. En este inicio rápido, seleccionaremos el ejemplo "**MNIST using TensorFlow**" y haremos clic en **Instalar**. Proporcione lo siguiente:

   - **Grupo de recursos**: grupo de recursos de Azure donde se almacenarán los metadatos
   - **Cuenta**: cuenta de Experimentación de Azure Machine Learning
   - **Área de trabajo**: área de trabajo de Azure Machine Learning
   - **Tipo de proyecto**: el marco de Machine Learning. En este caso, seleccione **TensorFlow**
   - **Agregar a solución**: determina si se va a agregar a la solución de Visual Studio actual o si se va a crear y abrir una solución nueva
   - **Ruta de acceso del proyecto**: ubicación donde se guarda el código
   - **Nombre de proyecto**: escriba **TensorFlowMNIST**

   ![Proyecto resultante al usar la plantilla de la aplicación Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio crea el archivo de proyecto (un archivo `.pyproj` que se almacena en disco) junto con otros archivos definidos en el ejemplo. Con la plantilla "MNIST", el proyecto contiene varios archivos.

    ![mnist](media/create-project-gallery/azml-mnist.png)

6. Envíe el trabajo a Azure Machine Learning.

    ![mnist](media/create-project-gallery/submit-azml.png)

7. Ejecútelo en un contenedor de Docker o en el equipo local

    ![mnist](media/create-project-gallery/azml-local.png)
