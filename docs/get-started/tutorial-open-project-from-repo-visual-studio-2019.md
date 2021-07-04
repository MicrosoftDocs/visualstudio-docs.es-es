---
title: 'Tutorial: Apertura de un proyecto desde un repositorio en Visual Studio 2019'
description: Obtenga información sobre cómo abrir un proyecto en un repositorio de Git o de Azure DevOps mediante Visual Studio 2019.
ms.custom: vs-acquisition, get-started
ms.date: 03/18/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2019
ms.openlocfilehash: b6f7cd57a1753ca5926ac73a9bb4c8c918d1bd10
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389948"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: Abrir un proyecto desde un repositorio

En este tutorial, usará Visual Studio para conectarse por primera vez a un repositorio y luego abrir un proyecto desde él.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

## <a name="open-a-project-from-a-github-repo"></a>Apertura de un proyecto desde un repositorio de GitHub

La forma de abrir un proyecto desde un repositorio de GitHub mediante Visual Studio 2019 depende de la versión que tiene. En concreto, si tiene instalada la [**versión 16.8**](/visualstudio/releases/2019/release-notes/) o una posterior, tiene a su disposición una nueva [experiencia de Git en Visual Studio](../ide/git-with-visual-studio.md) completamente integrada.

De todas formas, independientemente de la versión que tenga instalada, siempre puede abrir un proyecto desde un repositorio de GitHub con Visual Studio.

#### <a name="168-and-later"></a>[16.8 y versiones posteriores](#tab/vs168later)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonación de un repositorio de GitHub y apertura de un proyecto

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Clonar un repositorio**.

   ![Captura de pantalla del cuadro de diálogo "Clonar un repositorio" en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/clone-repository.png)

