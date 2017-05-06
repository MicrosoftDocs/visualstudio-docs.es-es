---
title: "Actualizar y migrar soluciones de Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], actualizar"
  - "proyectos de Office [desarrollo de Office en Visual Studio], actualizar"
  - "actualizar aplicaciones [desarrollo de Office en Visual Studio]"
  - "actualizar soluciones de Office en Visual Studio"
  - "migrar soluciones de Office en Visual Studio"
ms.assetid: cc60cdcb-593d-498a-8358-f1f3ac673fe1
caps.latest.revision: 105
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 101
---
# Actualizar y migrar soluciones de Office
  Si tiene un proyecto de Microsoft Office que se creó en una versión anterior de Visual Studio, deberá actualizarlo para usarlo en las versiones actuales de Visual Studio. Para ello, ábralo en una versión de Visual Studio que incluya las herramientas de desarrollo de Microsoft Office. Para obtener más información sobre las versiones de Visual Studio que incluyen las herramientas de desarrollo de Microsoft Office, consulte [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Visual Studio no puede actualizar proyectos de plantilla de formulario de InfoPath creados con versiones anteriores de Visual Studio. Estos tipos de proyectos no se admiten en la versión actual de Visual Studio.  
  
## Cambios en los proyectos actualizados  
 Cuando se actualiza un proyecto de Microsoft Office, Visual Studio modifica el proyecto para tener como destino los elementos siguientes:  
  
-   Visual Studio 2010 Tools para Office Runtime. Para obtener más información, consulta [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Las referencias de ensamblado actual.  
  
-   Una versión de .NET Framework que es compatible con el tipo de proyecto \(solo al actualizar a Visual Studio 2013\).  
  
-   Una versión de Microsoft Office que es compatible con el tipo de proyecto \(solo al actualizar a Visual Studio 2013\).  
  
## Referencias de ensamblado  
 Visual Studio actualiza las siguientes referencias de ensamblado en el proyecto:  
  
-   Ensamblados de interoperabilidad primarios de Microsoft Office \(PIA\).  
  
-   Ensamblados en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obtener más información sobre estos ensamblados, vea [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Versiones nuevas o actualizadas de ensamblados dependientes.  
  
## .NET Framework de destino  
 Al actualizar un proyecto en Visual Studio 2013, Visual Studio modifica el proyecto para que su destino sea [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La versión de .NET Framework que será el destino del proyecto depende de la versión de Office que está instalada en el equipo. Si está instalado [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)], Visual Studio modifica el proyecto para que el destino sea [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. De lo contrario, Visual Studio modifica el proyecto para que el destino sea [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Es posible que deba realizar algunos pasos adicionales para ejecutar una solución con destino nuevo en equipos de desarrollo y de usuario final. Asimismo, si el proyecto usa determinadas características, quizá no se compile. Para obtener más información, consulta [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Si elige como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior en un proyecto de Office, puede usar algunas características que no están disponibles cuando el destino es .NET Framework 3.5. Para obtener más información, consulta [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
## Aplicación de destino de Office  
 Cuando se actualiza un proyecto de Office en Visual Studio 2013, Visual Studio modifica ese proyecto para destinarlo a una versión de Microsoft Office que sea compatible con el tipo de proyecto, por ejemplo, un proyecto de personalización de nivel de documento o un proyecto de complemento de VSTO.  
  
 Los proyectos de Office en Visual Studio 2013 pueden tener como destino aplicaciones de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Visual Studio modifica el proyecto para tener como destino la versión más reciente de Office que tenga instalada. Si no se instala ninguna de estas versiones de Office, Visual Studio no actualiza el proyecto.  
  
> [!NOTE]  
>  Si actualiza un proyecto de complemento de VSTO para destinarlo a [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o versiones posteriores, asegúrese de que el controlador de eventos `ThisAddIn_Startup` del complemento de VSTO no contenga código con acceso a un documento en la aplicación. Para obtener más información, consulta [Obtener acceso a un documento cuando se inicia la aplicación de Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Para las personalizaciones de nivel de documento, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] convierte los documentos de un proyecto que tienen un formato binario \(como los documentos con extensión .xls o .doc\>\) al formato Office Open XML. Para obtener más información sobre Open XML, vea [Introducción a las nuevas extensiones de nombre de archivo y formatos Open XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Las etiquetas inteligentes dejaron de usarse en Excel 2010 y Word 2010. Por lo tanto, si la solución usa etiquetas inteligentes, quítelas antes de probar y depurar en Visual Studio 2013 o Visual Studio 2015.  
  
## Actualizar proyectos de Microsoft Office 2003  
 Hay algunas consideraciones adicionales que se deben tener en cuenta a la hora de actualizar las personalizaciones de nivel de documento y los complementos de VSTO cuyo destino es Microsoft Office 2003.  
  
### Proyectos de nivel del documento  
 Si el documento del proyecto contiene controles de formularios Windows Forms, también se debe tener instalado Visual Studio 2005 Tools para Office Second Edition Runtime antes de actualizar el proyecto. Si esta versión del runtime no está instalada en el equipo de desarrollo antes de actualizar el proyecto, el proyecto actualizado podría contener errores en tiempo de compilación o ejecución. Cuando termine de actualizar el proyecto, puede desinstalar Visual Studio 2005 Tools para Office Second Edition Runtime en el equipo de desarrollo si no lo usa ninguna otra solución de Office. Esta versión del runtime está disponible como paquete redistribuible en el Centro de descarga de Microsoft en [Microsoft Visual Studio 2005 Tools para Office Second Edition Runtime \(VSTO 2005 SE\) \(x86\)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### Proyectos de complementos de VSTO  
 Si el archivo de solución del proyecto original incluía un proyecto de instalación o InstallShield Limited Edition que estaba configurado para instalar el complemento de VSTO, Visual Studio actualiza el proyecto, pero no efectúa más cambios en el proyecto. Si desea seguir usando un archivo de Windows Installer para implementar el complemento de VSTO, modifique el proyecto de instalación o InstallShield Limited Edition para instalar nuevos requisitos previos como [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools para Office Runtime y, opcionalmente, los ensamblados de interoperabilidad primarios a los que hace referencia el complemento de VSTO. Para obtener más información, consulta [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Si desea usar ClickOnce para implementar el complemento de VSTO, puede eliminar completamente el proyecto de instalación o InstallShield Limited Edition. Para obtener más información acerca de la implementación de complementos de VSTO con ClickOnce, vea [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Cómo: Actualizar soluciones de Office](http://msdn.microsoft.com/es-es/a269e539-b717-4680-a568-2152b070347e)   
 [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Actualización de proyecto, cuadro de diálogo Opciones](../vsto/project-upgrade-options-dialog-box.md)  
  
  