---
title: Control de versiones TF
description: Conectarse a Team Foundation Server o Visual Studio Team Services con Control de versiones de Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 51d066289809842cd50974cbb37a89bc7a73d5dc
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37438466"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conectarse a Control de versiones de Team Foundation 

> [!NOTE]
> **Nota**: la compatibilidad con Control de versiones de Team Foundation está actualmente en vista previa y algunas funciones todavía no funcionan al completo. Nos encantaría recibir comentarios suyos sobre cualquier problema en la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/spaces/41/index.html). Hay más cambios pendientes.

Visual Studio Team Services (VSTS) y Team Foundation Server (TFS) proporcionan dos modelos de control de versiones: Git, que es un control de versiones distribuido y Control de versiones de Team Foundation (TFVC), que es un control de versiones centralizado. Este artículo proporciona información general y un punto de partida para usar Control de versiones de Team Foundation con Visual Studio para Mac.

## <a name="requirements"></a>Requisitos

* Visual Studio Community, Professional o Enterprise para Mac versión 7.5 o posterior.
* Visual Studio Team Services o Team Foundation Server 2013 y versiones posteriores.
* Un proyecto en Visual Studio Team Services o Team Foundation Server, configurado para que use Control de versiones de Team Foundation.

## <a name="installation"></a>Instalación

En Visual Studio para Mac, elija **Visual Studio > Extensiones...** en el menú. En la pestaña **Galería**, seleccione **Control de versiones > Control de versiones de Team Foundation para TFS y VSTS** y haga clic en **Instalar...**:

  ![Administrador de extensiones](media/tfvc-install.png) 

Siga las indicaciones para instalar la extensión. Una vez instalada, reinicie el IDE.

## <a name="updating-the-extension"></a>Actualizar la extensión

La extensión de TFVC se actualiza periódicamente. Para acceder a las actualizaciones, elija **Visual Studio > Extensiones** desde el menú y seleccione la pestaña **Actualizaciones**. Seleccione la extensión en la lista y haga clic en el botón **Actualización**:

  ![Administrador de extensiones mostrando la actualización](media/tfvc-update.png) 

Haga clic en **Instalar** en el cuadro de diálogo siguiente para desinstalar el paquete antiguo e instalar el nuevo.

