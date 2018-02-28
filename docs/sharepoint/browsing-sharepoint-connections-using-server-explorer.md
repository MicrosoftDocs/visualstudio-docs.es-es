---
title: Examinar las conexiones de SharePoint mediante el Explorador de servidores | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 5ea474f2439b6da519563f08ffe4ddc2f6dcef30
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>Examinar las conexiones de SharePoint utilizando el Explorador de servidores
  Ahora puede examinar las conexiones locales de SharePoint en **Explorador de servidores**. Mediante esta técnica, puede navegar por los componentes de un sitio de SharePoint en el sistema. Componentes de sitio de SharePoint, como las definiciones de lista y tipos de contenido aparecen en un nodo que se denomina **las conexiones de SharePoint** en la vista de árbol de **Explorador de servidores**. Para mostrar **Explorador de servidores**, en la barra de menús, elija **vista**, **Explorador de servidores**. Además de mostrar los componentes de sitio de SharePoint, puede quitar elementos, ver sus propiedades o actualizar la vista de árbol mediante comandos en el menú contextual.  
  
> [!IMPORTANT]  
>  Para examinar un sitio de SharePoint, debe ser un administrador de la colección de sitios de SharePoint y debe estar ejecutando Visual Studio como administrador del equipo local. En caso contrario, el sitio aparece en **Explorador de servidores**, pero no se puede expandir su nodo. Para comprobar si es un administrador de la colección de sitios, abra el sitio en un explorador web, abra el **acciones del sitio** menú, elija **permisos de sitio**y, a continuación, en la **permisos: equipo Sitio** página, elija la **Site Collection Administrators** línea de comandos desde el **administrar** grupo en la cinta de opciones. El nombre aparecerá en el cuadro de texto si es un administrador de colección de sitios. Si el **Site Collection Administrators** comando no aparece en el grupo de administrar en la cinta de opciones, no es un administrador de la colección de sitios y debe obtener los permisos adecuados del administrador del sitio.  
  
## <a name="server-explorer-nodes"></a>Nodos del explorador de servidores  
 Cada componente de un sitio de SharePoint se representa mediante un nodo en el **Explorador de servidores** en la vista de árbol **las conexiones de SharePoint**. Por ejemplo, sitios de SharePoint predeterminados incluyen un tipo de contenido denominado discusión, que representa un tipo de análisis que se muestra en el **discusiones** página del sitio de SharePoint. El tipo de contenido de discusión contiene varios campos. Para ver estos campos en **Explorador de servidores**, expanda la **tipos de contenido** nodo y, a continuación, el **discusión** nodo. En son varios nodos de campo, como el título, el asunto de discusión y cuerpo.  
  
## <a name="node-shortcut-menu-commands"></a>Comandos de menú contextual de nodo  
 Cada nodo tiene un menú contextual que tener acceso haciendo clic en el nodo o seleccionarlo y, a continuación, elija las teclas MAYÚS + F10. Los comandos de nodo pueden incluir lo siguiente:  
  
|Nombre de comando|Descripción|  
|------------------|-----------------|  
|Refresh|Actualiza la vista de árbol para reflejar los cambios que se hayan producido desde la última vez que se mostró el nodo.|  
|Eliminar|Quita el nodo seleccionado de la vista de árbol. **Nota:** este comando sólo está habilitado en las conexiones de SharePoint que aparecen en la **las conexiones de SharePoint** nodo.|  
|Propiedades|Muestra las propiedades disponibles para el nodo seleccionado en el **propiedades** ventana. Las propiedades son todas de sólo lectura y no todos los nodos tienen propiedades asociadas a él.|  
|Agregar conexión|Permite especificar un sitio de SharePoint que desea examinar. Disponible en la **las conexiones de SharePoint** nodo y los nodos secundarios del sitio.|  
|Ver en el explorador|Muestra la lista seleccionada en el explorador Web. Este comando está disponible en algunas listas bajo el **enumera** nodo que se encuentra en **listas y bibliotecas**.|  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Agregar o quitar conexiones de SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Describe los pasos necesarios para agregar un nuevo sitio de SharePoint para el **las conexiones de SharePoint** nodo **Explorador de servidores**.|  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  