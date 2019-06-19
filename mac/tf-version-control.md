---
title: Control de versiones de Team Foundation (TFVC)
description: Conectarse desde Visual Studio para Mac a Team Foundation Server/Azure DevOps Services con Control de versiones de Team Foundation (TFVC).
author: conceptdev
ms.author: crdun
ms.date: 04/28/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: c21658b6381405c05e5b0fedbb72e33f8ed72a83
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745553"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conectarse a Control de versiones de Team Foundation

> [!NOTE]
> Para una mejor experiencia de control de versiones en macOS, se recomienda usar Git en lugar del Control de versiones de Team Foundation (TFVC). Git es compatible con Visual Studio para Mac y es la opción predeterminada para los repositorios hospedados en Team Foundation Server (TFS)/Azure DevOps. Para más información sobre cómo usar Git con TFS/Azure DevOps, vea el artículo [Configurar un repositorio Git](/visualstudio/mac/set-up-git-repository).

Azure Repos ofrece dos modelos de control de versiones: [Git](/azure/devops/repos/git/?view=azure-devops), un sistema de control de versiones distribuido, y el [Control de versiones de Team Foundation](/azure/devops/repos/tfvc/index?view=azure-devops) (TFVC), un sistema de control de versiones centralizado.

Visual Studio para Mac proporciona compatibilidad total con repositorios Git, pero requiere algunas soluciones alternativas para trabajar con TFVC. Si usa TFVC para el control de versiones hoy en día, estas son algunas soluciones que puede usar para acceder al código fuente hospedado en TFVC:

