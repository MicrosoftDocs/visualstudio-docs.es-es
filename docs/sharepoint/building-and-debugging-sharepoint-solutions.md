---
title: Compilar y depurar soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1cdcf71821bd0f7e9739bc194834500c2dfc6fd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871568"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Compilar y depurar soluciones de SharePoint
  En general, compilar y depurar soluciones de SharePoint es el mismo que compilar y depurar otros tipos de proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Los temas de esta sección explican las diferencias que existen entre ellos.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Resultado del proyecto para soluciones de SharePoint
 Creación de soluciones de SharePoint crea ensamblados y un paquete de solución (*.wsp*) archivo. La siguiente tabla muestra las ubicaciones de estos archivos durante una compilación.  
  
|Crear elemento|Carpeta de salida|  
|----------------|-------------------|  
|Ensamblado, la base de datos de programa (*.pdb*), y *.wsp* archivos.|*\<NombreDeProyecto > \bin\debug* o  *\<NombreDelProyecto > \bin\release*|  
|Archivos de elementos de proyecto de SharePoint.|*\<ProjectName > \pkg\debug* o  *\<NombreDelProyecto > \pkg\release*|  
|Compilar los archivos intermedios.|*\<ProjectName > \obj\debug* o  *\<NombreDelProyecto > \obj\release*|  
|Archivos intermedios del paquete.|*\<ProjectName > \pkgobj\debug* o  *\<NombreDelProyecto > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Compilar soluciones de SharePoint
 Para compilar soluciones de SharePoint, el equipo de desarrollo debe tener la versión correcta del servidor de SharePoint instalado. En caso contrario, la creación de soluciones de SharePoint es el mismo que crear otros tipos de proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, vea [Cómo: Compilar soluciones de SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Depurar y probar soluciones de SharePoint
 Antes de depurar, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copias el *.wsp* paquete al servidor de SharePoint, activa el sitio y las características de ámbito Web y, en algunos casos, se inicia el proyecto. En otros casos, es posible que deba abrir manualmente el proyecto. Para obtener más información, consulte [soluciones de SharePoint de la solución de problemas de](../sharepoint/troubleshooting-sharepoint-solutions.md) y [soluciones de SharePoint depurar](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Depurar y comprobar las soluciones de SharePoint mediante el uso de características de los servicios de Azure DevOps
 Características de servicios de DevOps Azure como las pruebas unitarias y IntelliTrace le permiten con más problemas localizar con exactitud de las soluciones de SharePoint. Generación de perfiles le permite localizar e identificar las áreas de problema de rendimiento en las soluciones de SharePoint. Para obtener más información, consulte [comprobar y depurar código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) y [generación de perfiles de rendimiento de aplicaciones de SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Seguridad durante el proceso de compilación
 Para empaquetar o implementar soluciones de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debe tener permiso para copiar archivos en el servidor de SharePoint. Debe ejecutar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como un proceso elevado y el usuario de cuenta debe ser un administrador de colecciones de sitio en el servidor de SharePoint. Además, debe especificar si el proyecto es una solución en espacio aislado o una solución de granja de servidores. Para obtener más información, consulte [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Usar el comando Limpiar  
 Cuando una solución de SharePoint se instala en un servidor de SharePoint para la depuración, la **Clean** comando desinstala la solución. En su lugar, debe desactivar las características a través de la configuración de SharePoint.  
  
## <a name="see-also"></a>Vea también
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Examinar las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
