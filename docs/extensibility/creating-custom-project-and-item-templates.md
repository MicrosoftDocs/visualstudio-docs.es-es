---
title: "Creación de proyectos personalizados y plantillas de elemento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: be53e0aa5179a38f9c2079513661607b45767a11
ms.lasthandoff: 02/22/2017

---
# <a name="creating-custom-project-and-item-templates"></a>Creación de proyecto personalizadas y plantillas de elementos
El SDK de Visual Studio incluye plantillas de proyecto para creación una plantilla de proyecto personalizada y una plantilla de elemento personalizado. Estas plantillas incluyen algunas sustituciones de parámetros comunes y compilación como archivos zip. No se implementan automáticamente y no están disponibles en la instancia experimental. Debe copiar el archivo zip archivos a la ubicación  
  
 Las plantillas de creación de plantilla permiten incluir plantillas de extensiones de mayor. Esto le permite implementar el control de versiones en los archivos de origen y crear un grupo de proyectos de plantilla en un paquete VSIX.  
  
 Para escenarios de creación de la plantilla básica, debe utilizar el **Exportar plantilla** asistente, que muestra los resultados en un archivo comprimido. Para obtener más información acerca de la creación de una plantilla básica, vea [crear plantillas de proyectos y elemento](../ide/creating-project-and-item-templates.md).  
  
 A partir de Visual Studio de 2017, análisis de proyecto personalizadas y plantillas de elementos ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio de 2017 para actualizar las extensiones VSIX. Si implementa la extensión de un archivo MSI, debe generar manualmente los archivos de manifiesto de la plantilla. Para obtener más información, consulte [Actualizar proyecto de personalizados y plantillas de elementos de Visual Studio de 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema de manifiesto de la plantilla se documenta en [Visual Studio Template manifiesto Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Crear una plantilla de proyecto  
  
1.  Cree un proyecto de plantilla de proyecto. Puede encontrar la plantilla de proyecto en el **nuevo proyecto** cuadro de diálogo, en Visual Basic o Visual C# **extensibilidad** carpeta.  
  
     La plantilla genera un archivo de clase, un icono, un archivo .vstemplate, un archivo de proyecto editable denominado ProjectTemplate.vbproj o ProjectTemplate.csproj y algunos archivos que generan otros tipos de proyecto, este archivo resources.resx, el archivo AssemblyInfo y un archivo .settings. Cada archivo de código contiene sustituciones de parámetros comunes donde corresponda.  
  
2.  Agregar y quitar elementos del proyecto según sea necesario para su proyecto. No quite el archivo .vstemplate, el archivo AssemblyInfo o el archivo de proyecto puede modificar.  
  
3.  Actualice el archivo .vstemplate para reflejar las adiciones y eliminaciones. El [proyecto](../extensibility/project-element-visual-studio-templates.md) elemento debe contener un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) para cada archivo que se incluirán en la plantilla.  
  
4.  Modificar los archivos de código y otro contenido de cara al usuario y agregar sustituciones de parámetros adecuados.  
  
5.  Modificar el contenido generado según sea necesario.  
  
6.  Compile el proyecto.  
  
     Visual Studio crea un archivo .zip que contiene la plantilla. No se ha implementado y no está disponible en la instancia experimental.  
  
## <a name="creating-an-item-template"></a>Crear una plantilla de elemento  
  
1.  Crear un proyecto de plantilla de elemento.  
  
     La plantilla genera un archivo de clase, un icono, un archivo .vstemplate y el archivo AssemblyInfo. El archivo de clase contiene algunas sustituciones de parámetros comunes.  
  
2.  Agregar y quitar elementos del proyecto según sea necesario para su proyecto.  
  
3.  Actualice el archivo .vstemplate para reflejar las adiciones y eliminaciones. El [proyecto](../extensibility/project-element-visual-studio-templates.md) elemento debe contener un [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) (elemento) para cada archivo que se incluirán en la plantilla.  
  
4.  Modificar los archivos de código y otro contenido de cara al usuario y agregar sustituciones de parámetros adecuados.  
  
5.  Modificar el contenido generado según sea necesario.  
  
6.  Compile el proyecto.  
  
     Visual Studio crea un archivo comprimido que contiene la plantilla. No se ha implementado y no está disponible en la instancia experimental.  
  
## <a name="deployment"></a>Implementación  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Para implementar la plantilla de proyecto o elemento  
  
1.  Crear un proyecto de VSIX. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
2.  Establezca el proyecto VSIX como proyecto de inicio. En el **el Explorador de soluciones**, seleccione el nodo del proyecto VSIX, con el botón secundario y seleccione **establecer como proyecto de inicio**.  
  
3.  Establecer el proyecto de plantilla de proyecto como un recurso del proyecto VSIX. Abra el archivo .vsixmanifest. Vaya a la **activos** y haga clic en **nuevo**.  
  
    1.  Establecer el **tipo** campo **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  En origen, seleccione la **un proyecto de la solución actual** opción y, a continuación, seleccione el proyecto que contiene la plantilla.  
  
4.  Compile la solución y presione F5. Aparece la instancia experimental.  
  
5.  Para un proyecto de plantilla de proyecto, verá la plantilla de proyecto que se enumeran en la **nuevo proyecto** diálogo (**archivo / nuevo / proyecto**), en el nodo Visual Basic o Visual C#. Para un proyecto de plantilla de elemento, verá la plantilla de elemento aparece en el cuadro de diálogo Agregar nuevo elemento (en el **el Explorador de soluciones**, seleccione el nodo del proyecto y haga clic en **Agregar / nuevo elemento**).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de plantillas de Visual Studio](../ide/visual-studio-template-reference.md)
