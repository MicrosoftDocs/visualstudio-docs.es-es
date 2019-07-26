---
title: Crear plantillas de proyecto y de elemento personalizadas | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff4d3566dcfb4b40f1008eed09371e42459c3a5
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493118"
---
# <a name="create-custom-project-and-item-templates"></a>Crear plantillas de proyecto y de elemento personalizadas

El SDK de Visual Studio incluye plantillas de proyecto que crean una plantilla de proyecto personalizada y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y compilar como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Debe copiar el archivo zip generado en el directorio de plantillas de usuario.

Las plantillas de creación de plantillas permiten incluir plantillas en extensiones de mayor tamaño. Esto le permite implementar el control de versiones en los archivos de código fuente y compilar un grupo de proyectos de plantilla en un paquete VSIX.

También puede configurar una plantilla para instalar paquetes de NuGet. Para obtener más información, vea [paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

En el caso de escenarios de creación de plantillas básicas, debe usar el Asistente para **exportar plantillas** , que genera un archivo comprimido. Para obtener más información sobre la creación de plantillas básicas, vea [crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> A partir de Visual Studio 2017, ya no se realizará el análisis de las plantillas de proyecto y de elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un archivo MSI, debe generar los archivos de manifiesto de plantilla manualmente. Para obtener más información, vea [Actualizar plantillas de proyecto y de elemento personalizadas para Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema de manifiesto de plantilla se documenta en la [referencia de esquema de manifiesto de plantilla de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Crear una plantilla de proyecto

1. Cree un proyecto de plantilla de proyecto. Para encontrar la plantilla de proyecto en el cuadro de diálogo **nuevo proyecto** , busque "plantilla de proyecto" y seleccione la C# versión de o Visual Basic.

     La plantilla genera un archivo de clase, un icono, un archivo *. vstemplate* , un archivo de proyecto editable llamado *ProjectTemplate. vbproj* o *ProjectTemplate. csproj*, y algunos archivos generados normalmente por otros tipos de proyecto, como el archivo resources. resx, un archivo *AssemblyInfo* y un archivo *. Settings* . Cada archivo de código contiene sustituciones de parámetros comunes cuando sea necesario.

![selección de proyecto de plantilla de proyecto](media/project-template-selection.png)

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto. No quite el archivo de proyecto editable, el archivo *AssemblyInfo* o el archivo *. vstemplate* .

3. Actualice el archivo *. vstemplate* para reflejar las adiciones y eliminaciones. El elemento de [proyecto](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otros contenidos orientados al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo *. zip* que contiene la plantilla. No está implementado y no está disponible en la instancia experimental.

## <a name="create-an-item-template"></a>Creación de una plantilla de elemento

1. Cree un proyecto de plantilla de elemento.

     La plantilla genera un archivo de clase, un icono, un archivo *. vstemplate* y un archivo *AssemblyInfo* . El archivo de clase contiene algunas sustituciones de parámetros comunes.

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto.

3. Actualice el archivo *. vstemplate* para reflejar las adiciones y eliminaciones. El elemento de [proyecto](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otros contenidos orientados al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo comprimido que contiene la plantilla. No está implementado y no está disponible en la instancia experimental.

## <a name="deployment"></a>Implementación

### <a name="to-deploy-the-project-or-item-template"></a>Para implementar la plantilla de proyecto o de elemento

1. Crear un proyecto de VSIX. Para obtener más información, vea [plantilla de Proyecto VSIX](../extensibility/vsix-project-template.md).

2. Establezca el Proyecto VSIX como proyecto de inicio. En el **Explorador de soluciones**, seleccione el nodo del Proyecto VSIX, haga clic con el botón derecho y seleccione **establecer como proyecto de inicio**.

3. Establezca el proyecto de plantilla de proyecto como un recurso del Proyecto VSIX. Abra el archivo *. vsixmanifest* . Vaya a la pestaña **activos** y haga clic en **nuevo**.

    1. Establezca el campo **tipo** en **Microsoft. VisualStudio. ProjectTemplate** o **Microsoft. VisualStudio. ItemTemplate**.

    2. En origen, seleccione la opción **un proyecto en la solución actual** y, después, seleccione el proyecto que contiene la plantilla.

4. Compile la solución y presione **F5**. Aparece la instancia experimental.

5. En el caso de un proyecto de plantilla de proyecto, debería ver la plantilla de proyecto en el cuadro de diálogo **nuevo proyecto** (**archivo** > **nuevo** > **proyecto**), en el nodo visual C# o Visual Basic. Para un proyecto de plantilla de elemento, debería ver la plantilla de elemento en el cuadro de diálogo **Agregar nuevo elemento** . Para ver el cuadro de diálogo **Agregar nuevo elemento** , en el **Explorador de soluciones**, seleccione el nodo de proyecto y haga clic en **Agregar** > **nuevo elemento**.

## <a name="see-also"></a>Vea también

- [Referencia de plantillas de Visual Studio](../ide/creating-project-and-item-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
