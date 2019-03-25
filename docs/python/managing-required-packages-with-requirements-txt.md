---
title: Administración de las dependencias de paquete con un archivo requirements.txt
description: Un archivo requirements.txt describe las dependencias de un proyecto. Si recibe un proyecto que contiene un archivo requirements.txt, puede instalar fácilmente esas dependencias en un solo paso.
ms.date: 03/18/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 88cd2ee237a92aff4ca6f641556b8003be550c3d
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194845"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Administración de los paquetes necesarios con requirements.txt

Si comparte un proyecto con otros usuarios, usa un sistema de compilación o pretende copiar el proyecto en cualquier otra ubicación donde necesita restaurar un entorno, necesita especificar los paquetes externos que dicho proyecto requiere. El enfoque recomendado es usar un [archivo requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) que contiene una lista de comandos para pip que instala las versiones necesarias de los paquetes dependientes. El comando más común es `pip freeze > requirements.txt`, que registra la lista de paquetes actual del entorno en *requirements.txt*.

Técnicamente, se puede utilizar cualquier nombre de archivo para realizar un seguimiento de los requisitos (mediante el uso de `-r <full path to file>` al instalar un paquete), pero Visual Studio proporciona compatibilidad específica para *requirements.txt*:

- Si ha cargado un proyecto que contiene *requirements.txt* y desea instalar todos los paquetes enumerados en ese archivo, expanda el nodo **Python Environments** en el **Explorador de soluciones** y, luego, haga clic con el botón derecho en un nodo de entorno y seleccione **Instalar desde requirements.txt**:

    ![Instalar desde requirements.txt](media/environments/environments-requirements-txt-install.png)

- Si quiere instalar las dependencias en un entorno virtual, cree y active primero ese entorno y luego use el comando **Instalar desde requirements.txt**. Para más información sobre cómo crear un entorno virtual, consulte [Uso de entornos virtuales](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Si ya tiene todos los paquetes necesarios instalados en un entorno, puede hacer clic con el botón derecho en ese entorno en el **Explorador de soluciones** y seleccionar **Generar requirements.txt** para crear el archivo necesario. Si el archivo ya existe, aparece un mensaje sobre cómo actualizarlo:

    ![Opciones de actualización de requirements.txt](media/environments/environments-requirements-txt-replace.png)

  - **Replace entire file** (Reemplazar todo el archivo) quita todos los elementos, comentarios y opciones que existen.
  - **Actualizar entradas existentes** detecta los requisitos del paquete y actualiza los especificadores de versión para que coincidan con la versión actualmente instalada.
  - **Update and add entries** (Actualizar y agregar entradas) actualiza todos los requisitos que se encuentran y agrega todos los demás paquetes al final del archivo.

Dado que los archivos *requirements.txt* están pensados para inmovilizar los requisitos de un entorno, todos los paquetes instalados se escriben con versiones precisas. Usar versiones precisas garantiza que puede reproducir fácilmente el entorno en otro equipo. Los paquetes se incluyen aunque se instalaran con un intervalo de versiones, como una dependencia de otro paquete, o con un instalador distinto de pip.

Si un paquete no se puede instalar mediante pip y aparece en un archivo *requirements.txt*, toda la instalación produce un error. En este caso, edite manualmente el archivo para excluir este paquete o para usar [opciones de pip](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) para hacer referencia a una versión instalable del paquete. Por ejemplo, puede ser preferible usar [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) para compilar una dependencia y agregar la opción `--find-links <path>` a su *requirements.txt*:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Vea también

- [Creación y administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)
