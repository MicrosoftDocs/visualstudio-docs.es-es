---
title: Examinar las conexiones de SharePoint mediante Explorador de servidores | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016345"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Examinar las conexiones de SharePoint mediante Explorador de servidores
  Ahora puede examinar las conexiones de SharePoint locales en **Explorador de servidores**. Mediante esta técnica, puede navegar por los componentes de un sitio de SharePoint en el sistema. Los componentes del sitio de SharePoint, como las definiciones de lista y los tipos de contenido, aparecen en un nodo denominado **conexiones de SharePoint** en la vista de árbol de **Explorador de servidores**. Para mostrar **Explorador de servidores**, en la barra de menús, elija **Ver**  >  **Explorador de servidores**. Además de mostrar los componentes del sitio de SharePoint, puede quitar elementos, ver sus propiedades o actualizar la vista de árbol mediante los comandos del menú contextual.

> [!IMPORTANT]
> Para examinar un sitio de SharePoint, debe ser administrador de la colección de sitios de SharePoint y debe ejecutar Visual Studio como administrador del equipo local. De lo contrario, el sitio aparece en **Explorador de servidores**, pero no puede expandir su nodo. Para comprobar si es administrador de la colección de sitios, abra el sitio en un explorador Web, abra el menú **acciones del sitio** , elija **permisos del sitio**y, a continuación, en la página **permisos: sitio de grupo** , elija el comando administradores de la colección de **sitios** en el grupo **administrar** de la cinta de opciones. Su nombre aparecerá en el cuadro de texto si es administrador de la colección de sitios. Si el comando administradores de la **colección de sitios** no aparece en el grupo administrar de la cinta de opciones, no es administrador de la colección de sitios y debe obtener los permisos adecuados del administrador del sitio.

## <a name="server-explorer-nodes"></a>Explorador de servidores nodos
 Cada componente de un sitio de SharePoint se representa mediante un nodo en la vista de árbol **Explorador de servidores** en **conexiones de SharePoint**. Por ejemplo, los sitios predeterminados de SharePoint incluyen un tipo de contenido denominado Discussion, que representa un tipo de discusión que se muestra en la página **discusiones** del sitio de SharePoint. El tipo de contenido de discusión contiene varios campos. Para ver estos campos en **Explorador de servidores**, expanda el nodo **contentTypes** y, a continuación, el nodo **discusión** . En, hay varios nodos de campo, como cuerpo, asunto de discusión y título.

## <a name="node-shortcut-menu-commands"></a>Comandos del menú contextual de nodo
 Cada nodo tiene un menú contextual al que se tiene acceso haciendo clic con el botón secundario en el nodo, eligiendo y eligiendo las teclas **MAYÚS** + **F10** . Los comandos de nodo pueden incluir lo siguiente:

|Nombre de comando|Descripción|
|------------------|-----------------|
|Actualizar|Actualiza la vista de árbol para reflejar cualquier cambio que se haya producido desde la última vez que se mostró el nodo.|
|Eliminar|Quita el nodo seleccionado de la vista de árbol. **Nota:**  Este comando solo está habilitado en las conexiones de SharePoint que aparecen en el nodo **conexiones de SharePoint** .|
|Propiedades|Muestra las propiedades disponibles para el nodo seleccionado en la ventana **propiedades** . Todas las propiedades son de solo lectura y no todos los nodos tienen propiedades asociadas.|
|Agregar conexión|Permite especificar un sitio de SharePoint que desea examinar. Está disponible en el nodo **conexiones de SharePoint** y nodos secundarios.|
|Ver en el explorador|Muestra la lista seleccionada en el explorador Web. Este comando está disponible en algunas listas en el nodo **listas** que se encuentra en las **listas y bibliotecas**.|

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: agregar o quitar conexiones de SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Describe los pasos necesarios para agregar un nuevo sitio de SharePoint al nodo **conexiones de SharePoint** en **Explorador de servidores**.|

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
