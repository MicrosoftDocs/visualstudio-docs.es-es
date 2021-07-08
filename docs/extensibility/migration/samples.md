---
title: Ejemplo ImageOptimizer para actualizar extensiones de Visual Studio
description: Siga un ejemplo a fin de aprender a actualizar una extensión de Visual Studio para que funcione con Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602228"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer: actualización de una extensión de Visual Studio paso a paso

[!INCLUDE [preview-note](../includes/preview-note.md)]

En esta guía se mostrarán todos los pasos necesarios para agregar compatibilidad con Visual Studio 2022 mientras se mantiene la compatibilidad con Visual Studio 2019 mediante la extensión Image Optimizer como caso práctico.  
Está pensada para ser una guía exhaustiva con vínculos de confirmación de Git para cada paso, pero aquí puede ver la PR finalizada: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46).

Al final de esta guía también se incluyen [ejemplos adicionales](#other-samples).

## <a name="step-1---modernize-the-project"></a>Paso 1: Modernización del proyecto

Vea [Modernización del proyecto](update-visual-studio-extension.md#modernize-your-vsix-project).

[Confirmación de Git e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

En primer lugar, el proyecto VSIX y la prueba unitaria se escalan a .NET 4.7.2 en la página de propiedades de los proyectos:

   ![Escala de la versión de Framework](media/samples/framework-bump.png)

Image Optimizer hace referencia a algunos paquetes 14.* y 15.* personalizados antiguos; en su lugar, se instalará el [paquete NuGet `Microsoft.VisualStudio.Sdk`](https://www.nuget.org/packages/microsoft.visualstudio.sdk) que consolida todas las referencias necesarias.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

La compilación del proyecto se realiza correctamente y se generan algunas advertencias de subprocesos. Para corregir estas advertencias, se hace clic en `ctrl` y `.`, y se usa IntelliSense para agregar las líneas de cambio de subproceso que faltan.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>Paso 2: Refactorización del código fuente en un proyecto compartido

Vea [Proyectos compartidos](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting).

Para admitir Visual Studio 2022 es necesario agregar un nuevo proyecto compartido que contendrá el código fuente de la extensión que se compartirá entre los proyectos VSIX de Visual Studio 2019 y Visual Studio 2022.

1. Adición de un proyecto nuevo a la solución

   [Confirmación de Git abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Adición del proyecto compartido](media/samples/add-shared-project.png)

1. Agregue una referencia al proyecto compartido al proyecto VSIX.

   [Confirmación de Git e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Adición de una referencia del proyecto compartido" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Cambie los archivos de código fuente (cs, xaml, resx) al nuevo proyecto compartido **excepto** lo siguiente:
    - `source.extension.vsixmanifest`
    - Archivos de metadatos de extensión (iconos, licencias, notas de la versión, etc.)
    - Archivos VSCT
    - Archivos vinculados
    - Herramientas o bibliotecas externas que se deben incluir en VSIX

   [Confirmación de Git f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Movimiento de archivos al proyecto compartido](media/samples/move-to-shared-project.png)

1. Ahora. mueva todos los metadatos, archivos VSCT, archivos vinculados y herramientas o bibliotecas externas a una ubicación compartida y vuelva a agregarlos como elementos vinculados al proyecto VSIX. **No** quite `source.extension.vsixmanifest`.

   [Confirmación de Git 73ba920: movimiento de archivos](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [Confirmación de Git d5e36b2: adición de herramientas o bibliotecas externas](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Para este proyecto, es necesario mover el icono de extensión, el archivo VSCT y las herramientas externas a la nueva carpeta `ImageOptimizer\Resources`. Cópielos en la carpeta compartida y quítelos del proyecto VSIX.
   1. Vuélvalos a agregar como elementos vinculados y, si ya son elementos vinculados, se pueden conservar tal y como están (la licencia, por ejemplo).
   1. Para comprobar que la acción de compilación y otras propiedades están establecidas correctamente en los archivos vinculados agregados, seleccione cada una de ellas y compruebe la ventana de herramientas de propiedades. Para el proyecto, ha sido necesario establecer lo siguiente:
       - Se ha establecido la acción de compilación `icon.png` en `Content` y se ha marcado Incluir en VSIX como `true`
       - Se ha establecido la acción de compilación `ImageOptimizer.vsct` en `VSCTComplile` e Incluir en VSIX en `false`
       - Se han establecido todas las acciones de compilación de los archivos de `Resources\Tools` en `Content` y se marcado Incluir en VSIX como `true`

           ![Adición de archivos vinculados al proyecto VSIX](media/samples/add-linked-files.png)

       - Además, `ImageOptimizer.cs` es una dependencia de `ImageOptimizer.vsct`, por lo que hay que agregarla manualmente al archivo csproj:

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Si la ventana de herramientas de propiedades impide establecer una acción de compilación específica, puede modificar manualmente el archivo csproj como se ha hecho antes y establecer la acción de compilación según sea necesario.

1. Compile el proyecto para validar los cambios y corregir cualquier error o problema. Consulte la sección [Preguntas más frecuentes](update-visual-studio-extension.md#q--a) para ver los problemas comunes.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>Paso 3: Adición de un proyecto VSIX de Visual Studio 2022

Vea [Adición de un destino de Visual Studio 2022](update-visual-studio-extension.md#add-a-visual-studio-2022-target).

1. Agregue un proyecto VSIX nuevo a la solución.
1. Quite cualquier código fuente adicional en el nuevo proyecto, excepto para `source.extension.vsixmanifest.`

   ![Creación de proyecto VSIX](media/samples/visual-studio-2022-vsix-initial.png)

1. Agregue una referencia al proyecto compartido.

   [Confirmación de Git dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Adición de la referencia al proyecto compartido" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Agregue los archivos vinculados del proyecto VSIX de Visual Studio 2019 y compruebe que sus propiedades "Acción de compilación" e "Incluir en VSIX" coinciden. Copie también el archivo `source.extension.vsixmanifest`, que se modificará más adelante para admitir Visual Studio 2022.

   [Confirmación de Git 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![Adición de archivos vinculados al proyecto VSIX](media/samples/visual-studio-2022-add-linked-files.png)

1. Un intento de compilación muestra que falta una referencia a `System.Windows.Forms`. Solo tiene que agregarla al proyecto de Visual Studio 2022 y volver a compilar.

   [Confirmación de Git de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. Actualice las referencias de los paquetes `Microsoft.VisualStudio.SDK` y `Microsoft.VSSDK.BuildTools` a las versiones de Visual Studio 2022.

   [Confirmación de Git d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Estas eran las versiones más recientes disponibles cuando se ha creado esta guía. Se recomienda obtener las versiones más recientes disponibles.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Edite el archivo `source.extension.vsixmanifest` para reflejar la selección de Visual Studio 2022 como destino.

   [Confirmación de Git 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Establezca la etiqueta `<InstallationTarget>` para que refleje Visual Studio 2022 e indique una carga de amd64:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Modifique el requisito previo para incluir solo Visual Studio 2022 y versiones posteriores:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

Ya ha terminado.

Con esto, ahora la compilación genera archivos VSIX de Visual Studio 2019 y Visual Studio 2022.

## <a name="other-samples"></a>Otros ejemplos

- [ProPower Tools](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Permite ver el código sin salir en un explorador web con información de ayuda sobre la clase o el objeto seleccionados.
  - FixMixedTabs
    - Examina los documentos y reemplaza las tabulaciones por espacios o viceversa

## <a name="next-steps"></a>Pasos siguientes

Para preparar la actualización de la extensión, lea esta [guía de inicio a fin](update-visual-studio-extension.md).
