---
title: 'Cómo: buscar el nombre del proceso ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685956"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Cómo: Buscar el nombre de un proceso de ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para establecer una asociación a una aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que se está ejecutando, es preciso conocer el nombre del proceso [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
- Si está ejecutando IIS 6.0 o IIS 7.0, el nombre es w3wp.exe.  
  
- Si está ejecutando una versión anterior de IIS, el nombre es aspnet_wp.exe.  
  
  En el caso de las aplicaciones compiladas con [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] o versiones posteriores, el [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] código puede residir en el sistema de archivos y ejecutarse en el servidor de prueba WebDev.WebServer.exe. En ese caso, debe establecer una asociación a WebDev.WebServer.exe en lugar de al proceso [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Este escenario sólo se aplica a la depuración local.  
  
  Las aplicaciones ASP anteriores se ejecutan dentro del proceso de IIS inetinfo.exe cuando se ejecutan en proceso.  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Para determinar si el código de proyecto reside en el sistema de archivos o en IIS  
  
1. En Visual Studio, Abra **Explorador de soluciones** si aún no está abierto.  
  
2. Seleccione el nodo superior que contiene el nombre de la aplicación.  
  
3. Si el título de la ventana **propiedades** contiene una ruta de acceso de archivo, el código de la aplicación reside en el sistema de archivos.  
  
     De lo contrario, el título de la ventana **propiedades** contendrá el nombre del sitio Web.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Para determinar la versión de IIS en la que se está ejecutando la aplicación  
  
1. Busque **herramientas administrativas** y ejecútela. En función del sistema operativo, podría tratarse de un icono dentro del **Panel de control**o de una entrada de menú que aparece al hacer clic en **iniciar**.  
  
     En Windows XP, el **Panel de control** puede estar en la vista por categorías o en la vista clásica. En la vista por categorías, tiene que hacer clic en **cambiar a vista clásica** o en **rendimiento y mantenimiento** para ver el icono **herramientas administrativas** .  
  
2. En **herramientas administrativas**, ejecute Internet Information Services. Aparecerá un cuadro de diálogo de MMC.  
  
3. Si hay más de un equipo en el panel izquierdo, seleccione el equipo donde resida el código de la aplicación.  
  
4. La versión de IIS está en la columna **versión** del panel derecho.  
  
## <a name="see-also"></a>Consulte también  
 [Requisitos previos para la depuración remota de aplicaciones Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Preparación de la depuración de ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)
