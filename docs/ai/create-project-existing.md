---
ms.technology: vs-ai-tools
ms.openlocfilehash: 7e09023659b1f44af1951e157878d78b641be3f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915950"
---
# <a name="create-an-ai-project-from-existing-code"></a>Crear un proyecto de IA a partir de código existente

Una vez que haya [instalado Visual Studio Tools para IA](installation.md), es fácil incorporar el código de Python existente a un proyecto de Visual Studio.

> [!Important]
> El proceso que se describe aquí no mueve ni copia los archivos de código fuente originales. Si quiere trabajar con una copia, duplique primero la carpeta.

1. Inicie Visual Studio y seleccione **Archivo > Nuevo > Proyecto**.

2. En el cuadro de diálogo **Nuevo proyecto**, busque "**AI Tools**" (Herramientas de IA), seleccione la plantilla "**Desde código de Python existente**", asigne un nombre y una ubicación al proyecto y, después, haga clic en **Aceptar**.

   ![Nuevo proyecto a partir de código existente, paso 1](media/create-project-existing/new-ai-project.png)

3. En el asistente que aparece, establezca la ruta de acceso al código existente, un filtro para los tipos de archivo, especifique las rutas de acceso de búsqueda que requiera el proyecto y, después, haga clic en **Aceptar**. Si no sabe cuáles son las rutas de acceso de búsqueda, deje ese campo en blanco.

   ![Nuevo proyecto a partir de código existente, paso 2](media/create-project-existing/azurebatch-newproject.png)

   Si el código existente forma parte de un proyecto de Azure Machine Learning, active **Carpeta de Azure Machine Learning** para garantizar la conversión correcta de los detalles de configuración importantes de Azure Machine Learning como la cuenta de Experimentación, el área de trabajo, contextos de proceso se van a usar y mucho más.

4. Para establecer un archivo de inicio, localice el archivo en el **Explorador de soluciones**, haga clic con el botón derecho y seleccione **Establecer como archivo de inicio**.

5. Para ejecutar el programa, presione **Ctrl**+**F5** or seleccione **Depurar > Iniciar sin depurar**.

> [!div class="nextstepaction"]
> [Tutorial: Trabajar con Python en Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Vea también

- [Identificación manual de un entorno de Python existente](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)