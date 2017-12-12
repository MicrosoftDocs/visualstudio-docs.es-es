---
title: Crear un proyecto en Tools para AI en Visual Studio
description: "crear un proyecto con un ejemplo de la galería de Azure Machine Learning"
keywords: AI, Visual Studio, Azure Machine Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.technology: visual studio
ms.devlang: multiple
ms.service: multiple
ms.openlocfilehash: 2d8b5f1d06d31eaba9c75e0f0515b2526fc7efdf
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Crear un proyecto de AI desde la Galería de Azure Machine Learning en Visual Studio

Azure Machine Learning se integra con Visual Studio Tools para AI. Puede usarlo para enviar trabajos de Machine Learning a destinos de procesamiento remoto como, entre otros muchos, máquinas virtuales de Azure y clústeres de Spark. Obtenga más información sobre la [Experimentación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration). 

Después de haber [instalado Visual Studio Tools para AI](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

> ! Debe tener instalado Azure Machine Learning Workbench. Para instalarlo, vea el [inicio rápido de instalación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation). 

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Tools para AI) y elija **Seleccionar un clúster**.  

    ![Selección de clúster](media\create-project\select-cluster.png)

1. Inicie sesión en su suscripción de Azure Machine Learning; para ello, haga clic con el botón derecho en el nodo **Azure Machine Learning** en el Explorador de servidores, seleccione **Iniciar sesión** y siga las instrucciones.

    ![Inicio de sesión](media\create-project\azureml-login.png)
 
2. Seleccione **AI Tools > Azure Machine Learning Sample Gallery** (Tools para AI > Galería de ejemplos de Azure Machine Learning). 
    
    ![Galería de ejemplos](media\create-project\gallery.png)

1. En este inicio rápido, seleccionaremos el ejemplo "**MNIST using TensorFlow**" y haremos clic en **Instalar**. Indique lo siguiente: 
2.
 - **Grupo de recursos**: grupo de recursos de Azure donde se almacenarán los metadatos.
 - **Cuenta**: cuenta de Experimentación de Azure Machine Learning.
 - **Área de trabajo**: área de trabajo de Azure Machine Learning.
 - **Tipo de proyecto**: marco de Machine Learning. En este caso, elegiremos **TensorFlow**.
 - **Agregar a solución**: determina si se va a agregar a la solución de Visual Studio actual o si se va a crear y abrir una nueva solución.
 - **Ruta del proyecto**: ubicación donde guardar el código.
 - **Nombre de proyecto**: escriba **TensorFlowMNIST**.
   

    ![Proyecto resultante al usar la plantilla de la aplicación Python](media\create-project\new-AzureSampleProject.png)

1. Visual Studio crea el archivo de proyecto (un archivo `.pyproj` que se almacena en disco) junto con otros archivos definidos en el ejemplo. Con la plantilla "MNIST", el proyecto contiene varios archivos.

    ![mnist](media\create-project\azml-mnist.png)

1. Envíe el trabajo a Azure Machine Learning. 

    ![mnist](media\create-project\submit-azml.png)

1. Ejecútelo en un contenedor de Docker o en su equipo local.

    ![mnist](media\create-project\azml-local.png)