---
title: Crear un proyecto
description: crear un proyecto con un ejemplo de la galería de azure machine learning
keywords: ia, visual studio, azure machine learning
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: e6c5b8201b39f82e4c4645196ca543e2567b6e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841554"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Crear un proyecto de IA desde la galería de Azure Machine Learning en Visual Studio

Azure Machine Learning se integra con Visual Studio Tools para IA. Se puede usar para enviar trabajos de Machine Learning a destinos de procesamiento remoto como máquinas virtuales de Azure, clústeres de Spark y muchos más. 

Después de haber [instalado Visual Studio Tools para IA](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

> [!NOTE]
> Debe tener instalado Azure Machine Learning Workbench. 

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Herramientas para IA) y elija **Seleccionar un clúster**

    ![Selector de clúster](media/create-project-gallery/select-cluster.png)

2. Inicie sesión en su suscripción de Azure Machine Learning; para ello, haga clic con el botón derecho en el nodo **Azure Machine Learning** en el Explorador de servidores, seleccione **Iniciar sesión** y siga las instrucciones.

    ![inicio de sesión](media/create-project-gallery/azureml-login.png)

3. Seleccione **AI Tools > Azure Machine Learning Sample Gallery** (Herramientas de IA > Galería de ejemplos de Azure Machine Learning).

    ![Galería de ejemplos](media/create-project-gallery/gallery.png)

4. Para este inicio rápido, seleccione el ejemplo "**MNIST using TensorFlow**" y haga clic en **Instalar**. Proporcione lo siguiente:

   - **Grupo de recursos**: Grupo de recursos de Azure donde se van a almacenar los metadatos
   - **Cuenta**: Cuenta de experimentación de Azure Machine Learning
   - **Área de trabajo**: Área de trabajo de Azure Machine Learning
   - **Tipo de proyecto**: Marco de Machine Learning. En este caso, seleccione **TensorFlow**
   - **Agregar a solución**: determina si se va a agregar a la solución de Visual Studio actual o si se va a crear y abrir una solución nueva
   - **Ruta de acceso del proyecto**: Ubicación donde se guarda el código
   - **Nombre de proyecto**: Escriba **TensorFlowMNIST**

   ![Proyecto resultante al usar la plantilla Aplicación de Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Visual Studio crea el archivo de proyecto (un archivo `.pyproj` que se almacena en disco) junto con otros archivos definidos en el ejemplo. Con la plantilla "MNIST", el proyecto contiene varios archivos.

    ![Captura de pantalla del Explorador de soluciones de Visual Studio en la que se muestran los archivos del proyecto TensorFlowMNIST. El código de tf_mnist.py se muestra en la ventana principal.](media/create-project-gallery/azml-mnist.png)

6. Envíe el trabajo a Azure Machine Learning.

    ![Captura de pantalla del Explorador de soluciones de Visual Studio en la que se muestra el menú contextual del proyecto TensorFlowMNIST con la opción "Submit Job…" (Enviar trabajo…) seleccionada.](media/create-project-gallery/submit-azml.png)

7. Ejecútelo en un contenedor de Docker o en el equipo local

    ![Captura de pantalla del cuadro de diálogo Submit Job (Enviar trabajo) con el clúster de uso establecido en "azureml:/local" y el script de inicio establecido en "tf_mnist.py".](media/create-project-gallery/azml-local.png)
