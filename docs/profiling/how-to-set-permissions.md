---
title: Establecer permisos | Microsoft Docs
description: Obtenga información sobre cómo un administrador de un equipo concede los permisos de seguridad necesarios para la generación de perfiles a un usuario o grupo que no tiene permisos de administrador.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2ab51b317164b8f2e828e0327021fb595574583c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722001"
---
# <a name="how-to-set-permissions"></a>Procedimiento Establecer permisos

En este artículo se describe cómo un administrador de un equipo concede los permisos de seguridad necesarios para la generación de perfiles a un usuario o grupo que no tiene permisos de administrador en ese equipo.

Un principio de seguridad básico indica que las aplicaciones se deberían ejecutar solo con los permisos que necesitan. Este principio se aplica también a los usuarios. Si los usuarios pueden ser totalmente efectivos cuando inician sesión como miembros del grupo Usuarios en lugar del grupo Administradores, no se les deben conceder permisos de administrador. En el primer procedimiento, "Para crear una cuenta de usuario que tenga permisos de usuario", se describe cómo crear una cuenta de usuario para un miembro del grupo Usuarios.

Los miembros del grupo Usuarios necesitarán acceso a las carpetas y archivos en disco que se comparten con otros miembros del equipo. En el segundo procedimiento, "Para conceder acceso a los archivos de proyecto compartido", se describe cómo conceder acceso.

Los miembros del grupo Usuarios pueden ejecutar las herramientas de generación de perfiles si un administrador les concede acceso al controlador de software para las herramientas de generación de perfiles. En el último procedimiento, "Para conceder acceso al controlador de generación de perfiles", se describe cómo conceder acceso a ese controlador.

> [!NOTE]
> Necesita permisos de administrador para seguir los pasos de estos procedimientos.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Para crear una cuenta de usuario que tenga permisos de usuario

1. Haga clic con el botón derecho en **Mi equipo** y después haga clic en **Administrar**.

     Se abre la ventana **Administración de equipos**.

2. Expandir **Grupos y usuarios locales**.

3. Haga clic con el botón derecho en la carpeta **Usuarios** y después haga clic en **Nuevo usuario**.

     Aparece el cuadro de diálogo **New usuario**.

4. Complete los campos de este cuadro de diálogo con la información de la cuenta de usuario que está creando. Especifique una contraseña. Si lo desea, active la casilla que exige al usuario cambiar la contraseña en el siguiente inicio de sesión.

5. Haga clic en **Crear** y después en **Cerrar**.

     El nuevo usuario aparece en el grupo Usuarios, un grupo de usuarios que no tienen permisos de administrador.

## <a name="to-grant-access-to-shared-project-files"></a>Para conceder acceso a archivos compartidos del proyecto

1. En el Explorador de Windows (o Explorador de archivos), busque la raíz del árbol de carpetas para los archivos de proyecto utilizados por este usuario y compartidos por el equipo del proyecto.

     La ruta de acceso de esta carpeta puede ser similar a la siguiente:

    ```cmd
    D:\ourProject
    ```

2. Haga clic con el botón derecho en la carpeta y después haga clic en **Propiedades**.

     Aparecerá el cuadro de diálogo **Propiedades de \<folder name>** .

3. Haga clic en la pestaña **Seguridad** .

4. Haga clic en el nombre de la cuenta de usuario en el cuadro **Grupo o nombres de usuario**.

5. En el cuadro **Permisos para \<user name>** , active la casilla **Control total**.

6. Haga clic en **Aceptar**.

     Esto concede permisos al usuario para el árbol de carpetas compartidas que comienza con la carpeta seleccionada en el paso 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Para conceder acceso al controlador de generación de perfiles

1. Abra un símbolo del sistema como administrador.

2. Cambie el directorio a:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Ejecute el siguiente comando:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Este comando instala e inicia el controlador para las herramientas de generación de perfiles.

     Este comando inicia el controlador y el servicio de generación de perfiles para que los usuarios que no son administradores puedan utilizar las funciones de generación de perfiles que están disponibles en su espacio de proceso de usuario. Solo los administradores pueden ejecutar el comando; si intenta ejecutarlo un usuario que no es administrador, se producirá un error.

     Tenga en cuenta que los efectos de este paso se deshacen al reiniciar el equipo, a menos que también realice el paso final de este procedimiento.

4. Ejecute el comando para permitir el acceso a la funcionalidad del controlador de generación de perfiles por un usuario o grupo que no tiene acceso de administrador en el equipo:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Este comando concede a la cuenta de \<user name> o \<group name> acceso a las herramientas de generación de perfiles. La opción \<right> determina la funcionalidad de generación de perfiles a la que el usuario puede acceder. La opción \<right> puede ser uno o varios de los valores siguientes:

    - FullAccess: permite el acceso a todos los métodos de generación de perfiles, incluyendo la recopilación de datos de rendimiento de servicios, muestreo y generación de perfiles entre sesiones.

    - SampleProfiling: permite el acceso a los métodos de generación de perfiles de muestra.

    - CrossSession: permite al acceso a la generación de perfiles entre sesiones que se requiere para los servicios de generación de perfiles.

5. (Opcional) Para conservar los resultados de cualquiera de los pasos anteriores después de reiniciar el equipo, ejecute el siguiente comando:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Después de iniciar sesión, los usuarios especificados podrán usar las herramientas de generación de perfiles sin permisos de administrador.

## <a name="see-also"></a>Vea también

[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[VSPerfCmd](../profiling/vsperfcmd.md)
[Generación de perfiles y seguridad de Windows Vista](../profiling/profiling-and-windows-vista-security.md)
