---
title: Proyectos de Instalador de Visual Studio y .NET Core 3,1
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c35e6a12262083d09575b51f6c9f918ba30a27b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88714402"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Extensión de proyectos del Instalador de Visual Studio y .NET Core 3.1

Empaquetar aplicaciones como MSI se suele lograr mediante la extensión de proyectos de Instalador de Visual Studio.

Puede descargar la extensión aquí: [proyectos de instalador de Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>Actualización para .NET Core
.NET Core tiene dos modelos diferentes para la publicación.

- Implementaciones dependientes del marco de trabajo

- Las aplicaciones independientes incluyen el tiempo de ejecución.

Para obtener más información sobre estas estrategias de implementación, consulte [información general sobre la publicación de aplicaciones .net Core](https://docs.microsoft.com/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>Cambios de flujo de trabajo para .NET Core 3,1

1. Seleccione **publicar elementos** en lugar de **resultados principales** para obtener la salida correcta para los proyectos de .net Core 3,1.  Para abrir este cuadro de diálogo, seleccione **Agregar**  >  **resultados del proyecto...** en el menú contextual del proyecto.

    ![El grupo de salida publicar elementos en el cuadro de diálogo Agregar grupo de resultados del proyecto](../deployment/media/installer-projects-net-core-publish-items-output.png "Seleccionar publicar elementos")

2. Para crear un instalador independiente, establezca la propiedad **PublishProfilePath** en el nodo **publicar elementos** del proyecto de instalación mediante la ruta de acceso relativa de un perfil de publicación con las propiedades correctas establecidas.

    ![Establecer el perfil de publicación en el elemento de salida del proyecto publicar elementos](../deployment/media/installer-projects-net-core-publish-profile.png "Establecer Perfil de publicación")

### <a name="prerequisites-for-net-core-31"></a>Requisitos previos para .NET Core 3,1

Si desea que el instalador pueda instalar el tiempo de ejecución necesario para una aplicación .NET Core 3,1 dependiente del marco, puede hacerlo con los [requisitos previos](../deployment/application-deployment-prerequisites.md).  En el cuadro de diálogo de propiedades del proyecto de instalador, abra el cuadro de diálogo **requisitos previos...** y verá las siguientes entradas:

![Elementos de .NET Core en el cuadro de diálogo requisitos previos](../deployment/media/installer-projects-net-core-prerequisites.png "Requisitos previos de .NET Core")

Se debe seleccionar la opción **tiempo de ejecución de .net Core...** para las aplicaciones de consola, se debe seleccionar **.net Desktop Runtime..** . para las aplicaciones de WPF/WinForms.

>[!NOTE]
>Estos elementos están presentes a partir de la versión de Visual Studio 2019 Update 7.

## <a name="see-also"></a>Consulte también

- [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md)
- [Requisitos previos de la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)
