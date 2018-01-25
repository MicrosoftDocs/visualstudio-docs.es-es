---
title: "Inicio rápido: Crear un proyecto de Python mediante Cookiecutter en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: quickstart
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: dfe00af70cdbfbe9c583d15fc5431dc7a85d8276
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Inicio rápido: crear un proyecto a partir de una plantilla de Cookiecutter

Después de [instalar la compatibilidad con Python en Visual Studio 2017](installing-python-support-in-visual-studio.md), es fácil crear un proyecto a partir de una plantilla de Cookiecutter, incluidas muchas de las que se publican en GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) proporciona una interfaz gráfica de usuario para descubrir plantillas, opciones de plantilla de entrada y crear proyectos y archivos. Se incluye con Visual Studio de 2017 y puede instalarse por separado en versiones anteriores de Visual Studio.

1. Para este tutorial rápido, primero debe instalar la distribución de Python Anaconda3, que incluye los paquetes necesarios de Python para la plantilla de Cookiecutter que se muestra aquí. Ejecute el instalador de Visual Studio, haga clic en **Modificar**, expanda las opciones de **Desarrollo de Python** en el lado derecho y seleccione "Anaconda3" (32 bits o 64 bits). Tenga en cuenta que la instalación puede tardar un tiempo, según la velocidad de Internet, pero es la manera más sencilla de instalar los paquetes necesarios.

1. Inicie Visual Studio.

1. Seleccione **Archivo > Nuevo > Desde Cookiecutter**. Este comando abre una ventana en Visual Studio en la que puede buscar plantillas. 

    ![Proyecto nuevo a partir de una plantilla de Cookiecutter](media/projects-from-cookiecutter1.png)

1. Seleccione la plantilla "Microsoft/python-sklearn-classifier-cookiecutter" y, después, haga clic en **Siguiente**. (El proceso puede tardar varios minutos la primera vez que use Cookiecutter).

1. En el paso siguiente, indique una ubicación para el nuevo proyecto en el campo **Crear en** y, después, haga clic en **Crear**.

    ![Segundo paso de uso Cookiecutter: establecer propiedades del proyecto](media/projects-from-cookiecutter2.png)

1. Una vez completado el proceso, verá el mensaje "Los archivos se han creado correctamente". Seleccione el comando **Abrir en el Explorador de soluciones** para abrir el proyecto.

1. Presione Ctrl+F5 o seleccione **Depurar > Iniciar sin depurar** para ejecutar el programa. 

    ![Salida del proyecto de plantilla python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial: Trabajar con Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vea también

- [Uso de la extensión Cookiecutter](cookiecutter.md)
- [Creación de un entorno para un intérprete de Python existente](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Instalación de la compatibilidad con Python en Visual Studio 2015 y versiones anteriores](installing-python-support-in-visual-studio.md).
- [Ubicaciones de instalación](installing-python-support-in-visual-studio.md#install-locations).
