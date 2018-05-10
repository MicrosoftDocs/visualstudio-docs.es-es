---
title: 'Inició rápido: Clonación de un repositorio de código Python'
description: En este inicio rápido, creará un proyecto de Python en Visual Studio mediante la clonación del repositorio de Python Koans mediante Visual Studio Team Explorer.
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 8cad15dcb5bb7c9c8a774f645789d26e0e0ffd7e
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Inició rápido: Clonado de un repositorio de código Python en Visual Studio

Después de [instalar la compatibilidad con Python en Visual Studio 2017](installing-python-support-in-visual-studio.md), podrá clonar fácilmente un repositorio de código Python y crear un proyecto a partir de él.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Inicie Visual Studio.

3. Seleccione **Ver > Team Explorer** para abrir la ventana **Team Explorer** desde la que puede conectarse a GitHub o Visual Studio Team Services, o bien clonar un repositorio. (Si no ve la página **Conectar** que se muestra a continuación, seleccione el icono de enchufe en la barra de herramientas superior, que le llevará a esa página).

    ![Ventana de Team Explorer en la que se muestra Visual Studio Team Services, GitHub y la clonación de un repositorio](media/team-explorer.png)

4. En **Repositorios GIT locales**, seleccione el comando **Clonar** escriba `https://github.com/gregmalcolm/python_koans` en el campo de dirección URL, especifique una carpeta para los archivos clonados y seleccione el botón **Clonar**.

    > [!Tip]
    > La carpeta que especifique en Team Explorer es la carpeta exacta para recibir los archivos clonados. A diferencia del comando `git clone`, al crear un clon en Team Explorer no se crea automáticamente una subcarpeta con el nombre del repositorio.

5. Cuando se complete la clonación, aparecerá el nombre del repositorio en la lista **Repositorios GIT locales**. Haga doble clic en ese nombre para ir al panel de repositorio en **Team Explorer**.

6. En **Soluciones**, seleccione **Nueva**.

    ![Ventana de Team Explorer, con la creación de un proyecto nuevo a partir de un clon](media/team-explorer-new-project.png)

7. En el cuadro de diálogo **Nuevo proyecto** que se muestra, vaya al lenguaje Python (o busque "Python"), seleccione "Desde código de Python existente", especifique un nombre para el proyecto, establezca **Ubicación** en la misma carpeta que el repositorio y haga clic en **Aceptar**. En el asistente que aparece, haga clic en **Finalizar**.

8. Seleccione **Vista > Explorador de soluciones** en el menú.

9. En el **Explorador de soluciones**, expanda el nodo `python3`, haga clic con el botón derecho en `contemplate_koans.py` y seleccione **Establecer como archivo de inicio**. Este paso indica a Visual Studio qué archivo debe usar al ejecutar el proyecto.

10. Seleccione **Proyecto > Koans Properties** en el menú, seleccione la pestaña **General** y establezca **Directorio de trabajo** en "python3". Este paso es necesario porque, de forma predeterminada, Visual Studio establece el directorio de trabajo en la raíz del proyecto en lugar de hacerlo en la ubicación del archivo de inicio (`python3\contemplate_koans.py`, que también puede ver en las propiedades del proyecto). El código de programa busca un archivo `koans.txt` en la carpeta de trabajo por lo que, si no cambia este valor, verá un error en tiempo de ejecución.

    ![Configuración del directorio de trabajo para un proyecto de Python](media/projects-set-working-directory.png)

11. Presione Ctrl+F5 o seleccione **Depurar > Iniciar sin depurar** para ejecutar el programa. Si ve el parámetro `FileNotFoundError` para `koans.txt`, compruebe la configuración del directorio de trabajo tal y como se describe en el paso anterior.

12. Cuando el programa se ejecuta correctamente, muestra un error de aserción en la línea 17 de `python3/koans/about_asserts.py`. Este comportamiento es deliberado: el programa está diseñado para que, con sus correcciones de todos los errores intencionados, se pueda enseñar a Python. (Encontrará más información en [Ruby Koans](http://rubykoans.com/), en el que se inspira Python Koans).

    ![Primer resultado del programa Python Koans](media/koans-output.png)

13. Abra `python3/koans/about_asserts.py` desde el Explorador de soluciones y haga doble clic en el archivo. Tenga en cuenta que los números de línea no aparecen de forma predeterminada en el editor. Para cambiar esta configuración, seleccione **Herramientas > Opciones**, seleccione **Mostrar todas las configuraciones** en la parte inferior del cuadro de diálogo, vaya a **Editor de texto > Python > General** y seleccione **Números de línea**:

    ![Activar el número de línea para archivos de Python](media/options-general-line-numbers.png)

14. Para corregir el error, cambie el `False` argumento de la línea 17 por `True`. La línea debe indicar lo siguiente:

    ```python
    self.assertTrue(True) # This should be True
    ```

15. Ejecute el programa otra vez. Si Visual Studio le advierte sobre los errores, responda con **Sí** para continuar la ejecución de código. Verá entonces que se supera la primera comprobación y el programa se detiene en el siguiente koan. Siga corrigiendo los errores y ejecutando el programa como quiera.

> [!Important]
> En este inicio rápido, ha creado un clon directo del repositorio *python_koans* en GitHub. El autor de este repositorio lo protege de cambios directos, por lo que se produce un error al intentar aplicar cambios. En la práctica, los desarrolladores bifurcan este repositorio en su propia cuenta de GitHub, efectúan cambios y crean solicitudes de incorporación de cambios para enviarlos al repositorio original. Cuando tenga su propia rama, use su dirección URL en lugar de la dirección URL de repositorio original utilizada anteriormente.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial: Trabajar con Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vea también

- [Manually identifying an existing Python interpreter](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment) (Identificación manual de un intérprete de Python existente).
- [Instalación de la compatibilidad con Python en Visual Studio 2015 y versiones anteriores](installing-python-support-in-visual-studio.md).
- [Ubicaciones de instalación](installing-python-support-in-visual-studio.md#install-locations).
