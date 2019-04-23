---
title: Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f24b86f51d658ea2f228f1e72d18394fcba4b47b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072824"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5
  Si se cambia la plataforma de destino de un proyecto de Office a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior desde una versión anterior de .NET Framework, debe realizar las siguientes tareas para asegurarse de que puede ejecutar la solución en el equipo de desarrollo y en los equipos del usuario final:

- Quite <xref:System.Security.SecurityTransparentAttribute> del proyecto si lo actualizó desde Visual Studio 2008.

- Realizar una **Clean** en Visual Studio para poder ejecutar o depurar el proyecto en el equipo de desarrollo.

- Actualice el requisito previo de .NET Framework del proyecto.

- Los usuarios finales también deberán volver a instalar la solución si se implementó anteriormente mediante ClickOnce antes de cambiar el marco de trabajo de destino.

  Para obtener más información sobre estas tareas, consulte las siguientes secciones.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Quitar el atributo SecurityTransparent de los proyectos que se actualizan desde Visual Studio 2008
 Si actualiza un proyecto de Office desde Visual Studio 2008 y la plataforma de destino del proyecto cambia posteriormente a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, deberá quitar <xref:System.Security.SecurityTransparentAttribute> del proyecto. Visual Studio no quita automáticamente este atributo. Si no quita este atributo, recibirá un mensaje de error al compilar el proyecto.

 Para obtener más información acerca de las condiciones en que Visual Studio puede cambiar la plataforma de destino de un proyecto actualizado a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Para quitar SecurityTransparentAttribute

1. Con el proyecto abierto en Visual Studio, abra el **Explorador de soluciones**.

2. En el nodo **Propiedades** (en C#) o **Mi proyecto** (en Visual Basic), haga doble clic en el archivo de código AssemblyInfo para abrirlo en el editor de código.

    > [!NOTE]
    >  Para ver el archivo de código AssemblyInfo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones** .

3. Busque <xref:System.Security.SecurityTransparentAttribute> y quítelo del archivo o márquelo como comentario.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Realizar el comando clean para depurar o ejecutar un proyecto en el equipo de desarrollo
 Si se creó un proyecto de Office antes de la plataforma de destino del proyecto se cambia a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe realizar una **Clean** comando y, a continuación, recompile el proyecto después de cambia la plataforma de destino. Si no lleva a cabo una **Clean** comando, recibirá un <xref:System.Runtime.InteropServices.COMException> al intentar depurar o ejecutar el proyecto cuyo destino ha cambiado.

 Para obtener más información sobre la **Clean** de comandos, consulte [soluciones de Office de compilación](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Actualizar los requisitos previos para la implementación
 Cuando se redestina un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, también debe actualizar el requisito previo de .NET Framework correspondiente en el **requisitos previos** cuadro de diálogo. De lo contrario, el proyecto de implementación de ClickOnce o de InstallShield Limited Edition comprueba e instala una versión anterior de .NET Framework.

 Para obtener más información acerca de cómo actualizar los requisitos previos para la implementación en equipos de usuario final, consulte [Cómo: Instalar requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

## <a name="reinstall-solutions-on-end-user-computers"></a>Volver a instalar las soluciones en equipos de usuario final
 Si usa ClickOnce para implementar una solución de Office que tiene como destino .NET Framework 3.5 y redestina el proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, los usuarios finales deberán desinstalar la solución y volver a instalarla después de volver a publicarla. Si vuelve a publicar la solución cuyo destino ha cambiado y se actualiza la solución en equipos de usuario final, los usuarios finales recibirán un <xref:System.Runtime.InteropServices.COMException> cuando ejecuta la solución actualizada.

## <a name="see-also"></a>Vea también
- [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
