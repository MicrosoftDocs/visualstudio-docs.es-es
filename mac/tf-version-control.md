---
title: Control de versiones de Team Foundation (TFVC)
description: Conectarse a Team Foundation Server o Azure DevOps Services con Control de versiones de Team Foundation (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 9cb6a466d764c85012477fb2d849c05920908f02
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295935"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conectarse a Control de versiones de Team Foundation

> [!NOTE]
> La compatibilidad con Control de versiones de Team Foundation está actualmente en versión preliminar y algunas funciones todavía no funcionan por completo. Nos encantaría recibir comentarios suyos sobre cualquier problema en la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/spaces/41/index.html). Hay más cambios pendientes.

Azure Repos proporciona dos modelos de control de versiones: Git, que es un control de versiones distribuido, y Control de versiones de Team Foundation (TFVC), que es un control de versiones centralizado. En este artículo, se proporciona información general y un punto de partida para usar TFVC con Visual Studio para Mac.

## <a name="requirements"></a>Requisitos

* Visual Studio Community, Professional o Enterprise para Mac versión 7.5 o posterior.
* Azure DevOps Services o Team Foundation Server 2013 y versiones posteriores.
* Un proyecto en Azure DevOps Services o Team Foundation Server, configurado para que use Control de versiones de Team Foundation.

## <a name="installation"></a>Instalación

En Visual Studio para Mac, elija **Visual Studio > Extensiones** en el menú. En la pestaña **Galería**, seleccione **Control de versiones > Control de versiones de Team Foundation para TFS y VSTS** y haga clic en **Instalar**:

![Administrador de extensiones](media/tfvc-install.png)

Siga las indicaciones para instalar la extensión. Una vez instalada, reinicie el IDE.

## <a name="updating-the-extension"></a>Actualizar la extensión

La extensión de TFVC se actualiza periódicamente. Para acceder a las actualizaciones, elija **Visual Studio > Extensiones** desde el menú y seleccione la pestaña **Actualizaciones**. Seleccione la extensión en la lista y haga clic en el botón **Actualización**:

![Administrador de extensiones mostrando la actualización](media/tfvc-update.png)

Haga clic en **Instalar** en el cuadro de diálogo siguiente para desinstalar el paquete antiguo e instalar el nuevo.

