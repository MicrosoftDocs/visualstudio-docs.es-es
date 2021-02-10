---
title: REPL de IPython (ventana interactiva)
description: Use la ventana interactiva de Visual Studio en modo de IPython para tener un entorno de desarrollo interactivo fácil de usar con características de computación paralela interactiva.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 343c87f3c14e8ebafeb99a55a88d0b86df1bafcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942639"
---
# <a name="use-ipython-in-the-interactive-window"></a>Uso de IPython en la ventana interactiva

La ventana **interactiva** de Visual Studio en modo de IPython es un entorno de desarrollo interactivo avanzado y fácil de usar que tiene características de computación paralela interactiva. En este artículo se explica cómo usar IPython en la ventana **interactiva** de Visual Studio, en la que también están disponibles todas las características habituales de la [ventana interactiva](python-interactive-repl-in-visual-studio.md).

Para este tutorial, debe tener instalado el entorno de [Anaconda](https://www.continuum.io), que incluye IPython y las bibliotecas necesarias.

> [!Note]
> IronPython no admite IPython, a pesar de que puede seleccionarlo en el formulario **Interactive Options** (Opciones de interactivo). Para obtener más información, vea la [Solicitud de características](https://github.com/Microsoft/PTVS/issues/84).

1. Abra Visual Studio, cambie a la ventana **Entornos de Python**, en **Ver** > **Otras ventanas** > **Entornos de Python**, y después seleccione el entorno de Anaconda.

2. Vaya a la pestaña **Paquetes (Conda)** (que pueden aparecer como **pip** o **Paquetes**) de ese entorno para asegurarse de que `ipython` y `matplotlib` se muestren. De lo contrario, instálelos. Vea [Ventana Entorno de Python - pestaña Paquetes](python-environments-window-tab-reference.md).

3. Seleccione la pestaña **Información general** y después **Usar modo interactivo de IPython**. (En Visual Studio 2015, seleccione **Configurar opciones interactivas** para abrir el cuadro de diálogo **Opciones**, después establezca **Modo interactivo** en **IPython** y haga clic en **Aceptar**).

4. Seleccione **Abrir ventana interactiva** para que aparezca la ventana **interactiva** en modo de IPython. Puede que necesite restablecer la ventana si solo ha cambiado el modo interactivo; también puede que necesite presionar **Entrar** si solo aparece un mensaje >>>, para recibir una solicitud como **En [2]** .

    ![Ventana interactiva en modo de IPython](media/ipython-repl-03.png)

5. Escriba el siguiente código:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Después de escribir la última línea, debe aparecer un gráfico insertado, cuyo tamaño puede modificar si arrastra la esquina inferior derecha.

    ![Gráfico incorporado en la ventana interactiva](media/ipython-repl-04.png)

7. En lugar de escribir en el REPL, puede escribir código en el editor, seleccionarlo, hacer clic con el botón derecho y seleccionar el comando **Enviar a interactivo** (o presionar **Ctrl**+**Entrar**). Intente pegar el código siguiente en un nuevo archivo en el editor; selecciónelo con **Ctrl**+**A** y envíelo a la ventana **interactiva**. (Visual Studio envía el código como una unidad para evitar que se representen gráficos intermedios o parciales. Y si no tiene un proyecto de Python abierto con otro entorno seleccionado, Visual Studio abre una ventana **interactiva** para el entorno que esté seleccionado como predeterminado en la ventana **Entornos de Python**).

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

8. Para ver los gráficos fuera de la ventana **interactiva**, ejecute el código en lugar de utilizar el comando **Depurar** > **Iniciar sin depurar**.

IPython tiene muchas otras características útiles, como el escape al shell del sistema, la sustitución de variables, la captura de salidas, etc. Vea la [documentación de IPython](https://ipython.org/documentation.html) para obtener más información.

## <a name="see-also"></a>Vea también

- [Azure Data Science Virtual Machine](/azure/machine-learning/data-science-virtual-machine/overview) está preconfigurado para ejecutar cuadernos de Jupyter, junto con una amplia variedad de otras herramientas de ciencia de datos.
