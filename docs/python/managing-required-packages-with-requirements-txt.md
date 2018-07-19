---
title: Uso de un archivo requirements.txt para administrar los requisitos de un paquete
description: Puede usar un archivo requirements.txt para administrar las dependencias de un proyecto. Si recibe un proyecto que contiene un archivo requirements.txt, puede instalar fácilmente esas dependencias en un solo paso.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a97a274053f95aac3cc676c17e50e23906fea377
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117006"
---
# <a name="managing-required-packages-with-requirementstxt"></a>Administración de los paquetes necesarios con requirements.txt

Si comparte un proyecto con otros usuarios mediante un sistema de compilación o pretende [publicarlo en Microsoft Azure](python-azure-cloud-service-project-template.md), necesita especificar los paquetes externos que dicho proyecto requiere. El enfoque recomendado es usar un [archivo requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) que contiene una lista de comandos para pip que instala las versiones necesarias de los paquetes dependientes.

Técnicamente, se puede utilizar cualquier nombre de archivo para realizar un seguimiento de los requisitos (mediante el uso de `-r <full path to file>` al instalar un paquete), pero Visual Studio proporciona compatibilidad específica para `requirements.txt`:

- Si ha cargado un proyecto que contiene `requirements.txt` y desea instalar todos los paquetes enumerados en ese archivo, expanda el nodo **Python Environments** en el **Explorador de soluciones** y, luego, haga clic con el botón derecho en un nodo de entorno y seleccione **Install from requirements.txt** (Instalar desde requirements.txt):

    ![Instalar desde requirements.txt](media/environments-requirements-txt-install.png)

- Si ya tiene todos los paquetes necesarios instalados en un entorno, puede hacer clic con el botón derecho en ese entorno en el Explorador de soluciones y seleccionar **Generate requirements.txt** (Generar requirements.txt) para crear el archivo necesario. Si el archivo ya existe, aparece un mensaje sobre cómo actualizarlo:

    ![Opciones de actualización de requirements.txt](media/environments-requirements-txt-replace.png)

  - **Replace entire file** (Reemplazar todo el archivo) quita todos los elementos, comentarios y opciones que existen.
  - **Actualizar entradas existentes** detecta los requisitos del paquete y actualiza los especificadores de versión para que coincidan con la versión actualmente instalada.
  - **Update and add entries** (Actualizar y agregar entradas) actualiza todos los requisitos que se encuentran y agrega todos los demás paquetes al final del archivo.

Dado que los archivos `requirements.txt` están pensados para inmovilizar los requisitos de un entorno, todos los paquetes instalados se escriben con versiones precisas. Usar versiones precisas garantiza que puede reproducir fácilmente el entorno en otro equipo. Los paquetes se incluyen aunque se instalaran con un intervalo de versiones, como una dependencia de otro paquete, o con un instalador distinto de pip.

Si un paquete no se puede instalar mediante pip y aparece en un archivo `requirements.txt`, toda la instalación produce un error. En este caso, edite manualmente el archivo para excluir este paquete o para usar [opciones de pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) para hacer referencia a una versión instalable del paquete. Por ejemplo, puede ser preferible usar [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) para compilar una dependencia y agregar la opción `--find-links <path>` a su `requirements.txt`:

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

- [Administración de entornos de Python en Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selección de un intérprete para un proyecto](selecting-a-python-environment-for-a-project.md)
- [Rutas de acceso de búsqueda](search-paths.md)
- [Referencia de ventana Entornos de Python](python-environments-window-tab-reference.md)