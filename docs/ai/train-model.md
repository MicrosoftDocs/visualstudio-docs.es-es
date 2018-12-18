---
title: Enviar un trabajo para entrenar un modelo en Azure Batch AI
description: entrenar modelo en la nube
keywords: ai, visual studio, entrenar modelo, nube
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: 6cf5c2529d54637e1e6ad4a111c3d3c456e6fae1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882397"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Entrenar modelos de AI en Azure Batch AI

Batch AI es un servicio administrado que permite a los científicos de datos y a los investigadores de AI entrenar modelos de AI y otros modelos de Machine Learning en clústeres de máquinas virtuales de Azure, incluidas las máquinas virtuales compatibles con GPU. Para ello, es necesario describir los requisitos del trabajo y dónde encontrar las entradas y almacenar las salidas. Batch AI se encargará del resto del proceso. [Más información sobre Azure Batch AI](https://docs.microsoft.com/azure/batch-ai/overview).

Se integra con Visual Studio Tools para AI, lo que le permitirá escalar dinámicamente modelos de entrenamiento en Azure.  Después de haber [instalado Visual Studio Tools para IA](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Herramientas para IA) y elija **Seleccionar un clúster**

    ![Selección de clúster](media/train-model/select-cluster.png)

2. Expanda **AI Tools** (Tools para AI). Los recursos de Batch AI que tenga se detectarán automáticamente y aparecerán en el Explorador de servidores.

    ![Galería de ejemplos](media/train-model/batchai.png)

3. Seleccione **Ver > Team Explorer...** para abrir la ventana **Team Explorer** desde la que puede conectarse a GitHub o Azure DevOps, o bien clonar un repositorio.

    ![Ventana de Team Explorer en la que se muestra Azure DevOps, GitHub y la clonación de un repositorio](media/train-model/team-explorer.png)

4. En el campo de dirección URL en **Repositorios GIT locales**, escriba `https://github.com/Microsoft/samples-for-ai`, especifique una carpeta para los archivos clonados y haga clic en **Clonar**.

    > [!Tip]
    > La carpeta que especifique en Team Explorer es la carpeta específica para recibir los archivos clonados. A diferencia del comando `git clone`, al crear un clon en Team Explorer no se crea automáticamente una subcarpeta con el nombre del repositorio.

5. Cuando se complete la clonación, haga clic en **Archivo > Abrir solución > Proyecto/Solución**.

    ![Galería de ejemplos](media/train-model/open-solution.png)

6. Abra **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** en el directorio en el que ha clonado el repositorio.

    ![Galería de ejemplos](media/train-model/tensorflowexamples.png)

7. Establezca el proyecto de MNIST como proyecto de inicio.

    ![Galería de ejemplos](media/train-model/mnist-startup.png)

8. <strong>Haga clic con el botón derecho en el proyecto de **MNIST y seleccione **Enviar trabajo</strong>

    ![Galería de ejemplos](media/train-model/submit-job.png)
9. Seleccione el clúster **Azure Batch AI** y haga clic en **Importar**. Seleccione el archivo `AzureBatchAI_TF_MNIST.json` para rellenar rápidamente algunos valores predeterminados, como qué imagen de Docker usar. Luego, haga clic en **Enviar**.

    ![Galería de ejemplos](media/train-model/submit-batch.png)