* [Uso de Visual Studio Code y de la extensión de Azure Repos para una UI gráfica](#use-visual-studio-code-and-the-azure-repos-extension)
* [Conexión al repositorio con el cliente de la línea de comandos de Team Explorer Everywhere (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Conexión a TFVC mediante la extensión del Control de versiones de Team Foundation (incompatible) en Visual Studio para Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

El resto de la información de este artículo lo guiará en las opciones indicadas anteriormente.

## <a name="requirements"></a>Requisitos

* Visual Studio Community, Professional o Enterprise para Mac, versión 7.8 y posterior.
* Azure DevOps Services, Team Foundation Server 2013 y versiones posteriores o Azure DevOps Server 2018 y versiones posteriores.
* Un proyecto en Azure DevOps Services o Team Foundation Server/Azure DevOps Server, configurado para que use el Control de versiones de Team Foundation.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Uso de Visual Studio Code y de la extensión de Azure Repos

Si le gusta trabajar con una interfaz gráfica para administrar los archivos en el control de versiones, la extensión de Azure Repos para Visual Studio Code proporciona una solución compatible de Microsoft. Para comenzar, descargue [Visual Studio Code](https://code.visualstudio.com) y, a continuación, obtenga información sobre cómo [configurar la extensión de Azure Repos](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Conexión con el cliente de la línea de comandos de Team Explorer Everywhere

Si se siente cómodo con el uso del Terminal de macOS, entonces el cliente de la línea de comandos de Team Explorer Everywhere (TEE-CLC) ofrece un método compatible de conexión al origen en TFVC.

Puede completar los pasos siguientes para configurar la conexión con TFVC y confirmar los cambios.

### <a name="setting-up-the-tee-clc"></a>Configuración de la TEE-CLC

Hay dos formas de instalar la TEE-CLC.

* Utilice Homebrew para instalar el cliente.
* También puede descargar el cliente e instalarlo manualmente.

La solución más sencilla es **usar HomeBrew**, que es un administrador de paquetes para macOS. Para instalar con este método:

1. Inicie la aplicación Terminal de macOS.
1. Instale Homebrew mediante el Terminal y las instrucciones que aparecen en la [página principal de Homebrew](https://brew.sh/).
1. Una vez instalado Homebrew, ejecute el siguiente comando desde el Terminal: `brew install tee-clc`.

Para **instalar la TEE-CLC manualmente**:

1. [Descargue la última versión de la TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) de la página de versiones del repositorio de GitHub para Team Explorer Everywhere (por ejemplo, tee-clc-14.134.0.zip en el momento en que se redactó este artículo).
1. Extraiga el contenido del archivo ZIP en una carpeta del disco.
1. Abra la aplicación Terminal de macOS y use el comando `cd` para cambiar a la carpeta utilizada en el paso anterior.
1. Desde dentro de la carpeta, ejecute el comando `./tf` para comprobar que se puede ejecutar el cliente de la línea de comandos; puede que se le pida que instale Java u otras dependencias.

Una vez instalada la TEE-CLC, puede ejecutar el comando `tf eula` para ver y aceptar el contrato de licencia del cliente.

Por último, para autenticarse en su entorno de TFS/Azure DevOps, deberá crear un token de acceso personal en el servidor. Obtenga más información sobre la [autenticación con tokens de acceso personal](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/pats?view=azure-devops). Al crear un token de acceso personal para usarlo con TFVC, asegúrese de proporcionar acceso total al configurar el token.

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Uso de la TEE-CLC para conectarse a su repositorio

Para conectarse a su código fuente, primero debe crear un área de trabajo mediante el comando `tf workspace`. Por ejemplo, los siguientes comandos establecen conexión con una organización de Azure DevOps Services denominada "MyOrganization": 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

La configuración del entorno `TF_AUTO_SAVE_CREDENTIALS` se usa para guardar las credenciales, para que no se le pida que las escriba varias veces. Cuando se le pida un nombre de usuario, utilice el token de acceso personal que creó en la sección anterior y una contraseña en blanco.

Para crear una asignación de los archivos de origen a una carpeta local, se usa el comando `tf workfold`. En el ejemplo siguiente, se asociará una carpeta llamada "WebApp.Services" del proyecto de TFVC "MyRepository" y se configurará para que se copie en la carpeta local ~/Projects/ (por ejemplo, una carpeta "Proyectos" en la carpeta principal del usuario actual).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Por último, use el siguiente comando para obtener los archivos de origen del servidor y cópielos localmente:

```bash
tf get
```

### <a name="committing-changes-using-the-tee-clc"></a>Confirmación de los cambios mediante la TEE-CLC

Una vez realizados los cambios de los archivos en Visual Studio para Mac, puede cambiar al Terminal para registrar las modificaciones. El comando `tf add` se usa para agregar archivos a la lista de los cambios pendientes que se van a registrar y el comando `tf checkin` realiza el registro real en el servidor. El comando `checkin` incluye parámetros para agregar un comentario o asociar un elemento de trabajo relacionado. En el siguiente fragmento de código, se agregan al registro todos los archivos en una carpeta `WebApp.Services` de forma recursiva. A continuación, el código se registra con un comentario y se asocia con un elemento de trabajo con el identificador "42".

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Para obtener más información sobre los comandos mencionados aquí u otros, puede usar el siguiente comando desde el Terminal:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Conexión a TFVC con la extensión del Control de versiones de Team Foundation

> [!NOTE]
> Para una mejor experiencia de control de versiones en macOS, se recomienda usar Git en lugar del Control de versiones de Team Foundation (TFVC). Git es compatible con Visual Studio para Mac y es la opción predeterminada para los repositorios hospedados en Team Foundation Server (TFS)/Azure DevOps. Para más información sobre cómo usar Git con TFS/Azure DevOps, vea el artículo [Configurar un repositorio Git](/visualstudio/mac/set-up-git-repository).

En la galería de extensiones de Visual Studio para Mac, hay una extensión del Control de versiones de Team Foundation que ofrece compatibilidad limitada para establecer conexión con TFVC. La extensión no es compatible y presenta varios errores conocidos, por lo que su experiencia puede variar al utilizarla.

Para instalar la extensión, inicie Visual Studio para Mac y elija el menú **Visual Studio > Extensiones**. En la pestaña **Galería**, seleccione **Control de versiones > Control de versiones de Team Foundation para TFS y Azure DevOps** y haga clic en **Instalar...** :

![Administrador de extensiones](media/tfvc-install.png)

Siga las indicaciones para instalar la extensión. Una vez instalada, reinicie el IDE.

### <a name="updating-the-extension"></a>Actualizar la extensión

La extensión de TFVC se actualiza periódicamente. Para acceder a las actualizaciones, elija **Visual Studio > Extensiones** desde el menú y seleccione la pestaña **Actualizaciones**. Seleccione la extensión en la lista y haga clic en el botón **Actualización**:

Haga clic en **Instalar** en el cuadro de diálogo siguiente para desinstalar el paquete antiguo e instalar el nuevo.

### <a name="using-the-extension"></a>Utilizar la extensión

Una vez que la extensión está instalada, seleccione el elemento de menú **Control de versiones > TFS/Azure DevOps > Open from Remote Repository...** (Abrir desde el repositorio remoto...).

![Elemento de menú para abrir la extensión](media/tfvc-source-control-explorer-devops.png)

Elija entre VSTS o Team Foundation Server para comenzar y haga clic en **Continuar**:

![Conectar con un servidor](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Autenticación de Azure Repos

Cuando seleccione un proyecto que se hospeda en Azure Repos, se le pedirá que escriba los detalles de la cuenta de Microsoft:

![Conectarse con Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>Autenticación de TFS

Para conectarse a TFS, escriba los detalles del servidor y las credenciales de cuenta. Escriba un dominio para usar la autenticación NTLM. En caso contrario, déjelo en blanco para usar la autenticación básica. Seleccione **Agregar servidor**:

![Inicio de sesión en un servidor TFS](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Seleccionar un proyecto

Una vez que se ha autenticado correctamente, puede ver una lista de repositorios que están asociados con la cuenta en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Muestra del cuadro de diálogo Abrir desde el control de código fuente con proyectos](media/tfvc-vsts-projects.png)

Este cuadro de diálogo se organiza con los siguientes nodos:

- Organización o colección de Azure DevOps: se muestran todas las organizaciones conectadas a la cuenta de Microsoft con la que ha iniciado sesión.
- Proyectos: en cada organización o colección, puede tener una serie de proyectos. Un proyecto es donde se hospedan el código fuente, los elementos de trabajo y las compilaciones automatizadas.

En este momento, puede buscar y filtrar por el nombre de un proyecto u organización.

#### <a name="adding-a-new-server"></a>Agregar un nuevo servidor

Para agregar un nuevo servidor a la lista, haga clic en el botón **Agregar host** situado en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Botón de agregar resaltado para agregar un nuevo servidor a la lista](media/tfvc-add-new-server.png)

Seleccione el proveedor de la lista y escriba sus credenciales:

![Cuadro de diálogo que muestra la opción de proveedor de control de código fuente](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Crear una nueva área de trabajo

Para empezar a trabajar con un proyecto, debe tener un _área de trabajo_. Si aún no tiene un área de trabajo, puede crear una desde el cuadro combinado **Área de trabajo** en el cuadro de diálogo **Abrir desde el control de código fuente**:

![Opción del cuadro combinado para crear una nueva área de trabajo](media/tfvc-create-new-workspace.png)

Establezca el nombre y la ruta de acceso local para la nueva área de trabajo y seleccione **Crear área de trabajo**:

![Escribir un nombre y una ruta de acceso local para la nueva área de trabajo](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Usar el Explorador de código fuente

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

### <a name="managing-workspaces"></a>Administrar áreas de trabajo

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

## <a name="troubleshooting-and-known-issues"></a>Solución de problemas y problemas conocidos

#### <a name="problems-using-basic-authentication"></a>Problemas con la autenticación básica

Las siguientes opciones pueden usarse para autenticar con un servidor:

- OAuth
- Básico
- Ntlm

Para poder usar la autenticación básica, es necesario habilitar **credenciales de autenticación alternativas** en Azure DevOps Services. Para ello, siga estos pasos:

1. Inicie sesión en su organización de Azure DevOps como propietario (https:\//dev.azure.com/{organization}/{project}).

2. En la barra de herramientas de la organización, haga clic en el icono de engranaje y seleccione **Directiva**:

    ![Opción de configuración de directiva seleccionada](media/tfvc-auth2.png)

3. Revise la configuración de conexión de la aplicación. Cambie esta configuración en función de sus directivas de seguridad:

    ![Opción de configuración de directiva seleccionada](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>No veo nada en TFVC

Para configurar el Control de versiones de Team Foundation (TFVC) en el equipo de desarrollo, **debe** crear un área de trabajo, como se describe en la sección [Administrar áreas de trabajo](#managing-workspaces).

En el Explorador de control de código fuente, presione el botón **Administrar áreas de trabajo**. Siga los pasos para asignar el proyecto a una carpeta de su equipo de desarrollo.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>No veo ninguno o todos mis proyectos

Después de la autenticación, debería ver la lista de proyectos. De forma predeterminada, solo se muestran los proyectos de TFS. Para ver otros tipos de proyectos, active la casilla "Ver todos los proyectos".

Tenga en cuenta que los proyectos que están en el servidor no aparecerán si no tiene los privilegios adecuados.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Recibo el error "No se puede crear el área de trabajo. Vuelva a intentarlo".

Al intentar [crear una nueva área de trabajo](#creating-a-new-workspace), debe asegurarse de que se cumplen las siguientes condiciones:

- No se deben emplear caracteres no válidos en el nombre del área de trabajo.
- El nombre debe tener menos de 64 caracteres.
- La ruta de acceso local no se puede usar en otras áreas de trabajo.

### <a name="see-also"></a>Vea también

- [Develop and share your code in TFVC using Visual Studio (on Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs) (Desarrollar y compartir el código en TFVC con Visual Studio (en Windows))