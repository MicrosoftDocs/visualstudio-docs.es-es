---
title: 'Tutorial Trabajo con Python, paso 5: instalación de paquetes'
description: Paso 5 de un tutorial básico de las funcionalidades de Python en Visual Studio, en el que se muestran las características de Visual Studio para administrar paquetes en un entorno de Python.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 82cb54eb64d0864ba3b1d326d68f7303d3f2d882
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220513"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Paso 5: Instalar paquetes en un entorno de Python

**Paso anterior: [Ejecutar código en el depurador](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

La comunidad de desarrolladores de Python ha generado miles de paquetes útiles que puede incorporar a sus proyectos. Visual Studio proporciona una interfaz de usuario para administrar paquetes en los entornos de Python.

1. Seleccione el comando de menú **Vista** > **Otras ventanas** > **Entornos de Python** . La ventana **Entornos de Python** se abre como un elemento del mismo nivel para el **Explorador de soluciones** y muestra los distintos entornos disponibles. La lista incluye los entornos que ha instalado mediante el instalador de Visual Studio y los que ha instalado por separado. El entorno en negrita es el entorno predeterminado que se usa para los nuevos proyectos.

   ![Ventana Python Environments (Entornos de Python)](media/environments-default-view-blue.png)

2. La pestaña **Introducción** del entorno proporciona acceso rápido a una ventana **interactiva** para ese entorno junto con la carpeta de instalación y los intérpretes del entorno. Por ejemplo, al seleccionar **Abrir ventana interactiva** se muestra una ventana **interactiva** para ese entorno específico en Visual Studio.

3. Al seleccionar la pestaña **Paquetes**, verá una lista de los paquetes instalados en el entorno.

   ![Paquetes instalados en un entorno](media/environments-installed-packages-blue.png)

4. Instale `matplotlib` escribiendo su nombre en el campo de búsqueda y, a continuación, seleccione **pip install**

   ![Instalación de matplotlib en el entorno](media/environments-add-matplotlib1.png)

5. Si se le pide, dé su consentimiento para la elevación.

6. Una vez instalado el paquete, aparece en la ventana **Entornos de Python**. La **X** situada a la derecha del paquete lo desinstala.

   ![Finalización de la instalación de matplotlib en el entorno](media/environments-add-matplotlib2.png)

   Una barra de progreso pequeña podría aparecer debajo del entorno par indicar que Visual Studio está compilando la base de datos de IntelliSense para el paquete recién instalado. La pestaña **IntelliSense** también muestra información más detallada. Tenga en cuenta que hasta que se complete dicha base de datos, las características de IntelliSense, como la finalización automática y la comprobación de sintaxis, no estarán activas en el editor de ese paquete.

   Tenga en cuenta que **Visual Studio 2017, versión 15.6** y posteriores, utiliza un método diferente y más rápido para trabajar con IntelliSense, y muestra un mensaje a tal efecto en la pestaña **IntelliSense**.

7. Cree un proyecto con **Archivo** > **Nuevo** > **Proyecto** y seleccione la plantilla **Aplicación Python**. En el archivo de código que aparece, pegue el código siguiente, que crea una onda de coseno como en los pasos del tutorial anteriores, pero esta vez trazada en un gráfico:

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

8. Ejecute el programa con (**F5**) o sin el depurador (**Ctrl**+**F5**) para ver el resultado:

   ![Ejemplo de salida de matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>Paso siguiente

> [!div class="nextstepaction"]
> [Trabajar con Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Entornos de Python](managing-python-environments-in-visual-studio.md)
