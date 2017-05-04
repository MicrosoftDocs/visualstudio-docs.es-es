---
title: "Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5 | Microsoft Docs"
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
  - "proyectos de Office [desarrollo de Office en Visual Studio], migrar a .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5
  Si se cambia el marco de trabajo de destino de un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior desde una versión anterior de .NET Framework, debe llevar a cabo las siguientes tareas para asegurarse de que la solución se puede ejecutar en el equipo de desarrollo y en los equipos de los usuarios finales:  
  
-   Quite <xref:System.Security.SecurityTransparentAttribute> del proyecto si lo actualizó desde Visual Studio 2008.  
  
-   Aplique un comando **Clean** en Visual Studio para poder ejecutar o depurar el proyecto en el equipo de desarrollo.  
  
-   Actualice el requisito previo de .NET Framework del proyecto.  
  
-   Los usuarios finales también deberán volver a instalar la solución si se implementó anteriormente mediante ClickOnce antes de cambiar el marco de trabajo de destino.  
  
 Para obtener más información sobre estas tareas, consulte las siguientes secciones.  
  
## Quitar el atributo SecurityTransparent de los proyectos que se actualizan desde Visual Studio 2008  
 Si actualiza un proyecto de Office desde Visual Studio 2008 y el marco de trabajo de destino del proyecto cambia posteriormente a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, deberá quitar <xref:System.Security.SecurityTransparentAttribute> del proyecto. Visual Studio no quita automáticamente este atributo. Si no quita este atributo, recibirá un mensaje de error al compilar el proyecto.  
  
 Para obtener más información sobre las condiciones en las que Visual Studio puede cambiar el marco de trabajo de destino de un proyecto actualizado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### Para quitar SecurityTransparentAttribute  
  
1.  Con el proyecto abierto en Visual Studio, abra el **Explorador de soluciones**.  
  
2.  En el nodo **Propiedades** \(para C\#\) o **Mi proyecto** \(para Visual Basic\), haga doble clic en el archivo de código AssemblyInfo para abrirlo en el Editor de código.  
  
    > [!NOTE]  
    >  Para ver el archivo de código AssemblyInfo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones**.  
  
3.  Busque <xref:System.Security.SecurityTransparentAttribute> y quítelo del archivo o márquelo como comentario.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## Ejecutar el comando Clean para depurar o ejecutar un proyecto en el equipo de desarrollo  
 Si se creó un proyecto de Office antes de cambiar el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, debe efectuar un comando **Clean** y volver a generar el proyecto tras cambiar el marco de trabajo de destino.  Si no se ejecuta el comando **Clean**, recibirá una <xref:System.Runtime.InteropServices.COMException> al intentar depurar o ejecutar el proyecto cuyo destino ha cambiado.  
  
 Para obtener más información sobre el comando **Clean**, consulte [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
## Actualizar los requisitos previos para la implementación  
 Cuando se redestina un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, también debe actualizar el requisito previo de .NET Framework correspondiente en el cuadro de diálogo **Requisitos previos**.  De lo contrario, el proyecto de implementación de ClickOnce o de InstallShield Limited Edition comprueba e instala una versión anterior de .NET Framework.  
  
 Para obtener más información sobre cómo actualizar los requisitos previos para la implementación en equipos de usuarios finales, consulte [Cómo: Instalar los requisitos previos en equipos de usuarios finales para ejecutar las soluciones de Office](http://msdn.microsoft.com/es-es/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## Reinstalar las soluciones en los equipos de los usuarios finales  
 Si usa ClickOnce para implementar una solución de Office que tiene como destino .NET Framework 3.5 y redestina el proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, los usuarios finales deberán desinstalar la solución y volver a instalarla después de volver a publicarla.  Si vuelve a publicar la solución cuyo destino ha cambiado y se actualiza la solución en los equipos de los usuarios finales, estos recibirán una <xref:System.Runtime.InteropServices.COMException> al ejecutar la solución actualizada.  
  
## Vea también  
 [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  