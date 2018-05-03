---
title: REPL de IPython (ventana interactiva)
description: Uso de la ventana interactiva de Visual Studio en modo de IPython para tener un entorno de desarrollo interactivo fácil de usar que tiene características de computación paralela interactiva.
ms.date: 07/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a1581c9cd7cb317a50932e85bb46159c508d8522
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="using-ipython-in-the-interactive-window"></a>Uso de IPython en la ventana interactiva

La ventana interactiva de Visual Studio en modo de IPython es un entorno de desarrollo interactivo avanzado y fácil de usar que tiene características de computación paralela interactiva. En este artículo se explica cómo usar IPython en la ventana interactiva de Visual Studio, en la que también están disponibles todas las características habituales de la [ventana interactiva](python-interactive-repl-in-visual-studio.md).

Para este tutorial, debe tener instalado el entorno de [Anaconda](https://www.continuum.io), que incluye IPython y las bibliotecas necesarias.

> [!Note]
> IronPython no admite IPython, a pesar de que puede seleccionarlo en el formulario Interactive Options (Opciones de interactivo). Para obtener más información, vea la [Solicitud de características](https://github.com/Microsoft/PTVS/issues/84).

1. Abra Visual Studio, cambie a la ventana Entornos de Python, en **Ver > Otras ventanas > Entornos de Python**, y seleccione el entorno de Python que ha aparecido al iniciar IPython.

1. Vea la pestaña **Paquetes** (o **pip**) y asegúrese de que aparecen `IPython` y `matplotlib`. De lo contrario, instálelos.

1. Seleccione la pestaña **Información general** y después **Usar modo interactivo de IPython**. (En Visual Studio 2015, seleccione **Configurar opciones interactivas** para abrir el cuadro de diálogo **Opciones**, después establezca **Modo interactivo** en IPython y seleccione **Aceptar**).

1. Seleccione **Abrir ventana interactiva** para que aparezca la ventana interactiva en modo de IPython. Puede que necesite restablecer la ventana si solo ha cambiado el modo interactivo; también puede que necesite presionar Entrar si solo aparece un mensaje >>>.

    ![Ventana interactiva en modo de IPython](media/ipython-repl-03.png)

1. Escriba el siguiente código:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Después de escribir la última línea, debe aparecer un gráfico insertado, cuyo tamaño puede modificar si arrastra la esquina inferior derecha.

    ![Gráfico incorporado en la ventana interactiva](media/ipython-repl-04.png)

1. En lugar de escribir en el REPL, puede escribir código en el editor, seleccionarlo, hacer clic con el botón derecho y seleccionar el comando **Enviar a interactivo** (o presionar Ctrl-Entrar). Intente pegar el código siguiente en un nuevo archivo en el editor; selecciónelo con Ctrl-A y envíelo a la ventana interactiva. (Tenga en cuenta que Visual Studio envía el código como una unidad para evitar que se representen gráficos intermedios o parciales. También tenga en cuenta que si no tiene un proyecto de Python abierto con un entorno diferente seleccionado, Visual Studio abre una ventana interactiva para el entorno que esté seleccionado como su predeterminado en la ventana **Entornos de Python**).

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Envío de código desde el editor a la ventana interactiva](media/ipython-repl-05.png)

1. Para ver los gráficos fuera de la ventana interactiva, ejecute el código en lugar de utilizar el comando **Depurar > Iniciar sin depurar**.

IPython tiene muchas otras características útiles, como el escape al shell del sistema, la sustitución de variables, la captura de salidas, etc. Vea la [documentación de IPython](http://ipython.org/documentation.html) para obtener más información.

## <a name="related-articles"></a>Artículos relacionados

- Para usar Jupyter fácilmente y sin instalación, pruebe el [servicio hospedado en Azure Notebooks](https://notebooks.azure.com/) gratuito que le permite conservar y compartir sus blocs de notas con otras personas.

- También puede ejecutar Jupyter (conocido anteriormente como IPython) en su propia máquina virtual Linux o Windows en Azure. Para obtener más información, vea [Creación de una máquina virtual de Azure, e instalación y ejecución de cuadernos de Jupyter Notebook en Azure](/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).
