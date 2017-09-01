---
title: "Configuración de un repositorio Git en Visual Studio para Mac"
description: Empleo de Git y Subversion en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>Configuración de un repositorio Git

Git es un sistema de control de versiones distribuido que permite a los equipos trabajar en los mismos documentos de forma simultánea. Esto significa que hay un único servidor que contiene todos los archivos, pero que cada vez que se extrae un repositorio de este origen central, la totalidad del repositorio se clona localmente en el equipo del usuario.

Hay muchos hosts remotos que permiten trabajar con Git para el control de versiones, aunque el más común de estos es GitHub. En el ejemplo siguiente se usa un host de GitHub, pero puede usar cualquier host de Git para el control de versiones en Visual Studio para Mac.

Si quiere usar GitHub, asegúrese de haber creado y configurado una cuenta antes de seguir los pasos siguientes. 

## <a name="creating-a-remote-repo-on-github"></a>Creación de un repositorio remoto en GitHub

En el ejemplo siguiente se usa un host de GitHub, pero puede usar cualquier host de Git para el control de versiones en Visual Studio para Mac.

Para configurar un repositorio Git, ejecute los siguientes pasos:

1. Cree un nuevo repositorio Git en github.com:

    ![Creación de un nuevo repositorio Git](media/version-control-git1-sml.png)

2. Defina el nombre, la descripción y la privacidad del repositorio. **No** inicialice el repositorio. Establezca .gitignore y la licencia en None:

    ![Establecimiento de los detalles del repositorio Git](media/version-control-git2.png)

3. La siguiente ubicación le proporciona una opción para mostrar y copiar la dirección HTTPS o SSH en el repositorio que acaba de crear:

    ![Ver y copiar la dirección](media/version-control-git3.png) Necesitará la dirección HTTPS para dirigir Visual Studio para Mac a este repositorio.


## <a name="publishing-an-existing-project"></a>Publicación de un proyecto existente

4. Vuelva al proyecto abierto en Visual Studio para Mac. 

5. En la barra de menús, seleccione **Control de versiones > Publicar en Control de versiones...**:

    ![Iniciar la extracción del repositorio en Visual Studio para Mac](media/version-control-git4-sml.png)

6. Esto mostrará el cuadro de diálogo **Seleccionar repositorio**. Elija la pestaña **Repositorios registrados** y haga clic en el botón **Agregar**:

    ![](media/version-control-git5.png)

7. Escriba el nombre del repositorio tal y como quiera que se muestre localmente y pegue la dirección URL del paso 3. El cuadro de diálogo Configuración del repositorio debería tener un aspecto similar al siguiente. Haga clic en Aceptar: 

    ![Especificación en el cuadro de diálogo de detalles de Git](media/version-control-git6.png)

    Tenga en cuenta que también es posible usar SSH para conectarse a Git.

8. Para intentar publicar la aplicación en Git, seleccione el repositorio que acaba de crear y asegúrese de que se han rellenado los campos de texto **Nombre del módulo** y **Mensaje**:

    ![Intento de publicación del proyecto en Git](media/version-control-git7.png)

9. Haga clic en **Aceptar** y luego en **Publicar** en el cuadro de diálogo de alerta.

10. Si aún no ha escrito las credenciales de Git en las preferencias de Visual Studio para Mac, hágalo ahora. En primer lugar debe crear un token de acceso, que se usa en lugar de una contraseña. Para ello, siga los pasos de la documentación de Git [Token de acceso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).

11. Escriba el nombre de usuario y el token de acceso personal y haga clic en **Aceptar**:

    ![Especificación del nombre de usuario y la contraseña de Git](media/version-control-git9-sml.png)

12. Pasados unos segundos, la solución debe publicarse con su confirmación inicial. Confírmelo en el elemento de menú Control de versiones, que ahora debería contener muchas opciones: 

    ![Menú Control de versiones](media/version-control-git10.png)

13. Cuando empiece a realizar otros cambios, seleccione **Insertar cambios...** para enviar los cambios realizados al repositorio **remoto**. Esto permitirá a todos los usuarios adecuados verlo en github.com: 

    ![Enviar cambios al repositorio remoto](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publicación de un proyecto nuevo

El cuadro de diálogo Nuevo proyecto puede usarse para publicar un proyecto nuevo con Git. Para habilitarlo, active la casilla **Usar Git para el control de versiones**, como se muestra en la captura de pantalla siguiente. Esto inicializará el repositorio y agregará un archivo opcional .gitignore:

![Enviar cambios al repositorio remoto](media/version-control-git12.png)

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas con la inicialización del proyecto con un repositorio remoto vacío, puede probar los siguientes pasos:

- Vaya a la carpeta de la solución.
- Presione `Command + Shift + . ` para mostrar los archivos y las carpetas ocultos.
- Si hay una carpeta `.git`, elimínela.
- Si hay un archivo `gitignore`, elimínelo.
- Presione `Command + Shift + . ` para ocultar los archivos y las carpetas.
- Abra la solución en VS para Mac.
- En el panel de la solución, seleccione el nodo de esta.
- Vaya al menú Control de versiones y elija **Publicar en Control de versiones**.
- Siga los pasos del tutorial anterior a partir del paso 6.
