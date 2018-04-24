---
title: Configuración de un repositorio de Subversion en Visual Studio para Mac
description: Empleo de Git y Subversion en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: e6b6fd600d3f32c77651b9a4fbb0dff2cd754bcb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="setting-up-a-subversion-repository"></a>Configuración de un repositorio de Subversion

Subversion es un sistema de control de versiones centralizado. Esto significa que hay un único servidor que contiene todos los archivos y las revisiones desde el que los usuarios pueden extraer del repositorio cualquier versión de cualquier archivo. Cuando se extraen archivos de un repositorio remoto de Subversion, el usuario obtiene una instantánea del repositorio en ese momento dado.

Antes de comenzar a usar Subversion, se deben instalar las herramientas de línea de comandos de Xcode, ya que incluyen los paquetes de SVN correctos. Puede comprobar que SVN está instalado en Terminal con el siguiente comando:

`svn h`

1. Cree un repositorio gratuito de SVN en línea. En este ejemplo se ha usado [Assembla](https://app.assembla.com/). Una vez creado, se proporciona una dirección URL que se usa para conectarse al repositorio: 

    ![Obtención y copia de la dirección URL de SVN](media/version-control-subversion1-sml.png)

2. Abra o cree un proyecto de Visual Studio para Mac.

3. Haga clic con el botón derecho en el proyecto y seleccione **Control de versiones > Publicar en Control de versiones...**: 

    ![Inicio de publicación de proyecto](media/version-control-subversion2.png)

4. En la pestaña **Conectar a repositorio**, seleccione **Subversion** en la lista desplegable superior.

5. Escriba la dirección URL del paso 1. Esto debería rellenar los demás campos de forma predeterminada: 

    ![Cuadro de diálogo de selección de repositorio y especificación de detalles](media/version-control-subversion3.png)

7. Haga clic en **Aceptar** y luego confirme al hacer clic en **Publicar**.

7. Es posible que se le pida que escriba las credenciales del sitio en el que se crea el repositorio. Escríbalas como se muestra a continuación:

    ![](media/version-control-subversion5.png)

8.  Todos los comandos de control de versiones disponibles ya deberían aparecer en el menú de control de versiones.

