---
title: Creación de plantillas de proyecto y elementos personalizadas ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739459"
---
# <a name="create-custom-project-and-item-templates"></a>Crear plantillas de proyectos y elementos personalizadas

El SDK de Visual Studio incluye plantillas de proyecto que crean una plantilla de proyecto personalizada y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y se compilan como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Debe copiar el archivo zip generado en el directorio de plantilla de usuario.

Las plantillas de creación de plantillas le permiten incluir plantillas en extensiones más grandes. Esto le permite implementar el control de versiones en los archivos de origen y crear un grupo de proyectos de plantilla en un paquete VSIX.

También puede configurar una plantilla para instalar paquetes NuGet. Para obtener más información, vea [Paquetes NuGet en plantillas](/nuget/visual-studio-extensibility/visual-studio-templates)de Visual Studio .

Para escenarios básicos de creación de plantillas, debe usar el Asistente **para exportar plantilla,** que se genera en un archivo comprimido. Para obtener más información sobre la creación de plantillas básicas, vea [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> A partir de Visual Studio 2017, ya no se realizará el análisis de plantillas de proyecto y elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un MSI, debe generar los archivos de manifiesto de plantilla a mano. Para obtener más información, vea Actualizar plantillas de [proyecto y elemento personalizadas para Visual Studio 2017.](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) El esquema de manifiesto de plantilla se documenta en la referencia de esquema de manifiesto de plantilla de [Visual Studio.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="create-a-project-template"></a>Creación de una plantilla de proyecto

1. Cree un proyecto de plantilla de proyecto. Puede encontrar la plantilla de proyecto en el cuadro de diálogo **Nuevo proyecto,** buscando "plantilla de proyecto" y seleccionando la versión de Visual Basic o de C.

     La plantilla genera un archivo de clase, un icono, un archivo *.vstemplate,* un archivo de proyecto editable denominado *ProjectTemplate.vbproj* o *ProjectTemplate.csproj*y algunos archivos que normalmente generan otros tipos de proyecto, como un archivo *resources.resx,* un archivo *AssemblyInfo* y un archivo *.settings.* Cada archivo de código contiene sustituciones de parámetros comunes cuando sea apropiado.

![selección de proyectos de plantilla de proyecto](media/project-template-selection.png)

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto. No quite el archivo de proyecto editable, el archivo *AssemblyInfo* o el archivo *.vstemplate.*

3. Actualice el archivo *.vstemplate* para reflejar las adiciones y eliminaciones. El [elemento Project](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otro contenido orientado al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo *.zip* que contiene la plantilla. No se implementa y no está disponible en la instancia experimental.

## <a name="create-an-item-template"></a>Creación de una plantilla de elemento

1. Cree un proyecto de plantilla de elemento.

     La plantilla genera un archivo de clase, un icono, un archivo *.vstemplate* y un archivo *AssemblyInfo.* El archivo de clase contiene algunas sustituciones de parámetros comunes.

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto.

3. Actualice el archivo *.vstemplate* para reflejar las adiciones y eliminaciones. El [elemento Project](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otro contenido orientado al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo comprimido que contiene la plantilla. No se implementa y no está disponible en la instancia experimental.

## <a name="deployment"></a>Implementación

### <a name="to-deploy-the-project-or-item-template"></a>Para implementar la plantilla de proyecto o elemento

1. Crear un proyecto de VSIX. Para obtener más información, consulte Plantilla de [proyecto VSIX](../extensibility/vsix-project-template.md).

2. Establezca el proyecto VSIX como el proyecto de inicio. En el **Explorador**de soluciones , seleccione el nodo del proyecto VSIX, haga clic con el botón derecho y seleccione **Establecer como proyecto**de inicio .

3. Establezca el proyecto de plantilla de proyecto como un recurso del proyecto VSIX. Abra el archivo *.vsixmanifest.* Vaya a la pestaña **Activos** y haga clic en **Nuevo**.

    1. Establezca el campo **Type** en **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.

    2. Para el origen, seleccione la opción Un proyecto en la **solución actual** y, a continuación, seleccione el proyecto que contiene la plantilla.

4. Compile la solución y presione **F5**. Aparece la instancia experimental.

5. Para un proyecto de plantilla de proyecto, debería ver la plantilla de proyecto que aparece en el cuadro de diálogo **Nuevo proyecto** (**Archivo** > **nuevo** > **proyecto**), en el nodo Visual C o Visual Basic. Para un proyecto de plantilla de elemento, debería ver la plantilla de elemento en el cuadro de diálogo **Agregar nuevo elemento.** Para ver el cuadro de diálogo **Agregar nuevo elemento,** en el **Explorador**de soluciones , seleccione el nodo del proyecto y haga clic en **Agregar** > **nuevo elemento**).

## <a name="see-also"></a>Vea también

- [Referencia de plantilla de Visual Studio](../ide/creating-project-and-item-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
