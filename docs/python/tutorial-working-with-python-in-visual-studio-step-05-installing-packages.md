---
title: Paso 5 del Tutorial de Python en Visual Studio, Instalación de paquetes
titleSuffix: ''
description: Paso 5 de un tutorial básico de las funcionalidades de Python en Visual Studio, en el que se muestran las características de Visual Studio para administrar paquetes en un entorno de Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372946"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Paso 5: Instalación de paquetes en el entorno de Python

**Paso anterior: [Ejecución de código en el depurador](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La comunidad de desarrolladores de Python ha generado miles de paquetes útiles que puede incorporar a sus proyectos. Visual Studio proporciona una interfaz de usuario para administrar paquetes en los entornos de Python.

## <a name="view-environments"></a>Ver entornos

1. Seleccione el comando de menú **Vista** > **Otras ventanas** > **Entornos de Python**. La ventana **Entornos de Python** se abre como un elemento del mismo nivel para el **Explorador de soluciones** y muestra los distintos entornos disponibles. La lista muestra los entornos que ha instalado mediante el instalador de Visual Studio y los que ha instalado por separado. Esto incluye entornos globales, virtuales y de Conda. El entorno en negrita es el entorno predeterminado que se usa para los nuevos proyectos. Para obtener información adicional sobre cómo trabajar con entornos, vea [Creación y administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Ventana Python Environments (Entornos de Python)](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Otra manera de abrir la ventana Entornos de Python es hacer clic en la ventana Explorador de soluciones y usar el método abreviado de teclado Ctrl + K, Ctrl + '. Si el acceso directo no funciona y no encuentra la ventana Entornos de Python en el menú, es posible que no haya instalado la carga de trabajo de Python. Vea [Instalación de la compatibilidad con Python en Visual Studio](installing-python-support-in-visual-studio.md) para obtener instrucciones sobre cómo instalar Python.

2. La pestaña **Introducción** del entorno proporciona acceso rápido a una ventana **interactiva** para ese entorno junto con la carpeta de instalación y los intérpretes del entorno. Por ejemplo, al seleccionar **Abrir ventana interactiva** se muestra una ventana **interactiva** para ese entorno específico en Visual Studio.

3. Ahora, cree un proyecto con **Archivo** > **Nuevo** > **Proyecto** y seleccione la plantilla **Aplicación Python**. En el archivo de código que aparece, pegue el código siguiente, que crea una onda de coseno como en los pasos del tutorial anteriores, pero esta vez trazada en un gráfico. Como alternativa, puede usar el proyecto que creó anteriormente y reemplazar el código. 

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. Con un proyecto de Python abierto, también puede abrir la ventana Entornos de Python desde Explorador de soluciones. Basta con hacer clic con el botón derecho en Entornos de Python y seleccionar **Ver todos los entornos de Python**.

   ![Entorno](media/environments/environments-view-all-2019.png)

5. Al examinar la ventana del editor, observará que, si mantiene el puntero sobre las instrucciones Import `numpy` e `matplotlib`, no están resueltas. Esto se debe a que los paquetes no se han instalado en el entorno global predeterminado.

   ![Importación de paquetes sin resolver](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instalación de paquetes con la ventana Entornos de Python

1. En la ventana Entornos de Python, haga clic en el entorno predeterminado para los nuevos proyectos de Python y seleccione la pestaña **Paquetes**. Verá una lista de los paquetes que están instalados actualmente en el entorno.

   ![Paquetes instalados en un entorno](media/environments/environments-installed-packages-2019.png)

2. Para instalar `matplotlib`, escriba su nombre en el campo de búsqueda y, después, seleccione la opción **Ejecutar comando: pip install matplotlib**. Esto instalará `matplotlib`, así como los paquetes de los que depende (en este caso, `numpy`).

   ![Instalación de matplotlib en el entorno](media/environments/environments-add-matplotlib-2019.png)

5. Si se le pide, dé su consentimiento para la elevación.

6. Una vez instalado el paquete, aparece en la ventana **Entornos de Python**. La **X** situada a la derecha del paquete lo desinstala.

   ![Finalización de la instalación de matplotlib en el entorno](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Una barra de progreso pequeña podría aparecer debajo del entorno para indicar que Visual Studio está compilando la base de datos de IntelliSense para el paquete recién instalado. La pestaña **IntelliSense** también muestra información más detallada. Tenga en cuenta que hasta que se complete la base de datos, las características de IntelliSense, como la finalización automática y la comprobación de sintaxis, no estarán activas en el editor de ese paquete.
   > 
   > Visual Studio 2017, versión 15.6 y versiones posteriores, utiliza otro método más rápido para trabajar con IntelliSense y muestra un mensaje a tal efecto en la pestaña **IntelliSense**.

## <a name="run-the-program"></a>Ejecutar el programa

1. Ahora que [matplotlib](https://matplotlib.org/) está instalado, ejecute el programa con (**F5**) o sin el depurador (**Ctrl**+**F5**) para ver el resultado:

   ![Ejemplo de salida de matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Paso siguiente

> [!div class="nextstepaction"]
> [Trabajar con Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Entornos de Python](managing-python-environments-in-visual-studio.md)
- [Información sobre Django en Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Información sobre Flask en Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