1. Especifique o escriba la ubicación del repositorio y, luego, seleccione **Clonar**.

   ![Captura de pantalla del cuadro de diálogo "Clonar un repositorio", donde se debe escribir la dirección URL de un repositorio de Git en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Es posible que se le solicite su información de inicio de sesión en el cuadro de diálogo **Información de usuario de GIT**. Puede agregar su información o editar la información predeterminada que se proporciona.

   ![Captura de pantalla del cuadro de diálogo "Información de usuario de GIT", donde se debe escribir o editar la información de la cuenta en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/git-user-information-dialog.png)

    Seleccione **Guardar** para agregar la información al archivo global .gitconfig, o bien, seleccione **Cancelar** para agregarla más adelante.

    > [!TIP]
    > Para obtener más información sobre cómo iniciar sesión en Visual Studio, consulte la página [Iniciar sesión en Visual Studio](../ide/signing-in-to-visual-studio.md). Asimismo, para obtener información específica sobre cómo usar su cuenta de GitHub para iniciar sesión, consulte la página [Trabajar con cuentas de GitHub en Visual Studio](../ide/work-with-github-accounts.md).

    Después de esto, Visual Studio carga automáticamente la solución y la abre desde el repositorio.

   ![Captura de pantalla de un proyecto de Git que está abierto en el Explorador de soluciones en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/git-solution-explorer.png )

1. Si el repositorio contiene varias soluciones, las verá en Explorador de soluciones. Para ver la lista de soluciones, seleccione el botón **Cambiar vistas** del Explorador de soluciones.

   ![Captura de pantalla de un proyecto de Git que está abierto en el Explorador de soluciones con el botón "Cambiar vistas" resaltado en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   El Explorador de soluciones le permite abrir la carpeta raíz en **Vista de carpetas** o seleccionar un archivo de solución para abrirlo.

   ![Captura de pantalla del archivo .sln en Git abierto en el Explorador de soluciones después de seleccionar el botón "Cambiar vistas" en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Para alternar la vista, seleccione de nuevo el botón **Cambiar vistas**.

    > [!TIP]
    > También puede usar el menú **Git** en el IDE de Visual Studio para clonar un repositorio y abrir un proyecto.
    >
    > ![Captura de pantalla del menú "Git" en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Apertura de un proyecto de forma local desde un repositorio de GitHub clonado anteriormente

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Abrir un proyecto o una solución**.

    Visual Studio abre una instancia del Explorador de archivos, donde puede buscar la solución o el proyecto y seleccionarlos para abrirlos.

   ![Captura de pantalla de la ventana "Abrir un proyecto o una solución" en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Si ha abierto el proyecto o la solución recientemente, selecciónelos en la sección **Abrir recientes** para abrirlos de nuevo rápidamente.

    > [!TIP]
    > También puede usar el menú **Git** en el IDE de Visual Studio para abrir archivos y carpetas locales desde un repositorio que haya clonado previamente.
    >
    > ![Captura de pantalla del menú "Git" en Visual Studio 2019, versión 16.8 y posteriores, con la opción "Local Repositories" (Repositorios locales) expandida](../ide/media/vs-2019/git-menu-local-repositories.png)

    Ya puede empezar a codificar.

#### <a name="167-and-earlier"></a>[16.7 y versiones anteriores](#tab/vs167earlier)

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Clonación de un repositorio de GitHub y apertura de un proyecto

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Clonar o extraer código del repositorio**.

   ![Captura de pantalla de la ventana "Crear un proyecto" en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Especifique o escriba la ubicación del repositorio y, luego, seleccione **Clonar**.

   ![Captura de pantalla de la ventana "Clonar o extraer código del repositorio" en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio abre el proyecto desde el repositorio.

1. Si hay disponible un archivo de solución, aparecerá en el menú emergente "Soluciones y carpetas". Selecciónelo y Visual Studio abrirá la solución.

   ![Captura de pantalla de la lista desplegable del Explorador de soluciones en Visual Studio 2019, versión 16.7 y anteriores](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si no hay un archivo de solución (específicamente, un archivo .sln) en el repositorio, el menú desplegable indica "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

    Ya puede empezar a codificar.

---

> [!NOTE]
> Para obtener información específica de Visual Studio 2017, vea la página [Apertura de un proyecto desde un repositorio en Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md).

## <a name="connect-to-an-azure-devops-server"></a>Conexión a un servidor de Azure DevOps

Lo que ve cuando se conecta a un servidor de Azure DevOps mediante Visual Studio 2019 depende de la versión que tiene. En concreto, si tiene instalada la [**versión 16.8**](/visualstudio/releases/2019/release-notes/) o una versión posterior, hemos cambiado la interfaz de usuario para ofrecer una nueva [experiencia de Git en Visual Studio](../ide/git-with-visual-studio.md) completamente integrada.

De todas formas, independientemente de la versión que tenga instalada, siempre puede conectarse a un servidor de Azure DevOps con Visual Studio.

#### <a name="168-and-later"></a>[16.8 y versiones posteriores](#tab/vs168later)

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Clonar un repositorio**.

   ![Captura de pantalla del cuadro de diálogo "Clonar un repositorio" en Visual Studio 2019, versión 16.8 y posteriores, para Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. En la sección **Examinar un repositorio**, seleccione **Azure DevOps**.

    ![Captura de pantalla de la sección "Examinar un repositorio" del cuadro de diálogo "Conectar a un proyecto" en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Si se abre una ventana de inicio de sesión, inicie sesión en su cuenta.

1. En el cuadro de diálogo **Conectar a un proyecto**, seleccione el repositorio al que quiere conectarse y, después, haga clic en **Clonar**.

      ![Captura de pantalla del cuadro de diálogo "Conectar a un proyecto" que se genera en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Si no ve una lista previamente rellenada de repositorios a los que conectarse, seleccione **Agregar una instancia de Azure DevOps Server** para escribir la dirección URL de un servidor. También es posible que vea el mensaje "No se han encontrado servidores", que incluye vínculos para agregar una instancia existente de Azure DevOps Server o crear una cuenta de Azure DevOps.

   Después, Visual Studio abre el **Explorador de soluciones** y muestra las carpetas y los archivos.

1. Seleccione la pestaña **Team Explorer** para ver las acciones de Azure DevOps.

      ![Captura de pantalla del cuadro de diálogo "Team Explorer" que se genera en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="167-and-earlier"></a>[16.7 y versiones anteriores](#tab/vs167earlier)

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Clonar o extraer código del repositorio**.

   ![Captura de pantalla de la ventana "Crear un proyecto" en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. En la sección **Examinar un repositorio**, seleccione **Azure DevOps**.

   ![Captura de pantalla de la sección "Examinar un repositorio" con la opción "Azure DevOps" en la ventana "Clonar o extraer código del repositorio" en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Si se abre una ventana de inicio de sesión, inicie sesión en su cuenta.

1. En el cuadro de diálogo **Conectar a un proyecto**, seleccione el repositorio al que quiere conectarse y, después, haga clic en **Clonar**.

      ![Captura de pantalla del cuadro de diálogo "Conectar a un proyecto" que se genera en Visual Studio 2019, versión 16.7 y anteriores](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > El contenido del cuadro de lista depende de los repositorios de Azure DevOps a los que tiene acceso.

   Visual Studio abre **Team Explorer** y aparece una notificación cuando se completa la clonación.

     ![Captura de pantalla de la ventana "Team Explorer" que se muestra en Visual Studio 2019, versión 16.7 y anteriores, cuando se completa la clonación](./media/vs-2019/clone-complete-azure-devops.png)

1. Para ver los archivos y carpetas, seleccione el vínculo **Mostrar vista de carpeta**.

     ![Captura de pantalla de la sección "Soluciones" de la ventana "Team Explorer" en Visual Studio 2019, versión 16.7 y anteriores, una vez completada la clonación](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio abre el **Explorador de soluciones**.

1. Elija el vínculo **Soluciones y carpetas** para buscar un archivo de solución (específicamente, un archivo .sln).

      ![Captura de pantalla de la notificación de "Soluciones y carpetas" desde Team Explorer en Visual Studio 2019, versión 16.7 y anteriores](./media/open-proj-repo-solutions-folders.png)

   Si no hay ningún archivo de solución en el repositorio, aparecerá el mensaje "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

---

## <a name="next-steps"></a>Pasos siguientes

Si está listo para codificar con Visual Studio, explore en profundidad cualquiera de los siguientes tutoriales específicos del lenguaje:

- [Tutoriales de Visual Studio | **C#**](./csharp/index.yml)
- [Tutoriales de Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Tutoriales de Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Tutoriales de Visual Studio | **Python**](../python/index.yml)
- [Tutoriales de Visual Studio | **JavaScript**, **TypeScript** y **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Consulte también

- [Apertura de un proyecto desde un repositorio en Visual Studio 2017](tutorial-open-project-from-repo-visual-studio-2017.md)
- [Nueva experiencia de Git en Visual Studio 2019](../ide/git-with-visual-studio.md)
- [Comparación de Git y Team Explorer en paralelo](../ide/git-team-explorer-feature-comparison.md)
- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services: Introducción a Azure Repos y Visual Studio)
- [Microsoft Learn: Introducción a Azure DevOps](/learn/modules/get-started-with-devops/)
