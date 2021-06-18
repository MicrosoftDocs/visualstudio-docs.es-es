---
title: Destino Visual Studio 2019 al crear una extensión en Visual Studio versión preliminar de 2022
description: Obtenga información sobre cómo hacer que la extensión Visual Studio funcione con Visual Studio 2019 si crea el proyecto con Visual Studio versión preliminar de 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308647"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Destino de una versión anterior al crear una extensión en Visual Studio versión preliminar de 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Al crear un nuevo proyecto VSIX mediante Visual Studio versión preliminar de 2022, el proyecto se crea a partir de una plantilla que tiene como destino Visual Studio 2022. Si desea establecer como destino Visual Studio 2019 o una versión anterior, debe modificar el proyecto creado.

Considere la [posibilidad de](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) usar proyectos compartidos Visual Studio 2019 y Visual Studio 2022 al compartir la mayoría o todo el código de la extensión.

Siga estos pasos en el proyecto VSIX que debe tener como destino Visual Studio 2019:

1. Edite `source.extension.vsixmanifest` el archivo para quitar el elemento y el intervalo de `ProductArchitecture` versiones:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Actualice también el requisito previo:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Revise el archivo para ver si hay otras actualizaciones que puedan ser necesarias.

1. Cambie las versiones de los paquetes de VS SDK a los que hace referencia en el archivo de proyecto:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
