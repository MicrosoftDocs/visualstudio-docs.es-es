---
title: Ejecutar un modelo de TensorFlow en la nube
description: ejecutar un modelo de TensorFlow en una máquina virtual de aprendizaje profundo de azure
keywords: ai, visual studio, máquina virtual de aprendizaje profundo de azure
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 8f6aef2d0cf8fe727036dda91256ac0330e15d37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841320"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Entrenar un modelo de TensorFlow en la nube

En este tutorial, entrenaremos un modelo de TensorFlow con el [conjunto de datos MNIST](http://yann.lecun.com/exdb/mnist/) en una máquina virtual de [aprendizaje profundo](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) de Azure.

La base de datos MNIST tiene un conjunto de entrenamiento de 60 000 ejemplos y un conjunto de pruebas de 10 000 ejemplos de dígitos escritos a mano.

## <a name="prerequisites"></a>Requisitos previos
Antes de comenzar, asegúrese de que tener instalado y configurado lo siguiente:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Configurar la máquina virtual de aprendizaje profundo de Azure

> [!NOTE]
> Establezca **Tipo de SO** en Linux.

[Aquí](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm) encontrará instrucciones para configurar la máquina virtual de aprendizaje profundo.

### <a name="remove-comment-in-parens"></a>Quitar comentario entre paréntesis

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Descargar el código de ejemplo

Descargue este [repositorio de GitHub](https://github.com/Microsoft/samples-for-ai), que contiene ejemplos para comenzar a usar el aprendizaje profundo en TensorFlow, CNTK, Theano y mucho más.

## <a name="open-project"></a>Abrir el proyecto

- Abra Visual Studio y seleccione **Archivo > Nuevo > Proyecto o solución**.

- Seleccione la carpeta **Tensorflow Examples** en el repositorio de ejemplos descargado y abra el archivo **TensorflowExamples.sln**.

   ![Abrir el proyecto](media/tensorflow-local/open-project.png)

   ![Abrir la solución](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Agregar la máquina virtual remota de Azure

En el Explorador de servidores, haga clic con el botón derecho en el nodo **Remote Machines** (Equipos remotos) dentro del nodo de Tools para AI y seleccione "Agregar...". Especifique el nombre para mostrar, el host IP, el puerto SSH, el nombre de usuario y el archivo de clave/contraseña del equipo remoto.

![Agregar un nuevo equipo remoto](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Enviar el trabajo a Azure VM
En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de MNIST y seleccione **Enviar trabajo**.

![Envío de trabajo a un equipo remoto](media/tensorflow-vm/job-submission.png)

En la ventana de envío:

- En la lista de **clústeres para usar**, seleccione el equipo remoto (con el prefijo "rm:") al que quiere enviar el trabajo.

- Escriba un **Nombre del trabajo**.

- Haga clic en **Enviar**.

## <a name="check-status-of-job"></a>Comprobar el estado del trabajo
Para ver el estado y los detalles de los trabajos: expanda la máquina virtual a la que envió el trabajo en el **Explorador de servidores**. Haga doble clic en **Trabajos**.

![Explorador de trabajos](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Limpiar los recursos

Detenga la máquina virtual si tiene previsto usarla en un futuro próximo. Si ya ha terminado este tutorial, ejecute el siguiente comando para limpiar los recursos:

```azurecli-interactive
az group delete --name myResourceGroup
```
