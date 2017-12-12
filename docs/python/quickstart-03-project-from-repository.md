---
title: "Inició rápido: Clonado de un repositorio de código Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ce09377-9073-404c-9339-fa871a4b0841
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 8ba37a922c24a02d7586b9c95f57ad27a7152736
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Inició rápido: Clonado de un repositorio de código Python en Visual Studio

Después de [instalar la compatibilidad con Python en Visual Studio 2017](installation.md), podrá clonar fácilmente un repositorio de código Python y crear un proyecto a partir de él.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Inicie Visual Studio.

3. Seleccione **Ver > Team Explorer...**  para abrir la ventana **Team Explorer** desde la que podrá conectarse a GitHub o Visual Studio Team Services o clonar un repositorio.

    ![Ventana de Team Explorer en la que se muestra Visual Studio Team Services, GitHub y el clonado de un repositorio](media/team-explorer.png)

4. En el campo de dirección URL en **Repositorios Git locales**, escriba `https://github.com/gregmalcolm/python_koans`, especifique una carpeta para los archivos clonados y seleccione **Clonar**.

    > [!Tip]
    > La carpeta que especifique en Team Explorer es la carpeta específica para recibir los archivos clonados. A diferencia del comando `git clone`, al crear un clon en Team Explorer no se crea automáticamente una subcarpeta con el nombre del repositorio.

5. Al finalizar el clonado, haga doble clic en la carpeta del repositorio en la parte inferior de Team Explorer para ir al panel de repositorio. En **Soluciones**, seleccione **Nueva...**.

    ![Ventana de Team Explorer en al que se muestra la creación de un nuevo proyecto a partir de un clon](media/team-explorer-new-project.png)

6. En el cuadro de diálogo **Nuevo proyecto** que se muestra, seleccione "Desde código de Python existente", especifique un nombre para el proyecto, establezca **Ubicación** en la misma carpeta que el repositorio y seleccione **Aceptar**. En el asistente que aparece, seleccione **Finalizar**.

7. Seleccione **Vista > Explorador de soluciones** en el menú.

8. En el Explorador de soluciones, expanda el nodo `python3`, haga clic con el botón derecho en `contemplate_koans.py` y seleccione **Establecer como archivo de inicio**. Este paso indica a Visual Studio qué archivo debe utilizar al ejecutar el proyecto.

9. Seleccione **Proyecto > Propiedades** en el menú, seleccione la pestaña **General** y establezca el **Directorio de trabajo** en "python3". Este paso es necesario porque, de forma predeterminada, Visual Studio establece el directorio de trabajo en la raíz del proyecto en lugar de hacerlo en la ubicación del archivo de inicio (`python3\contemplate_koans.py`, que también puede ver en las propiedades del proyecto). El código de programa busca un archivo `koans.txt` en la carpeta de trabajo, por lo que si no cambia este valor, verá un error en tiempo de ejecución.

    ![Configuración del directorio de trabajo para un proyecto de Python](media/projects-set-working-directory.png)

10. Presione Ctrl+F5 o seleccione **Depurar > Iniciar sin depurar** para ejecutar el programa. Si ve el parámetro `FileNotFoundError` para `koans.txt`, vuelva a comprobar la configuración del directorio de trabajo en el paso anterior.

11. Cuando el programa se ejecuta correctamente, muestra un error de aserción en la línea 17 de `python3/koans/about_asserts.py`. Este comportamiento es deliberado: el programa está diseñado para que, con sus correcciones de todos los errores intencionados, se pueda enseñar a Python. (Encontrará más información en [Ruby Koans](http://rubykoans.com/), en el que se inspira Python Koans).

    ![Primer resultado del programa Python Koans](media/koans-output.png)

12. Abra `python3/koans/about_asserts.py` desde el Explorador de soluciones y haga doble clic en el archivo. Tenga en cuenta que los números de línea no aparecen de forma predeterminada en el editor. Para cambiar esta configuración, seleccione **Herramientas > Opciones**, seleccione **Mostrar todas las configuraciones** en la parte inferior del cuadro de diálogo, vaya a **Editor de texto > Python > General** y seleccione **Números de línea**:

    ![Activar el número de línea para archivos de Python](media/options-general-line-numbers.png)

13. Para corregir el error, cambie el `False` argumento de la línea 17 por `True`. La línea debe indicar lo siguiente:

    ```python
    self.assertTrue(True) # This should be True
    ```

14. Vuelva a ejecutar el programa para ver si se supera la primera comprobación y el programa se detiene en el siguiente koan. Siga corrigiendo los errores y volviendo a ejecutar el programa como quiera.

> [!Important]
> En este tutorial rápido, ha creado un clon directo del repositorio *python_koans* en GitHub. El autor de este repositorio lo protege de cambios directos, por lo que se produce un error al intentar aplicar cambios. En la práctica, los desarrolladores bifurcan este repositorio en su propia cuenta de GitHub, efectúan cambios y crean solicitudes de incorporación de cambios para enviarlos al repositorio original. Estos pasos se describen en [Tutorial, paso 6: Uso de Git](vs-tutorial-01-06.md).

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial: Uso de Python en Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Vea también

- [Creación de un entorno para un intérprete de Python existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Instalación de la compatibilidad con Python en Visual Studio 2015 y versiones anteriores](installation.md).
- [Ubicaciones de instalación](installation.md#install-locations).
