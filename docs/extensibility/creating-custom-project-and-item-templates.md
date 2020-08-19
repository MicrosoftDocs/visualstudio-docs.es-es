---
title: Creación de plantillas de proyecto y de elemento personalizadas | Microsoft Docs
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d520c92e84286ab05f13ad140a9e2e5a3454e09
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248571"
---
# <a name="create-custom-project-and-item-templates"></a>Creación de plantillas de proyecto y de elemento personalizadas

El SDK de Visual Studio incluye plantillas de proyecto que crean una plantilla de proyecto personalizada y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y se compilan como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Debe copiar el archivo zip generado en el directorio de plantillas de usuario.

Las plantillas de creación de plantillas le permiten incluir plantillas con extensiones de mayor tamaño. Esto le permite implementar el control de versiones en los archivos de origen y compilar un grupo de proyectos de plantilla en un paquete VSIX.

También puede configurar una plantilla para instalar paquetes NuGet. Para obtener más información, consulte [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Para los escenarios de creación de plantillas básicas, debe usar el asistente para **exportar plantillas**, el cual genera los resultados a un archivo comprimido. Para obtener más información sobre la creación de plantillas básicas, consulte [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> A partir de Visual Studio 2017, ya no se comprobará si hay plantillas de proyecto y de elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un archivo MSI, debe generar los archivos de manifiesto de plantilla manualmente. Para obtener más información, consulte [Actualización de plantillas de proyecto y elemento para Visual Studio 2017 personalizadas](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema de manifiesto de plantilla se documenta en [Referencia de esquema de manifiesto de plantillas de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Creación de una plantilla de proyecto

1. Cree un proyecto de plantilla de proyecto. Puede encontrar la plantilla de proyecto en el cuadro de diálogo **Nuevo proyecto** buscando "plantilla de proyecto" y seleccionando la versión C# o Visual Basic.

     La plantilla genera un archivo de clase, un icono, un archivo *.vstemplate*, un archivo de proyecto editable denominado *ProjectTemplate.vbproj* o *ProjectTemplate.csproj*y algunos archivos generados normalmente por otros tipos de proyecto, como un archivo *resources.resx*, un archivo *AssemblyInfo* y un archivo *.settings*. Cada archivo de código contiene sustituciones de parámetros comunes donde corresponda.

![selección de proyecto de plantilla de proyecto](media/project-template-selection.png)

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto. No quite el archivo de proyecto editable, el archivo *AssemblyInfo* o el archivo de *.vstemplate*.

3. Actualice el archivo *.vstemplate* para reflejar las adiciones y eliminaciones. El elemento [Project](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otros contenidos orientados al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo *.zip* que contiene la plantilla. No está implementado y no está disponible en la instancia experimental.

## <a name="create-an-item-template"></a>Creación de una plantilla de elemento

1. Cree un proyecto de plantilla de elemento.

     La plantilla genera un archivo de clase, un icono, un archivo *.vstemplate* y un archivo *AssemblyInfo*. El archivo de clase contiene algunas sustituciones de parámetros comunes.

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto.

3. Actualice el archivo *.vstemplate* para reflejar las adiciones y eliminaciones. El elemento [Project](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otros contenidos orientados al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo comprimido que contiene la plantilla. No está implementado y no está disponible en la instancia experimental.

## <a name="deployment"></a>Implementación

### <a name="to-deploy-the-project-or-item-template"></a>Para implementar la plantilla de proyecto o de elemento

1. Crear un proyecto de VSIX. Para obtener más información, consulte [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).

2. Establezca el proyecto VSIX como proyecto de inicio. En el **Explorador de soluciones**, seleccione el nodo del proyecto VSIX, seleccione y mantenga presionado (o haga clic con el botón derecho) y seleccione **Establecer como proyecto de inicio**.

3. Establezca el proyecto de plantilla de proyecto como un recurso del proyecto VSIX. Abra el archivo *.vsixmanifest*. Cambie a la pestaña **Recursos** y haga clic en **Nuevo**.

    1. Establezca el campo **Tipo** en **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.

    2. Para el origen, seleccione la opción **Un proyecto en la solución actual** y posteriormente seleccione el proyecto que contiene la plantilla.

4. Compile la solución y presione **F5**. Aparece la instancia experimental.

5. En el caso de un proyecto de plantilla de proyecto, debería ver la plantilla de proyecto en el cuadro de diálogo **Nuevo proyecto** (**Archivo** > **Nuevo** > **Proyecto**), en el nodo Visual C# o Visual Basic. Para un proyecto de plantilla de elemento, debería aparecer la plantilla de elemento en el cuadro de diálogo **Agregar nuevo elemento**. Para ver el cuadro de diálogo **Agregar nuevo elemento** desde el **Explorador de soluciones**, seleccione el nodo del proyecto y seleccione **Agregar** > **Nuevo elemento**).

## <a name="see-also"></a>Vea también

- [Referencia de plantillas de Visual Studio](../ide/creating-project-and-item-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
