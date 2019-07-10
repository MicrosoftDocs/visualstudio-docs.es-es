---
title: Configuración de un repositorio Git
description: Empleo de Git y Subversion en Visual Studio para Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 4fbee486a2e0263621f501b511d62abddbda8059
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692391"
---
# <a name="set-up-a-git-repository"></a>Configurar un repositorio Git

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

1. Seleccione el nombre de la solución en el Panel de solución de Visual Studio para Mac.

2. En la barra de menús, seleccione **Control de versiones > Publicar en control de versiones** para mostrar el cuadro de diálogo **Seleccionar repositorio**:

    ![Iniciar la extracción del repositorio en Visual Studio para Mac](media/version-control-git4-sml.png)

    Si este elemento de menú aparece atenuado, asegúrese de que ha seleccionado el nombre de la solución.

3. Elija la pestaña **Repositorios registrados** y haga clic en el botón **Agregar**:

    ![](media/version-control-git5.png)

4. Escriba el nombre del repositorio tal y como quiera que se muestre localmente y pegue la dirección URL del paso 3. El cuadro de diálogo Configuración del repositorio debería tener un aspecto similar al siguiente. Haga clic en Aceptar:

    ![Especificación en el cuadro de diálogo de detalles de Git](media/version-control-git6.png)

    También es posible usar SSH para conectarse a Git.

5. Para intentar publicar la aplicación en Git, seleccione el repositorio y asegúrese de que se hayan rellenado los campos de texto **Nombre del módulo** y **Mensaje**:

    ![Intento de publicación del proyecto en Git](media/version-control-git7.png)

6. Haga clic en **Aceptar** y luego en **Publicar** en el cuadro de diálogo de alerta.

7. En la ventana **Credenciales de Git**, escriba el nombre de usuario de GitHub y la contraseña. 

> [!NOTE]
> Si la cuenta tiene habilitada la autenticación de dos factores (2FA), deberá crear un token de acceso para usarlo en lugar de una contraseña. Si no ha creado un token de acceso, siga los pasos descritos en la documentación del [token de acceso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) de Git.

8. Escriba el nombre de usuario y el token de acceso personal y haga clic en **Aceptar**:

    ![Especificación del nombre de usuario y la contraseña de Git](media/version-control-git9-sml.png)

9. Pasados unos segundos, la solución debe publicarse con su confirmación inicial. Confirme que se ha publicado; para ello, vaya al elemento de menú Control de versiones, que ahora debería contener muchas opciones:

    ![Menú Control de versiones](media/version-control-git10.png)

10. Cuando empiece a realizar otros cambios, seleccione  **Insertar cambios**  para enviar los cambios realizados al repositorio  **remoto** . Esto permitirá a todos los usuarios adecuados verlo en github.com:

    ![Enviar cambios al repositorio remoto](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publicación de un proyecto nuevo

El cuadro de diálogo de nuevo proyecto puede usarse para crear un proyecto con un repositorio Git local. Para habilitarlo, seleccione la casilla **Usar Git para el control de versiones**, como se muestra en la captura de pantalla siguiente. Esto inicializará el repositorio y agregará un archivo .gitignore opcional:

![Crear un proyecto nuevo con compatibilidad con Git](media/version-control-git-publish-new1.png)

Siga estos pasos para insertar el nuevo repositorio local en un repositorio de GitHub también nuevo:

> [!NOTE]
> Si aún no ha creado un repositorio de GitHub, consulte la sección [Creación de un repositorio remoto en GitHub](#creating-a-remote-repo-on-github).

1. Cree su primera confirmación. Para ello, vaya a **Control de versiones > Revisar la solución y confirmar** en la barra de menús.

2. En la pestaña de estado, haga clic en **Confirmar** en la parte superior izquierda.

3. Escriba un mensaje de confirmación como, por ejemplo, "Primera confirmación" y, después, haga clic en **Confirmar**:

    ![Confirmar cambios iniciales en el repositorio Git](media/version-control-git-publish-new2.png)

4. A continuación, en la barra de menús vaya a **Control de versiones > Administrar ramas y orígenes remotos**.

5. Vaya a la **Orígenes remotos** y, después, haga clic en **Agregar**.

6. En la ventana **Origen remoto**, agregue los detalles del repositorio de GitHub creado anteriormente y haga clic en **Aceptar**:

    ![Configurar orígenes remotos para el repositorio de Git](media/version-control-git-publish-new3.png)

7. Cierre la ventana **Configuración del repositorio Git** y después, en la barra de menús, vaya a **Control de versiones > Insertar cambios**.

8. En la ventana **Insertar en el repositorio**, haga clic en el botón **Insertar cambios**:

    ![Insertar los cambios en el repositorio remoto](media/version-control-git-publish-new4.png)

9. Cuando se le solicite, escriba el nombre de usuario de GitHub y la contraseña.

> [!NOTE]
> Si la cuenta tiene habilitada la autenticación de dos factores (2FA), deberá crear un token de acceso para usarlo en lugar de una contraseña. Si no ha creado un token de acceso, siga los pasos descritos en la documentación del [token de acceso](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) de Git.

Visual Studio para Mac ahora insertará los cambios en el repositorio de GitHub remoto:

![Confirmación de que la operación de inserción se completó correctamente](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Desproteger un repositorio existente

Es probable que tenga que trabajar con un repositorio de GitHub que solo exista en el equipo remoto y no en el local. Visual Studio para Mac permite desproteger este repositorio rápidamente. Siga estos pasos para clonarlo en el equipo:

1. En la barra de menús, seleccione **Control de versiones > Desproteger**:

2. Se mostrará la pestaña **Conectar a repositorio**:

    ![Pestaña Conectar a repositorio con detalles especificados](media/version-control-git13.png)

3. En la página de GitHub del repositorio remoto, presione el botón **Clonar o descargar** y copie la URL proporcionada:

    ![url de github mostrada](media/version-control-git14.png)

4. Reemplace todo el texto del campo de entrada de la **URL** en la pestaña **Conectar a repositorio**. Se rellenarán automáticamente la mayoría de los campos de la pestaña, como se muestra en la imagen del paso 2.

5. Escriba el directorio en el que quiere clonar el repositorio y presione **Desproteger**.

> [!NOTE]
> Puede que tenga problemas si el repositorio tiene más de 4 GB.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas para inicializar el proyecto con un repositorio remoto vacío, pruebe a seguir estos pasos:

1. Vaya a la carpeta de la solución.
1. Presione **Comando + Mayús + .** para mostrar los archivos y las carpetas ocultos.
1. Si hay una carpeta **.git**, elimínela.
1. Si hay un archivo **gitignore**, elimínelo.
1. Presione **Comando + Mayús + .** para ocultar los archivos y las carpetas.
1. Abra la solución en VS para Mac.
1. En el panel de la solución, seleccione el nodo de esta.
1. Vaya al menú Control de versiones y elija **Publicar en Control de versiones**.
1. Siga los pasos del tutorial anterior a partir del paso 6.

## <a name="see-also"></a>Vea también

- [Version control in Visual Studio (on Windows)](/visualstudio/version-control/) (Control de versiones en Visual Studio [en Windows])
