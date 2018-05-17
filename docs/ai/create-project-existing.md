---
ms.technology: vs-ai-tools
ms.openlocfilehash: b86097cc1e0e531fe6f95a01cfa1cae5e4ac42d7
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="create-an-ai-project-from-existing-code"></a>Crear un proyecto de IA a partir de código existente

Una vez que haya [instalado Visual Studio Tools para IA](installation.md), es fácil incorporar el código de Python existente a un proyecto de Visual Studio.

> [!Important]
>
> El proceso que se describe aquí no mueve ni copia los archivos de código fuente originales. Si quiere trabajar con una copia, duplique primero la carpeta.

1. Inicie Visual Studio y seleccione **Archivo > Nuevo > Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, busque "**AI Tools**" (Herramientas de IA), seleccione la plantilla "**Desde código de Python existente**", asigne un nombre y una ubicación al proyecto y, después, haga clic en **Aceptar**.

    ![Nuevo proyecto a partir de código existente, paso 1](media\create-project-existing\new-ai-project.png)

1. En el asistente que aparece, establezca la ruta de acceso al código existente, un filtro para los tipos de archivo, especifique las rutas de acceso de búsqueda que requiera el proyecto y, después, haga clic en **Aceptar**. Si no sabe cuáles son las rutas de acceso de búsqueda, deje ese campo en blanco.

![Nuevo proyecto a partir de código existente, paso 2](media\create-project-existing\azurebatch-newproject.png)

> Si el código existente forma parte de un proyecto de Azure Machine Learning, active "**Carpeta de Azure Machine Learning**" para garantizar la conversión correcta de los detalles de configuración importantes de Azure Machine Learning como qué cuenta de Experimentación, área de trabajo, contextos de proceso se van a usar y mucho más.

1. Para establecer un archivo de inicio, localice el archivo en el Explorador de soluciones, haga clic con el botón derecho y seleccione **Establecer como archivo de inicio**.

1. Si quiere, ejecute el programa presionando Ctrl+F5 o seleccionando **Depurar > Iniciar sin depurar**.

> [!div class="nextstepaction"]
> [Tutorial: Trabajar con Python en Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Vea también

- [Identificación manual de un entorno de Python existente](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)