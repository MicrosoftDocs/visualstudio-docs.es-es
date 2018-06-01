---
title: Compilar y depurar soluciones de SharePoint | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e04f60ea5cfe72235bac6630b413c9c437255681
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691292"
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Compilar y depurar soluciones de SharePoint
  En general, compilar y depurar soluciones de SharePoint es el mismo que compilar y depurar otros tipos de proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Los temas de esta sección explican las diferencias que existen entre ellos.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Resultado del proyecto para soluciones de SharePoint
 Compilar soluciones de SharePoint crea un archivo de solución (.wsp) de paquete y ensamblados. La siguiente tabla muestra las ubicaciones de estos archivos durante una compilación.  
  
|Elemento de compilación|Carpeta de salida|  
|----------------|-------------------|  
|Ensamblado, base de datos de programa (PDB) y archivos .wsp.|*ProjectName*\bin\debug o *ProjectName*\bin\release|  
|Archivos de elementos de proyecto de SharePoint.|*ProjectName*\pkg\debug o *ProjectName*\pkg\release|  
|Compilar los archivos intermedios.|*ProjectName*\obj\debug o *ProjectName*\obj\release|  
|Archivos intermedios de paquete.|*ProjectName*\pkgobj\debug o *ProjectName*\pkgobj\release|  
  
## <a name="build-sharepoint-solutions"></a>Compilar soluciones de SharePoint
 Para compilar soluciones de SharePoint, el equipo de desarrollo debe tener la versión correcta del servidor de SharePoint instalado. En caso contrario, compilar soluciones de SharePoint es el mismo que la creación de otros tipos de proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [Cómo: compilar soluciones de SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Depurar y probar soluciones de SharePoint
 Antes de depurar, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia el paquete .wsp en el servidor de SharePoint, activa el sitio y las características de los ámbitos de Web y, en algunos casos, se inicia el proyecto. En otros casos, tendrá que abrir el proyecto manualmente. Para obtener más información, consulte [solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) y [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Depurar y comprobar las soluciones de SharePoint mediante el uso de características de ALM
 Las características de Visual Studio ALM, como pruebas unitarias y IntelliTrace permiten más problemas identificar con exactitud con precisión en las soluciones de SharePoint. Generación de perfiles le permite ubicar e identificar áreas de problema de rendimiento en las soluciones de SharePoint. Para obtener más información, consulte [comprobar y depurar código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) y [generación de perfiles de rendimiento de aplicaciones de SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Seguridad durante el proceso de compilación
 Para empaquetar o implementar soluciones de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debe tener el permiso para copiar archivos en el servidor de SharePoint. Debe ejecutar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como un proceso con privilegios elevados y es el usuario de cuenta debe ser un administrador de colecciones de sitio en el servidor de SharePoint. Además, debe especificar si el proyecto es una solución en espacio aislado o una solución de granja de servidores. Para obtener más información, consulte [diferencias entre en un espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Usar el comando Limpiar  
 Cuando una solución de SharePoint se instala en un servidor de SharePoint para la depuración, el **limpiar** comando desinstalar la solución. En su lugar, debe desactivar las características a través de la configuración de SharePoint.  
  
## <a name="see-also"></a>Vea también
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Examinar las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 