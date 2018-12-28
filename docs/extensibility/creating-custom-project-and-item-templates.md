---
title: Creación de plantillas de elementos y proyectos personalizadas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2a8e95d8ea8e169eb75a3ecba886a96808b87a1
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802740"
---
# <a name="create-custom-project-and-item-templates"></a>Crear plantillas de proyecto y elemento personalizadas

El SDK de Visual Studio incluye plantillas de proyecto que creación una plantilla de proyecto personalizado y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y compilación como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Debe copiar el archivo zip generado en el directorio de plantillas de usuario.

Las plantillas de creación de plantilla permiten incluir plantillas de extensiones de mayor tamaño. Esto le permite implementar el control de versiones en los archivos de origen y crear un grupo de proyectos de plantilla en un paquete VSIX.

También puede configurar una plantilla para instalar paquetes de NuGet. Para obtener más información, consulte [paquetes de NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Para escenarios de creación de la plantilla básica, debe usar el **Exportar plantilla** asistente, que muestra los resultados en un archivo comprimido. Para obtener más información sobre la creación de una plantilla básica, vea [crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> A partir de Visual Studio 2017, análisis de proyecto personalizado y las plantillas de elemento ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión con un archivo MSI, debe generar manualmente los archivos de manifiesto de plantilla. Para obtener más información, consulte [actualizar plantillas de proyecto y elemento personalizadas para Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema del manifiesto de plantilla está documentado en [referencia de esquema del manifiesto de plantilla de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Crear una plantilla de proyecto

1.  Cree un proyecto de plantilla de proyecto. Puede encontrar la plantilla de proyecto en el **nuevo proyecto** cuadro de diálogo, en Visual Basic o Visual C# *extensibilidad* carpeta.

     La plantilla genera un archivo de clase, un icono, un *.vstemplate* de archivos, un archivo de proyecto editable denominado *ProjectTemplate.vbproj* o *ProjectTemplate.csproj*y algunos los archivos que normalmente se generan por otros tipos de proyecto, este tipo una *resources.resx* archivo, un *AssemblyInfo* archivo y un *.settings* archivo. Cada archivo de código contiene las sustituciones de parámetros comunes donde corresponda.

2.  Agregar y quitar elementos del proyecto según sea necesario para el proyecto. No quite el archivo de proyecto puede editar el *AssemblyInfo* archivo, o el *.vstemplate* archivo.

3.  Actualización de la *.vstemplate* archivo para reflejar las adiciones y eliminaciones. El [proyecto](../extensibility/project-element-visual-studio-templates.md) elemento debe contener un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) para cada archivo que se incluirán en la plantilla.

4.  Modificar los archivos de código y otros contenidos de cara al usuario y agregue las sustituciones de parámetros apropiado.

5.  Modificar el contenido generado según sea necesario.

6.  Compile el proyecto.

     Visual Studio crea un *.zip* archivo que contiene la plantilla. No se ha implementado y no está disponible en la instancia experimental.

## <a name="create-an-item-template"></a>Crear una plantilla de elemento

1.  Cree un proyecto de plantilla de elemento.

     La plantilla genera un archivo de clase, un icono, un *.vstemplate* archivo y un *AssemblyInfo* archivo. El archivo de clase contiene algunas sustituciones de parámetros comunes.

2.  Agregar y quitar elementos del proyecto según sea necesario para el proyecto.

3.  Actualización de la *.vstemplate* archivo para reflejar las adiciones y eliminaciones. El [proyecto](../extensibility/project-element-visual-studio-templates.md) elemento debe contener un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) para cada archivo que se incluirán en la plantilla.

4.  Modificar los archivos de código y otros contenidos de cara al usuario y agregue las sustituciones de parámetros apropiado.

5.  Modificar el contenido generado según sea necesario.

6.  Compile el proyecto.

     Visual Studio crea un archivo comprimido que contiene la plantilla. No se ha implementado y no está disponible en la instancia experimental.

## <a name="deployment"></a>Implementación

### <a name="to-deploy-the-project-or-item-template"></a>Para implementar la plantilla de proyecto o elemento

1.  Crear un proyecto de VSIX. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).

2.  Establezca el proyecto VSIX como proyecto de inicio. En el **el Explorador de soluciones**, seleccione el nodo del proyecto VSIX, contextual y seleccione **establecer como proyecto de inicio**.

3.  Establezca el proyecto de plantilla de proyecto como un recurso del proyecto VSIX. Abra el *.vsixmanifest* archivo. Vaya a la **activos** ficha y haga clic en **New**.

    1.  Establecer el **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.

    2.  Para el origen, seleccione el **un proyecto de la solución actual** opción y, a continuación, seleccione el proyecto que contiene la plantilla.

4.  Compile la solución y presione **F5**. Aparece la instancia experimental.

5.  Para un proyecto de plantilla de proyecto, verá la plantilla de proyecto aparecen en la **nuevo proyecto** diálogo (**archivo** > **New**  >  **Proyecto**), en el nodo de Visual Basic o Visual C#. Para un proyecto de plantilla de elemento, debería ver la plantilla de elemento aparece en el **Agregar nuevo elemento** cuadro de diálogo. Para ver el **Agregar nuevo elemento** cuadro de diálogo, desde el **el Explorador de soluciones**, seleccione el nodo del proyecto y haga clic en **agregar** > **nuevo elemento**).

## <a name="see-also"></a>Vea también

[Referencia de plantillas de Visual Studio](../ide/creating-project-and-item-templates.md)
[paquetes de NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
