---
title: Creación de plantillas de elementos y proyectos personalizadas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3229eb90dad59269d81bfd34b7eb5fa15bdab6d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794613"
---
# <a name="creating-custom-project-and-item-templates"></a>Creación de plantillas de proyectos y de elementos personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El SDK de Visual Studio incluye plantillas de proyecto que creación una plantilla de proyecto personalizado y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y compilación como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Debe copiar el archivo zip archivos a la ubicación  
  
 Las plantillas de creación de plantilla permiten incluir plantillas de extensiones de mayor tamaño. Esto le permite implementar el control de versiones en los archivos de origen y crear un grupo de proyectos de plantilla en un paquete VSIX.  
  
 Para escenarios de creación de la plantilla básica, debe usar el **Exportar plantilla** asistente, que muestra los resultados en un archivo comprimido. Para obtener más información sobre la creación de una plantilla básica, vea [crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md).  
  
 A partir de Visual Studio "15" Preview 4, análisis de proyecto personalizado y las plantillas de elemento ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar la instalación de Preview 2 para actualizar las extensiones VSIX. Si implementa la extensión con un archivo MSI, debe generar manualmente los archivos de manifiesto de plantilla. Para obtener más información, consulte [actualización del proyecto personalizado y las plantillas de elemento para Visual Studio "15"](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema del manifiesto de plantilla está documentado en [referencia de esquema de manifiesto de Visual Studio plantilla](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Creación de una plantilla de proyecto  
  
1.  Cree un proyecto de plantilla de proyecto. Puede encontrar la plantilla de proyecto en el **nuevo proyecto** cuadro de diálogo, en Visual Basic o Visual C# **extensibilidad** carpeta.  
  
     La plantilla genera un archivo de clase, un icono, un archivo .vstemplate, un archivo de proyecto editable denominado ProjectTemplate.vbproj o ProjectTemplate.csproj y algunos archivos que normalmente se generan por otros tipos de proyecto, este archivo de resources.resx, un AssemblyInfo. archivo y un archivo .settings. Cada archivo de código contiene las sustituciones de parámetros comunes donde corresponda.  
  
2.  Agregar y quitar elementos del proyecto según sea necesario para el proyecto. No quite el archivo .vstemplate, el archivo AssemblyInfo o el archivo de proyecto editable.  
  
3.  Actualice el archivo .vstemplate para reflejar las adiciones y eliminaciones. El [proyecto](../extensibility/project-element-visual-studio-templates.md) elemento debe contener un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) para cada archivo que se incluirán en la plantilla.  
  
4.  Modificar los archivos de código y otros contenidos de cara al usuario y agregue las sustituciones de parámetros apropiado.  
  
5.  Modificar el contenido generado según sea necesario.  
  
6.  Compile el proyecto.  
  
     Visual Studio crea un archivo .zip que contiene la plantilla. No se ha implementado y no está disponible en la instancia experimental.  
  
## <a name="creating-an-item-template"></a>Creación de una plantilla de elemento  
  
1.  Cree un proyecto de plantilla de elemento.  
  
     La plantilla genera un archivo de clase, un icono, un archivo .vstemplate y un archivo AssemblyInfo. El archivo de clase contiene algunas sustituciones de parámetros comunes.  
  
2.  Agregar y quitar elementos del proyecto según sea necesario para el proyecto.  
  
3.  Actualice el archivo .vstemplate para reflejar las adiciones y eliminaciones. El [proyecto](../extensibility/project-element-visual-studio-templates.md) elemento debe contener un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) para cada archivo que se incluirán en la plantilla.  
  
4.  Modificar los archivos de código y otros contenidos de cara al usuario y agregue las sustituciones de parámetros apropiado.  
  
5.  Modificar el contenido generado según sea necesario.  
  
6.  Compile el proyecto.  
  
     Visual Studio crea un archivo comprimido que contiene la plantilla. No se ha implementado y no está disponible en la instancia experimental.  
  
## <a name="deployment"></a>Implementación  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Para implementar la plantilla de proyecto o elemento  
  
1.  Crear un proyecto de VSIX. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
2.  Establezca el proyecto VSIX como proyecto de inicio. En el **el Explorador de soluciones**, seleccione el nodo del proyecto VSIX, contextual y seleccione **establecer como proyecto de inicio**.  
  
3.  Establezca el proyecto de plantilla de proyecto como un recurso del proyecto VSIX. Abra el archivo .vsixmanifest. Vaya a la **activos** ficha y haga clic en **New**.  
  
    1.  Establecer el **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Para el origen, seleccione el **un proyecto de la solución actual** opción y, a continuación, seleccione el proyecto que contiene la plantilla.  
  
4.  Compile la solución y presione F5. Aparece la instancia experimental.  
  
5.  Para un proyecto de plantilla de proyecto, verá la plantilla de proyecto aparecen en la **nuevo proyecto** diálogo (**archivo / nuevo / proyecto**), en el nodo de Visual Basic o Visual C#. Para un proyecto de plantilla de elemento, debería ver la plantilla de elemento aparece en el cuadro de diálogo Agregar nuevo elemento (en el **el Explorador de soluciones**, seleccione el nodo del proyecto y haga clic en **Agregar / nuevo elemento**).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de plantillas de Visual Studio](../ide/visual-studio-template-reference.md)

