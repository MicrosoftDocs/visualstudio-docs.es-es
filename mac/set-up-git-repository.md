---
title: Configuración de un repositorio Git en Visual Studio para Mac | Microsoft Docs
description: Empleo de Git y Subversion en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 3eb3e0874cfc46fc98209113cf60a32cdb92787d
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="setting-up-a-git-repository"></a>Configuración de un repositorio Git

Git es un sistema de control de versiones distribuido que permite a los equipos trabajar en los mismos documentos de forma simultánea. Esto significa que hay un único servidor que contiene todos los archivos, pero que cada vez que se extrae un repositorio de este origen central, la totalidad del repositorio se clona localmente en el equipo del usuario.

Hay muchos hosts remotos que permiten trabajar con Git para el control de versiones, aunque el más común de estos es GitHub. En el ejemplo siguiente se usa un host de GitHub, pero puede usar cualquier host de Git para el control de versiones en Visual Studio para Mac.

Si quiere usar GitHub, asegúrese de haber creado y configurado una cuenta antes de seguir los pasos de este artículo. 

## <a name="creating-a-remote-repo-on-github"></a>Creación de un repositorio remoto en GitHub

En el ejemplo siguiente se usa un host de GitHub, pero puede usar cualquier host de Git para el control de versiones en Visual Studio para Mac.

Para configurar un repositorio Git, ejecute los siguientes pasos:

1. Cree un nuevo repositorio Git en github.com:

    ![Creación de un nuevo repositorio Git](media/version-control-git1-sml.png)

2. Defina el nombre, la descripción y la privacidad del repositorio. **No** inicialice el repositorio. Establezca .gitignore y la licencia en None:

    ![Establecimiento de los detalles del repositorio Git](media/version-control-git2.png)

3. La siguiente página le proporciona una opción para mostrar y copiar la dirección HTTPS o SSH en el repositorio que ha creado:

    ![ver y copiar la dirección](media/version-control-git3.png)

  Necesitará la dirección HTTPS para dirigir Visual Studio para Mac a este repositorio.


## <a name="publishing-an-existing-project"></a>Publicación de un proyecto existente

Si dispone de un proyecto que _aún no está_ en control de versiones, siga estos pasos para configurarlo en Git:

4.  Seleccione el nombre de la solución en el Panel de solución de Visual Studio para Mac. 

5. En la barra de menús, seleccione **Control de versiones > Publicar en Control de versiones...** para que aparezca el cuadro de diálogo **Seleccionar repositorio**:

    ![Iniciar la extracción del repositorio en Visual Studio para Mac](media/version-control-git4-sml.png)

    Si este elemento de menú aparece atenuado, asegúrese de que ha seleccionado el nombre de la solución.  

6. Elija la pestaña **Repositorios registrados** y haga clic en el botón **Agregar**:

    ![](media/version-control-git5.png)

7. Escriba el nombre del repositorio tal y como quiera que se muestre localmente y pegue la dirección URL del paso 3. El cuadro de diálogo Configuración del repositorio debería tener un aspecto similar al siguiente. Haga clic en Aceptar: 

    ![Especificación en el cuadro de diálogo de detalles de Git](media/version-control-git6.png)

    Tenga en cuenta que también es posible usar SSH para conectarse a Git.

8. Para intentar publicar la aplicación en Git, seleccione el repositorio y asegúrese de que se han rellenado los campos de texto **Nombre del módulo** y **Mensaje**:

    ![Intento de publicación del proyecto en Git](media/version-control-git7.png)

9. Haga clic en **Aceptar** y luego en **Publicar** en el cuadro de diálogo de alerta.

10. Si aún no ha escrito las credenciales de Git en las preferencias de Visual Studio para Mac, hágalo ahora. En primer lugar debe crear un token de acceso, que se usa en lugar de una contraseña. Si no ha creado un token de acceso, siga los pasos descritos en la documentación del [token de acceso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) de Git.

11. Escriba el nombre de usuario y el token de acceso personal y haga clic en **Aceptar**:

    ![Especificación del nombre de usuario y la contraseña de Git](media/version-control-git9-sml.png)

12. Pasados unos segundos, la solución debe publicarse con su confirmación inicial. Confirme que se ha publicado; para ello, vaya al elemento de menú Control de versiones, que ahora debería contener muchas opciones: 

    ![Menú Control de versiones](media/version-control-git10.png)

13. Cuando empiece a realizar otros cambios, seleccione **Insertar cambios...** para enviar los cambios realizados al repositorio **remoto**. Esto permitirá a todos los usuarios adecuados verlo en github.com: 

    ![Enviar cambios al repositorio remoto](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publicación de un proyecto nuevo

El cuadro de diálogo Nuevo proyecto puede usarse para publicar un proyecto nuevo con Git. Para habilitarlo, active la casilla **Usar Git para el control de versiones**, como se muestra en la captura de pantalla siguiente. Esto inicializará el repositorio y agregará un archivo .gitignore opcional:

![Enviar cambios al repositorio remoto](media/version-control-git12.png)

## <a name="checkout-an-existing-repository"></a>Desproteger un repositorio existente

Es muy probable que tenga que trabajar con un repositorio de GitHub que existe solo en el equipo remoto y no en el equipo local. Visual Studio para Mac permite desproteger este repositorio rápidamente. Siga estos pasos para clonarlo en el equipo:

1. En la barra de menús, seleccione **Control de versiones > Desproteger...** :

2. Se mostrará la pestaña **Conectar a repositorio**:

    ![Pestaña Conectar a repositorio con detalles especificados](media/version-control-git13.png)

3. En la página de GitHub del repositorio remoto, presione el botón **Clonar o descargar** y copie la URL proporcionada:

    ![url de github mostrada](media/version-control-git14.png)

4. Reemplace todo el texto del campo de entrada de la **URL** en la pestaña **Conectar a repositorio**. Se rellenarán automáticamente la mayoría de los campos de la pestaña, como se muestra en la imagen del paso 2.

5. Escriba el directorio en el que quiere clonar el repositorio y presione **Desproteger**.

> [!NOTE]
Puede que tenga problemas si el repositorio tiene más de 4 GB.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas para inicializar el proyecto con un repositorio remoto vacío, pruebe a seguir estos pasos:

- Vaya a la carpeta de la solución.
- Presione `Command + Shift + . ` para mostrar los archivos y las carpetas ocultos.
- Si hay una carpeta **.git**, elimínela.
- Si hay un archivo **gitignore**, elimínelo.
- Presione `Command + Shift + . ` para ocultar los archivos y las carpetas.
- Abra la solución en VS para Mac.
- En el panel de la solución, seleccione el nodo de esta.
- Vaya al menú Control de versiones y elija **Publicar en Control de versiones**.
- Siga los pasos del tutorial anterior a partir del paso 6.