---
title: Envío de un trabajo para entrenar un modelo
description: Envío de un trabajo para entrenar un modelo con Azure Batch AI
ms.custom: SEO-VS-2020
keywords: ai, visual studio, entrenar modelo, nube
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 72f5fa5aab9f9afa6268f8acd737430af0568928
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727364"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Entrenar modelos de AI en Azure Batch AI

Batch AI es un servicio administrado que permite a los científicos de datos y a los investigadores de AI entrenar modelos de AI y otros modelos de Machine Learning en clústeres de máquinas virtuales de Azure, incluidas las máquinas virtuales compatibles con GPU. Para ello, es necesario describir los requisitos del trabajo y dónde encontrar las entradas y almacenar las salidas. Batch AI se encargará del resto del proceso. [Más información sobre Azure Batch AI](/azure/batch-ai/overview).

Se integra con Visual Studio Tools para AI, lo que le permitirá escalar dinámicamente modelos de entrenamiento en Azure.  Después de haber [instalado Visual Studio Tools para IA](installation.md), podrá crear un proyecto de Python muy fácilmente con las recetas ya preparadas de la galería de ejemplos de Azure Machine Learning.

1. Inicie Visual Studio. Abra el **Explorador de servidores**; para ello, abra el menú **AI Tools** (Herramientas para IA) y elija **Seleccionar un clúster**

    ![Selección de clúster](media/train-model/select-cluster.png)

2. Expanda **AI Tools** (Tools para AI). Los recursos de Batch AI que tenga se detectarán automáticamente y aparecerán en el Explorador de servidores.

    ![Captura de pantalla del árbol de carpetas expandido del menú AI Tools (Herramientas de IA) en el Explorador de servidores, en la que se muestran las subcarpetas Azure Batch AI y Azure Machine Learning expandidas.](media/train-model/batchai.png)

3. Seleccione **Ver > Team Explorer...** para abrir la ventana **Team Explorer** desde la que puede conectarse a GitHub o Azure DevOps, o bien clonar un repositorio.

    ![Ventana de Team Explorer en la que se muestra Azure DevOps, GitHub y la clonación de un repositorio](media/train-model/team-explorer-devops.png)

4. En el campo de dirección URL en **Repositorios GIT locales**, escriba `https://github.com/Microsoft/samples-for-ai`, especifique una carpeta para los archivos clonados y haga clic en **Clonar**.

    > [!Tip]
    > La carpeta que especifique en Team Explorer es la carpeta específica para recibir los archivos clonados. A diferencia del comando `git clone`, al crear un clon en Team Explorer no se crea automáticamente una subcarpeta con el nombre del repositorio.

5. Cuando se complete la clonación, haga clic en **Archivo > Abrir solución > Proyecto/Solución**.

    ![Captura de pantalla en la que se muestra parte del menú Archivo del Explorador de servidores con el comando Abrir seleccionado y la opción Proyecto o solución seleccionada en el menú contextual.](media/train-model/open-solution.png)

6. Abra **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** en el directorio en el que ha clonado el repositorio.

    ![Captura de pantalla en la que se muestra el archivo de solución TensorflowExamples.sln en el contenido de la carpeta TensorflowExamples del repositorio samples-for-ai.](media/train-model/tensorflowexamples.png)

7. Establezca el proyecto de MNIST como **Proyecto de inicio**.

    ![Captura de pantalla en la que se muestra la opción Establecer como proyecto de inicio seleccionada en el menú contextual del proyecto MNIST en el Explorador de soluciones.](media/train-model/mnist-startup.png)

8. <strong>Haga clic con el botón derecho en **Proyecto de MNIST,** **Enviar trabajo**</strong>.

    ![Captura de pantalla en la que se muestra la opción Submit Job (Enviar trabajo) seleccionada en el menú contextual del proyecto MNIST en el Explorador de soluciones.](media/train-model/submit-job.png)
9. Seleccione el clúster **Azure Batch AI** y haga clic en **Importar**. Seleccione el archivo `AzureBatchAI_TF_MNIST.json` para rellenar rápidamente algunos valores predeterminados, como qué imagen de Docker usar. Luego, haga clic en **Enviar**.

    ![Captura de pantalla del cuadro de diálogo Submit Job (Enviar trabajo) con valores rellenados para Use cluster (Clúster de uso), Script de inicio, Nombre del trabajo, Nombre de la imagen, Prefijo de la ruta de acceso de stdOut/Err y CLI parameters (Parámetros de CLI).](media/train-model/submit-batch.png)
