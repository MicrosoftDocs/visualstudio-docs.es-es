---
title: Identificadores de componente y carga de trabajo de Visual Studio Test Agent 2017 | Microsoft Docs
description: Uso de identificadores de componente y carga de trabajo de Visual Studio para ejecutar pruebas automatizadas y pruebas de carga de manera remota
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: 55aea29b-1066-4e5a-aa99-fc87d4efb6d5
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: 78a656f32068055326567223b8ce6cd68095e647
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---

# <a name="visual-studio-test-agent-2017-component-directory"></a>Directorio de componentes de Visual Studio Test Agent 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo. Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="test-agent"></a>Test Agent

**Id.:** Microsoft.VisualStudio.Workload.TestAgent

**Descripción:** admite la ejecución de pruebas automatizadas y la carga de pruebas de manera remota

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestAgent | Características principales de Test Agent | 15.0.26606.0 | Obligatorio

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | Nombre | Versión
--- | --- | ---
no disponible | no disponible | no disponible


## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)

