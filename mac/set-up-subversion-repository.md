---
title: Configuración de un repositorio de Subversion
description: Empleo de Subversion en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: e5f395511ad3b2b3cc4568a4d701ca5dbcc02736
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="setting-up-a-subversion-repository"></a>Configuración de un repositorio de Subversion

Subversion es un _sistema centralizado de control de versiones_, lo que significa que hay un único servidor que contiene todos los archivos y las revisiones desde el que los usuarios pueden extraer del repositorio cualquier versión de cualquier archivo. Cuando se extraen archivos de un repositorio remoto de Subversion, el usuario obtiene una instantánea del repositorio en ese momento dado.

Para usar Subversion para el control de versiones, debe instalarlo en el equipo. Para comprobar si Subversion está instalado en el equipo, use el comando siguiente en la terminal:

```bash
svn --version
```

Este comando devuelve el número de versión.

Si Subversion aún no está instalado, la manera más fácil de obtenerlo es instalar las _Herramientas de línea de comandos de Xcode_. Use el comando siguiente para instalar las Herramientas de línea de comandos de Xcode y Subversion.

```bash
xcode-select --install
```

Una vez que Subversion esté instalado en el equipo, siga estos pasos para publicar el proyecto en SVN.

1. Cree un repositorio gratuito de SVN en línea. En este ejemplo se ha usado [Assembla](https://app.assembla.com/). Una vez creado, se proporciona una dirección URL que se usa para conectarse al repositorio: 

    ![Copiar la URL de SVN](media/version-control-subversion1-sml.png)

2. Abra o cree un proyecto de Visual Studio para Mac.

3. Haga clic con el botón derecho en el proyecto y seleccione **Control de versiones > Publicar en Control de versiones...**: 

    ![Inicio de publicación de proyecto](media/version-control-subversion2.png)

4. En la pestaña **Conectar a repositorio**, seleccione **Subversion** en la lista desplegable superior.

5. Escriba la dirección URL del paso 1. Cuando escriba la dirección URL, los demás campos se rellenan de forma predeterminada: 

    ![Cuadro de diálogo de selección de repositorio y especificación de detalles](media/version-control-subversion3.png)

7. Haga clic en **Aceptar** y luego confirme al hacer clic en **Publicar**.

7. Si se le pide, escriba las credenciales del sitio en el que se crea el repositorio, tal y como se muestra a continuación:

    ![Escribir las credenciales del repositorio de Subversion](media/version-control-subversion5.png)

8.  Todos los comandos de control de versiones disponibles ya deberían aparecer en el menú de control de versiones.

