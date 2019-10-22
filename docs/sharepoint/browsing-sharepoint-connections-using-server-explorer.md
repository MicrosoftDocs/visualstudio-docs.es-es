---
title: Examinar las conexiones de SharePoint mediante el Explorador de servidores | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8dfde37125b78e2ff8077712321b3a19816582cf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387805"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Examinar las conexiones de SharePoint mediante el Explorador de servidores
  Ahora puede examinar las conexiones locales de SharePoint en **Explorador de servidores**. Mediante esta técnica, puede navegar a través de los componentes de un sitio de SharePoint en el sistema. Componentes de sitio de SharePoint, como las definiciones de lista y tipos de contenido aparecen en un nodo que se denomina **conexiones de SharePoint** en la vista de árbol de **Explorador de servidores**. Para mostrar **Explorador de servidores**, en la barra de menús, elija **vista** > **Explorador de servidores**. Además de mostrar los componentes de sitio de SharePoint, puede quitar elementos, ver sus propiedades o actualizar la vista de árbol mediante comandos en el menú contextual.

> [!IMPORTANT]
> Para examinar un sitio de SharePoint, debe ser un administrador de la colección de sitios de SharePoint, y debe ejecutar Visual Studio como administrador del equipo local. En caso contrario, el sitio aparece en **Explorador de servidores**, pero no se puede expandir el nodo. Para comprobar si es administrador de la colección de sitios, abra el sitio en un explorador web, abrirlo el **acciones del sitio** menú, elija **los permisos de sitio**y, a continuación, en el **permisos: Sitio del equipo** página, elija el **Site Collection Administrators** comando desde el **administrar** grupo en la cinta de opciones. El nombre aparecerá en el cuadro de texto si es un administrador de colección de sitios. Si el **Site Collection Administrators** comando no aparece en el grupo de administración en la cinta de opciones, no es un administrador de la colección de sitios y debe obtener los permisos adecuados al administrador del sitio.

## <a name="server-explorer-nodes"></a>Nodos del explorador de servidores
 Todos los componentes de un sitio de SharePoint están representado por un nodo en el **Explorador de servidores** en la vista de árbol **conexiones de SharePoint**. Por ejemplo, los sitios de SharePoint predeterminada incluyen un tipo de contenido denominado discusión, que representa un tipo de análisis que se muestra en el **discusiones** página del sitio de SharePoint. El tipo de contenido contiene varios campos. Para ver estos campos en **Explorador de servidores**, expanda el **ContentTypes** nodo y, a continuación, el **discusión** nodo. En existen varios nodos de campo, como cuerpo, asunto de discusión y título.

## <a name="node-shortcut-menu-commands"></a>Comandos del menú contextual del nodo
 Cada nodo tiene un menú contextual que tener acceso haciendo clic en el nodo o seleccionarlo y, a continuación, elegir el **MAYÚS**+**F10** claves. Comandos de nodo pueden incluir lo siguiente:

|Nombre de comando|Descripción|
|------------------|-----------------|
|Refresh|Actualiza la vista de árbol para reflejar cualquier cambio que puedan haberse producido desde la última vez que se mostró el nodo.|
|Eliminar|Quita el nodo seleccionado de la vista de árbol. **Nota:**  Este comando está habilitado en las conexiones de SharePoint que aparece en el **conexiones de SharePoint** nodo.|
|Propiedades|Muestra las propiedades disponibles para el nodo seleccionado en el **propiedades** ventana. Las propiedades son todas de solo lectura y no todos los nodos tienen propiedades asociadas con él.|
|Agregar conexión|Le permite especificar un sitio de SharePoint que desea examinar. Disponible en el **conexiones de SharePoint** nodo y los nodos secundarios del sitio.|
|Ver en el explorador|Muestra la lista seleccionada en el explorador Web. Este comando está disponible en algunas listas bajo el **enumera** nodo que se encuentra en **listas y bibliotecas**.|

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Cómo: Agregar o quitar conexiones de SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Describe los pasos necesarios para agregar un nuevo sitio de SharePoint para el **conexiones de SharePoint** nodo **Explorador de servidores**.|

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