Para obtener información sobre cuáles son las novedades en cada versión, vea las [Notas de la versión](/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Usar el complemento

Una vez que la extensión está instalada, seleccione el elemento de menú **Control de versiones > TFS/Azure DevOps > Open from Remote Repository** (Abrir desde el repositorio remoto).

![Elemento de menú para abrir la extensión](media/tfvc-source-control-explorer-devops.png)

Elija entre VSTS o Team Foundation Server para comenzar y haga clic en **Continuar**:

![Conectar con un servidor](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Autenticación de Azure Repos

Cuando seleccione un proyecto que se hospeda en Azure Repos, se le pedirá que escriba los detalles de la cuenta de Microsoft:

![Conectarse con Azure Repos](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Autenticación de TFS

Para conectarse a TFS, escriba los detalles del servidor y las credenciales de cuenta. Escriba un dominio para usar la autenticación NTLM. En caso contrario, déjelo en blanco para usar la autenticación básica. Seleccione **Agregar servidor**:

![Inicio de sesión en un servidor TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Seleccionar un proyecto

Una vez que se ha autenticado correctamente, puede ver una lista de repositorios que están asociados con la cuenta en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Muestra del cuadro de diálogo Abrir desde el control de código fuente con proyectos](media/tfvc-vsts-projects.png)

Este cuadro de diálogo se organiza con los siguientes nodos:

- Organización o colección de Azure DevOps: se muestran todas las organizaciones conectadas a la cuenta de Microsoft con la que ha iniciado sesión.
- Proyectos: en cada organización o colección, puede tener una serie de proyectos. Un proyecto es donde se hospedan el código fuente, los elementos de trabajo y las compilaciones automatizadas.

En este momento, puede buscar y filtrar por el nombre de un proyecto u organización.

### <a name="adding-a-new-server"></a>Agregar un nuevo servidor

Para agregar un nuevo servidor a la lista, haga clic en el botón **Agregar host** situado en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Botón de agregar resaltado para agregar un nuevo servidor a la lista](media/tfvc-add-new-server.png)

Seleccione el proveedor de la lista y escriba sus credenciales:

![Cuadro de diálogo que muestra la opción de proveedor de control de código fuente](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Crear una nueva área de trabajo

Para empezar a trabajar con un proyecto, debe tener un _área de trabajo_. Si aún no tiene un área de trabajo, puede crear una desde el cuadro combinado **Área de trabajo** en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Opción del cuadro combinado para crear una nueva área de trabajo](media/tfvc-create-new-workspace.png)

Establezca el nombre y la ruta de acceso local para la nueva área de trabajo y seleccione **Crear área de trabajo**:

![Escribir un nombre y una ruta de acceso local para la nueva área de trabajo](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Usar el Explorador de código fuente

Una vez que ha creado un área de trabajo y asigna el proyecto, puede empezar a trabajar con el _Explorador de código fuente_.

Para abrir el Explorador de código fuente, seleccione el elemento de menú **Control de versiones > TFS/Azure DevOps > Explorador de control de código fuente**.

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

Si aún no lo ha hecho, cree un área de trabajo, como se describe en la sección [Crear un área de trabajo](#creating-a-new-workspace), y observará que el Explorador de código fuente está vacío:

![Explorador de código fuente vacío](media/tfvc-setup-empty-sce.png)

Para configurar el proyecto remoto con un área de trabajo local, siga estos pasos:

1. Seleccione el **Servidor** del cuadro combinado.
1. Tenga en cuenta que no hay "ningún área de trabajo" y que la ruta de acceso local está "Sin asignar". Seleccione el vínculo **Sin asignar** para mostrar el cuadro de diálogo **Crear nueva área de trabajo**.
1. Proporcione un nombre para el área de trabajo y, después, haga clic en **Add Working Folder** (Agregar carpeta de trabajo) para asignar el proyecto a una carpeta local en el equipo:

    ![Cuadro de diálogo para crear un área de trabajo que muestra las opciones predeterminadas](media/tfvc-workspace1.png)

1. Seleccione la carpeta "$" para asignar todos los proyectos del servidor a la misma área de trabajo, o bien seleccione un proyecto individual y haga clic en **Aceptar**:

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

Para poder usar la autenticación básica, es necesario habilitar **credenciales de autenticación alternativas** en Azure DevOps Services. Para ello, siga estos pasos:

1. Inicie sesión en su organización de Azure DevOps como propietario (https://dev.azure.com/{organization}/{project}).

2. En la barra de herramientas de la organización, haga clic en el icono de engranaje y seleccione **Directiva**:

    ![Opción de configuración de directiva seleccionada](media/tfvc-auth2.png)

3. Revise la configuración de conexión de la aplicación. Cambie esta configuración en función de sus directivas de seguridad:

    ![Opción de configuración de directiva seleccionada](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>No veo nada en TFVC

Para configurar el Control de versiones de Team Foundation (TFVC) en el equipo de desarrollo, **debe** crear un área de trabajo, como se describe en la sección [Administrar áreas de trabajo](#managing-workspaces).

En el Explorador de control de código fuente, presione el botón **Administrar áreas de trabajo**. Siga los pasos para asignar el proyecto a una carpeta de su equipo de desarrollo.

### <a name="i-do-not-see-any--all-of-my-projects"></a>No veo ninguno o todos mis proyectos

Después de la autenticación, debería ver la lista de proyectos. De forma predeterminada, solo se muestran los proyectos de TFS. Para ver otros tipos de proyectos, active la casilla "Ver todos los proyectos".

Tenga en cuenta que los proyectos que están en el servidor no aparecerán si no tiene los privilegios adecuados.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Recibo el error "No se puede crear el área de trabajo. Vuelva a intentarlo".

Al intentar [crear una nueva área de trabajo](#creating-a-new-workspace), debe asegurarse de que se cumplen las siguientes condiciones:

- No se deben emplear caracteres no válidos en el nombre del área de trabajo.
- El nombre debe tener menos de 64 caracteres.
- La ruta de acceso local no se puede usar en otras áreas de trabajo.

## <a name="see-also"></a>Vea también

- [Develop and share your code in TFVC using Visual Studio (on Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs) (Desarrollar y compartir el código en TFVC con Visual Studio (en Windows))