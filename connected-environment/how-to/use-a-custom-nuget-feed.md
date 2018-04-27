---
title: Uso de una fuente NuGet personalizada con un entorno conectado | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Utilice una fuente NuGet para acceder a los paquetes NuGet y utilizarlos en un entorno conectado.
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 71fcf1c3cfb37d783de13514f6a048c3b3711a53
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Uso de una fuente NuGet personalizada en un entorno conectado

Una fuente NuGet proporciona una manera cómoda de incluir orígenes de paquetes en un proyecto. Connected Environment deberá ser capaz de acceder a esta fuente para que las dependencias se instalen correctamente en el contenedor de Docker.

Para configurar una fuente NuGet:
1. Agregue una [referencia del paquete](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) en el archivo `*.csproj` en el nodo `PackageReference`.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Cree un archivo [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) en la carpeta del proyecto.
     * Use la sección `packageSources` para hacer referencia a la ubicación de la fuente NuGet. Importante: La fuente NuGet debe estar accesible públicamente.
     * Use la sección `packageSourceCredentials` para configurar las credenciales de nombre de usuario y contraseña. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Si usa control de código fuente:
    - Haga referencia a `NuGet.Config` en el archivo `.gitignore` para no tener que confirmar accidentalmente las credenciales en el repositorio de origen.
    - Abra el archivo `vsce.yaml` del proyecto, busque la sección `build` e inserte el siguiente fragmento de código para asegurarse de que el archivo `NuGet.Config` se sincronizará con Azure para que se utilice durante el proceso de compilación de la imagen de contenedor. (De forma predeterminada, Connected Environment no sincroniza los archivos que coinciden con las reglas `.gitignore` y `.dockerignore`).

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Pasos siguientes

Una vez completados los pasos anteriores, la próxima vez ejecute `vsce up` (o haga clic en `F5` en VSCode o Visual Studio), Connected Environment sincronizará el archivo `NuGet.Config` con Azure, que después lo utilizará `dotnet restore` para instalar dependencias de paquete en el contenedor.

