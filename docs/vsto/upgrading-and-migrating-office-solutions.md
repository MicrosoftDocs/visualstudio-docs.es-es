---
title: Actualizar y migrar soluciones de Office
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416541"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Actualizar y migrar soluciones de Office
  Si tiene un proyecto de Microsoft Office que se creó en una versión anterior de Visual Studio, deberá actualizarlo para usarlo en las versiones actuales de Visual Studio. Para ello, ábralo en una versión de Visual Studio que incluya las herramientas de desarrollo de Microsoft Office. Para obtener más información sobre las versiones de Visual Studio que incluyen las herramientas de desarrollo de Microsoft Office, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio no puede actualizar proyectos de plantilla de formulario de InfoPath creados con versiones anteriores de Visual Studio. Estos tipos de proyectos no se admiten en la versión actual de Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Cambios en los proyectos actualizados
 Cuando se actualiza un proyecto de Microsoft Office, Visual Studio modifica el proyecto para tener como destino los elementos siguientes:

- Visual Studio 2010 Tools para Office Runtime. Para obtener más información, vea [información general de Visual Studio Tools para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Las referencias de ensamblado actual.

- Una versión de .NET Framework que es compatible con el tipo de proyecto (solo al actualizar a Visual Studio 2013).

- Una versión de Microsoft Office que es compatible con el tipo de proyecto (solo al actualizar a Visual Studio 2013).

## <a name="assembly-references"></a>Referencias de ensamblado
 Visual Studio actualiza las siguientes referencias de ensamblado en el proyecto:

- Ensamblados de interoperabilidad primarios de Microsoft Office (PIA).

- Ensamblados en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obtener más información sobre estos ensamblados, vea [información general de Visual Studio Tools para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Versiones nuevas o actualizadas de ensamblados dependientes.

## <a name="targeted-net-framework"></a>.NET Framework de destino
 Al actualizar un proyecto en Visual Studio 2013, Visual Studio modifica el proyecto para que su destino sea [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La versión de .NET Framework que será el destino del proyecto depende de la versión de Office que está instalada en el equipo. Si está instalado [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , Visual Studio modifica el proyecto para que el destino sea [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. De lo contrario, Visual Studio modifica el proyecto para que el destino sea [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

> [!NOTE]
> Es posible que deba realizar algunos pasos adicionales para ejecutar una solución con destino nuevo en equipos de desarrollo y de usuario final. Asimismo, si el proyecto usa determinadas características, quizá no se compile. Para obtener más información, vea [migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Si elige como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior en un proyecto de Office, puede usar algunas características que no están disponibles cuando el destino es .NET Framework 3.5. Para obtener más información, vea [diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Aplicación de Office de destino
 Cuando se actualiza un proyecto de Office en Visual Studio 2013, Visual Studio modifica ese proyecto para destinarlo a una versión de Microsoft Office que sea compatible con el tipo de proyecto, por ejemplo, un proyecto de personalización de nivel de documento o un proyecto de complemento de VSTO.

 Los proyectos de Office en Visual Studio 2013 pueden tener como destino aplicaciones de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Visual Studio modifica el proyecto para tener como destino la versión más reciente de Office que tenga instalada. Si no se instala ninguna de estas versiones de Office, Visual Studio no actualiza el proyecto.

> [!NOTE]
> Si actualiza un proyecto de complemento de VSTO para que tenga como destino [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o posterior, asegúrese de que el `ThisAddIn_Startup` controlador de eventos del complemento de VSTO no contenga código que tenga acceso a un documento de la aplicación. Para obtener más información, vea [acceso a un documento cuando se inicia la aplicación de Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 En el caso de las personalizaciones de nivel de documento, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] convierte los documentos de un proyecto que tienen un formato binario, como los documentos que tienen una extensión *. xls* o *. doc* , en el formato XML abierto de Office. Para obtener más información sobre Open XML, vea [Introducción a las nuevas extensiones de nombre de archivo y formatos XML abiertos](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Las etiquetas inteligentes dejaron de usarse en Excel 2010 y Word 2010. Por lo tanto, si la solución usa etiquetas inteligentes, quítelas antes de probar y depurar en Visual Studio 2013 o Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Actualización de proyectos de Microsoft Office 2003
 Hay algunas consideraciones adicionales que se deben tener en cuenta a la hora de actualizar las personalizaciones de nivel de documento y los complementos de VSTO cuyo destino es Microsoft Office 2003.

### <a name="document-level-projects"></a>Proyectos de nivel de documento
 Si el documento del proyecto contiene controles de formularios Windows Forms, también se debe tener instalado Visual Studio 2005 Tools para Office Second Edition Runtime antes de actualizar el proyecto. Si esta versión del runtime no está instalada en el equipo de desarrollo antes de actualizar el proyecto, el proyecto actualizado podría contener errores en tiempo de compilación o ejecución. Cuando termine de actualizar el proyecto, puede desinstalar Visual Studio 2005 Tools para Office Second Edition Runtime en el equipo de desarrollo si no lo usa ninguna otra solución de Office. Esta versión del runtime está disponible como paquete redistribuible en el Centro de descarga de Microsoft en [Microsoft Visual Studio 2005 Tools para Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Proyectos de complemento de VSTO
 Si el archivo de solución del proyecto original incluía un proyecto de instalación o InstallShield Limited Edition que estaba configurado para instalar el complemento de VSTO, Visual Studio actualiza el proyecto, pero no efectúa más cambios en el proyecto. Si desea seguir usando un archivo de Windows Installer para implementar el complemento de VSTO, modifique el proyecto de instalación o InstallShield Limited Edition para instalar nuevos requisitos previos como [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools para Office Runtime y, opcionalmente, los ensamblados de interoperabilidad primarios a los que hace referencia el complemento de VSTO. Para obtener más información, vea [implementar una solución de Office mediante Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Si desea usar ClickOnce para implementar el complemento de VSTO, puede eliminar completamente el proyecto de instalación o InstallShield Limited Edition. Para obtener más información sobre la implementación de complementos de VSTO mediante ClickOnce, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Consulte también
- [Cómo: actualizar soluciones de Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Actualización de proyecto, cuadro de diálogo Opciones](../vsto/project-upgrade-options-dialog-box.md)
