---
title: Identificadores de componente y carga de trabajo de Visual Studio Team Explorer 2017
description: Uso de identificadores de componente y carga de trabajo de Visual Studio para proporcionar herramientas de pruebas integradas para evaluadores generalistas
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: c6ef9a3b-d13d-49b4-9faa-51fa06b21e1f
ms.workload:
- multiple
ms.openlocfilehash: 57d34c8ea2c79c9d9444e553d37da353e4e3ece3
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607450"
---
# <a name="visual-studio-team-explorer-2017-component-directory"></a>Directorio de componentes de Visual Studio Team Explorer 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos o que puede especificar como una dependencia en un manifiesto VSIX. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo.
* Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Al establecer las dependencias del manifiesto de VSIX, debe especificar solo identificadores de componentes. Utilice las tablas de esta página para determinar las dependencias de componente mínimas. En algunos casos, esto podría significar que se especifique solo un componente de una carga de trabajo. En otros escenarios, puede significar que especifique varios componentes de una sola carga de trabajo o varios componentes de varias cargas de trabajo. Para obtener más información, consulte la página [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Migración de proyectos de extensibilidad a Visual Studio 2017).

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="visual-studio-core-editor-included-with-visual-studio-team-explorer-2017"></a>Editor de núcleo de Visual Studio (incluido con Visual Studio Team Explorer 2017)

**Id.:** Microsoft.VisualStudio.Workload.CoreEditor

**Descripción:** la experiencia del shell principal de Visual Studio, que incluye edición de código compatible con la sintaxis, control de código fuente y administración de elementos de trabajo.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor de núcleo de Visual Studio | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Página principal de Visual Studio para usuarios de C++ | 15.0.27128.1 | Optional

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | nombre | Versión
--- | --- | ---
N/D | N/D | N/D

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
