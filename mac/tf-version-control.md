---
title: Control de versiones TF
description: Conectarse a Team Foundation Server o Visual Studio Team Services con Control de versiones de Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693778"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conectarse a Control de versiones de Team Foundation 

> [!NOTE]
> **Nota**: la compatibilidad con Control de versiones de Team Foundation está actualmente en vista previa y algunas funciones todavía no funcionan al completo. Nos encantaría recibir comentarios suyos sobre cualquier problema en la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/spaces/41/index.html). Hay más cambios pendientes.

Visual Studio Team Services (VSTS) y Team Foundation Server (TFS) proporcionan dos modelos de control de versiones: Git, que es un control de versiones distribuido y Control de versiones de Team Foundation (TFVC), que es un control de versiones centralizado. Este artículo proporciona información general y un punto de partida para usar Control de versiones de Team Foundation con Visual Studio para Mac.

## <a name="requirements"></a>Requisitos

* Visual Studio para Mac, versión 7.5 o posterior.
* Visual Studio Team Services o Team Foundation Server 2013 y versiones posteriores
* Un proyecto en Visual Studio Team Services o Team Foundation Server, configurado para que use Control de versiones de Team Foundation.

## <a name="installation"></a>Instalación

En Visual Studio para Mac, elija **Visual Studio > Extensiones...** en el menú. En la pestaña **Galería**, seleccione **Control de versiones > Control de versiones de Team Foundation para TFS y VSTS** y haga clic en **Instalar...**:

  ![Administrador de extensiones](media/tfvc-install.png) 

Siga las indicaciones para instalar la extensión. Una vez instalada, reinicie el IDE.

## <a name="using-the-add-in"></a>Usar el complemento

Una vez que la extensión esté instalada, seleccione el elemento de menú **Control de versiones > TFS/VSTS > Connect to Team Foundation Version Control...** (Conectarse a Control de versiones de Team Foundation...). Haga clic en **Agregar** para agregar una cuenta nueva: 

![Agregar un servidor TFVC](media/tfvc-add-remove-server.png)

Elija entre Visual Studio Team Services o Team Foundation Server para comenzar:

![Conectar con un servidor TFVC](media/tfvc-choose-server-type.png)

Escriba sus credenciales y haga clic en **Iniciar sesión**: 

![Inicie sesión en un servidor TFVC](media/tfvc-login.png)

Cuando haya iniciado sesión correctamente, seleccione los proyectos a los que quiere obtener acceso y presione **Aceptar**: 

![Elegir proyectos](media/tfvc-choose-projects.png)

Seleccione el elemento de menú **Control de versiones > TFS/VSTS > Explorador de control de código fuente** para abrir el Explorador de control de código fuente, con el que podrá examinar el código fuente.

> [!IMPORTANT]
> **Problema conocido**: en esta versión preliminar, la primera vez que abra el explorador de control de código fuente, tendrá que [crear una nueva área de trabajo](#creating-a-new-workspace).

![Explorador de código fuente](media/tfvc-source-explorer.png)

En el explorador de código fuente puede examinar el código fuente en el servidor y realizar las siguientes acciones:

- Administrar áreas de trabajo (crear, editar o eliminar).
- Navegar entre la estructura del proyecto.
- Asignar proyectos.
- Obtener proyectos.
- Bloquear y desbloquear archivos.
- Cambiar nombre de archivos.
- Eliminar archivos.
- Agregar nuevo archivo.
- Desproteger.
- Proteger.
- Ver historial de cambios.
- Comparar cambios.

## <a name="creating-a-new-workspace"></a>Crear una nueva área de trabajo

En el explorador de control de código fuente, haga clic en el botón **Administrar áreas de trabajo**. 

![Administrar áreas de trabajo](media/tfvc-manage-workspaces.png)

Haga clic en el botón **Agregar** para crear una nueva área de trabajo.

![Crear área de trabajo](media/tfvc-create-workspace.png)

Proporcione un nombre para el área de trabajo y, después, haga clic en **Add Working Folder** (Agregar carpeta de trabajo) para asignar el proyecto a una carpeta local en el equipo.

Cuando termine, haga clic en **Aceptar** y luego cierre el cuadro de diálogo Administrar áreas de trabajo. Ya está listo para obtener los archivos a través del editor de código de origen y empezar a trabajar.

## <a name="troubleshooting"></a>Solución de problemas

### <a name="problems-using-basic-authentication"></a>Problemas con la autenticación básica

Hay una serie de opciones disponibles para llevar a cabo la autenticación con un servidor:

- OAuth
- Básico
- Ntlm

Para poder usar la autenticación básica, es necesario habilitar **Credenciales de autenticación alternativas** en VSTS. Para ello, siga estos pasos:

1. Inicie sesión como propietario en la cuenta de VSTS (https://{su_cuenta}.visualstudio.com).
2. En la barra de herramientas de la cuenta, haga clic en el icono de engranaje y seleccione **Directiva**: ![Opción Configuración de directiva seleccionada](media/tfvc-auth2.png) 
3. Revise la configuración de conexión de la aplicación. Cambie esta configuración en función de sus directivas de seguridad: ![Opción Configuración de directiva seleccionada](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>No veo nada en TFVC

Para configurar el Control de versiones de Team Foundation (TFVC) en el equipo de desarrollo, **debe** crear un área de trabajo, como se describe en la sección [Crear una nueva área de trabajo](#creating-a-new-workspace).

En el Explorador de control de código fuente, presione el botón **Administrar áreas de trabajo**. Siga los pasos para asignar el proyecto de equipo a una carpeta de su equipo de desarrollo.

### <a name="i-do-not-see-any--all-of-my-projects"></a>No veo ninguno o todos mis proyectos

Después de la autenticación, debería ver la lista de proyectos. De forma predeterminada solo se muestran los proyectos de TFS. Para ver otros tipos de proyectos, active la casilla "Ver todos los proyectos".

Tenga en cuenta que los proyectos que están en el servidor no aparecerán si no tiene los privilegios adecuados.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Recibo el error "No se puede crear el área de trabajo. Vuelva a intentarlo".

Al intentar [crear una nueva área de trabajo](#creating-a-new-workspace), debe asegurarse de que se cumplen las siguientes condiciones:

- No se deben emplear caracteres no válidos en el nombre del área de trabajo.
- El nombre debe tener menos de 64 caracteres.
- La ruta de acceso local no se puede usar en otras áreas de trabajo.