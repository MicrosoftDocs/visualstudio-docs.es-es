---
title: Actualizar y migrar soluciones de Office | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 920fc096072cb4304e76ca8171d52d3e40caeb3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="upgrading-and-migrating-office-solutions"></a>Actualizar y migrar soluciones de Office
  Si tiene un proyecto de Microsoft Office que se creó en una versión anterior de Visual Studio, deberá actualizarlo para usarlo en las versiones actuales de Visual Studio. Para ello, ábralo en una versión de Visual Studio que incluya las herramientas de desarrollo de Microsoft Office. Para obtener más información acerca de las versiones de Visual Studio que incluyen las herramientas de desarrollo de Microsoft Office, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
> [!NOTE]  
>  Visual Studio no puede actualizar proyectos de plantilla de formulario de InfoPath creados con versiones anteriores de Visual Studio. Estos tipos de proyectos no se admiten en la versión actual de Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Cambios en los proyectos actualizados  
 Cuando se actualiza un proyecto de Microsoft Office, Visual Studio modifica el proyecto para tener como destino los elementos siguientes:  
  
-   Visual Studio 2010 Tools para Office Runtime. Para obtener más información, consulta [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Las referencias de ensamblado actual.  
  
-   Una versión de .NET Framework que es compatible con el tipo de proyecto (solo al actualizar a Visual Studio 2013).  
  
-   Una versión de Microsoft Office que es compatible con el tipo de proyecto (solo al actualizar a Visual Studio 2013).  
  
## <a name="assembly-references"></a>Referencias de ensamblado  
 Visual Studio actualiza las siguientes referencias de ensamblado en el proyecto:  
  
-   Ensamblados de interoperabilidad primarios de Microsoft Office (PIA).  
  
-   Ensamblados en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obtener más información sobre estos ensamblados, vea [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Versiones nuevas o actualizadas de ensamblados dependientes.  
  
## <a name="targeted-net-framework"></a>.NET Framework de destino  
 Al actualizar un proyecto en Visual Studio 2013, Visual Studio modifica el proyecto para que su destino sea [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La versión de .NET Framework que será el destino del proyecto depende de la versión de Office que está instalada en el equipo. Si está instalado [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , Visual Studio modifica el proyecto para que el destino sea [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. De lo contrario, Visual Studio modifica el proyecto para que el destino sea [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Es posible que deba realizar algunos pasos adicionales para ejecutar una solución con destino nuevo en equipos de desarrollo y de usuario final. Asimismo, si el proyecto usa determinadas características, quizá no se compile. Para obtener más información, consulte [migrar soluciones de Office para .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Si elige como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior en un proyecto de Office, puede usar algunas características que no están disponibles cuando el destino es .NET Framework 3.5. Para obtener más información, consulta [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Aplicación de destino de Office  
 Cuando se actualiza un proyecto de Office en Visual Studio 2013, Visual Studio modifica ese proyecto para destinarlo a una versión de Microsoft Office que sea compatible con el tipo de proyecto, por ejemplo, un proyecto de personalización de nivel de documento o un proyecto de complemento de VSTO.  
  
 Los proyectos de Office en Visual Studio 2013 pueden tener como destino aplicaciones de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Visual Studio modifica el proyecto para tener como destino la versión más reciente de Office que tenga instalada. Si no se instala ninguna de estas versiones de Office, Visual Studio no actualiza el proyecto.  
  
> [!NOTE]  
>  Si actualiza un proyecto de complemento de VSTO para destinarlo a [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o versiones posteriores, asegúrese de que el `ThisAddIn_Startup` controlador de eventos del complemento de VSTO no contenga código con acceso a un documento en la aplicación. Para obtener más información, consulta [Obtener acceso a un documento cuando se inicia la aplicación de Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Para las personalizaciones de nivel de documento, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] convierte los documentos de un proyecto que tienen un formato binario (como los documentos con extensión .xls o .doc&gt;) al formato Office Open XML. Para obtener más información sobre Open XML, vea [Introducción a las nuevas extensiones de nombre de archivo y formatos Open XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Las etiquetas inteligentes dejaron de usarse en Excel 2010 y Word 2010. Por lo tanto, si la solución usa etiquetas inteligentes, quítelas antes de probar y depurar en Visual Studio 2013 o Visual Studio 2015.  
  
## <a name="upgrading-microsoft-office-2003-projects"></a>Actualizar proyectos de Microsoft Office 2003  
 Hay algunas consideraciones adicionales que se deben tener en cuenta a la hora de actualizar las personalizaciones de nivel de documento y los complementos de VSTO cuyo destino es Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Proyectos de nivel del documento  
 Si el documento del proyecto contiene controles de formularios Windows Forms, también se debe tener instalado Visual Studio 2005 Tools para Office Second Edition Runtime antes de actualizar el proyecto. Si esta versión del runtime no está instalada en el equipo de desarrollo antes de actualizar el proyecto, el proyecto actualizado podría contener errores en tiempo de compilación o ejecución. Cuando termine de actualizar el proyecto, puede desinstalar Visual Studio 2005 Tools para Office Second Edition Runtime en el equipo de desarrollo si no lo usa ninguna otra solución de Office. Esta versión del runtime está disponible como paquete redistribuible en el Centro de descarga de Microsoft en [Microsoft Visual Studio 2005 Tools para Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Proyectos de complementos de VSTO  
 Si el archivo de solución del proyecto original incluía un proyecto de instalación o InstallShield Limited Edition que estaba configurado para instalar el complemento de VSTO, Visual Studio actualiza el proyecto, pero no efectúa más cambios en el proyecto. Si desea seguir usando un archivo de Windows Installer para implementar el complemento de VSTO, modifique el proyecto de instalación o InstallShield Limited Edition para instalar nuevos requisitos previos como [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools para Office Runtime y, opcionalmente, los ensamblados de interoperabilidad primarios a los que hace referencia el complemento de VSTO. Para obtener más información, consulta [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Si desea usar ClickOnce para implementar el complemento de VSTO, puede eliminar completamente el proyecto de instalación o InstallShield Limited Edition. Para obtener más información acerca de la implementación de complementos VSTO con ClickOnce, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Actualizar soluciones de Office](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)   
 [Migración de soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Actualización del proyecto, cuadro de diálogo Opciones](../vsto/project-upgrade-options-dialog-box.md)  
  
  