---
title: Trabajar con Python en Visual Studio, paso 5 | Microsoft Docs
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 69e51c46-9a10-4d6f-9f74-2d1385beb1ac
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 30f89023d09ab90cae2698de976eaef44165b0fb
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2017
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Paso 5: Instalación de paquetes en un entorno de Python

**Paso anterior: [Ejecución de código en el depurador](vs-tutorial-01-04.md)**

La comunidad de desarrolladores de Python ha generado miles de paquetes útiles que puede incorporar a sus proyectos. Visual Studio proporciona una interfaz de usuario para administrar paquetes en los entornos de Python.

1. Seleccione el comando de menú **Vista > Otras ventanas > Entornos de Python (Entornos de Python)**. La ventana **Entornos de Python** se abre como un elemento del mismo nivel para el Explorador de soluciones y muestra los distintos entornos disponibles. La lista incluye los entornos que ha instalado mediante el instalador de Visual Studio y los que ha instalado por separado. El entorno en negrita es el entorno predeterminado que se usa para los nuevos proyectos.

  ![Ventana Python Environments (Entornos de Python)](media/environments-default-view-blue.png)

1. La pestaña **Introducción** del entorno proporciona acceso rápido a una ventana interactiva para ese entorno junto con la carpeta de instalación y los intérpretes del entorno. Por ejemplo, al seleccionar **Abrir ventana interactiva** se muestra una ventana interactiva para ese entorno específico en Visual Studio.

1. Al seleccionar la pestaña **Paquetes**, verá una lista de los paquetes instalados en el entorno.

  ![Paquetes instalados en un entorno](media/environments-installed-packages-blue.png)

1. Instale `matplotlib` escribiendo su nombre en el campo de búsqueda y, a continuación, seleccione el `pip install`.

  ![Instalación de matplotlib en el entorno](media/environments-add-matplotlib1.png)

1. Si se le pide, dé su consentimiento para la elevación.
 
1. Una vez instalado el paquete, aparece en la ventana Entornos de Python. La **X** situada a la derecha del paquete lo desinstala. 

  ![Finalización de la instalación de matplotlib en el entorno](media/environments-add-matplotlib2.png)

  La barra de progreso pequeña situada debajo del entorno indica que Visual Studio está compilando la base de datos de IntelliSense para el paquete recién instalado. La pestaña **IntelliSense** también muestra información más detallada. Tenga en cuenta que hasta que se complete dicha base de datos, las características de IntelliSense, como la finalización automática y la comprobación de sintaxis, no estarán activas en el editor de ese paquete.

1. Cree un proyecto con **Archivo > Nuevo > Proyecto** y seleccione la plantilla "Aplicación Python". En el archivo de código que aparece, pegue el código siguiente, que crea una onda de coseno como en los pasos del tutorial anteriores, pero esta vez trazada en un gráfico:

    ```python  
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt
    from math import radians

    def main():  
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()
                    
    main()
    ```  

1. Ejecute el programa con (F5) o sin el depurador (Ctrl+F5) para ver el resultado:

  ![Ejemplo de salida de matplotlib](media/environments-add-matplotlib3.png)


## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Trabajar con GIT](vs-tutorial-01-06.md)

### <a name="going-deeper"></a>Mayor profundización
- [Entornos de Python](python-environments.md)
