---
title: Creación de un proyecto de IA a partir de una plantilla
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 0b537d80b8db9150c6804aff2ee3de0e6c879bb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62546743"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Creación de un proyecto de IA desde una plantilla en Visual Studio

Después de [instalar Visual Studio Tools para IA](installation.md), resulta fácil crear un proyecto de IA con diversas plantillas.

1. Inicie Visual Studio.

2. Seleccione **Archivo > Nuevo > Proyecto** (Ctrl+Shift+N). En el cuadro de diálogo **Nuevo proyecto**, busque "**AI Tools**" (Tools para IA) y seleccione la plantilla que desea. Tenga en cuenta que al seleccionar una plantilla se muestra una breve descripción de lo que proporciona esa plantilla.

    ![Cuadro de diálogo Nuevo proyecto con plantillas de Python en VS2017](media/create-project/new-ai-project.png)

3. Para esta guía de inicio rápido, seleccione la plantilla "**Aplicación de TensorFlow**", asigne un nombre al proyecto (como "MNIST") y una ubicación, y seleccione **Aceptar**.

4. Visual Studio crea el archivo de proyecto (un archivo `.pyproj` que se almacena en disco) junto con cualquier otro archivo descritos por la plantilla. Con la plantilla "Aplicación de TensorFlow", el proyecto contiene un archivo con el mismo nombre que el proyecto. El archivo se abre en el editor de Visual Studio de manera predeterminada.

    ![Proyecto resultante al usar la plantilla de la aplicación Python](media/create-project/new-tensorflowapp.png)

5. Observe que el código ya importa varias bibliotecas, entre las que se incluye TensorFlow, numpy, sys y os. Además, inicia la aplicación lista con algunos argumentos de entrada para habilitar fácilmente la modificación de la ubicación de los datos de aprendizaje de entrada, los modelos de salida y los archivos de registro. Estos parámetros resultan útiles cuando envía los trabajos a varios contextos de proceso (es decir, a un directorio distinto en el Dev Box local en un recurso compartido de Azure).

6. El proyecto también tiene algunas propiedades que se crearon para facilitar la depuración de la aplicación al pasar automáticamente argumentos de la línea de comandos a estos parámetros de entrada. **Haga clic con el botón derecho** en el proyecto y, luego, seleccione **Propiedades**

    ![Propiedades](media/create-project/project-properties.png)

7. Haga clic en la pestaña **Depurar** para ver los argumentos de script que se agregaron automáticamente. Puede cambiarlos según sea necesario a la ubicación de los datos de entrada y dónde le gustaría almacenar la salida.

    ![Propiedades](media/create-project//project-properties_1.png)

8. Ejecute el programa presionando CTRL+F5 o seleccionando **Depurar > Iniciar sin depurar** en el menú. Los resultados se muestran en una ventana de la consola.
