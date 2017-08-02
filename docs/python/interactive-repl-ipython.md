---
title: REPL de IPython en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>Uso de Python en la ventana interactiva

La ventana interactiva de Visual Studio en modo de IPython es un entorno de desarrollo interactivo avanzado y fácil de usar que tiene características de computación paralela interactiva. En este tema se ofrece orientación sobre el uso de IPython en la ventana interactiva de Visual Studio. Para ello, debe tener instalado el entorno de [Anaconda](https://www.continuum.io), que incluye IPython y las bibliotecas necesarias.

> [!Note]
> IronPython no admite IPython, a pesar de que puede seleccionarlo en el formulario Interactive Options (Opciones de interactivo). Puede votar a favor de la [solicitud de característica](https://github.com/Microsoft/PTVS/issues/84) o implementarla, si así lo desea.

1. Asegúrese de que el paquete de IPython está instalado correctamente; para ello, vaya al directorio de instalación de Python e inicie IPython en modo de PyLab:

  ```bash
  ipython --pylab
  ```

1. Escriba lo siguiente:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. Si todo está configurado correctamente, debería ver algo parecido a esto:

    ![Salida de la configuración de IPython ](~/python/media/ipython-repl-01.png)

1. Abra Visual Studio, cambie a la ventana Python Environments (Entornos de Python), en **View > Other Windows > Python Environments** (Ver > Otras ventanas > Entornos de Python), y después seleccione el entorno de Python.
1. Consulte la pestaña **pip**, donde deben aparecer `IPython` y `matplotlib`. De lo contrario, instálelos.
1. Seleccione la pestaña **Overview** (Información general) y **Configure interactive options** (Configurar opciones interactivas), defina la opción **Interactive Mode** (Modo interactivo) en IPython y seleccione **OK** (Aceptar):

    ![Establecimiento del modo interactivo en IPython](~/python/media/ipython-repl-02.png)

1. Seleccione **Open interactive window** (Abrir ventana interactiva) para que aparezca la ventana interactiva en modo de IPython con PyLab. Puede ser necesario restablecer la ventana si ha cambiado el modo interactivo:

    ![Ventana interactiva en modo de IPython](~/python/media/ipython-repl-03.png)

1. Escriba el siguiente código:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Después de escribir la última línea, debe aparecer un gráfico insertado, cuyo tamaño puede modificar si arrastra la esquina inferior derecha.

    ![Gráfico incorporado en la ventana interactiva](~/python/media/ipython-repl-04.png)

1. En lugar de escribir en el REPL, puede escribir código en el editor, seleccionarlo, hacer clic con el botón derecho y seleccionar el comando **Enviar a Interactive** (Ctrl-E, E). Intente pegar el código siguiente en el editor; selecciónelo con Ctrl-A y envíelo a la ventana interactiva. (Tenga en cuenta que, cuando Visual Studio envía el código a la ventana interactiva, lo hace como una unidad, a fin de evitar que se representen gráficos intermedios o parciales).

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
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![Envío de código desde el editor a la ventana interactiva](~/python/media/ipython-repl-05.png)

1. Para ver los gráficos fuera de la ventana interactiva, ejecute el código en lugar de utilizar el comando **Depurar > Iniciar sin depurar**.
    
1. IPython tiene una serie de características útiles, como el escape al shell del sistema, la sustitución de variables, la captura de salidas, etc. Consulte la guía de referencia de IPython para obtener más información:

    ![Escape al shell del sistema](~/python/media/ipython-repl-06.png)

1. También puede usar IPython en modo "cuaderno", donde puede utilizar como lienzo cualquier explorador de cualquier sistema operativo. El motor de IPython de back-end puede ser local en el equipo o remoto. Azure admite la ejecución de [IPython en una VM Linux o Windows](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook). Vea también la [versión preliminar de Azure Notebooks](https://notebooks.azure.com) para la aplicación gratuita Jupyter Notebook como servicio en Azure:

    ![Modo cuaderno de IPython](~/python/media/ipython-repl-07.png)