Para obtener información sobre cuáles son las novedades en cada versión, vea las [Notas de la versión](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Usar el complemento

Una vez que la extensión está instalada, seleccione el elemento de menú **Control de versiones > TFS/VSTS > Open from Remote Repository** (Abrir desde el repositorio remoto). 

Elija entre Visual Studio Team Services o Team Foundation Server para comenzar y haga clic en **Continuar**:

  ![Conectar con un servidor](media/tfvc-choose-server-type.png)

### <a name="vsts-authentication"></a>Autenticación de VSTS

Cuando selecciona un proyecto que se hospeda en VSTS, se le pedirá que escriba los detalles de la cuenta de Microsoft:

  ![Conectar con un servidor VSTS](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Autenticación de TFS

Para conectarse a TFS, escriba los detalles del servidor y las credenciales de cuenta. Escriba un dominio para usar la autenticación NTLM. En caso contrario, déjelo en blanco para usar la autenticación básica. Seleccione **Agregar servidor**: 

![Inicio de sesión en un servidor TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Seleccionar un proyecto

Una vez que se ha autenticado correctamente, puede ver una lista de repositorios que están asociados con la cuenta en el cuadro de diálogo **Abrir desde el control de código fuente**:

  ![Muestra del cuadro de diálogo Abrir desde el control de código fuente con proyectos](media/tfvc-vsts-projects.png)

Este cuadro de diálogo se organiza con los siguientes nodos:

- Cuenta de VSTS o colección: esto muestra todas las cuentas conectadas a la cuenta de Microsoft con la que inició sesión.
- Proyectos de equipo: dentro de cada VSTS puede tener una serie de proyectos de equipo. Un proyecto de equipo es donde se hospedan el código fuente, los elementos de trabajo y las compilaciones automatizadas.

En este momento, puede buscar y filtrar por el nombre de un proyecto o la cuenta.

### <a name="adding-a-new-server"></a>Agregar un nuevo servidor

Para agregar un nuevo servidor a la lista, haga clic en el botón **Agregar host** situado en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Botón de agregar resaltado para agregar un nuevo servidor a la lista](media/tfvc-add-new-server.png)

Seleccione el proveedor de la lista y escriba sus credenciales:

![Cuadro de diálogo que muestra la opción de proveedor de control de código fuente](media/tfvc-add-new-creds.png)

## <a name="creating-a-new-workspace"></a>Crear una nueva área de trabajo

Para empezar a trabajar con un proyecto, debe tener un _área de trabajo_. Si aún no tiene un área de trabajo, puede crear una desde el cuadro combinado **Área de trabajo** en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Opción del cuadro combinado para crear una nueva área de trabajo](media/tfvc-create-new-workspace.png)

Establezca el nombre y la ruta de acceso local para la nueva área de trabajo y seleccione **Crear área de trabajo**:

![Escribir un nombre y una ruta de acceso local para la nueva área de trabajo](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Usar el Explorador de código fuente

Una vez que ha creado un área de trabajo y asigna el proyecto, puede empezar a trabajar con el _Explorador de código fuente_.

Para abrir el Explorador de código fuente, seleccione **Control de versiones > TFS/VSTS > Explorador de control de código fuente**:

![Elemento de menú para abrir el Explorador de código fuente](media/tfvc-source-control-explorer.png)

El Explorador de código fuente permite navegar por todos los proyectos asignados, sus archivos y carpetas. También permite realizar todas las acciones de control de código fuente básicas, como:

- Obtener la última versión
- Obtener una versión específica
- Proteger y desproteger archivos
- Bloquear y desbloquear archivos
- Agregar, eliminar y cambiar el nombre de archivos
- Ver historial
- Comparar cambios.

Muchas de estas acciones están disponibles a través de acciones del menú contextual en el proyecto:

![Acciones del menú contextual para un proyecto](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Administrar áreas de trabajo

Si no lo ha hecho ya, cree un área de trabajo, como se describe en la sección [Crear un área de trabajo](#creating-a-new-workspace), y observará que el Explorador de código fuente está vacío:

![Explorador de código fuente vacío](media/tfvc-setup-empty-sce.png) 

Para configurar el proyecto remoto con un área de trabajo local, siga estos pasos:

1. Seleccione el **Servidor** del cuadro combinado.
1. Tenga en cuenta que no hay "ningún área de trabajo" y que la ruta de acceso local está "Sin asignar". Seleccione el vínculo **Sin asignar** para mostrar el cuadro de diálogo **Crear nueva área de trabajo**.
1. Proporcione un nombre para el área de trabajo y, después, haga clic en **Add Working Folder** (Agregar carpeta de trabajo) para asignar el proyecto a una carpeta local en el equipo:
    
    ![Cuadro de diálogo para crear un área de trabajo que muestra las opciones predeterminadas](media/tfvc-workspace1.png) 

1. Seleccione la carpeta "$" para asignar todos los proyectos de equipo del servidor a la misma área de trabajo, o bien seleccione un proyecto individual y haga clic en **Aceptar**:
    
    ![Cuadro de diálogo para examinar las carpetas que muestra todos los proyectos](media/tfvc-workspace2.png) 

1. Seleccione la ubicación en el equipo local a la que quiera asignar los proyectos y haga clic en **Seleccionar carpeta**.
1. Confirme los detalles de la nueva área de trabajo presionando **Aceptar**.
    
    ![Cuadro de diálogo de creación de una nueva área de trabajo con la carpeta de trabajo agregada](media/tfvc-workspace3.png) 

Una vez configurada el área de trabajo, se puede cambiar o quitar haciendo clic en el botón **Administrar áreas de trabajo** del Explorador de código fuente.

![Administrar áreas de trabajo](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Solución de problemas

### <a name="problems-using-basic-authentication"></a>Problemas con la autenticación básica

Las siguientes opciones pueden usarse para autenticar con un servidor:

- OAuth
- Básico
- Ntlm

Para poder usar la autenticación básica, es necesario habilitar **credenciales de autenticación alternativas** en VSTS. Para ello, siga estos pasos:

1. Inicie sesión como propietario en la cuenta de VSTS (https://{su_cuenta}.visualstudio.com).
2. Desde la barra de herramientas de la cuenta, haga clic en el icono de engranaje y seleccione **Directiva**:
    
    ![Opción de configuración de directiva seleccionada](media/tfvc-auth2.png) 

3. Revise la configuración de conexión de la aplicación. Cambie esta configuración en función de sus directivas de seguridad:
    
    ![Opción de configuración de directiva seleccionada](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>No veo nada en TFVC

Para configurar el Control de versiones de Team Foundation (TFVC) en el equipo de desarrollo, **debe** crear un área de trabajo, como se describe en la sección [Administrar áreas de trabajo](#managing-workspaces).

En el Explorador de control de código fuente, presione el botón **Administrar áreas de trabajo**. Siga los pasos para asignar el proyecto de equipo a una carpeta de su equipo de desarrollo.

### <a name="i-do-not-see-any--all-of-my-projects"></a>No veo ninguno o todos mis proyectos

Después de la autenticación, debería ver la lista de proyectos. De forma predeterminada solo se muestran los proyectos de TFS. Para ver otros tipos de proyectos, active la casilla "Ver todos los proyectos".

Tenga en cuenta que los proyectos que están en el servidor no aparecerán si no tiene los privilegios adecuados.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Recibo el error "No se puede crear el área de trabajo. Vuelva a intentarlo".

Al intentar [crear una nueva área de trabajo](#creating-a-new-workspace), debe asegurarse de que se cumplen las siguientes condiciones:

- No se deben emplear caracteres no válidos en el nombre del área de trabajo.
- El nombre debe tener menos de 64 caracteres.
- La ruta de acceso local no se puede usar en otras áreas de trabajo.