---
title: Cambios necesarios para los proyectos de Office migrados a .NET Framework 4, 4,5
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
ms.openlocfilehash: 82ae3f8a43b65e6ff617192dc38149691d229455
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836058"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Cambios necesarios para ejecutar proyectos de Office que se migran al .NET Framework 4 o al .NET Framework 4,5
  Si el marco de trabajo de destino de un proyecto de Office se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores de una versión anterior de la .NET Framework, debe realizar las siguientes tareas para asegurarse de que la solución se puede ejecutar en el equipo de desarrollo y en los equipos de los usuarios finales:

- Quite <xref:System.Security.SecurityTransparentAttribute> del proyecto si lo actualizó desde Visual Studio 2008.

- Realice un comando **Clean** en Visual Studio para poder ejecutar o depurar el proyecto en el equipo de desarrollo.

- Actualice el requisito previo de .NET Framework del proyecto.

- Los usuarios finales también deberán volver a instalar la solución si se implementó anteriormente mediante ClickOnce antes de cambiar el marco de trabajo de destino.

  Para obtener más información sobre estas tareas, consulte las siguientes secciones.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Quitar el atributo SecurityTransparent de los proyectos que se actualizan desde Visual Studio 2008
 Si actualiza un proyecto de Office desde Visual Studio 2008 y la plataforma de destino del proyecto cambia posteriormente a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, deberá quitar <xref:System.Security.SecurityTransparentAttribute> del proyecto. Visual Studio no quita automáticamente este atributo. Si no quita este atributo, recibirá un mensaje de error al compilar el proyecto.

 Para obtener más información sobre las condiciones en las que Visual Studio puede cambiar el marco de trabajo de destino de un proyecto actualizado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , consulte [actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Para quitar SecurityTransparentAttribute

1. Con el proyecto abierto en Visual Studio, abra el **Explorador de soluciones**.

2. En el nodo **Propiedades** (en C#) o **Mi proyecto** (en Visual Basic), haga doble clic en el archivo de código AssemblyInfo para abrirlo en el editor de código.

    > [!NOTE]
    > Para ver el archivo de código AssemblyInfo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones** .

3. Busque <xref:System.Security.SecurityTransparentAttribute> y quítelo del archivo o márquelo como comentario.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Ejecutar el comando Clean para depurar o ejecutar un proyecto en el equipo de desarrollo
 Si se compiló un proyecto de Office antes de que el marco de trabajo de destino del proyecto se cambie a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe realizar un comando **Clean** y volver a compilar el proyecto después de cambiar la versión de .NET Framework de destino. Si no se realiza un comando **Clean** , recibirá una <xref:System.Runtime.InteropServices.COMException> al intentar depurar o ejecutar el proyecto redestinado.

 Para obtener más información sobre el comando **Clean** , vea [compilar soluciones de Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Actualizar los requisitos previos para la implementación
 Al redestinar un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, también debe actualizar los requisitos previos de .NET Framework correspondientes en el cuadro de diálogo **requisitos previos** . De lo contrario, el proyecto de implementación de ClickOnce o de InstallShield Limited Edition comprueba e instala una versión anterior de .NET Framework.

 Para obtener más información acerca de cómo actualizar los requisitos previos para la implementación en los equipos de los usuarios finales, consulte [Cómo: instalar los requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

## <a name="reinstall-solutions-on-end-user-computers"></a>Reinstalar soluciones en los equipos de los usuarios finales
 Si usa ClickOnce para implementar una solución de Office que tiene como destino .NET Framework 3.5 y redestina el proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, los usuarios finales deberán desinstalar la solución y volver a instalarla después de volver a publicarla. Si vuelve a publicar la solución redestinada y la solución se actualiza en los equipos de los usuarios finales, los usuarios finales recibirán una <xref:System.Runtime.InteropServices.COMException> cuando ejecuten la solución actualizada.

## <a name="see-also"></a>Consulte también
- [Migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
