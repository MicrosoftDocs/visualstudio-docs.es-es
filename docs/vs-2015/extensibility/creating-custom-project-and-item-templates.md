---
title: Creación de plantillas de proyectos y de elementos personalizadas
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197398"
---
# <a name="creating-custom-project-and-item-templates"></a>Creación de plantillas de proyectos y de elementos personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El SDK de Visual Studio incluye plantillas de proyecto que crean una plantilla de proyecto personalizada y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y se compilan como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Copie el archivo zip en la ubicación que

Las plantillas de creación de plantillas le permiten incluir plantillas con extensiones de mayor tamaño. La inclusión de plantillas en extensiones permite implementar el control de versiones en los archivos de código fuente y compilar un grupo de proyectos de plantilla en un paquete VSIX.

Para los escenarios de creación de plantillas básicas, debe usar el asistente para **exportar plantillas**, el cual genera los resultados a un archivo comprimido. Para obtener más información sobre la creación de plantillas básicas, vea [crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md).

A partir de Visual Studio 2017, ya no se realiza el análisis de las plantillas de proyecto y de elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar la instalación de Preview 2 para actualizar las extensiones VSIX. Si implementa la extensión mediante un archivo MSI, debe generar los archivos de manifiesto de plantilla manualmente. Para obtener más información, consulte [actualización del plantillas de proyecto y elemento para Visual Studio personalizado 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). El esquema de manifiesto de plantilla se documenta en la [referencia de esquema de manifiesto de plantilla de Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Crear una plantilla de proyecto

1. Cree un proyecto de plantilla de proyecto. Puede encontrar la plantilla de proyecto en el cuadro de diálogo **nuevo proyecto** , en la carpeta **extensibilidad** de Visual Basic o Visual C#.

     La plantilla genera un archivo de clase, un icono, un archivo .vstemplate, un archivo de proyecto editable denominado ProjectTemplate.vbproj o ProjectTemplate.csprojy algunos archivos generados normalmente por otros tipos de proyecto, como un archivo resources.resx, un archivo AssemblyInfo y un archivo .settings. Cada archivo de código contiene sustituciones de parámetros comunes donde corresponda.

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto. No quite el archivo de proyecto editable, el archivo AssemblyInfo o el archivo de .vstemplate.

3. Actualice el archivo .vstemplate para reflejar las adiciones y eliminaciones. El elemento [Project](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otros contenidos orientados al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo .zip que contiene la plantilla. No está implementado y no está disponible en la instancia experimental.

## <a name="create-an-item-template"></a>Crear una plantilla de elemento

1. Cree un proyecto de plantilla de elemento.

     La plantilla genera un archivo de clase, un icono, un archivo .vstemplate y un archivo AssemblyInfo. El archivo de clase contiene algunas sustituciones de parámetros comunes.

2. Agregue y quite elementos del proyecto según sea necesario para el proyecto.

3. Actualice el archivo .vstemplate para reflejar las adiciones y eliminaciones. El elemento [Project](../extensibility/project-element-visual-studio-templates.md) debe contener un elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada archivo que se va a incluir en la plantilla.

4. Modifique los archivos de código y otros contenidos orientados al usuario y agregue las sustituciones de parámetros adecuadas.

5. Modifique el contenido generado según sea necesario.

6. Compile el proyecto.

     Visual Studio crea un archivo comprimido que contiene la plantilla. No está implementado y no está disponible en la instancia experimental.

## <a name="deploy-the-project-or-item-template"></a>Implementar la plantilla de proyecto o de elemento

1. Crear un proyecto de VSIX. Para obtener más información, vea [plantilla de Proyecto VSIX](../extensibility/vsix-project-template.md).

2. Establezca el proyecto VSIX como proyecto de inicio. En el **Explorador de soluciones**, seleccione el nodo del proyecto VSIX, haga clic con el botón derecho y, después, seleccione **Establecer como proyecto de inicio**.

3. Establezca el proyecto de plantilla de proyecto como un recurso del proyecto VSIX. Abra el archivo .vsixmanifest. Vaya a la pestaña **activos** y haga clic en **nuevo**.

    1. Establezca el campo **Tipo** en **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.

    2. Para el origen, seleccione la opción **Un proyecto en la solución actual** y posteriormente seleccione el proyecto que contiene la plantilla.

4. Compile la solución y presione F5. Aparece la instancia experimental.

5. En el caso de un proyecto de plantilla de proyecto, debería ver la plantilla de proyecto en el cuadro de diálogo **nuevo proyecto** (**archivo/nuevo/proyecto**), en el nodo Visual C# o Visual Basic. Para un proyecto de plantilla de elemento, debería ver la plantilla de elemento en el cuadro de diálogo Agregar nuevo elemento (en el **Explorador de soluciones**, seleccione el nodo de proyecto y haga clic en **Agregar/nuevo elemento**).

## <a name="see-also"></a>Consulte también

- [Referencia de plantillas de Visual Studio](../ide/visual-studio-template-reference.md)