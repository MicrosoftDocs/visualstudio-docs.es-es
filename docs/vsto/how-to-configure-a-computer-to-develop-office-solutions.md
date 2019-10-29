---
title: 'Cómo: configurar un equipo para desarrollar soluciones de Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb29dc4151bc457eb60ce836986817bc1b0137c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985963"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Cómo: configurar un equipo para desarrollar soluciones de Office
  Para configurar un equipo de desarrollo de modo que puede usar las herramientas de desarrollo de Microsoft Office en Visual Studio, siga las instrucciones de este tema. Debe tener privilegios administrativos en el equipo de desarrollo para seguir estos pasos.

### <a name="to-configure-the-development-computer"></a>Para configurar el equipo de desarrollo

1. Instala una versión de Visual Studio que incluye las herramientas para desarrolladores de Office. Office Developer Tools se instala de forma predeterminada. Si personaliza la instalación de Visual Studio seleccionando las características que se van a instalar, asegúrese de que **Microsoft Office herramientas de desarrollo** esté seleccionado durante la instalación. Para obtener más información sobre las versiones de Visual Studio que incluyen las herramientas de desarrollo de Office, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Instale una versión de Office que sea compatible con Office Developer Tools en Visual Studio. Para obtener más información, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Asegúrese de instalar también los PIA para la versión de Office que instale. De forma predeterminada, los PIA se instalan con Office. Si modifica la instalación de Office, asegúrese de que la característica **compatibilidad con programación de .net** esté seleccionada para las aplicaciones a las que desea dirigirse.

3. Si tiene una versión en Inglés de Visual Studio pero usa una configuración distinta del inglés para Windows, puede instalar el paquete de idioma de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para ver [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mensajes en el mismo idioma que Windows. Las versiones de Visual Studio en otros idiomas instalan automáticamente el paquete de idioma. El paquete de idioma está disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Vea también

- [Introducción &#40;al desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Cómo: instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
