---
title: Crear un proyecto en Visual Studio Tools para IA
description: "crear un proyecto con un ejemplo de la galería de azure machine learning"
keywords: ia, visual studio, azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.devlang: multiple
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: 0b45aa6b2ddfb37b99f7f1d92d4d2b205e905488
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Crear un proyecto de IA desde la galería de Azure Machine Learning en Visual Studio

Azure Machine Learning se integra con Visual Studio Tools para IA. Se puede usar para enviar trabajos de Machine Learning a destinos de procesamiento remoto como máquinas virtuales de Azure, clústeres de Spark y muchos más. Obtenga más información sobre la [Experimentación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration) 

Después de haber [instalado Visual Studio Tools para IA](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

> [!NOTE] 
> Debe tener instalado Azure Machine Learning Workbench. Para instalarlo, vea el [inicio rápido de instalación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation) 

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Herramientas para IA) y elija **Seleccionar un clúster**  

    ![Selector de clúster](media\create-project-gallery\select-cluster.png)

1. Inicie sesión en su suscripción de Azure Machine Learning; para ello, haga clic con el botón derecho en el nodo **Azure Machine Learning** en el Explorador de servidores, seleccione **Iniciar sesión** y siga las instrucciones.

    ![inicio de sesión](media\create-project-gallery\azureml-login.png)
 
2. Seleccione **AI Tools > Azure Machine Learning Sample Gallery** (Herramientas de IA > Galería de ejemplos de Azure Machine Learning). 
    
    ![Galería de ejemplos](media\create-project-gallery\gallery.png)

1. Para este inicio rápido, seleccione el ejemplo "**MNIST using TensorFlow**" y haga clic en **Instalar**. Proporcione lo siguiente:

 - **Grupo de recursos**: grupo de recursos de Azure donde se almacenarán los metadatos
 - **Cuenta**: cuenta de Experimentación de Azure Machine Learning
 - **Área de trabajo**: área de trabajo de Azure Machine Learning
 - **Tipo de proyecto**: el marco de Machine Learning. En este caso, seleccione **TensorFlow**
 - **Agregar a solución**: determina si se va a agregar a la solución de Visual Studio actual o si se va a crear y abrir una solución nueva
 - **Ruta de acceso del proyecto**: ubicación donde se guarda el código
 - **Nombre de proyecto**: escriba **TensorFlowMNIST**
   
![Proyecto resultante al usar la plantilla Aplicación de Python](media/create-project-gallery/new-AzureSampleProject.png)

1. Visual Studio crea el archivo de proyecto (un archivo `.pyproj` que se almacena en disco) junto con otros archivos definidos en el ejemplo. Con la plantilla "MNIST", el proyecto contiene varios archivos.

    ![mnist](media\create-project-gallery\azml-mnist.png)

1. Envíe el trabajo a Azure Machine Learning. 

    ![mnist](media\create-project-gallery\submit-azml.png)

1. Ejecútelo en un contenedor de Docker o en el equipo local

    ![mnist](media\create-project-gallery\azml-local.png)