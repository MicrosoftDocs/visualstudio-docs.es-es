---
title: 'Inicio rápido: Crear proyectos de Python mediante Cookiecutter'
description: En este inicio rápido, creará un proyecto de Visual Studio para Python utilizando una plantilla de Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902432"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Inicio rápido: Creación de un proyecto a partir de una plantilla de Cookiecutter

Cuando se ha [instalado la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md), resulta fácil crear un proyecto a partir de una plantilla de Cookiecutter, incluidas muchas de las que se publican en GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) proporciona una interfaz gráfica de usuario para descubrir plantillas, opciones de plantilla de entrada y crear proyectos y archivos. Se incluye con Visual Studio 2017 y versiones posteriores y puede instalarse por separado en versiones anteriores de Visual Studio.

1. Para este tutorial rápido, primero debe instalar la distribución de Python Anaconda3, que incluye los paquetes necesarios de Python para la plantilla de Cookiecutter que se muestra aquí. Ejecute el instalador de Visual Studio, haga clic en **Modificar**, expanda las opciones de **Desarrollo de Python** en el lado derecho y seleccione **Anaconda3** (32 bits o 64 bits). Tenga en cuenta que la instalación puede tardar un tiempo, según la velocidad de Internet, pero es la manera más sencilla de instalar los paquetes necesarios.

1. Inicie Visual Studio.

1. Seleccione **Archivo** > **Nuevo** > **Desde Cookiecutter**. Este comando abre una ventana en Visual Studio en la que puede buscar plantillas.

    ![Proyecto nuevo a partir de una plantilla de Cookiecutter](media/projects-from-cookiecutter1.png)

1. Seleccione la plantilla **Microsoft/python-sklearn-classifier-cookiecutter** y, después, haga clic en **Siguiente**. (El proceso puede tardar varios minutos la primera vez que use una plantilla en particular, ya que Visual Studio instala los paquetes de Python necesarios).

1. En el paso siguiente, indique una ubicación para el nuevo proyecto en el campo **Crear en** y, después, haga clic en **Crear y Abrir proyecto**.

    ![Segundo paso de uso Cookiecutter: establecer propiedades del proyecto](media/projects-from-cookiecutter2.png)

1. Una vez completado el proceso, verá el mensaje **Archivos creados correctamente con la plantilla...** . El proyecto se abre automáticamente en el Explorador de soluciones.

1. Presione **Ctrl**+**F5** o seleccione **Depurar** > **Iniciar sin depurar** para ejecutar el programa.

    ![Salida del proyecto de plantilla python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial: Uso de Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vea también

- [Uso de la extensión Cookiecutter](using-python-cookiecutter-templates.md)
- [Manually identifying an existing Python interpreter](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment) (Identificación manual de un intérprete de Python existente)
- [Instalación de la compatibilidad con Python en Visual Studio 2015 y versiones anteriores](installing-python-support-in-visual-studio.md)
- [Ubicaciones de instalación](installing-python-support-in-visual-studio.md#install-locations)
