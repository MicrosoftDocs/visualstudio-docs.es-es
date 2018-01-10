---
title: Identificadores de componente y carga de trabajo de Visual Studio Test Controller 2017 | Microsoft Docs
description: "Uso de identificadores de componente y carga de trabajo de Visual Studio para distribuir pruebas automatizadas en varias máquinas"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 12/1/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: fbbda9c8-d2c6-474d-b52d-a95227d52fe7
ms.workload: multiple
ms.openlocfilehash: e3a45c67e3104f6f01c509c379e49dbe1c07a0c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-test-controller-2017-component-directory"></a>Directorio de componentes de Visual Studio Test Controller 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo. Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="test-controller"></a>Test Controller

**Id.:** Microsoft.VisualStudio.Workload.TestController

**Descripción:** distribuya las pruebas automatizadas en varias máquinas

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestController | Características principales de Test Controller | 15.0.27128.1 | Obligatorio

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | nombre | Versión
--- | --- | ---
N/D | N/D | N/D

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
