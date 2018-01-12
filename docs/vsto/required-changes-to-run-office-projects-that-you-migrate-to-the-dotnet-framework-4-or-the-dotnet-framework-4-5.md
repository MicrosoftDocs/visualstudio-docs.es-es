---
title: Los cambios requeridos para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5 | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ee90d5c205f58736f7ccb6536e29b2fd6d16b152
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5
  Si se cambia la plataforma de destino de un proyecto de Office a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior desde una versión anterior de .NET Framework, debe realizar las siguientes tareas para asegurarse de que la solución se puede ejecutar en el equipo de desarrollo y en equipos de usuarios finales:  
  
-   Quite <xref:System.Security.SecurityTransparentAttribute> del proyecto si lo actualizó desde Visual Studio 2008.  
  
-   Realizar una **limpiar** comando en Visual Studio para que pueda ejecutar o depurar el proyecto en el equipo de desarrollo.  
  
-   Actualice el requisito previo de .NET Framework del proyecto.  
  
-   Los usuarios finales también deberán volver a instalar la solución si se implementó anteriormente mediante ClickOnce antes de cambiar el marco de trabajo de destino.  
  
 Para obtener más información sobre estas tareas, consulte las siguientes secciones.  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Quitar el atributo SecurityTransparent de los proyectos que se actualizan desde Visual Studio 2008  
 Si actualiza un proyecto de Office desde Visual Studio 2008 y el marco de trabajo de destino del proyecto cambia posteriormente a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, deberá quitar <xref:System.Security.SecurityTransparentAttribute> del proyecto. Visual Studio no quita automáticamente este atributo. Si no quita este atributo, recibirá un mensaje de error al compilar el proyecto.  
  
 Para obtener más información acerca de las condiciones en que Visual Studio puede cambiar la plataforma de destino de un proyecto actualizado a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Para quitar SecurityTransparentAttribute  
  
1.  Con el proyecto abierto en Visual Studio, abra el **Explorador de soluciones**.  
  
2.  En el nodo **Propiedades** (en C#) o **Mi proyecto** (en Visual Basic), haga doble clic en el archivo de código AssemblyInfo para abrirlo en el editor de código.  
  
    > [!NOTE]  
    >  Para ver el archivo de código AssemblyInfo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones** .  
  
3.  Busque <xref:System.Security.SecurityTransparentAttribute> y quítelo del archivo o márquelo como comentario.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Ejecutar el comando Clean para depurar o ejecutar un proyecto en el equipo de desarrollo  
 Si se creó un proyecto de Office antes de que se cambia la plataforma de destino del proyecto a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe realizar una **limpiar** comando y, a continuación, volver a generar el proyecto después de cambia la plataforma de destino. Si no tienen que realizar un **limpiar** comando, recibirá un <xref:System.Runtime.InteropServices.COMException> al intentar depurar o ejecutar el proyecto cuyo destino ha cambiado.  
  
 Para obtener más información sobre la **limpiar** command, consulte [compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
## <a name="updating-the-prerequisites-for-deployment"></a>Actualizar los requisitos previos para la implementación  
 Cuando se redestina un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, también debe actualizar el requisito previo de .NET Framework correspondiente en el **requisitos previos** cuadro de diálogo. De lo contrario, el proyecto de implementación de ClickOnce o de InstallShield Limited Edition comprueba e instala una versión anterior de .NET Framework.  
  
 Para obtener más información acerca de cómo actualizar los requisitos previos para la implementación en equipos de usuario final, consulte [Cómo: instalar los requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>Reinstalar las soluciones en los equipos de los usuarios finales  
 Si usa ClickOnce para implementar una solución de Office que tiene como destino .NET Framework 3.5 y redestina el proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, los usuarios finales deberán desinstalar la solución y volver a instalarla después de volver a publicarla. Si vuelve a publicar la solución cuyo destino ha cambiado y se actualiza la solución en los equipos de los usuarios finales, estos recibirán una <xref:System.Runtime.InteropServices.COMException> al ejecutar la solución actualizada.  
  
## <a name="see-also"></a>Vea también  
 [Migración de soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  